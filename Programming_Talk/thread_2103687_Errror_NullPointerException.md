---
title: "Errror: NullPointerException"
date: 2013-01-10
forum: Programming Talk
---

### Post by loremaster on 2013-01-10
Hi guys,

I am trying to create a file object with a pathname to a file directory  and using the method listFiles() to return an array of pathnames under this file directory.

The code: 

File allFile=new File("~/Desktop/matlab/CAT_00");
File[] fileList = allFile.listFiles();

However when i ran the the code, i get an exception declaring 

Exception in thread "main" java.lang.NullPointerException
    at CatTest.main(CatTest.java:29)
Java Result: 1

So it appears that either my allFile object contains null object? I am not really sure myself. I tried checking the directory path that i wanted which was "~/Desktop/matlab/CAT_00" and it was correct. So i can't really figure out what can be wrong here?

Edit:

I tried using the debugging mode to check these 2 lines of code and found that listFiles() returned this exception error. However i do not understand why there should be an null exception error since there was files and directories under the CAT_00 main directory i created the File object with in the 1st place and hence should have returned an array of pathnames for these files and directories instead.

Help is appreciated! Thank you!

---

### Post by bird1500 on 2013-01-10
You either feed a path starting with "." or "/" or the name of the dir (These 3 options are for relative paths) or the full (absolute) path of the dir. Java doesn't understand/decode the "~" to the home path. So Java doesn't find the directory with that path and returns null for allFile, hence when you call a method on it it throws a null pointer exception.

---

### Post by muteXe on 2013-01-11
> 
So it appears that my allFile object contains null object?


No, it means your allFile object IS a null object.  Follow bird1500's post and put in the full path to your directory.

When you're doing stuff like this it's always good to test for nullness, or stick a try/catch around it.

---

