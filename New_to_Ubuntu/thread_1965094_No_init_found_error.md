---
title: "No init found error"
date: 2012-04-25
forum: New to Ubuntu
---

### Post by neo1691 on 2012-04-25
Hi.
Recently in my college's net lab, windows operating systems where frequently crashing due to viruses and malwares that were being downloaded.

So I bragged a lot about ubuntu (and linux in general) and installed ubuntu 10.04 LTS on all computers along with windows xp (dual boot).

I had one user , icoer, created while installing, and had setup the password abc123 for it.

So whenever i wanted to install anything using sudo apt-get, i used to login using abc123 and download anything.

Many people in the net lab had this password, abc123, as it was used for many reasons.

Now after sometime, ubuntu stopped booting with an error init not found.

[HERE]("http://i.minus.com/iWSggpfaap91Y.jpg") is a screenshot of the same.

I would like to know what could have caused this, and how it can be prevented. I know linux is much more secure than windows, i just need to prove it again to the other folks at my college!! 
Also i dont just want to repair it, i will create a new installation. But i want my machine to be more secure!!
Thanks a lot!

---

### Post by zeljkojagust on 2012-04-25
As the message says: The target filesystem doesn't have /sbin/init. Now either your GRUB didn't update along with when kernel was updated; means you have updated kernel to a new version and there is still an old entry in your grub menu (it's known to happen). The other scenario is that someone of your users deleted or permanently moved contents of boot partition so there are no init files to boot from. Either way you should know how to manually edit boot menu, you should know how to use LiveCD distros to get information related to disks and partitions of failed system and some general knowledge of Linux boot process.... tell me what you know and I may be able to help you.

---

### Post by neo1691 on 2012-04-25
> **zeljkojagust said:**
> As the message says: The target filesystem doesn't have /sbin/init. Now either your GRUB didn't update along with when kernel was updated; means you have updated kernel to a new version and there is still an old entry in your grub menu (it's known to happen). The other scenario is that someone of your users deleted or permanently moved contents of boot partition so there are no init files to boot from. Either way you should know how to manually edit boot menu, you should know how to use LiveCD distros to get information related to disks and partitions of failed system and some general knowledge of Linux boot process.... tell me what you know and I may be able to help you.
Thank you so much for such a helpful reply. 

I can update the boot menu, but the systems at the laboratory have now been formatted due to exams. So even the ubuntu partition is gone. I am gonna install ubuntu again!! 

So i would like to know how to manage passwords. One for normal user and one password that is required for all changes like moving all contents of boot/init

---

### Post by zeljkojagust on 2012-04-26
You can enable root account for administration tasks with password that only you as an administrator will know. For all the other users create normal accounts and if needed add them to sudoers (by using visudo), so they can use "sudo" in front of commands that require elevated privileges.

---

### Post by skabople on 2012-04-26
```
chattr -R +i /boot
```

Then whenever you want to edit that just type:

```
chattr -R -i /boot
```

This will cause a "mute attribute" on all files within that directory. Meaning that even root cannot edit or delete those files without removing the mute attribute.

Just a thought.

---

### Post by neo1691 on 2012-04-26
> **zeljkojagust said:**
> You can enable root account for administration tasks with password that only you as an administrator will know. For all the other users create normal accounts and if needed add them to sudoers (by using visudo), so they can use "sudo" in front of commands that require elevated privileges.
Yeah i would do that, as it seems the perfect solution. Any links and guids for the same will be truly appreciated!

---

### Post by CLCressman on 2012-04-26
You can use the "Users and Groups" menu option for that. If you don't have that, I think that I had to install a package to get that. But I don't remember which one. I found it here [http://www.liberiangeek.net/2012/01/enable-the-old-users-groups-management-tool-in-ubuntu-11-10-oneiric-ocelot/](http://www.liberiangeek.net/2012/01/enable-the-old-users-groups-management-tool-in-ubuntu-11-10-oneiric-ocelot/)

I am downloading Precise now so I haven't had a chance to check it. Hopefully something similar will work for it.

---

### Post by neo1691 on 2012-04-28
> **CLCressman said:**
> You can use the "Users and Groups" menu option for that. If you don't have that, I think that I had to install a package to get that. But I don't remember which one. I found it here [http://www.liberiangeek.net/2012/01/enable-the-old-users-groups-management-tool-in-ubuntu-11-10-oneiric-ocelot/](http://www.liberiangeek.net/2012/01/enable-the-old-users-groups-management-tool-in-ubuntu-11-10-oneiric-ocelot/)

I am downloading Precise now so I haven't had a chance to check it. Hopefully something similar will work for it.
Ok thanks a lot!! Since this was just a discussion now, i guess i should mark the thread to be solved!! Thanks!

---

