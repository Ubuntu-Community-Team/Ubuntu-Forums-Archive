---
title: "Understanding a .patch file."
date: 2012-06-06
forum: New to Ubuntu
---

### Post by Kaspberger on 2012-06-06
This is going to be a "n00b" question, but, since I'm in the Beginner forum, I have no shame.

I am attempting to do this fix: [http://code.google.com/p/textroom/issues/detail?id=71](http://code.google.com/p/textroom/issues/detail?id=71) -- I have to apply to a .patch file to an application.pro file and have no clue how to process this.

This is the .patch file.

> Index: textroom-0.8.2/application/application.pro
===================================================================
--- textroom-0.8.2/application/application.pro
+++ textroom-0.8.2/application/application.pro    2011-05-17 10:52:37.810863678 -0300
@@ -98,7 +98,7 @@
         icon
     LIBS = -lSDL_mixer \
     -lSDL \
-        -lhunspell \
+        -lhunspell-1.2 \
     -lglibmm-2.4 \
     -lcurl \
     -lxml++-2.6 \
Any help would be appreciated. It's for the TextRoom application. I'm using Xubuntu 12.04.

---

### Post by Kaspberger on 2012-06-06
I understand that this will be a beginner's question, but I've not had much fortune in the "Beginner's forum," so I've moved on to the General one.

I'm attempting to complete this fix: [http://code.google.com/p/textroom/issues/detail?id=71](http://code.google.com/p/textroom/issues/detail?id=71). Supposedly, I have to apply a .patch file to an application.pro file, but I have no idea how to do this.

The application.pro file is for the TextRoom 8.2 program. I'm using Xubuntu 12.04.

The .patch file is as follows...

> Index: textroom-0.8.2/application/application.pro
===================================================================
--- textroom-0.8.2/application/application.pro
+++ textroom-0.8.2/application/application.pro    2011-05-17 10:52:37.810863678 -0300
@@ -98,7 +98,7 @@
         icon
     LIBS = -lSDL_mixer \
     -lSDL \
-        -lhunspell \
+        -lhunspell-1.2 \
     -lglibmm-2.4 \
     -lcurl \
     -lxml++-2.6 \
Thanks in advance for the help.

---

### Post by 3Miro on 2012-06-06
A patch file contains information of how to modify the source code to fix a bug. Put the patch file in the main folder with the source code, i.e. /home/your_name/MyApp_Source_Code. Then go into the terminal, cd into the folder and type:
```
patch -p1 < patch_file.patch
```

The patch command will read the patch file and modify the source code accordingly.

---

### Post by cariboo on 2012-06-06
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by stmiller on 2012-06-06
This is how you patch a file:

```
patch -p1 < patchfile.patch
```

Cheers,

---

### Post by 3Miro on 2012-06-06
> **stmiller said:**
> This is how you patch a file:

```
patch -p1 < patchfile.patch
```

Cheers,

My bad, I fixed my post.

---

### Post by Kaspberger on 2012-06-07
Thanks for all the information. I had tried the first suggestion but, after it didn't process, I figured that I was doing something wrong and just abandoned it altogether... Now I know that it was just a typo.

And, to the admin, sorry for the double post.

---

