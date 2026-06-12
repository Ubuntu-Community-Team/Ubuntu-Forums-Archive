---
title: "Recover &quot;Untitled Document 1&quot; from gedit crash"
date: 2015-08-18
forum: New to Ubuntu
---

### Post by furioususer on 2015-08-18
I had an unsaved document opened in gedit on Ubuntu 14.04 LTS and suddenly it froze so I had to shut it down by "force quit". I have Edit--> Preferences--> Editor--> File Saving--> check mark on "Autosave files every 4 minutes". 

[B]Is there any way to recover or find the lost text? Are "Untitled Documents" stored somewhere temporarily?
[/B]
In this link it says that you can find it under such circumstances: 
[https://lists.ubuntu.com/archives/ubuntu-users/2008-January/135065.html](https://lists.ubuntu.com/archives/ubuntu-users/2008-January/135065.html)
*If you have set Edit --> Preferences --> --> Editor --> File Saving > check mark on ¨Autosave files...¨, then you should be able to open your home folder, select view hidden files, and find the name of the file you were editing/finishing. If you had not saved it, it will be called unsaved file, I think.*


But I can't find such a file as described in the text. Is this correct?

---

### Post by howefield on 2015-08-18
Yes, it is correct - have you tried looking in the folder in which the document was originally saved ?

Ctrl + h to view hidden files.

---

### Post by tgalati4 on 2015-08-18
It doesn't work the way you expect.  If you make changes to a document and then save it, you will get 1 backup copy:

> tgalati4@Mint17 ~/Documents $ ls -la U*
-rw-r--r-- 1 tgalati4 tgalati4 102 Aug 18 08:48 Unsaved Document 1
-rw-r--r-- 1 tgalati4 tgalati4  39 Aug 18 07:48 Unsaved Document 1~


If you have a sudden shutdown, you will lose work from the last automatic save point.  You might also lose the current, active file that you are editing. You may be able to retrieve pieces of the current file using *photorec*.  That will definitely take more than 4 minutes.

Some reading:  [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by furioususer on 2015-08-23
> **howefield said:**
> Yes, it is correct - have you tried looking in the folder in which the document was originally saved ?

Ctrl + h to view hidden files.

You misunderstand. Like I wrote in my original post: **"**[COLOR=#000000]**I had an unsaved document..."** and the link I referred to wrote **"**[/COLOR]**If you had not saved it, it will be called unsaved file, I think."**
[COLOR=#000000]
So I'm a bit confused about your contradicting post by first stating "it is correct" and then asking about where the document was originally saved. The document was not saved, but I had enabled the "save every 4 min" function in gedit since months ago.

Please clarify.

[/COLOR]

---

### Post by tgalati4 on 2015-08-23
You will have to verify this, but the auto-save function is broken.  You have to manually save the file first, then you will have a file that the auto-save function will write to every 4, 10 minutes, or whatever you set it to.  If you create a new document, do a bunch of typing but don't save it, then loose power, you have lost that file.

---

