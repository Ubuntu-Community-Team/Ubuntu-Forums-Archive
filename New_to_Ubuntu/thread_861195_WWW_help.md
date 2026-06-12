---
title: "WWW help"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by ramsam on 2008-07-16
Hello guys I am new to this fourm and of course uBuntu  

I installed ubuntu and have been playing around with it for couple  of days..... I installed apache web server

I get the webpage and all but the .zip file that I have put up using a <a href> link will not download.

It downloads but its not the complete file ?

I am sure that I am missing some settings ?

can any one help !!!

**this is how my INDEX.HTML file looks**
***************************************************
<html><body><h1>It works!</h1></body></html>


<a href="/var/www/maine.zip"<font size=15> <B> MAINE pictures </B></font></a>

***************************************************

Any clu or help is appreciated 
Thank you guys !!!

-ramsam

---

### Post by WorldTripping on 2008-07-16
The link has to be between the <html></html>

Try:

<html>
<body>
<h1>It works!</h1>
<a href="maine.zip"<font size=15><B>MAINE pictures</B></font></a>
</body>
</html>

Assuming that maine.zip is next to the index.html file.

---

### Post by fatality_uk on 2008-07-16
Think of it this way. "/var/www" is your base from which all files paths are taken. Apache assumes this already so you don't need that physicla address there.

Like WorldTripping said, if the zip file is in your www directory, then all you need is the file name. If it is in a sub directory, then use the path from there, i.e. if the physical path is /var/www**/myfiles/myzips/myzip.zip** then all you need is the section in bold.

---

### Post by Barrucadu on 2008-07-16
You missed a '>', the content needs to be within the <body> and <html> tags, and you missed the <head> section:
```
<html>
<head>
<title>It works!</title>
</head>
<body>
<h1>It works!</h1>
<a href="maine.zip" style="font-size:15px;font-weight:bold;">MAINE pictures</a>
</body>
</html>
```
Oh, and you could tidy up that a bit with CSS (as I have done), and you shouldn't need to specify the full path.

---

### Post by init1 on 2008-07-16
This should work
```

<html><body><h1>It works!</h1></body></html>


<a href="/var/www/maine.zip"><font size=15> <B> MAINE pictures </B></font></a>
```
You were missing a ">" before the font tag.

---

### Post by Sef on 2008-07-16
Moved to Absolute Beginners.

---

