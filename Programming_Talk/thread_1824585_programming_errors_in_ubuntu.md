---
title: "programming errors in ubuntu"
date: 2011-08-14
forum: Programming Talk
---

### Post by suryaD on 2011-08-14
hey guys hello.u guys are awesome...well coming to my problem below is the code that i'm enclosing..problem is that its doing nothing..practically nothing..its a jquery code..

what does this code do..?
it writes some text into the browser page and on clicking that text it slowly fades out..

and one more thing guys where do i need to save my jquery files(inside which folder?)...?

code below
(saved it with .html extension)

> 
<!doctype html>
<html lang="us">
<head>
<meta charset="utf-8">
<title>jquery examples</title> 

</head>
<body>
<div id="message" style="display: none;">welcome to my website</div>
<script type="text/javascript" src="jquery/jquery.js"></script>
<script type="text/javascript" src="jquery/init.js"></script>
</body>
</html>


> 
[init.js]
$(document).ready(function()
{
$('#message').fadeIn('slow');
});


there is jquery.js file inside the folder where these files are saved

---

### Post by simeon87 on 2011-08-14
The jQuery file needs to be in a jquery directory. When the browser can find your jQuery file, it should run that code and it the message should fade in slowly.

---

### Post by suryaD on 2011-08-14
as i said they are in the same folder mate..!

---

### Post by simeon87 on 2011-08-14
That's precisely your problem. According to the HTML code, the jQuery needs to be in a jquery directory, not in the same directory. The structure needs to be:

- yourfile.html
- jquery/jquery.js
- jquery/init.js

---

### Post by suryaD on 2011-08-14
are u saying that jquery.js and init.js should be in the jquery folder and .html file can be saved anywhere irespective of jquery folder..? if so then will try ur precedure...

---

### Post by simeon87 on 2011-08-14
No, I didn't say the html can be saved anywhere irrespective of the jquery folder.

Have you tried moving the files around so they're stored like in my previous post? That should work.

---

