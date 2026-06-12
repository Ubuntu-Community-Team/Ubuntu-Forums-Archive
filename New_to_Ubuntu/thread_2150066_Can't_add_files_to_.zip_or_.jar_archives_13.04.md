---
title: "Can't add files to .zip or .jar archives 13.04"
date: 2013-05-30
forum: New to Ubuntu
---

### Post by Thunder7102 on 2013-05-30
Whenever I attempt to drag a file into a folder of a jar or zip, it says "An Error has Occurred". If I try to click "Add File" nothing happens. I have tried multiple archive managers and I cannot seem to find a fix. I just want to be able to add .png's to a .jar file. I thought it would be easier than this...

I have very little experience with the command-line, but I am familier enough to move around, change owner, permissions, and copy/remove files. I have no idea what to do with .jar's, but I'd like to think GUIs should support all archives, especially something as well-known as a jar.

My installation was a blank 13.04 install in the past week (it was a reinstall), and I had to run an installation aid to the harddrive due to GRUB not getting reinstalled correctly.

---

### Post by Thunder7102 on 2013-05-31
No solution? I really need this to work with .jars in Eclipse, and I thought Ubuntu worked great with programming...do I have to switch back to Windows to do even that?

---

### Post by drbcladd on 2013-07-02
Workaround: Had similar problem. Wanted to add an image file to a resources folder in an existisg .jar file. Archive Manager gave an unhelpfully terse error message with drag or Add Files.... I can add files to the root of the file (I used Add Files...) and I can cut and paste the file within the archive. I did not uncover the cause of the problem though I may have to since the workaround is awkward.

---

### Post by wsxadf on 2013-07-03
Can you try this?

```
jar uf jar-file-name.jar input-file-name
```

The u option indicates that you want to *update* an existing JAR file. The f option indicates that the JAR file to update is specified on the command line. The first argument is the name of the jar file, *.jar, and the second argument is the name of the file that you want to update into jar.

---

