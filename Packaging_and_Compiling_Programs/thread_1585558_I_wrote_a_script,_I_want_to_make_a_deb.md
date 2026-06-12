---
title: "I wrote a script, I want to make a deb"
date: 2010-09-30
forum: Packaging and Compiling Programs
---

### Post by kr651129 on 2010-09-30
So I wrote a script to download and extract tools into the correct directories.  It's a real simple script filled with wget, tar xvf, mkdir, and rm

So my question is how do I make a deb out of this?  Or could i just download the packages and ball them up in the deb and have my deb extract them to the correct place and then run a post install script adding the correct variables to the bashrc?

---

### Post by Sub101 on 2010-09-30
Take a look here:

[http://ubuntuforums.org/showthread.php?t=545380](http://ubuntuforums.org/showthread.php?t=545380)

---

### Post by kr651129 on 2010-09-30
thank you so much!

---

### Post by kr651129 on 2010-10-01
so I created the deb, and I made a post install script that the deb runs.  But the line of code the appends some variables to .bashrc wont work, but it works if I run the script from term

ideas?

---

