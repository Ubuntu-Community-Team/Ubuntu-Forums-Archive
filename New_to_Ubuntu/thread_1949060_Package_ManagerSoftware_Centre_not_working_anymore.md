---
title: "Package Manager/Software Centre not working anymore."
date: 2012-03-29
forum: New to Ubuntu
---

### Post by miguelratone on 2012-03-29
Hi all, 

new to the forum and Kubuntu/linux but trying my best!

Got a problem with the Package Manager and MUON software Centre, it was working fine and I have managed to install and uninstall several programms using Package Manager and MUON. However, this week I have been getting the following message in both:

"unable to select package s..."

"Another application seems to be using the package system at this time. You must close all other package managers before you will be able to install or remove any packages."

As far as I can see nothing else is using it, but then I'm new to this. 

Can anyone help?

Quick graphical fix preferred but command line ok (just be gentle as I'm still learning).

Thanks in advance!

Mick

---

### Post by jerrrys on 2012-03-29
If you have more than one package manager open or trying to use apt-get in terminal with a package manager open, you will get this message.

Terminal command for installing a package:

sudo apt-get install [COLOR=Black]NAME-OF-PACKAGE[/COLOR]

---

### Post by cortman on 2012-03-29
The simple answer: If you have no other package programs running and it still gives the error, reboot.
The more involved answer that will also tell you some of how it actually works: [This post.]("http://cortman.wordpress.com/2012/02/24/unable-to-obtain-lock-for-software-installation/")

---

