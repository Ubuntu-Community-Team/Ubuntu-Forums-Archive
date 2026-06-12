---
title: "pass argument to event listener?"
date: 2016-12-12
forum: Programming Talk
---

### Post by maclenin on 2016-12-12
Essentially:
```
document.getElementById("button").addEventListener("click", function() {change_color(0);}, false);
```
```
function change_color(c) {
if (c === 0) {
document.getElementById("box").style.background = "black";
} else {
document.getElementById("box").style.background = "blue";
}
}
```

How can I modify / toggle the change_color argument - from 0 to 1, for example - so that I can turn the black box blue?

Thanks for any guidance!

---

### Post by Dimarchi on 2016-12-21
Simply put, try
```

document.getElementById("button").addEventListener("click", change_color(0), false);

```

and see if it makes a difference.

---

### Post by The Cog on 2016-12-21
How about this:
```

function change_color() {
  var box = document.getElementById("box");
  if (box.style.background == "black") {
    box.style.background = "blue";
  } else {
    box.style.background = "black";
  }
}

```

---

### Post by maclenin on 2016-12-22
Dimarchi!

Thanks for the suggestion. My goal is to affect a change in the value of the **argument** within change_color(**0**), namely **0** or 1 to 1 or the other - and to preserve that value until it's requested by a manual onclick....

The Cog!

Yep. That string literal swap, certainly, worked for me before. However, I am wondering whether I can change, as I describe to Dimarchi, the value of the **argument** within change_color(**argument**) within the addEventListener configuration - to lead to a similar end to the one you've articulated.

One other (onclick) option seems to be...
```
document.getElementById("button").onclick = function() {change_color(**0**);};

function change_color(c) {
if (c === 0) {
document.getElementById("box").style.background = "black";
document.getElementById("button").onclick = function() {change_color(**1**);};
} else {
document.getElementById("box").style.background = "blue";
document.getElementById("button").onclick = function() {change_color(**0**);};
}
}
```

...with **argument** highlighted for effect.

Would like to be able to do the same with addEventListener.

Cheers!

---

### Post by Odexios on 2016-12-22
Wouldn't a closure do what you need? Something like

[php](function() {    
    var next = 0;
    document.getElementById("button").addEventListener("click", function() {
        change_color(next);
        next = 1 - next;
    }, false);
})();[/php]

---

### Post by maclenin on 2016-12-22
Odexios!

That'll play (in [jsbin]("https://jsbin.com/")) !

Here's a slightly re-jiggered version of your closure, with div.
```
document.body.innerHTML = "<div id = box>BOX</div>";

(function() {
var next = 0, c;
document.getElementById("box").addEventListener("click", function() {
if (next === 0) {c = "orange";} else {c = "";}
document.getElementById("box").style.color = c;  
next = 1 - next;
}, false);
}());
```
Thanks!

---

