---
title: "PHP Download Unix Binary"
date: 2012-03-10
forum: Programming Talk
---

### Post by smilinggoomba on 2012-03-10
Hello all.  I'm a newbie at PHP and HTML, but for my website I decided to put a download link for a Unix Executable (a compiled C program) in PHP.  After <a href>-ing to the link, the PHP looks like this:

<?php
header('Content-disposition: attachment; filename=conjugate');
header('Content-type:application/octet-stream');
readfile('conjugate');
?>

The problem is that I don't know what to do for content-type.  When I try octet-stream, an HTML file downloads.  How can make it so an executable downloads???

NOTE: The program was compiled on a Mac, but it's a Unix Executable, so it will work on GNU-Linux.

---

