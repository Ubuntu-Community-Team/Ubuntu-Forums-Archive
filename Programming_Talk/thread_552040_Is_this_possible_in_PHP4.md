---
title: "Is this possible in PHP4?"
date: 2007-09-16
forum: Programming Talk
---

### Post by x1a4 on 2007-09-16
Hi, 

Is the following possible in PHP 4.4.6, and if so what libraries and functions should I use?  

A small script that:  
* reads contents of specified directories containing images, 
* count the number of files therein, 
* display files beginning with 'tn_'  in a specified number of rows and columns, 
* and make the thumbnails links to display the corresponding (based on the file name) large images
* create 'previous' and 'next' links

Essentially I want a mini-gallery.  

Thank you.

---

### Post by ryno519 on 2007-09-16
Yes. You'll need the GD library in PHP.

[http://php.net](http://php.net) should have references to directory iteration functions.

---

