---
title: "Programming with wxPython in Linux"
date: 2006-06-02
forum: Programming Talk
---

### Post by rowanparker on 2006-06-02
Hello,
I'm rather new to programming (all though I'm good at PHP) and was wanting to create cross-platform apps using wxPython. For Windows, I would use py2exe and that would include the wxPython files in the exe. But for Linux, I was going to give out the source but was thinking the person would need to have wxPython installed for it to work. Is there anyway way to ship the files needed with my program so it's an easier installation or is there a better way to do it?

Thanks, Rowan.

---

### Post by Corvillus on 2006-06-02
Typically, the Linux way to do this would be to distribute your application in a package, and make it dependent on Python, wxPython, and whatever other applications or libraries it needs to run. I don't know too much about how to actually go about doing this though.

---

### Post by rowanparker on 2006-06-02
Ok, Thanks.
Is there anyone who does know about this?

---

### Post by toojays on 2006-06-02
The [Debian New Maintainer's Guide](http://www.debian.org/doc/maint-guide/) is the first place to start when you're learning about the package system. After you know the basics of packaging, have a look at another package which depends on wxPython and see how they do it.

---

### Post by stani on 2006-07-18
This might als interest you: [howto install latest wxPython & SPE (Feature rich Python IDE)]("http://www.ubuntuforums.org/showthread.php?t=218001&highlight=wxpython").

---

