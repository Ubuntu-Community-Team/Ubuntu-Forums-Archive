---
title: "How to remove BTNX?"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by captgadget on 2008-05-04
When I try to remove it I get the message package not found. What am I doing wrong?

---

### Post by Monicker on 2008-05-04
Did you install from source?


Is this it?

[http://www.ollisalonen.com/btnx/man/btnx-manual.html#AEN259]("http://www.ollisalonen.com/btnx/man/btnx-manual.html#AEN259")


"make uninstall" is a standard way of removing applications compiled from source.  This is usually indiicated in the README or INSTALL files.

This thread might also help:

[http://ubuntuforums.org/showthread.php?t=455656]("http://ubuntuforums.org/showthread.php?t=455656")

---

### Post by captgadget on 2008-05-05
That's what gives me the message.

---

### Post by Monicker on 2008-05-05
> **captgadget said:**
> That's what gives me the message.


Please be more specific.  What error exact error message are you getting, and  what are you doing which causes it?

You also did not mention if you installed from source or not.

---

### Post by dondad on 2008-05-05
> **captgadget said:**
> When I try to remove it I get the message package not found. What am I doing wrong?


If you installed from source, then you have to change to the install directory to do the uninstall.

---

### Post by captgadget on 2008-05-05
When I copy and paste this in terminal: sudo apt-get remove btnx btnx-config
It returns this: E: Couldn't find package btnx
I did a search and the search comes back that btnx-conf is in hda1/usr/share/omf so I typed in  cd hda1/usr/share/omf
& I get this:No such file or directory

---

### Post by Xiong Chiamiov on 2008-05-05
If you installed it from source (doing a ./configure, sudo make, sudo make install?), then you have to navigate to the source folder (or redownload it if you don't have it any more), then do a
```

./configure
sudo make uninstall

```

---

### Post by Xiong Chiamiov on 2008-05-05
.

---

### Post by Monicker on 2008-05-05
> **captgadget said:**
> When I copy and paste this in terminal: sudo apt-get remove btnx btnx-config
It returns this: E: Couldn't find package btnx
I did a search and the search comes back that btnx-conf is in hda1/usr/share/omf so I typed in  cd hda1/usr/share/omf
& I get this:No such file or directory

If you installed from source, you can't remove it using apt-get.


Use "make uninstall".

---

### Post by captgadget on 2008-05-06
I followed the install procedure outlined on this webpage:[http://www.ollisalonen.com/btnx/man/btnx-manual.html#AEN259](http://www.ollisalonen.com/btnx/man/btnx-manual.html#AEN259)

All I want to do is remove btnx since it isn't working and I don't know how to do it.

Thanks to everyone for all the guidance.

---

### Post by mlentink on 2008-05-06
Again: we really need to know how you installed this in the first place. The website tells me that you could have done so through apt-get/synaptic (they list a repository), but also from source.
Which one was it?

---

### Post by yottaflops on 2008-06-17
I have the same problem of not being able to uninstall BTNX.

I have installed BTNX from source, and I realize I need to use make uninstall.  However, I don't know where the source directory is.

Can anyone point me to where this directory might be, or how to find out where it is?

Thanks.

---

