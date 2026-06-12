---
title: "[SOLVED] directory structure visibility under Apache"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by voytec on 2008-08-01
Hi all
I do not want anybody to be able to see my directory structure! What and how I should do it?

lets say I have folder 'example': var/www/example
so when you type in a browser 'www.mydomain.com/example/' i do not want anybody to see the content of my example folder.

Thank you

---

### Post by hrod beraht on 2008-08-01
Put an **index.html** file in that folder and that will load instead.
The list of files only shows up as a default if there isn't an index.html file to read.

You know, like the default Apache **It works!** page in the root /var/www folder.

A neat way to do it would be to make the /var/www/example/index.html page just redirect to the main page /var/www/index.html. Like so:
```
<html>
<head>
<meta http-equiv="REFRESH" content="0;url=http://www.yourdomain.com">
</head>
<body>
Nothing to see here...please move along.
</body>
</html>

```

That code saved as /var/www/example/index.html would mean that when someone went to [www.yourdomain.com/example](www.yourdomain.com/example), it would load that index.html page which would just automatically redirect them to your main [www.yourdomain.com](www.yourdomain.com) page.

Bob

---

### Post by voytec on 2008-08-01
Brilliant! Thank you very much!

---

