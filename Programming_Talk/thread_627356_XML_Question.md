---
title: "XML Question"
date: 2007-11-30
forum: Programming Talk
---

### Post by 71fnRVVm on 2007-11-30
Hi everyone,

I'm rendering XML output to the browser (or AJAX request) using PHP, but Firefox isn't recognizing it as an XML file, and therefore not displaying it using the XML characteristics.

You can see a sample output:
[http://www.myshoutoutloud.com/api/?user=KyleBrady&req=1&types=0](http://www.myshoutoutloud.com/api/?user=KyleBrady&req=1&types=0) 

Right click, View Source... it looks fine, doesn't it?

Thanks

---

### Post by MicahCarrick on 2007-11-30
Did you specify an XML mime type in the PHP file which outputs that using the header() function? 

For example:

```
header('Content-Type: text/xml; charset=utf-8'); 
```

---

### Post by 71fnRVVm on 2007-11-30
Oh.  No.

Let me try that.

Thanks

---

### Post by 71fnRVVm on 2007-11-30
Perfect!

Thanks again!

---

