---
title: "externally loading javascript ?"
date: 2009-09-25
forum: Programming Talk
---

### Post by abhilashm86 on 2009-09-25
when i use <script src......> to load an external javascript, it is not loading?
this is pgm1.js
```
<script language="JavaScript">
var mes="message goes here......"
</script>
```
this is pgm3.html
```

<html>
<title> display</title>
<head>
<script src="/home/abhilash/pgm1.js"> </script>
</head>

<body>
<script language="JavaScript">
document.write("<p>"+mes+"</p>");
</script>
</body>

</html>


```
what is problem?

---

### Post by credobyte on 2009-09-25
pgm1.js
[php]var message = "Message from JavaScript";[/php]pgm3.html
[php]
<script type="text/javascript">
    document.write("<p>" + message + "</p>");
</script>
[/php]

P.S. - <title> in the wrong place :)

---

### Post by CyberJack on 2009-09-25
The problem is the / in the beginning of /home/abhilash/pgm1.js
The external javascript file will be loaded from the root of the url you provide.

If your url is [http://localhost/pgm3.html](http://localhost/pgm3.html) the browser will try to load the javascript file from [http://localhost/home/abhilash/pgm1.js](http://localhost/home/abhilash/pgm1.js)
If you want to load the javascript file from your home directory try:
```
<script src="file:///home/abhilash/pgm1.js"></script>
```

This should work but only for the local pc. Any external pc will try to load the javascript file locally.

If you placed the javascript file in the same directory as the html file, you can use:
```
<script src="pgm1.js"></script>
```
The browser will try to load the javascript file from the same location as the html file ([http://localhost/pgm1.js](http://localhost/pgm1.js))

---

### Post by abhilashm86 on 2009-09-25
after making changes, it wont display mes (message), it prints like this onto browser, ```
document.write("

" + mes + "

"); 
```

---

### Post by abhilashm86 on 2009-09-25
where should i use type and language? in javascript?
sometimes we use,
```
<script language="JavaScript">
var t=100;
alert(t);
</script>
``` 
and most of times, in many places

```
<script type="text/javascript">
var t=100;
alert(t);
</script>
```
what is difference between type and language, if i want to use alert and use type, no output......

---

### Post by CyberJack on 2009-09-25
It depends on the version of html you are using.
When using a HTML4 file you can use <script language="javascript"></script>
When using a xhtml file (recommended) you have to use <script type="text/javascript"></script>

You can specify the type of file by using the currect doctype.
see: [http://htmlhelp.com/tools/validator/doctype.html](http://htmlhelp.com/tools/validator/doctype.html)

Differences between HTML4 and xhtml: [http://www.w3schools.com/XHTML/xhtml_html.asp](http://www.w3schools.com/XHTML/xhtml_html.asp)

---

### Post by bobince on 2009-09-25
Always use 'type'. 'language' is the way it used to be done in very old browsers, but it has never been valid in any version of HTML.

---

