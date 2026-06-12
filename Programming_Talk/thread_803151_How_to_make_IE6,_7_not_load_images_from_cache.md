---
title: "How to make IE6, 7 not load images from cache"
date: 2008-05-22
forum: Programming Talk
---

### Post by figo2476 on 2008-05-22
Basically, a image will be updated over time, but it is always has the same name.
Safari and firefox understand the difference and will load the latest image. IE6,7 have
a little problem and it will load the cache image.

I have tried
<?php header("Cache-Control: no-cache, must-revalidate"); // HTTP/1.1 ?>
<?php header('Pragma: no-cache'); ?>
It doesn't work in all browsers and I guess the php page flow is not as simple as from top to bottom.
It won't be desirable, since the page has many images and it should reload a particular image.

Not sure how to work around this....

---

### Post by soapytheclown on 2008-05-22
try:
[php]header("Pragma: public");

header("Expires: 0"); // set expiration time

header("Cache-Control: must-revalidate, post-check=0,pre-check=0");

header("Cache-Control: private",false); // required for certain browsers[/php]

works for me :)

---

### Post by figo2476 on 2008-05-22
solved by using <img src="....image.jpg?<?php echo uniqid() ?>"

---

