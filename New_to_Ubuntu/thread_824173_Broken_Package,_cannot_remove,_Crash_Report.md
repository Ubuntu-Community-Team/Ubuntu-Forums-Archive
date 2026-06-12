---
title: "Broken Package, cannot remove, Crash Report"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by cwmoser on 2008-06-09
I tried to install the Brother MFC-440CN printer driver but it won't install.  I am trying to remove the package "mfc440cncupswrapper" but Synaptic can't remove it.  I get a Crash Report.

E: mfc440cncupswrapper: subprocess pre-removal script returned error exit status 127

I am at a deadlock -- what should I do????

Thanks

Carl

---

### Post by Vadi on 2008-06-09
Try "sudo apt-get install -f" and then removing it again. Does that help?

---

### Post by Paul Vega on 2008-06-13
Hi there
I am having a similar problem (again) with my Brother DCP-130C. I also have a broken package with the following error message;

paul@paul-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package dcp130ccupswrapper needs to be reinstalled, but I can't find an archive for it.
paul@paul-desktop:~$ 


Can anyone point me in the right direction?

Paul Vega

---

### Post by hyper_ch on 2008-06-13
where is the .deb file?

Try to run:

```

sudo dpkg -i filename.deb

```

---

### Post by Paul Vega on 2008-06-13
Kia Ora Hyper_ch

Thanks for the help. Here is what I get,

dpkg: error processing filename.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 filename.deb

As you may have guessed, I am a bit green with this. 

Paul

---

### Post by hyper_ch on 2008-06-13
you have to run this command in the location where you did download those drivers to (assuming it's a .deb file) and of course you have to rename filename.deb with the actual one.

---

