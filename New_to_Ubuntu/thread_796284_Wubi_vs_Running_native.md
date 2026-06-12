---
title: "Wubi vs Running native"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by maddkid53 on 2008-05-16
I am currently running Hardy Heron through Wubi, and I want to know if there is any real difference between Wubi and running it natively.

Also, is there a way to save all of my current settings, so if I reinstalled Ubuntu natively, I could like drag and drop a folder somewhere and all my old settings would be back?

thanks 

-kyle

---

### Post by Paqman on 2008-05-16
Wubi may be very slightly slower whenever it accesses the hard drive, due to the nature of it's virtual partition. I've not heard any figures about how much slower, but I believe it's a very minor concern for general use.

As for switching to a traditional install, you can migrate your whole installation using [LVPM](http://lubi.sourceforge.net/lvpm.html). Currently LVPM needs to be updated for 8.04, so if you're running that you might want to hold off.

Otherwise, the same advice holds for any other time you do a reinstall. Back up your /home folder, [create a list of your installed packages](http://ubuntuforums.org/showthread.php?t=261366), and you're good to go.

---

### Post by maddkid53 on 2008-05-16
I am running 8.04, and i have no problem with waiting, i still need to free up space on my harddrive.  

And if i do that, i'll still have the boot loader and everything when i start up?

thanks for your help

---

### Post by Paqman on 2008-05-16
> **maddkid53 said:**
> 
And if i do that, i'll still have the boot loader and everything when i start up?


You mean using LVPM? Take a look at the link I posted, you'll see that towards the end of the process you re-install Grub, which is the standard bootloader.

---

### Post by maddkid53 on 2008-05-16
Sweet, ill definitely take a look at that when it comes out for 8.04.

Thanks for your help :)

---

### Post by philinux on 2008-05-16
[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

---

