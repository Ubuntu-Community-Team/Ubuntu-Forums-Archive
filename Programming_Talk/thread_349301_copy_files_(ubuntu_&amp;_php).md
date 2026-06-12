---
title: "copy files (ubuntu &amp; php)"
date: 2007-01-30
forum: Programming Talk
---

### Post by suessw on 2007-01-30
I would like to copy 3 files from /var/lib/mysql/bibliothek to /media/SWISSMEMORY/

the program looks like

<html>
  <head>
  <h1><center>Datensicherung</center></h1>
  </head>
  <?php
   $a = date(d.m.Y);
   echo $a;
   echo mkdir('/media/SWISSMEMORY/'.$a.'');
   echo opendir('/media/SWISSMEMORY/'.$a.'');
   echo copy('/var/lib/mysql/bibliothek/*.MDY /media/SWISSMEMORY/'.$a.'');
   echo copy('/var/lib/mysql/bibliothek/*.MDI /media/SWISSMEMORY/'.$a.'');
   echo copy('/var/lib/mxsq/bibliothek/*.frm /media/SWISSMEMORY/'.$a.'');
 ?>
</html>

$a has the date stored.
mkdir does not create a dir at the media.
  (permission denite )
the rest of the commands won't work because dir does not exist as well
  permission denite

Question: what do I to change that it will work?
Mybe someone can give a tipp

Thx

---

