---
title: "Grub"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by Fleon on 2008-11-07
Hi, My pc have just one bus cable with two connections and one sata cable, and before installing ubuntu I had one sata hd connected, one ide hd 40 gb and one dvd drive.

Now because that those 2 hd are almost full, the 40 gb hd haves windows xp x64, and some files, and the other ones just files, I disconnected the hd were xp is installed and I started installing ubuntu in a 80 gb hd.

Then I connected both hds with os's, the 40 gb with xp and the 80 gb with ubuntu, but i didnt worked, so I just connected the 40 gb one and i inserted the xp x64 disc and I used the fixmbr option and now xp works

Then I connected again both hds, but it just bots right into windows xp x64, so how can I reinstall grub so I can choose between ubuntu and windows? (I read somewhere that I need to run the live cd and do some commands) But as I said I have just one bus cable and just one bus cable connection on my maindboard intel dg35ec, so either I connect both hds or I connect one and the dvd drive

Hope there is a solution, thanks in advance

---

### Post by Sceiron on 2008-11-07
Have you tried alter the boot order in BIOS?

Since you disconnected the xp disk while installing ubuntu, the grub is now on the 80 GB disk. But when you turn on your computer the BIOS will get the bootloader from the primary partition. Windows bootloader will start since if it is the primary boot-option (your 40 gb disk).

From my experience its more convenient to have the OS's on the same disk.

---

### Post by B34ST1Y on 2008-11-07
otherwise, you could always try using a boot manager, such as one built into the ultimate boot cd ([www.ultimatebootcd.com/](www.ultimatebootcd.com/) ) 



from there, you should be able to fully manipulate boot order, boot.ini .....mbr....all that jazz :) 


let me know if it works. Burn it to a disc and boot to it

---

### Post by caljohnsmith on 2008-11-07
Can you set your BIOS to boot the Ubuntu drive first on start up? If you can do that, I could help you install Grub to that drive if it isn't all ready installed to the Ubuntu drive. If you can't do that, I would recommend installing Grub4DOS within Windows on your Windows drive, and then you can use Grub4DOS to boot either Ubuntu or Windows. Let me know if you would like my help with the specifics of doing either of those scenarios.

---

### Post by Fleon on 2008-11-07
Thanks for all the answers but I have already resolved the problem for what it's worth I used super grub disk in a diskette it was a little hard at first but now both os are working.

Offtopic, I have installed smplayer with mplayer package from here [http://smplayer.berlios.de/forums/viewtopic.php?id=741&p=2](http://smplayer.berlios.de/forums/viewtopic.php?id=741&p=2) (see lastest post), and I have an intel dg35ec mainboard with the internal graphic card intel x3500, and the xvid videos seems to lag a little more on fast scenes, how can i fix that

---

