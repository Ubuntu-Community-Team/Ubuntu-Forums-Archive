---
title: "[SOLVED] How do I do MD5Sum in Ubuntu?"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by andrewwg94 on 2008-10-07
look at my post down there

---

### Post by Elfy on 2008-10-07
In a terminal - 

```
md5sum /path/to/file
```

You can use tab to autocomplete the path

---

### Post by phidia on 2008-10-07
Open a terminal and enter "md5sum <filename>".

---

### Post by overdrank on 2008-10-07
> **andrewwg94 said:**
> read title^^

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by HellNoire on 2008-10-07
Using terminal, go to the directory the file is located and run md5sum.

desktop would be easiest with it being *cd ~/desktop* to change to it.

then type  *md5sum* and the name of the file.

Should pop up under Terminal a second later.

---

### Post by andrewwg94 on 2008-10-07
this is the name of the file:
xubuntu-7.04-desktop-powerpc+ps3.iso

it's on my desktop, and my username is 'andrew'
 
please give me the exact command because this wont work

---

### Post by HellNoire on 2008-10-07
open terminal
cd ~/Desktop
md5sum xubuntu-7.04-desktop-powerpc+ps3.iso

That should be all you need to do.

---

### Post by bodhi.zazen on 2008-10-07
The easiest way is with the -c flag

Lets say you have a file , foo, and the md5sum in a file foo.md5

(or an ubuntu iso and the MD5SUMS file)

```
md5sum -c foo.md5
```

---

