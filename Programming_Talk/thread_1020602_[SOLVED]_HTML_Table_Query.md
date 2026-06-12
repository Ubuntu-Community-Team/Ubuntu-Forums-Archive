---
title: "[SOLVED] HTML Table Query"
date: 2008-12-24
forum: Programming Talk
---

### Post by s.fox on 2008-12-24
Hi,

Does anybody know why this table has a slight white border between all the cells?  Not totally sure why it's showing it.  The only border should be a black outline around the whole table.

[PHP]
<table align="center" style="border: 1px solid black;"><tr bgcolor='#FFC600'>
<td>1</td><td>Stone Roses</td><td>A group dedicated to the stone roses</td>
</tr><tr bgcolor='#C6FF00'>
<td>2</td><td>Beatles</td><td>A group dedicated to the beatles</td>
</tr><tr bgcolor='#FFC600'>
<td>3</td><td>Rolling Stones</td><td>A group dedicated to the rolling stones</td>
</tr><tr bgcolor='#C6FF00'>
<td>4</td><td>Slade</td><td>A group dedicated to slade</td>
</tr></table> [/PHP]

Any help would be much appreciated.

Ash R

---

### Post by ilrudie on 2008-12-24
Use the *border-collapse: collapse* CSS property.

---

### Post by Reiger on 2008-12-24
Yes, that one (table borders are a special kind of animal... savage too...). And you may find your table rendering browser works with a default padding/margin for cells that you may wish to override.

---

### Post by s.fox on 2008-12-27
Thanks for the help.  I did have a look at collapse but it didn't work last time I tried it.   Does work now though.  Must have done something wrong.   Anyway,  thanks for the help!  Here is the table now as it stands.  Only thing left to do now is change the hideous colours :P

[php]<html>
<head>
<style type="text/css">
table.coll 
{
border-collapse: collapse
}
</style>
</head>
<body>

<table class="coll" style="border: 1px solid black;" border="0">
<tr bgcolor='#FFC600'>
<td>1</td><td>Stone Roses</td><td>A group dedicated to the stone roses</td>
</tr><tr bgcolor='#C6FF00'>
<td>2</td><td>Beatles</td><td>A group dedicated to the beatles</td>
</tr><tr bgcolor='#FFC600'>
<td>3</td><td>Rolling Stones</td><td>A group dedicated to the rolling stones</td>
</tr><tr bgcolor='#C6FF00'>
<td>4</td><td>Slade</td><td>A group dedicated to slade</td>
</tr></table> 
</body>
</html>[/php]

---

