---
title: "[SOLVED] Practice Linux on Windows?"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by melbs on 2008-07-25
Hi all, forgive me if this isn't strictly about Ubuntu but does anyone know any programs (online or offline) that I could run on Windows Vista to practice Linux commands? Like a fake terminal or something?

I do have Hardy Heron installed on my desktop computer I want to be able to practice Linux on my lap top, which is Vista.

Any help would be much appreciated. Thank you.

---

### Post by Thelasko on 2008-07-25
cygwin or xming.  Considering you seem mostly interested in the terminal, you should probably go with cygwin.

---

### Post by cozmicharlie on 2008-07-25
Also, you can set up Linux in Windows as a Virtual Box.  It is real easy and it allows you to run a full Linux distro in Windows.  It is free also.  Go here to check it out [http://www.virtualbox.org/](http://www.virtualbox.org/).

enjoy

---

### Post by fatality_uk on 2008-07-25
Can I also suggest Wubi. That gives you easy dual boot functionality and if you need to grab Vista back, just un-install Linux

---

### Post by ohjajoh on 2008-07-25
You could run ubuntu live too....

---

### Post by melbs on 2008-07-25
Great, thanks! I'll check out all of your suggestions : )

---

### Post by gunashekar on 2008-07-25
> **melbs said:**
> Great, thanks! I'll check out all of your suggestions : )

Good luck with your practice. If you think any of these suggestions solves your question, do remember to mark your thread as SOLVED.

---

### Post by melbs on 2008-07-25
Oh, will do! I am currently installing Cygwin to see how it will work out.

---

### Post by Darkade on 2008-07-25
You can download [Damn Small Linux]("http://www.damnsmalllinux.org/"), the embeded.zip file, and run it inside windows, at the office that's what I do LOL

---

### Post by rossjman1 on 2008-07-25
I used to use quemu (sp?), which is a simple virtual machine.

---

### Post by SunnyRabbiera on 2008-07-25
The best way to learn in my experience is to use the live CD.

---

### Post by AndyCooll on 2008-07-25
There's also [SDF public access unix system]("http://sdf.lonestar.org/index.cgi"). You can sign up for an account and you have access to an online Unix server. Play around on that.

:cool:

---

### Post by melbs on 2008-07-25
I just installed cygwin. At first it said the installed failed, I re tried and it seemed to work. I opened up the terminal and typed "su" but it said there was no root user. Is this normal? Also, I'm a little confused as to what directory it is going to. Is it going to the cygwin folder it created itself or is it going into my windows files? Thanks. 

Man too many programs too look into! Thanks guys.

---

### Post by Joeb454 on 2008-07-25
It creates a folder at C:\cygwin

In there it contains the usual file structure :)

That said, I think wubi may be of interest to you, as it installs Ubuntu under Windows. You can choose to run Ubuntu as opposed to Windows then (as a full installation), and if you want to get rid of it, you can remove it from Control Panel &#8594; Programs & Features :D

I believe it comes on the 8.04 cd by default too :)

---

### Post by Vivaldi Gloria on 2008-07-25
> **cozmicharlie said:**
> also, you can set up linux in windows as a virtual box.  It is real easy and it allows you to run a full linux distro in windows.  It is free also.  Go here to check it out [http://www.virtualbox.org/](http://www.virtualbox.org/).

Enjoy

+1

---

### Post by unicorn_2003_1 on 2008-07-25
Use Wubi, do it now! Virtual machines can't give you the whole experience, I'd tap Vbox/Xen for servers, but not a desktop.

---

### Post by cozmicharlie on 2008-07-25
cygwin may be a bit difficult for someone just learning Linux.

---

### Post by melbs on 2008-07-25
I think the main thing I want to be able to do is be on my Vista OS but practice and work with the terminal. cygwin looks like it may help but I'm going to look into the ones mentioned a couple of times and test them out!

---

### Post by kdb424 on 2008-07-25
you want linux IN windows? andlinux.org It is quite amaxing. You get everything linux except the linux desktop!

edit: org not com

---

### Post by Vivaldi Gloria on 2008-07-25
> **unicorn_2003_1 said:**
> Virtual machines can't give you the whole experience.

I can't see why unless you're trying to get 3D or multithread support in it. Care to explain?

Besides:

1) You can break an OS in vm as you wish. No worries. 
2) You can try any OS in vm, not only ubuntu.
3) You can run as many OSes at the same time as you want.
4) Much easier to backup and/or copy.

---

### Post by kdb424 on 2008-07-25
> **Vivaldi Gloria said:**
> I can't see why unless you're trying to get 3D or multithread support in it. Care to explain?

Besides:

1) You can break an OS in vm as you wish. No worries. 
2) You can try any OS in vm, not only ubuntu.
3) You can run as many OSes at the same time as you want.
4) Much easier to backup and/or copy.


You loose things like finding drivers, compiz fusion, and believe me, when you have 2 desktops on the screen, even n mac with 2 spaces, it feels like one is a VM. It's never the same.

---

### Post by Vivaldi Gloria on 2008-07-25
> **kdb424 said:**
> You loose things like finding drivers

I don't understand what you mean.

> **kdb424 said:**
>  compiz fusion, 

And I already said above that you cannot get 3D effects in vm. So what? OP wants to learn command line, not see 3D effects.

> **kdb424 said:**
> and believe me, when you have 2 desktops on the screen, even n mac with 2 spaces, it feels like one is a VM. It's never the same.

Then goto fullscreen (rightCTRL+F in virtualbox).

Please go above and read my post above again. Can you do any of those things in wubi? Wubi is a joke for people who know how to partition.

---

### Post by melbs on 2008-07-25
I'm going to try out the Virtual Box app. I'm going to download it but how do I know if it's Windows AMD64 or Windows x86? I'm running Vista on a fairly new lap top.

---

### Post by Vivaldi Gloria on 2008-07-25
> **melbs said:**
> I'm going to try out the Virtual Box app. I'm going to download it but how do I know if it's Windows AMD64 or Windows x86? I'm running Vista on a fairly new lap top.

Are you running vista 32 bit or vista 64 bit?

---

### Post by melbs on 2008-07-25
32 bit

---

### Post by Vivaldi Gloria on 2008-07-25
> **melbs said:**
> 32 bit

Then download the windows x86 version from here:

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

---

### Post by melbs on 2008-07-25
I installed Virtual Box and created a new virtual machine (ubuntu). When I start it up it tells me "no bootable medium found" system halted.   Any ideas on what's wrong?

---

### Post by Joeb454 on 2008-07-25
You need to install Ubuntu in virtual box ;)

---

### Post by melbs on 2008-07-25
That might be a good idea. Do I have to have it on a CD or can I just download it on my computer and install it that way?

---

### Post by Joeb454 on 2008-07-25
Either.

I believe VirtualBox can mount the .iso file straight from your PC. That way you don't have to burn a CD

---

### Post by melbs on 2008-07-25
Everything is working well so far. The only thing I can't figure out is that it gives me a warning that I am using the 16 bit of color in the virtual box and I should switch it to 32 bit. How do I do this?

---

### Post by cozmicharlie on 2008-07-26
I checked there VB  forums and saw a few posts with the same problems.  The only fix I could find was to install the Guest Additions.  The web site has a good tutorial on how to do this.  It will be good practice for your command line skills.

Also, since you are practicing your commands in terminal this may come in handy .
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

---

### Post by melbs on 2008-07-29
Thanks for all of the info guys!

---

### Post by cozmicharlie on 2008-07-30
Glad it worked out for you.  Please mark the thread as solved.

Enjoy!

---

