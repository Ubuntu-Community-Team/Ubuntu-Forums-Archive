---
title: "rmdir wget folder"
date: 2007-02-26
forum: Programming Talk
---

### Post by nhandler on 2007-02-26
I used wget to download a website. For testing purposes, I downloaded the google homepage. So, now I have an index.html file inside a [www.google.com](www.google.com) folder on my desktop. The only problem is I can't remove the folder from the terminal. I can remove it by right clicking it and moving it to the trash. If I use this command to remove it:
rmdir --ignore-fail-on-non-empty [www.google.com](www.google.com)
or
rmdir --ignore-fail-on-non-empty "www.google.com"

nothing happens. No error, no deletion. I'v tried using mv to rename the folder and then delete it, but that didn't work. According to the permissions, I am the owner. But even sudo can't delete it. Could someone give me a hand?

---

### Post by lloyd_b on 2007-02-27
In a terminal window:
"rm -r www.google.com"

In many years with Linux/Unix systems, I've NEVER used the "rmdir" command.  "rm" is simply easier to use.  The "-r" option stands for "recursive", which will delete all files and subdirectories underneath of the specified directory (if you attempt to "rm www.google.com", you'll get an error unless the directory is empty).

Lloyd B.

---

### Post by nhandler on 2007-02-27
Thank you, that worked great. I never knew you could use rm to delete a folder.

---

