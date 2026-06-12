---
title: "Javascript Anon Functions vs Defined"
date: 2011-11-01
forum: Programming Talk
---

### Post by era86 on 2011-11-01
Calling all web devs!

The terms in the title are probably wrong, but I was wondering how Javascript handles the following while using JQuery:

[PHP]
$(".element").each(function() {
    alert("HI");
});
[/PHP]

vs

[PHP]
var hi = function() {
   alert("HI");
}

$(".element").each(hi);
[/PHP]

Let's say I have five of these classes ".element" in my document.  Does it create five anonymous functions in the first case?  Or is this optimized in some way?  I imagine the second piece of code is how you want things to be done.  I'm just curious and couldn't find a straightforward answer via Google.  Thanks!

---

### Post by crdlb on 2011-11-01
I'm not a web developer, but I am familiar with JS.

You are calling the "each" function and passing a function object. It makes no difference whether you do that with an anonymous function or with a variable that references a function. That function may be called multiple times within the "each" function, but it is only created once (when the function body is evaluated).

---

