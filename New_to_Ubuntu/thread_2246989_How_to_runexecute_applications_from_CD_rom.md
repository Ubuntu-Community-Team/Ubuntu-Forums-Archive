---
title: "How to run\execute applications from CD rom?"
date: 2014-10-04
forum: New to Ubuntu
---

### Post by han5 on 2014-10-04
I can use some help. Here is the problem video:
[https://www.youtube.com/watch?v=nIezuWVuVRM&feature=youtu.be](https://www.youtube.com/watch?v=nIezuWVuVRM&feature=youtu.be)

---

### Post by yancek on 2014-10-04
You can't change permissions or anything else really on a CD as a CD uses iso-9660 filesystem which is read-only.  You changed permissions for the runner file when it was on your Desktop but for some reason these permissions were not saved when you copied it to the CD.     You video also shows "unable to locate program" error.  You might check the script paths which it expects to run.  Can't think of any other options.  Does it work when you run it from the Desktop of the installed Ubuntu or have you tried that?

---

### Post by ian-weisser on 2014-10-04
Many possible causes, and their solutions, are discussed at [http://askubuntu.com/questions/22778/how-can-i-run-an-executable-from-a-cd-when-it-doesnt-have-the-executable-bit-se](http://askubuntu.com/questions/22778/how-can-i-run-an-executable-from-a-cd-when-it-doesnt-have-the-executable-bit-se)

---

