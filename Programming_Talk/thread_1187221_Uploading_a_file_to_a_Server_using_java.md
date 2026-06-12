---
title: "Uploading a file to a Server using java"
date: 2009-06-14
forum: Programming Talk
---

### Post by jucas_lo on 2009-06-14
Hi I've started working with java just two months ago, so I'm prety much a newbie in java.

Still I gotta do upload a file to a server using java and I don't know how to do it. I've been googling around but all I found is information about servlets and stuff, which isn't quite my case...

You see I have to make the equivalent of an HTML form, like this one:

<form method='POST' enctype='multipart/form-data' action='server.cgi'> 
File to upload: <input type=file name=upfile><br> 
<input type=submit value=Press> to upload the file!
</form> 

How can I do it in pure Java??

thanks in advance!

---

### Post by myrtle1908 on 2009-06-15
Use the FileUpload tool from the Apache Commons library.  Very easy to use.  [http://commons.apache.org/fileupload/using.html](http://commons.apache.org/fileupload/using.html)

---

