---
title: "Can't boot Ubuntu"
date: 2011-11-12
forum: New to Ubuntu
---

### Post by Gojira on 2011-11-12
**Can't boot Ubuntu** 			
 			 			 		   		 		 		Hello,

I have installed Wubi but I cannot boot in Ubuntu. When I reboot my  computer and I choose ubuntu it directly opens the GNU GRUB console. Is  it normal? What should I write/do next? Should'nt Ubuntu open  automatically?

Thanks for your patience

---

### Post by Frogs Hair on 2011-11-12
Select the first option by pressing enter . The other options can be selected by using the arrow up/down .

---

### Post by lolpenguin on 2011-11-12
Loading the GRUB console is not normal, and usually means a disk cannot be read.
What version of GRUB do you have? Do you see any errors? Is root.disk present under C:\ubuntu\disks? is grub.cfg present under C:\ubuntu\install\boot\grub?
If you are using GRUB 2 (usually GNU GRUB 1.xx) hold shift when selecting Ubuntu in Windows Boot Manager.

---

### Post by Frogs Hair on 2011-11-12
It depends on what version of Ubuntu . On 11.04 and before after making the Ubuntu selection in the Windows boot loader Grub would open and the user was allowed to make kernel selections , boot Windows or recovery .

If you are booting directly into a terminal then there is problem as   lolpenguin indicated .

---

### Post by Gojira on 2011-11-13
Disk root is present but C:\ubuntu\install\boot\grub is empty... I don't know why

My installation didn't not go flawless anyway. As I installed ubuntu and it first got booted, the system was very very slow and ultimately I had to reset it. I thought the installed was over anyway. Nevertheless, I have installed it 3 time and I still have the same problem.

I am using the latest version available on ubuntu's official website (Wubi).

In order to complete the installation I had to reboot my computer, as asked. As I did so, these lines apparead and it took a century before it got to an end:

pwconv:failed to change the mode of /etc/passwd - to 0600
Shadow passwords are now on
Warning: [something something about "locale"]

I don't know wheter this is normal or not. These are all the details I can give.
What should I do? I'm becoming a little nervous =)

And a big thanks for the previous answers

---

### Post by bcbc on 2011-11-13
What computer brand/model and graphics card do you have?


If C:\ubuntu\install\boot\grub is empty then likely you have this file instead: C:\ubuntu\install\wubildr-disk.cfg
With 11.10 there is a new way that Wubi installs and I suspect you are using this option (you'll have that file if you are). And probably it's not booting because of a hardware issue. Having to hard reset is not helping and so you likely need a kernel boot workaround.

More info on the new install method in 11.10: [http://ubuntu-with-wubi.blogspot.com/2011/10/oneric-ocelot-1110-released.html](http://ubuntu-with-wubi.blogspot.com/2011/10/oneric-ocelot-1110-released.html)

---

