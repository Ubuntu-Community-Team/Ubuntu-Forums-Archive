---
title: "[SOLVED] javascript menu"
date: 2007-12-12
forum: Programming Talk
---

### Post by snickers295 on 2007-12-12
does anyone know how to make a javascript menu like the menu for ubuntu forums (no, not php)?

---

### Post by zach12 on 2007-12-12
Do you mean the Menu at the top of the screen

If so PM me

---

### Post by Kadrus on 2007-12-12
I do..
So here's how you do it...I am assuming that it is a drop down menu with an onmousover onmouseout functions..
```

<style>
body{font-family:arial;}
table{font-size:80%;background:black}
a{color:black;text-decoration:none;font:bold}
a:hover{color:black}
td.menu{background:beige}
table.menu
{
font-size:100%;
position:absolute;
visibility:hidden;
}
</style>
<script type="text/javascript">
function showmenu(elmnt)
{
document.getElementById(elmnt).style.visibility="visible";
}
function hidemenu(elmnt)
{
document.getElementById(elmnt).style.visibility="hidden";
}
</script>
</head>

<body>

<table width="100%">
 <tr bgcolor="beige">
  <td onmouseover="showmenu('products')" onmouseout="hidemenu('products')">
   <a href="products.html">Products</a><br />
   <table class="menu" id="products" width="120">

   <tr><td class="menu"><a href="What.html">What is Ubuntu</a></td></tr>
   <tr><td class="menu"><a href="down.html">Download</a></td></tr>
   <tr><td class="menu"><a href="get.html">get ubuntu</a></td></tr>
   <tr><td class="menu"><a href="sc.html">catalogue</a></td></tr>
   <tr><td class="menu"><a href="m.html">Marchandise</a></td></tr>
   </table>

  </td>
  <td onmouseover="showmenu('blala')" onmouseout="hidemenu('blala')">
   <a href="vlalal">blalla</a><br />
   <table class="menu" id="blala" width="120">
   <tr><td class="menu"><a href="s.html">blalal</a></td></tr>
   <tr><td class="menu"><a href="bbb">bbb</a></td></tr>
   <tr><td class="menu"><a href="bbb">bbb</a></td></tr>

   <tr><td class="menu"><a href="bbb">bbb</a></td></tr>
   <tr><td class="menu"><a href="bbb">bbb</a></td></tr>
   </table>
  </td>
  <td onmouseover="showmenu('bbb')" onmouseout="hidemenu('bbb')">
   <a href="bbb">bbb</a><br />
   <table class="menu" id="bbb" width="120">

   <tr><td class="menu"><a href="bbb">bbb</a></td></tr>
   <tr><td class="menu"><a href="bbb">bbb</a></td></tr>
   <tr><td class="menu"><a href="bbb">bbb</a></td></tr>
   <tr><td class="menu"><a href="bbb">bbb</a></td></tr>
   <tr><td class="menu"><a href="bbb">bbb</a></td></tr>
   </table>

  </td>
 </tr>
</table>

```
Of course change the "bbb" with what you want to put...i did it quickly..
Hope it will help

---

### Post by snickers295 on 2007-12-12
perfect!
thanks 
the reason i wanted it was my mom wanted me to write my siblings Christmas lists down so i thought i would show off with one of these.

---

### Post by Kadrus on 2007-12-12
> **snickers295 said:**
> perfect!
thanks 
the reason i wanted it was my mom wanted me to write my siblings Christmas lists down so i thought i would show off with one of these.
Glad to help :)

---

