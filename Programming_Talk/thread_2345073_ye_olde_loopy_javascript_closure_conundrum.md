---
title: "ye olde loopy javascript closure conundrum"
date: 2016-11-30
forum: Programming Talk
---

### Post by maclenin on 2016-11-30
So, very simply - in jsbin - I have deployed the following:

/*css*/
```
#a_0 {height:100px; width:100px; background:gray;}
#a_1 {height:100px; width:100px; background:tan;}
#a_2 {height:100px; width:100px; background:sienna;}
```

//js
```
for (var i = 0; i < 3; i += 1) {
document.body.innerHTML  += '<div id = "a_' + i + '"></div>';
document.getElementById("a_" + i).addEventListener('mouseover', (function(i) {return function() {change(i);};}(i)), false);
}

function change(g) {
document.getElementById("a_" + g).style.background = "green";
}
```

Only div #a_2 changes to green when I pass my mouseover.

I would like all 3 divs to change to green when I pass my mouseover (each respective div).

Thanks for any guidance!

---

### Post by maclenin on 2016-12-26
Here are a couple of simplified jsbin-tested closure scenarios (yes, deploying functions inside loops), with onmouseover and addEventListener...

...which seem to work using two separate loops / variables (similar, perhaps, to [this]("http://stackoverflow.com/questions/750486/javascript-closure-inside-loops-simple-practical-example?rq=1") example):
```
for (var i = 0; i < 3; i += 1) {
document.body.innerHTML += "<div id = a_" + i + ">Box " + i + "</div>";
}

for (var j = 0; j < 3; j += 1) {
//document.getElementById("a_" + j).onmouseover = (function(j) {return function() {alert(j);};}(j));
document.getElementById("a_" + j).addEventListener("mouseover", (function(j) {return function() {alert(j);};}(j)), false);
}
```

...and seem to fail when consolidated under a single loop / variable:
```
for (var i = 0; i < 3; i += 1) {
document.body.innerHTML += "<div id = a_" + i + ">Box " + i + "</div>";

document.getElementById("a_" + i).onmouseover = (function(i) {return function() {alert(i);};}(i));
//document.getElementById("a_" + i).addEventListener("mouseover", (function(i) {return function() {alert(i);};}(i)), false);
}
```

Essentially, how best to assign an event listener dynamically?

Thanks for any thoughts!

---

### Post by Dimarchi on 2016-12-31
It is better to keep stuff that does different things separate, in this case the creation of divs and the assignment of event listeners to them. It will result in a code that is easier to handle and debug.

---

