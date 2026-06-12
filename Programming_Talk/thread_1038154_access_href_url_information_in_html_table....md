---
title: "access href url information in html table..."
date: 2009-01-12
forum: Programming Talk
---

### Post by zpzpzp on 2009-01-12
Hi,

I have an html table like this:

<table class="example table-stripeclass:alternate" id= "Results" border="2">
<thead>
</thead>
<tbody class="table-nosort">
<tr>
<td>
<a href="www.mysite.com">My Site</a>
</td>
... ...

Does anyone know how to access the "www.mysite.com" information using Javasccript (possibly through the DOM tree?)

Thanks a lot.

Paul

---

### Post by kjohansen on 2009-01-12
to do that through javascript you are either going to give the anchor tag a unique or return all anchor tags

```
document.getElementById("ID here").href
```
 or 

see here:

[http://www.w3schools.com/HTMLDOM/dom_obj_anchor.asp](http://www.w3schools.com/HTMLDOM/dom_obj_anchor.asp)

---

### Post by zpzpzp on 2009-01-12
Thanks!

I also discovered that if you do

```
<a href="www.mysite.com" onmouseover="myFunction(this)">My Site</a>
```

Then inside of the function, the variable passed in is actually the URL. This is true at least in IE.

Cheers,

Paul

---

### Post by mssever on 2009-01-12
> **zpzpzp said:**
> Thanks!

I also discovered that if you do

```
<a href="www.mysite.com" onmouseover="myFunction(this)">My Site</a>
```Then inside of the function, the variable passed in is actually the URL. This is true at least in IE.

Cheers,

Paul
Are you sure? It should be a reference to the A element. But who knows what stupid stuff IE might be doing.

By the way, I consider the Firebug extension for Firefox to be indispensable for JS development.

---

### Post by zpzpzp on 2009-01-16
> **mssever said:**
> Are you sure? It should be a reference to the A element. But who knows what stupid stuff IE might be doing.
-- Thansk for your reply. Yes I am sure of this. I found this out by experimenting. Ya IE is a little unusual... for example the drop down box would always appear on top of div's, even if the div is used for developing popup boxes.

> **mssever said:**
> By the way, I consider the Firebug extension for Firefox to be indispensable for JS development.
Oh I did not know about Firebug. I will give it a try.
The sad thing is though, for some big companies like the one that I work in, they only support IE... maybe because it comes with Windows.

---

