---
title: "lost openoffice.org"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by bradleyporter on 2008-05-13
I have recently converted to Ubuntu so am experiencing what I hope are the usual teething problems. open office was working fine until I need to open a .pub file. this meant downloading Scribus. However I then found I couldn't open any of the other open office applications. I tried re-installing it from the synaptic package manager and later downloading it from the site - to no avail.I have since tried going to the terminal and loading the following...mv .openoffice.org2/ old.openoffice.org...which didn't work either. Any suggestions?
Also if I try to open a .doc file the attached screenshot appears:

---

### Post by pytheas22 on 2008-05-13
You could try:
```

sudo apt-get remove --purge openoffice*
```

and then reinstall the application using Synaptic.  This should clear out configuration files and hopefully solve the problem.

---

### Post by gn2 on 2008-05-13
This might be useful reading: [http://wiki.scribus.net/index.php/Import_Publisher_to_Scribus](http://wiki.scribus.net/index.php/Import_Publisher_to_Scribus)

---

### Post by SlappyPappy on 2008-05-13
Hey Bradley, you double posting? You dog you!  :)

You do know that .pub files can't be opened in Scribus. That file type is proprietary to Microsoft. If you're absolutely stuck having to use .pub files you should use VirtualBox and install Windows and the appropriate Windows software.

I use Scribus and it works fine. I'm using the version in Synaptic. Hope you figure out what happened to OO.

---

### Post by bradleyporter on 2008-05-14
sorry about that not quite sure why that happened. Thanks for the feedback, I've resorted to phoning a friend who has sorted out the problem for me.

---

### Post by bradleyporter on 2008-05-14
thanks

---

