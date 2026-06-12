---
title: "Ubuntu won't load on dual boot"
date: 2012-03-31
forum: New to Ubuntu
---

### Post by Lemuel111 on 2012-03-31
Hi folks, 

I am trying to have both Ubuntu and Windows Vista on my laptop. I loaded  Ubuntu 10.10 but it didn't install properly so I put 11.10 on via Wubi.  I then discovered the 'correct broken packages' option and was able to  fully install 10.10 which I prefer, as I don't like the 11.10 at all. I  installed EasyBCD on Vista to get tidy up the start up mode and deleted  Ubuntu in the options thinking this was for 11.10. I then tried to  uninstall 11.10 via wubi but an error message saying 'files not found'  kept on coming up. When I turn on each time now I can only go into  Vista. 
    So if possible I just want to run 10.10 and delete 11.10 (I know  both are installed properly but I just can't access them). Any help most  appreciated.

---

### Post by critin on 2012-03-31
Check your Add/Remove programs for Wubi/Ubuntu.  Remove it from there.  Since you already deleted some of its files, you may have to do a search (in Windows) for all things wubi and delete.    I'm assuming 10.10 was installed on its own partition, without Wubi.  

If 10.10 was also installed through Wubi, you can simply reinstall when the other one is cleaned out.

---

### Post by Lemuel111 on 2012-03-31
Yes, 10.10 was in it's own partition.

---

### Post by critin on 2012-03-31
Since it's a new install, I'd simple reinstall 10.10 over itself for a fresh new start.  It will pick up grub and should boot both.

---

### Post by Lemuel111 on 2012-03-31
Wubi didn't show up on the add/remove but ubuntu 11.10 did. I tried to un install but error message "Error executing command, C:/Windows/System32/bcdedit.ex/delete (followed by a load of letters/numbers).

---

### Post by critin on 2012-03-31
Search for the ubuntu/wubi folder and delete it.

I don't think that would keep 10.10 from booting though.

---

### Post by Lemuel111 on 2012-03-31
Found it and clicked on it but then it said "A previous instalation was detected, please unistall before continuing". Which brings me back to the previous uninstall problem

---

### Post by critin on 2012-03-31
Yes, the previous installation must be deleted.  All references to wubi.  Did you do a search?  Do you have CCleaner?

Are you sure 10.10 is not being installed by wubi?  I believe if you're installing on the hdd, wubi installs won't matter.

---

### Post by Lemuel111 on 2012-04-01
Right, I have established that I need to re-install GRUB loader from the rescue CD. I started the process but got as far as 'partitioning method' and then freaked because this is way out of my league! Which option do I go for? I only want to reinstall the start up menu to allow me to select Ubuntu (which is already install) rather than mess around with repartitioning etc.

---

### Post by critin on 2012-04-01
> I started the process but got as far as 'partitioning method'This sounds like a new insttall to me.  choose Quit.


I betcha it's a wubi and is on the Windows partition.

Boot the ubuntu live and run this in the teminal.  Post the results here.

> sudo fdisk -lu

---

### Post by Lemuel111 on 2012-04-01
Sorted! Used Boot repair disk ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)).
Thanks for those who helped.

---

### Post by critin on 2012-04-01
> **Lemuel111 said:**
> Right, I have established that I need to re-install GRUB loader from the rescue CD. I started the process but got as far as 'partitioning method' and then freaked because this is way out of my league! Which option do I go for? I only want to reinstall the start up menu to allow me to select Ubuntu (which is already install) rather than mess around with repartitioning etc.


[https://wiki.ubuntu.com/WubiGuide#Other_boot_or_video_problems](https://wiki.ubuntu.com/WubiGuide#Other_boot_or_video_problems)

Bookmark this link and study it.

Here's a quote from the link:  
> **Cannot boot into Ubuntu**

 Never  try to correct Wubi boot problems by reinstalling Grub2. This will  prevent Windows from booting and will not fix the Wubi install. 

---

