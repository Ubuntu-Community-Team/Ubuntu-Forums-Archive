---
title: "javascript src file not working on explorer"
date: 2007-07-07
forum: Programming Talk
---

### Post by prostock3 on 2007-07-07
Hi,

i'm just starting my first program in javascript.  i use ubuntu feisty fawn.  For some reason, I try to source the *.js file, the js only works on firefox.  When I try explorer, it does not work.  If I code the alert directly into the *.html file, it works fine.  Anyone have any ideas?  

Thanks!  I posted the code below.

Inside /var/www/apache2-default , I have two files which i created (example.js, test.html)

test.html:

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN"
"http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
<html xmlns="http://www.w3.org/1999/xhtml11" xml:lang="en">
 <head>
  <meta http-equiv="content-type" content="text/html; charset=utf-8" />
  <title>Just a test</title>
  <script type="text/javascript" >
  alert(234);
  </script>
</head>
<body>
</body>
</html>

example.js
alert(20);

---

### Post by prostock3 on 2007-07-07
sorry,

i posted the wrong html file...it should be

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN"
"http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
<html xmlns="http://www.w3.org/1999/xhtml11" xml:lang="en">
 <head>
  <meta http-equiv="content-type" content="text/html; charset=utf-8" />
  <title>Just a test</title>
  <script type="text/javascript" src="example.js">
  </script>
</head>
<body>
</body>
</html>

---

### Post by Modred on 2007-07-07
It works fine for me in Firefox, IE6, and IE7.  Chances are your internet settings for IE are not allowing local files to execute their scripts as a security precaution.

Also, wrap your HTML in [noparse][html][/html][/noparse] blocks to make them easier to read and stand out from the rest of your post.

[html]
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN"
"http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
<html xmlns="http://www.w3.org/1999/xhtml11" xml:lang="en">
<head>
<meta http-equiv="content-type" content="text/html; charset=utf-8" />
<title>Just a test</title>
<script type="text/javascript" src="example.js">
</script>
</head>
<body>
</body>
</html>
[/html]

---

### Post by prostock3 on 2007-07-07
Thanks Modred for trying it out for me.  I found that not only scripts, but also css files cannot be loaded on explorer.  What are the settings I need to change?

Thanks again.

---

