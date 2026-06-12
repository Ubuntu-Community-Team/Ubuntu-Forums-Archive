---
title: "Udate Manager &amp; Add/Remove Have Stopped Working...twice!"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by JEighmey on 2008-06-06
Hello, 

I am setting up a little printserver in Ubuntu 8.04 x64 (abit board, intel duo, 1gb mem) and have a recurrent problem. The update manager and software utility have stopped working. This happened two days ago and I completely re-installed, thinking I had inadvertantly cut off an installation. I have everything up and running again (not easy!) and now it has frozen..again. It was working five hours ago, so here are the changes I think I made since then: 

Set a static IP address (have since reverted to auto DNS...no change)
Set my workgroup to the local domain name
Reloaded the HP printing utility HPLIP to handle the HP printers
Set up TurboPrint to drive the Cannon printers. 

Thats about it. I am too much of a noob to have done anything outside the GUI.  Pretty frustrating. I cannot seem to get this thing stabile enough to do the job for more than a hour or two. 

:icon_frown:

---

### Post by briandu on 2008-06-06
Ok do this:

open xterm

enter:
apt-get upfate

and the update should work and bring your pc to spec.

---

### Post by SunnyRabbiera on 2008-06-06
You may have to jumpstart the repositories, this happens sometimes.

---

### Post by JEighmey on 2008-06-06
Thanks for the quick response!  
I entered 
<$ apt-get upfate>
and got 
<sudo: unable to resolve host Yahi
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [191B]> 

and a long list of other packages. Fair enough. But then I recieved a notice of three additional evolution updates. When I started the update manager it froze again! So I am updated, but the two install features still do not work.  Cannot "change software source" either (locks up). I though maybe it was a bad repository. 

Any other suggestions? Thanks in advance.

---

