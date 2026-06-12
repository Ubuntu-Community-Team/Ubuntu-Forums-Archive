---
title: "saving an html file with all tags using PHP"
date: 2008-01-02
forum: Programming Talk
---

### Post by mohtasham1983 on 2008-01-02
Hi,

I'm trying to find all images in an html file. Therefore, I'm looking for a way to save the content of a page with all html tags in a text file and then search for "<img" keyword to find the picture. 

I have been searching google for that, but I couldn't find any function in PHP which can do that for me.

Any idea what function I have to use?

---

### Post by ghostdog74 on 2008-01-02
one way out of the many
```

<?php
$pattern = '/<img(.*?)>/';
preg_match($pattern, $htmlfile, $matches);
print_r($matches);
?>

```

---

### Post by dhtseany on 2008-01-02
I like ghostdog74's idea but if you want ALL the images I'd search for common file extensions used (.jpg, .jpeg, .gif, .png) because some tags will use <img src="dfdfgdfgdfg.jpg"> and other tags could be <body background="dfgdfgd.gif"> or <td background="dfgdfg.png">.

Just a thought

Peace

---

### Post by ThinkBuntu on 2008-01-02
You're also going to miss a ton of images on modern websites which often use the CSS background-image property for its flexibility and because it's not obtrusive. It also allows for easy layering. I'd suggest searching linked CSS files for image extensions to round out this scan.

---

### Post by slavik on 2008-01-02
umm, the OP did say he was looking for <img ... so why not just do that?

---

### Post by mohtasham1983 on 2008-01-02
Thank you very much. I'm not really interested in pictures which are specified in CSS.

---

