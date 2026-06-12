---
title: "IE7 pdf download impossible!"
date: 2007-05-03
forum: Programming Talk
---

### Post by Thyme on 2007-05-03
Hello everyone,

I'm trying to create a "run of the mill" PHP script that will allow users to download a PDF from some website. The script works great in Firefox but not in IE7. Please have a look at the script and tell me what I'm doing wrong...
it's attached below. I've tried a few of the scripts provided at php.net but those result in either IE7 or Firefox working and the other not...

Thanks,
Thyme

EDIT:

The script is:

##########################################################

<?php
session_start();                                                  

$document = $_GET['show'];
$client = <some client ID>;

// We'll be outputting a PDF
header('Content-type: application/pdf');

// It will be called downloaded.pdf
header('Content-Disposition: attachment; filename="'.$document.'" ');

header('Content-Description: pdf');

// The PDF source is in original.pdf
readfile('../../../download/'.$client.'/'.$document.'');

?> 

##########################################################

It seems as thought IE is not picking up the readfile() path as well as Firefox does...

---

### Post by Mirrorball on 2007-05-03
```
$document = $_GET['show'];
readfile('../../../download/'.$client.'/'.$document.'');
```
Anyone could download any file in the server by choosing the right path in $_GET['show']. This is a big security hole.

---

### Post by Thyme on 2007-05-03
Thanks for the feedback, Mirrorball. I will  definitely keep that in mind and try to change that once my PHP skills have improved.

 However, do you perhaps know how I can download PDF's with a script that works with both IE7 and Firefox? Any help will be greatly appreciated...

---

### Post by Mirrorball on 2007-05-03
I don't know. But here several possibilities are suggested:
[http://www.php.net/header](http://www.php.net/header)
[http://www.php.net/readfile](http://www.php.net/readfile)

---

