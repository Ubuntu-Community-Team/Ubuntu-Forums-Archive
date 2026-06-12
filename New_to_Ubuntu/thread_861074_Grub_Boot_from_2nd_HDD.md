---
title: "Grub Boot from 2nd HDD"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by Dumpy Dumpster on 2008-07-16
I have installed Puppy on HDD2 with Hardy on HDD1.  But the Grub menu on startup only gives Ubuntu options.  I feel that I must adjust the jumpers on the two HDDs.  If this is so, what should each be set to - i.e. Master/Slave/Cable select?
While I have your attention, is there any way to increase the time in which to press ESC to view the Grub options - it is set at 3 secs at present whereas Feisty was 10 seconds?

---

### Post by aomlives on 2008-07-16
> **Dumpy Dumpster said:**
> While I have your attention, is there any way to increase the time in which to press ESC to view the Grub options - it is set at 3 secs at present whereas Feisty was 10 seconds?

It's an option in /boot/grub/menu.lst I think.

---

### Post by benfindlay on 2008-07-16
You should be able to manually add your extra boot options to the end of the grub menu.lst file. There are pelnty of guides on the forum to help you with this!

You edit grub's config file with ```
sudo gedit /boot/grub/menu.lst
```

Also, in here you can change the timeout value from 3 seconds to whatever you want!

Hope this helps!

---

### Post by Dumpy Dumpster on 2008-07-16
Thanks - done the bit on the timing.  But I am not up to writing a bit to boot into Puppy.  Any help here?
Also can one delete old versions of linux kernel i.e. 2.6.24-18 and 16 in both generic and generic(recovery mode)?

---

### Post by benfindlay on 2008-07-16
Ok, I'm a little bit rusty on this, so I have to say BACKUP YOUR MENU.LST FIRST! ;)

Right, try adding the following to the end of the menu.lst file:> title Puppy Linux
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd0,0)
chainloader +1

If that doesn't work, try > title Puppy Linux
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

If either of these work, please let me know which!

Also, yes you can remove old ones, but as I understand it, linux removes them automatically for you each time you update the kernel. It keeps the previous version each time you update the kernel in case the update breaks your system. That way you can boot the old kernel, remove the new one and your back to full working order again. Therefore I'd recommend you leave them in.

Hope this helps!

---

### Post by philinux on 2008-07-16
> **Dumpy Dumpster said:**
> Thanks - done the bit on the timing.  But I am not up to writing a bit to boot into Puppy.  Any help here?
Also can one delete old versions of linux kernel i.e. 2.6.24-18 and 16 in both generic and generic(recovery mode)?

I leave the old kernels in. Sometimes you might need to use them if an update breaks things.

If you install startupmanager you can change all sorts of boot stuff with it's nice gui. Including countdown timer and the number of kernels to show.

You might be as well using the supergrub disk or reinstall grub from the live cd. That way it will pick up both os's for you.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Dumpy Dumpster on 2008-07-16
Sorry, fellas.  I have read through Supergrub and I cannot make head or tail of it!  It is Double Dutch to me.  It seems that Ubuntu have one numbering system for discs and yet I find others in use as well  e.e. hdo and sda1 and so on and then there are partition numbers( which I do not have).  If I can't get anywhere I will just scrub off the Puppy and put it down as unfriendly!  I do not want to start messing about with menu lists in the dark

---

