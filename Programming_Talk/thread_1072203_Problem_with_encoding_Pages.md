---
title: "Problem with encoding Pages"
date: 2009-02-17
forum: Programming Talk
---

### Post by Uchiha_madara on 2009-02-17
I am working on translating websites using php and mo files

i have done the translation successfully ....

but the problem is the output .......

i have to change the Encoding ......

i need to tranlate the website with out change the encoding of the page from the browser

---

### Post by albandy on 2009-02-17
Make sure php and html head encoding tag are the same
if not and you couldn't change it, use php functions like iconv to change the encoding

<?php echo iconv('ISO-8859-1', 'UTF-8', $text); ?> 
or
<?php echo iconv('UTF-8', 'ISO-8859-1', $text); ?>

read the php documentation of iconv

---

