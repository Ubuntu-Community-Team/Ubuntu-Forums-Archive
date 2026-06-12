---
title: "[SOLVED] how do I install ndisgtk without an internet connection"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by binobooks on 2008-08-17
I have determined that I need to install ndisgtk in order to get my netgear wb311v2 pci card to work with ubuntu... however.... I don't have an internet connection to the ubuntu desktop.  I saw that I can install this file in the live cd mode.. but can't with the installed desktop.. please help.. how do I get ndisgtk so my internet can work... I have spent over 5 hours on this

---

### Post by nicedude on 2008-08-17
You can add the CD to your sources and thereby install things from it. But you will also need a Windows XP driver that is for your adapter, and there won't be one on the ubuntu CD so you would have to get one off the net. I assume you have some form of Internet going or you couldn't leave the post.

---

### Post by neurostu on 2008-08-17
Here:
[http://packages.ubuntu.com/hardy/ndisgtk](http://packages.ubuntu.com/hardy/ndisgtk) 

or more specifically here:
[http://packages.ubuntu.com/hardy/i386/ndisgtk/download](http://packages.ubuntu.com/hardy/i386/ndisgtk/download) 

just google for :Ubuntu Package Hardy <package name>

---

### Post by binobooks on 2008-08-17
I have the .inf file for my driver... how do I add the CD to my sources?

---

### Post by DezSP on 2008-08-17
It appears to be down at the moment so I can't check, but you should be able to search out and download the right package [from here](http://packages.ubuntu.com/hardy/). That's assuming you're on Hardy Heron, if not, you need a different repository.

---

### Post by kool_kat_os on 2008-08-17
> **DezSP said:**
> It appears to be down at the moment so I can't check, but you should be able to search out and download the right package [from here]("http://packages.ubuntu.com/hardy/"). That's assuming you're on Hardy Heron, if not, you need a different repository.
ya...that would be the easiest way...without getting to complicated

---

### Post by binobooks on 2008-08-17
Okay... I figured out how to download the ndisgtk and the 2 ndiswrapper files into tte synaptic package manager from the live cd. and the windows wireless drivers interface is now available.  However, when I tried installing the .inf file it said it was and invalid driver.  what now
also... I can see wireless networks on the list but it just won't connect... is this a driver problem

---

### Post by kool_kat_os on 2008-08-17
> **binobooks said:**
> Okay... I figured out how to download the ndisgtk and the 2 ndiswrapper files into tte synaptic package manager from the live cd. and the windows wireless drivers interface is now available.  However, when I tried installing the .inf file it said it was and invalid driver.  what now
also... I can see wireless networks on the list but it just won't connect... is this a driver problem
by "it just won't connect" do you mean that it keeps on saying "Connecting" (i dont know if ubuntu says that, but you get what i mean)

---

### Post by binobooks on 2008-08-17
YAY!!!!!!!!!!!!!!!!!!!!!!!!!!  thanks for the help.. succefully loaded the driver into Windows wireless driver program and then resatarted my computer... and amazing.. it worked.  Thanks for the help.

---

### Post by nicedude on 2008-08-17
Glad you got it fixed and you can now mark this thread as "SOLVED" :-)

---

