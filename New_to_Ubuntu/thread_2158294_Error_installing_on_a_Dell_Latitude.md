---
title: "Error installing on a Dell Latitude"
date: 2013-06-28
forum: New to Ubuntu
---

### Post by maemouse on 2013-06-28
I have been trying to install the free version of ubuntu on my Dell Latitude D630 which has Intel Centrino and runs Windows 7 at the moment. (I have no clue if this information is pertinent to the question, just trying to cover all my bases.) I downloaded the installation program from the ubuntu webpage and started it up by mounting the image using daemon tools, once I restarted the computer I had it try to run ubuntu as the OS. It said it was completing installation and then went to the ubuntu loading screen, it's stays that way for a minute and then says that it was unable to find a medium containing a live file system. Can anyone help me out? I don't know much about computers except the basics (and that I know enough about computers that I hate windows >_<), any help you can give would be appreciated.

---

### Post by Mark Phelps on 2013-06-28
> It said it was completing installation Did you know it was going to try to force an install on you?

Have you checked since then to confirm that Win7 still boots and runs OK?

---

### Post by maemouse on 2013-06-28
Yeah, Windows still works (it's how I'm typing this at the moment) Didn't force download, I hit the install button after all. (unless I have the definition of force install completely wrong)

---

### Post by kabukiM0n0 on 2013-06-28
This might seem silly. But did you mount the iso onto a usb/Dvd and boot from there?

---

### Post by maemouse on 2013-06-28
No I didn't... I'm not technically minded so I get most of my info from friends, I just used Daemon Tools and hit "mount image".

---

### Post by kabukiM0n0 on 2013-06-28
Try this:

(for usb)
Download [this]("http://unetbootin.sourceforge.net/") or [this]("http://sourceforge.net/projects/win32diskimager/") burn the bootable iso onto your usb. 
Edit your BIOS to boot from usb
Install

(from cd/Dvd)
burn an image from Nero onto your cd
change BIOS to boot from CD
Install

---

### Post by maemouse on 2013-06-28
That worked! Thank you so much!! Now the question is, how do I get all my files and programs onto Ubuntu?

---

### Post by kabukiM0n0 on 2013-06-28
Your files ... I'm not entirely sure the compatibility of a m$ partition while running linux ..but I think linux won't read them - so you would have to put them on some external device, and then put them back onto your new linux machine - assuming you are talking about files which were on your previous m$ internal hard drive. 
But there are others here with much more knowledge about this than I. 

And referring to your programs. Everything you need can be found in the software centre or Synaptics. If the program isn't linux compatible you can find an alternative .. or you could always use Wine.

---

### Post by Rob Sayer on 2013-06-28
I've written data files to and from the windows partition on the one machine I have windows on many times.  From ubuntu, anyway.  Windows doesn't recognize the linux partition.

But your programs?  They won't work unless you use an emulator, and that's complex for a newbie and not necessarily reliable.  I'd stick to your windows partition for windows programs.

I use mostly the same programs in linux as I did in windows.  That's because I was using linux ported programs in windows whenever possible anyway.  They're usually better behaved and won't screw up your windows registry.  But linux doesn't run windows executables per se.

---

