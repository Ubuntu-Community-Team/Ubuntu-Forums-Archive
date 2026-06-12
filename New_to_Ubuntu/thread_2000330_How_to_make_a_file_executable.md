---
title: "How to make a file executable"
date: 2012-06-09
forum: New to Ubuntu
---

### Post by sanderella on 2012-06-09
I have downloaded OpenJDK Java 6 Runtime because I need it to enable my Internet Scrabble Club game. I did it using the Terminal. But when I try to use it I got the following message:

"The file '/home/sandra/Desktop/wordbiz.jar' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit."

I did download it from a trusted source, and I do want to make it executable, and I don't understand the complicated instructions on [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Please can someone give me a simple code to make this file executable? :confused:

---

### Post by MG&amp;TL on 2012-06-09
Either right-click on the file->Properties->Permissions->Allow executing file as a program, or (terminal)

```
chmod +x <file>
```

---

### Post by Enigmapond on 2012-06-09
Simple way: Right-click/Permissions and click executable.

---

### Post by sanderella on 2012-06-09
Thanks guys, Scrabble up and running now. :KS

---

