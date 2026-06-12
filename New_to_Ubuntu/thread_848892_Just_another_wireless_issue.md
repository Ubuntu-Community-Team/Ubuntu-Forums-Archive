---
title: "Just another wireless issue"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by simynona on 2008-07-03
I am a noob of all noobs, and i just installed the latest version of Ubuntu on my Gateway T-1628 laptop. It has a built-in wireless receiver, but I'm getting no connection. I have a wireless signal coming from a Windows computer in my house, and it worked just fine when I booted up in Windows on my laptop. It makes me very sad that I have no internet, and that I have to use this yucky Windows computer instead.

Please help me.

---

### Post by Dark_Stang on 2008-07-03
What type of wireless card is it? If you don't know open up a terminal window, and run "lspci" (without the quotes) and post it's output. Then run "lsusb" and post it's about.

---

### Post by ZabiGG on 2008-07-03
Hi and welcome to Ubuntu :)

I'm sorry to say that wireless is one of the most complex things to set up in Ubuntu. There are a number of HowTos 

[here]("http://ubuntuforums.org/showpost.php?p=5129251&postcount=4")

But first, you might want to familiarize yourself better with the terminal and Ubuntu in general (following the howtos can be confusing if you do not understand how the commands work).

For getting started info, and a great guide on using the terminal for beginners, just click on the "Look here" link in my signature below. I'll also recommend ugm6hr's very informative sticky you'll find [here]("http://ubuntuforums.org/showthread.php?t=801404") 

Have fun. Ubuntu takes a little bit of work and has a tad of a learning curve, but it's definitely worth the effort :)

Z.

---

### Post by berksted on 2008-07-03
Your in good company. I eventually had to install ndiswrapper to get my wifi working, then I upgraded and it stopped working.

Anyone out there know of an out of the box USB wifi adapter or something that is friendly to Ubuntu? The laptop-wifi issues are certainly a problem for new users.

---

### Post by ZabiGG on 2008-07-04
That's called thread hijacking, Berk, but there's an easy answer to your problem here:

[http://ubuntuforums.org/showthread.php?t=824625](http://ubuntuforums.org/showthread.php?t=824625)

What happens when you use modules like ndiswrapper is that you have to recompile them every time there is a kernel upgrade (when your linux version changes).

Right now, if you enter the command 

uname -r

in a terminal, you'll probably get version 2.6.24-19-generic

When that version number changes, you'll need to do the steps described in the post above to update your module again.

If you experience problems with those instructions, please start a new thread ;)

But I don't think you need to replace your hardware. It's a quick fix.

Cheers,

Z.

---

