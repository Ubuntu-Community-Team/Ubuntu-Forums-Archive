---
title: "[SOLVED] Need to edit a .db file"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by gjoellee on 2008-09-06
I there! I am so lucky that I have to open and edit a .db file     ( ex:     <filename>.db ). But how do I do that? 

Thank you for the help:)

---

### Post by wolfen69 on 2008-09-06
have you tried right click>open with>text editor ?

---

### Post by gjoellee on 2008-09-06
no that does not work.... neither with openoffice......

---

### Post by unutbu on 2008-09-06
What is the output when you run

```
file FILENAME.db
```

The file command might be able to tell you what kind of file it is.

---

### Post by gjoellee on 2008-09-06
**Thumbs.db: Microsoft Office Document**

 too bad I only have OOo 2.4

---

### Post by pedro3005 on 2008-09-06
isnt Thumbs.db a file windows creates when you view a folder with image preview?
anyway, dont know if theres anything to open that, and why would you wanna open it?

---

### Post by wolfen69 on 2008-09-06
i found assogiate in synaptic. you might try that.

---

### Post by gjoellee on 2008-09-06
> **pedro3005 said:**
> isnt Thumbs.db a file windows creates when you view a folder with image preview?
anyway, dont know if theres anything to open that, and why would you wanna open it?

I am a developer for [www.kshoster.net](www.kshoster.net) and on the Tux page we use php which reads of the file (Thumbs.db). That will make the code needed to show all the tuxes we have. This way is much esier then to write the code by hand. I have just edited a little so you have to fix the code by hand to make it work (so you don't copy it)...you see why I don't want to write that by hand:)

---

### Post by gjoellee on 2008-09-06
> **wolfen69 said:**
> i found assogiate in synaptic. you might try that.
  thx, but didn't help

---

### Post by Fixman on 2008-09-06
> **gjoellee said:**
> thx, but didn't help

Can you post the file here? Maybe its a special type of file.

---

### Post by unutbu on 2008-09-06
Do you use gqview? This program creates thumbnails of images in a directory and it seems to store them in a file called Thumbs.db. When I run `file` on it, `file` erroneously identifies it as a "Microsoft Office Document". 

If your Thumbs.db was created by gqview, then perhaps you can use the gqview GUI to regenerate the Thumbs.db.

---

### Post by gjoellee on 2008-09-07
> **unutbu said:**
> Do you use gqview? This program creates thumbnails of images in a directory and it seems to store them in a file called Thumbs.db. When I run `file` on it, `file` erroneously identifies it as a "Microsoft Office Document". 

If your Thumbs.db was created by gqview, then perhaps you can use the gqview GUI to regenerate the Thumbs.db.

Thanks!!!!!:):)

---

