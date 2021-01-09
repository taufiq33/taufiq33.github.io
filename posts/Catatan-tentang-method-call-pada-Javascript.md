# Method call pada Function Javascript.

Di Javascript _function_ adalah _instance_ dari Objek _Function_ .
ketika membuat fungsi dengan syntax :

```javascript
function say(person){
	return `Hello, ${person}!`;
}
```

nah setiap fungsi yang dideklarasikan dengar cara begitu, punya method `call` . Dengan syntax :


```javascript
function.call(thisArg, funcArg1, funcArg2);
```

thisArg = objek yang ingin dijadikan reference. Jika tdk diisi maka mengacu pada `window` (Browser), dan `global` (Node JS).

normal nya ketika memanggil sebuah fungsi di javascript, menggunakan cara :
```javascript
say("Taufiq") // Hello, Taufiq!
```

sebenarnya juga bisa dipanggil menggunakan method `call` :
```javascript
say.call(this, "Taufiq");
```

bedanya ketika menggunakan method `call` , ada benefit tambahan yaitu bisa diset `reference` dari `this` nya.

duh bingung .

Mari pakai contoh. objek window pada browser, punya propery `innerHeight` . kita bisa manfaatkan ini.

```javascript
let objekBebas = {
	innerHeight : 1212
}

function ngomong(sapaan){
	return `${sapaan}, tinggi kamu ${this.innerHeight}`;
}

console.log(ngomong("Hei!")); // Hei!, tinggi kamu 648

console.log(ngomong.call(objekBebas, "Bro!")); // Bro!, tinggi kamu 1212
```

648 dapat dari mana??? tentu dari `innerHeight` browser yang sya gunakan (mungkin berbeda dengan kalian). (Kode dijalankan di browser, jadi `this` nya mengacu ke objek `window`)

sementara satunya kenapa hasilnya 1212?? ya karena pemanggilan kedua menggunakan method call, dan `thisArg` nya diset variabel `objekBebas` . yang mana `this.innerHeight` akan mengacu pada property `innerHeight` milik `objekBebas`

Yah kurang lebih begitu catatannya. Saya bingung pas pertama tau istilah ini.