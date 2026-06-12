---
title: "capturing if statement output in javascript"
date: 2011-09-06
forum: Programming Talk
---

### Post by maclenin on 2011-09-06
I would like to "capture output" from the following "if" statement...

```
**if (x==g)**
```

...where g is a value to be found in an array snippet x.

As matches are found - I would like them to be captured in some systematic way for use in creating additional arrays - dynamically.

I have - to this point - been able to "isolate the output" from the if statement in the following manner:

```
**a=arrayA();** // hard-coded original arrayA
```
```
**b=arrayB();** // dynamically-generated sub arrayB
```
```
**g=value;** // which I wish to find in arrayA
```

```
**for (i=0; i<length.of.arrayA; i++)** // loop through arrayA
**{**
**x=a[i][2];** // isolate the arrayA value I wish to match
**if (x==g)** 
**{**
**for (h=0; h<=number.of.matching.values; h++)** 
**b[h]=a[i];** // kick-out matching instances to create arrayB
[B]}
}
}[/B]

```

I am able to "see" all of the output I'd like - I just haven't figured out a way to grab it and organize it!

Thanks for any guidance!

---

### Post by myrtle1908 on 2011-09-06
> **maclenin said:**
> As matches are found - I would like them to be captured in some systematic way for use in creating additional arrays - dynamically.

Not sure I understand exactly what you want but ... the following will loop through an array (a), find matches and store these in another array (b).

```
var a = 'linux,win32,win64,*nix,linux,iOS,random'.split(','), // cheap way to create an array
    b = [], // matches go here
    find = 'linux', // look for this string in a
    item = null; // current loop item from a
for (var i=0; i<a.length; i++) {
    item = a[i];
    if (item == find) {
        b.push(item); // found one
    }
}
console.debug(b); // needs firebug or chrome dev console
```

Yields: ```
["linux", "linux"]
```

If you wanted to eliminate duplicates you should consider using a hash (basically a JS object) to store the matches.

Do yourself a favour and use Firebug or Chrome dev tools (CTRL+SHIFT+I) to inspect and step through your code!

---

### Post by maclenin on 2011-09-07
You've pushed me far enough, **myrtle1908**...

> As matches are found - I would like them to be **captured in some systematic way** for use in creating additional arrays - **[COLOR="DarkOrange"]dynamically[/COLOR]**....the **push()** statement **SOLVED** the problem!

```
[B]function arraySet()
{
gIP=new ArrayB();[/B] // **[COLOR="DarkOrange"]dynamically[/COLOR]** created arrays - differently constituted based on g
**for (i=0; i<lenArrayA; i++)** // loop through the original ArrayA
[B]{
x=imIP[i][2];[/B] // address of x in the multi-dimensional original ArrayA
**if (g==x)** // (how many times) does g match x
[B]{
gIP.push(i);[/B] // matches **captured in some systematic way** to create ArrayB
[B]}
else if (g=="AL")[/B] // display all contents of the the original ArrayA
[B]{
gIP.push(i);[/B] // reproduce the original ArrayA
[B]}
len=gIP.length;[/B] // length of dynamically generated Array (A or B)
[B]}
}[/B]
```

Essentially, this code breaks down a large gallery of images (ArrayA) into sub-galleries (ArrayB) based on theme (g). Each of the photos in ArrayA is "tagged" - "Lakes","Mountains" or "Rivers" (respective values of x). The themes (g - again, "Lakes","Mountains","Rivers") can then be clicked as links - to dynamically match the array values - "pushing" separate galleries of Lakes only, Mountains only or Rivers only - or ALL....

Thank you **myrtle1908!**

---

