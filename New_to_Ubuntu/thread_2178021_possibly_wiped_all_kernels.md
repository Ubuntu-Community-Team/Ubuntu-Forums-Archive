---
title: "possibly wiped all kernels ?"
date: 2013-10-01
forum: New to Ubuntu
---

### Post by ButchMel on 2013-10-01
As i had warnings over recent weeks that my boot partition was full, i looked for a solution and found:[http://ubuntuforums.org/showthread.php?t=1435818](http://ubuntuforums.org/showthread.php?t=1435818)

I applied simply the line for removing the whole bunch of kernels as explained there. 

Everything was ok until i rebooted and now i only get a blue screen with memory counting and it goes no further.

I was told i possibly inverted boot order, and that i should just go in the grub menu then select the right kernel...

However, i have no idea how to do this.  If i press and maintain the SHIFT (is that the one?) key at boot up, it does nothing and i eventually have to press F1 which brings me again to that blue screen.

I am using 10.04 LTS (server) and use the gnome grafic interface even though it's a server.

Thanks for any help on this

---

### Post by VMC on 2013-10-01
Did you apply the "1-liner" from post#5. If so what, do you remember, was removed. What kernel was left.

I think also the shift key will bring grub into focus.

Can you dump the contents of grub.cfg using a livecd and copy the results back here?

---

### Post by poettone on 2013-10-01
I can see how this can happen as I've done it before. 

Please read the following link and see if you can get back to a running system using the steps listed here: 

[http://askubuntu.com/questions/145241/how-do-i-run-update-grub-from-a-livecd](http://askubuntu.com/questions/145241/how-do-i-run-update-grub-from-a-livecd)

what this is allowing you to do is to change your grub file to point to the proper kernel to allow your system to boot to the correct kernel by changing/updating the boot system (Grub) in Ubuntu.

Thanks

---

### Post by tgalati4 on 2013-10-01
Since you will have to boot to a LiveCD to fix or troubleshoot this problem, try listing what it in /boot.  That is where your kernels are (or were).

It will be mounted when you click on the hard disk icon on the desktop and will be found in /media/disk/boot.  Disk may be called something else depending on what LiveCD that you use.

*Only delete the kernels that you don't want to boot into.*

---

### Post by ButchMel on 2013-10-02
> **VMC said:**
> Did you apply the "1-liner" from post#5. If so what, do you remember, was removed. What kernel was left.

I think also the shift key will bring grub into focus.

Can you dump the contents of grub.cfg using a livecd and copy the results back here?


Just to make it clear: do I have GRUB considering the only OS on this machine is Linux ?

---

### Post by VMC on 2013-10-02
Linux needs something to boot from, so yes, you have grub2, unless of course you install another boot program. 
What can make this more clear is to download and run bootinfoscript (see my blue link) then paste the output back here, between "[CODE]" tags.

---

