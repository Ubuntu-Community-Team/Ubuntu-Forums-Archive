---
title: "Possible Tri Booting Issues with Mint???...."
date: 2007-10-06
forum: Other OS Talk
---

### Post by multifaceted on 2007-10-06
I have an extra 60GB of disk space available on my local drive in which Ubuntu and Xp are installed dual boot.  Rather than let it lay to waste I was thinking about installing Linux mint Xfce in the reaming space.

My main concern is that I do not want to screw up the boot loader. Will GRUB identify both my Xp and Ubuntu partitions too in addition to the proposed Mint partition?

I DO NOT want to mess up my Ubuntu partition, I am in love with it... but I'm having an affair with Xfce.... would this be more of a hassle than what it's worth?

---

### Post by rsambuca on 2007-10-06
It shouldn't be a hassle at all.  If you install mint or any other distro, just have the grub from the new distro install to the new partition, not to the mbr.  ie, if you install Mint to hda2, then have grub install to (hd0,1).  Then add an entry to your existing Ubuntu  /boot/grub/menu.lst to point it to the Mint grub if selected.  To do this, add the following to the very end of your /boot/grub/menu.lst:

title  Mint (or new distro)
root (hd0,2)   <-- you will have to change this to the correct partition on your system
chainloader +1

---

### Post by multifaceted on 2007-10-07
Is it really necessary to edit the boot files? If I let Mint GRUB install it's partition, then it will load that by default and give me the option to load other operating systems correct?

If I do as you say, do I need to perform these edits before Install from the LiveCD? Or, do I edit the boot files from Mint after I have installed?

Please excuse, I'm not to familiar with the inner working of GRUB.

---

### Post by SuperDuck on 2007-10-07
I wasn't really comfortable with GRUB until after I read this - hopefully it will prove helpful to you as well.

[http://www.dedoimedo.com/computers/grub.html](http://www.dedoimedo.com/computers/grub.html)

---

### Post by rsambuca on 2007-10-07
> **multifaceted said:**
> Is it really necessary to edit the boot files? If I let Mint GRUB install it's partition, then it will load that by default and give me the option to load other operating systems correct?Usually the grub loader will detect other OS's, but not always.  If it does detect them, then you do not *have *to manually edit the menu.lst file, but I still prefer the manual method.

> **multifaceted said:**
> If I do as you say, do I need to perform these edits before Install from the LiveCD? Or, do I edit the boot files from Mint after I have installed?You would edit the grub menu.lst after you have installed another distro.  The benefit of chainloading your distro's grub menus is that you only edit the list once, and then it is automatically updated after that.  If you don't chainload, then you have to manually edit the file with every kernel patch.

---

### Post by Bart_D on 2007-10-07
I tried U(xu),buntu and Mint Xfce in triple boot n the SAME hd and it worked fine out of the box.  I hated Mint so just removed it.

---

### Post by multifaceted on 2007-10-07
Thanks, **rsambuca...** 

I am just a little weary of trying out what you are suggesting, purely on the fact that I am inexperienced user. I am however, researching your suggestions and learning a great deal in the process. And for that, I thank you very much!

---

### Post by multifaceted on 2007-10-07
> **Bart_D said:**
> I tried U(xu),buntu and Mint Xfce in triple boot n the SAME hd and it worked fine out of the box.  I hated Mint so just removed it.

Really?..

I have been using Xubuntu on another machine for a while and think it's okay...

Mint Xfce edition is great as far as I can tell from playing with the liveCD on various machines.  What turned you away from it???

---

### Post by wolfen69 on 2007-10-08
> **rsambuca said:**
> It shouldn't be a hassle at all.  If you install mint or any other distro, just have the grub from the new distro install to the new partition, not to the mbr.  ie, if you install Mint to hda2, then have grub install to (hd0,1).  Then add an entry to your existing Ubuntu  /boot/grub/menu.lst to point it to the Mint grub if selected.  To do this, add the following to the very end of your /boot/grub/menu.lst:

title  Mint (or new distro)
root (hd0,2)   <-- you will have to change this to the correct partition on your system
chainloader +1

i can install any linux distro and have handle the boot options no problems.(i triple boot)
no matter which drive i install linux on, grub handles it fine.

---

### Post by rsambuca on 2007-10-08
> **wolfen69 said:**
> i can install any linux distro and have handle the boot options no problems.(i triple boot)
no matter which drive i install linux on, grub handles it fine.

I know, but if you read my followup post (#5), you would have seen that the reason for doing this is that you don't have to be continually editing the menu.lst by hand with every distro's kernel updates.

---

