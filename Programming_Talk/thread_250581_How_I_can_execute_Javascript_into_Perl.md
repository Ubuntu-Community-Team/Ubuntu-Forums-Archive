---
title: "How I can execute Javascript into Perl?"
date: 2006-09-04
forum: Programming Talk
---

### Post by CarryT on 2006-09-04
I don't know how I can execute an event of Javascript into a link in a program in Perl. 
This event of JavaScript have executed a function that return a HTML page. 
Anybody know how I can it? 

Is it possible do it this?: 
$datos=$datos.""<a href='"" . $me . ""?C=OFERTAS2&EMPRESA="".$empresa_param.""&NREF="".$nref.""' onMouseOver=""linkFTecnica(nref2)"">""; 

What is bad in this code? 

Thank you very much.

---

### Post by ifokkema on 2006-09-06
What's with all those double double quotes?

---

### Post by geek_Man on 2006-11-19
What you have to do is this (I don't know for sure if it'll work though):```
$datos = $datos . "<a href=\"" . $me . "\"?C=OFERTAS2&EMPRESA=\"" . $empresa_param . "\"&NREF=\"" . $nref ."\" onMouseOver=\""linkFTecnica(nref2)"\">";
``` You have to put backslashes before the quotations of the code you want it to print out. So for example: print "<a href=\"" . $foo . "\" />";
If I hadn't had put those backslashes in there it wouldn't have worked.
Best of luck with your web pages! :D

---

