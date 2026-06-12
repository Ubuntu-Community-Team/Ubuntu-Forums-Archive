---
title: "Ubuntu support for old PC"
date: 2008-03-12
forum: Other OS Talk
---

### Post by Saponsky09 on 2008-03-12
Hi there, the thing is I have an old  machine with the following specs: 
- Pentium IV 2.5 GHz processor.
- 128 MB RAM
- 40 GB Master HD
- 20 GB Slave HD
- CD-RW unit
- floppy drive
 
  I've installed Ubuntu 7.10 and it runs 'ok' but I use the machine to provide remote services while I'm on the go with my laptop. By services I mean MySQL, ssh, CUPS for printing purposes, Apache, and some others.  Can you sugest me a ligth distibution to run all these services 'better-than-ok' and that is fully compatible with my Ubuntu 7.10 laptop???  I would prefer an Ubuntu related one.  If not, can you tell me what i need to do to make the already installed Ubuntu 7.10 lighter??? I've already removed most of the graphical applications and every unneeded one.  Thanks for your attention.

---

### Post by jrusso2 on 2008-03-12
It would be best if you bought more ram.  That would help a lot.  I am surpised that 7.10 runs on 128 mb of ram.

If not try Fluxbuntu thats a lot lighter, or Damn Small or Puppy Linux or even Slackware with XFCE

---

### Post by jcwmoore on 2008-03-12
do you have the desktop edition or server edition.
I have a P III 500 MHz 98 M RAM running server edition and it is great for a file server, web site host, and mysql DB host.  There is no desktop installed on this system (command line only) and it runs great.  Adding a desktop, Gnome, KDE or xfce, greatly increases the horse power your PC needs.  Every thing that I need GUI wise, I use on my laptop and remote into that machine, like mysql management and file management.  If you need a desktop for day to day use then based on what you provided you just need a lighter desktop to improve performance.  I suggest you install the xfce desktop and use it rather than the default (gnome desktop)

---

### Post by Saponsky09 on 2008-03-12
Tanx for your replies.
1- No I didn't installed the server edition but then I installed php, mysql, apache and so on so you know...
2-And Yep it is running the Desktop edition. 
 And.. on the other hand.. how do I install Xfce if I have already Gnome installed???

---

### Post by wolfen69 on 2008-03-12
no disrespect to the OP, but there's at least a million of these type posts in other OS. every other day someone asks about an OS for old computers. cant we have one thread (i know there's a sticky) devoted to it?

---

### Post by jcwmoore on 2008-03-12
> **Saponsky09 said:**
> Tanx for your replies.
1- No I didn't installed the server edition but then I installed php, mysql, apache and so on so you know...
2-And Yep it is running the Desktop edition. 
 And.. on the other hand.. how do I install Xfce if I have already Gnome installed???

look here

[http://http://www.debianadmin.com/install-xfce-desktop-in-ubuntu.html]("http://http://www.debianadmin.com/install-xfce-desktop-in-ubuntu.html")

---

### Post by ksennin on 2008-03-12
> **wolfen69 said:**
> no disrespect to the OP, but there's at least a million of these type posts in other OS. every other day someone asks about an OS for old computers. cant we have one thread (i know there's a sticky) devoted to it?

  It still feels weird to hear a P4-2.5ghz called "an old PC".  I am still doing most of my CAD and STAADPro structural design on a P4-3ghz.

  That machine just needs more ram and the server version.

---

### Post by jcwmoore on 2008-03-12
> It still feels weird to hear a P4-2.5ghz called "an old PC"

well I feel bad saying that my 700 MHz machine is "old."  It runs just fine as a basic desktop, spread sheets, word processing, internet, email, basic stuff...

---

### Post by bluewraith on 2008-03-12
I know theres a wiki page that explains how to install ubuntu 7.10 minimal... it starts from the server edition and then you build up from there. I hear its pretty spunky on older hardware, too. You might want to think about getting more RAM though... 128 is pretty low, especially for that speed proccessor. Maybe enlarge the swap drive too and stick it on the slave.

---

### Post by K.Mandla on 2008-03-13
> **Saponsky09 said:**
> Hi there, the thing is I have an old  machine with the following specs: 
- Pentium IV 2.5 GHz processor.
- 128 MB RAM
- 40 GB Master HD
- 20 GB Slave HD
- CD-RW unit
- floppy drive
 
  I've installed Ubuntu 7.10 and it runs 'ok' but I use the machine to provide remote services while I'm on the go with my laptop. By services I mean MySQL, ssh, CUPS for printing purposes, Apache, and some others.  Can you sugest me a ligth distibution to run all these services 'better-than-ok' and that is fully compatible with my Ubuntu 7.10 laptop???  I would prefer an Ubuntu related one.  If not, can you tell me what i need to do to make the already installed Ubuntu 7.10 lighter??? I've already removed most of the graphical applications and every unneeded one.  Thanks for your attention.
That's not old. [This]("http://ubuntuforums.org/showthread.php?t=294292") is old.

Put a little more memory in it and keep the desktop you have. It'll be easier to manage with a GUI than a server installation, and a Pentium 4 is more than enough to handle remote services.

---

### Post by wolfen69 on 2008-03-13
> **jcwmoore said:**
> well I feel bad saying that my 700 MHz machine is "old."  It runs just fine as a basic desktop, spread sheets, word processing, internet, email, basic stuff...

exactly. i just paid 25$ for a laptop. win98 on it. i'm really glad im all linux now.
 i fix win pc's for $,
 do what ya gotta do.

---

### Post by daengbo on 2008-03-13
See my post about this here:
[http://www.ibeentoubuntu.com/2008/02/installing-ubuntus-on-windows-98-era.html](http://www.ibeentoubuntu.com/2008/02/installing-ubuntus-on-windows-98-era.html)

---

### Post by ksennin on 2008-03-13
> **jcwmoore said:**
> well I feel bad saying that my 700 MHz machine is "old."  It runs just fine as a basic desktop, spread sheets, word processing, internet, email, basic stuff...
Just this week I turned on (ahem) my old PentiumI-133mhz/64ram.  Standalone, but it still can run spreadsheets, documents, browse images, and run the 3.1 version of StaadPro, which I can design a 30,000 sq. feet building with.

I hate unnecessary hardware escalation demands.

---

### Post by ksennin on 2008-03-13
> **wolfen69 said:**
> exactly. i just paid 25$ for a laptop. win98 on it. i'm really glad im all linux now.
 i fix win pc's for $,
 do what ya gotta do.
A $25 laptop?  Cool.  I wouldnt mind finding one on that range.  What specs?

---

### Post by Saponsky09 on 2008-03-13
Ok, here go the "Oops" lol, by "old PC" I just wanted to referr to it that way because the laptop I mention is "new" like brandnew.  I wasn't referring to old hardware hehe, just ownership. :D .  And yes, I have in mind adding more RAM, changing its CPU fan to more silent one (the actual one is too noisy) and adding a larger HD as slave 'cus the one I currently have, pertains to a P-III PC with a damaged video card (which I also plan to repair and put some linux flavor to it :D). Sorry for the "old" issue, I hope P-IV users didn't get offended hehe.

---

### Post by seanc7 on 2008-03-14
For Ubuntu a P4 is not old. Just up the RAM to 512MB and you'll be set.

Never mind I missed a couple of the posts...

---

### Post by emshains on 2008-03-15
You call that old?

Pfff. p3 are still quite new....

Gosh get  ram and you wont complain about speed.

---

