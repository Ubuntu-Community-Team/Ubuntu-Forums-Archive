---
title: "I Want My Ubuntu Back  :("
date: 2008-06-05
forum: New to Ubuntu
---

### Post by DanielHarrisonBergeron on 2008-06-05
OK, admittedly a stupid mistake but I will do my best to explain how I lost access to my beloved Ubuntu.

Warning: I'm fairly noobish with Linux.
::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

I was playing with Acronis' Disk Director in windows using it to resize my Win/*nix partitions. It was so much fun I did it twice and both times for reasons unknown and without my telling it to it inserted a small and useless 15.6 MB NTFS partition. No problem I thought, I'll just delete (both of) them. Uh-uh. At the next reboot, it didn't. I really needed to get windows back up quickly so after booting using a live Ubuntu CD, I went in and edited my boot.ini file. No matter what I did I couldn't get either OS to come up so I just stuck w/what I knew and set it to boot into windows. Arrggghhhh. 

Here is my boot.ini file as it stands:

__________________________________
[boot loader]
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

__________________________________

Is there a simple way to put Ubuntu back in there or would it be less trouble to reinstall?

Here is a cap of my disk management:
__________________________________
http://picasaweb.google.com/dnjseen/SentToUbuntuForums/photo#5208433306130736946[/IMG]
__________________________________

Thanks In Advance and I will be very grateful to anyone that can help me.

Dan

---

### Post by rockstar on 2008-06-05
Go to this site and then burn the Iso into a Boot CD

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

See if Gparted can identify your partitions correctly.  If your partition is still there it should show up with this live cd.  You can also make changes to the MBR, but be careful or you could scrap your whole drive and have to start from scratch.

---

### Post by Oldsoldier2003 on 2008-06-05
you can either boot to a live cd and reinstall grub or download the supergrub live cd and have it attempt to repair your grub [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by DanielHarrisonBergeron on 2008-06-05
> **rockstar said:**
> Go to this site and then burn the Iso into a Boot CD

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

See if Gparted can identify your partitions correctly.  If your partition is still there it should show up with this live cd.  You can also make changes to the MBR, but be careful or you could scrap your whole drive and have to start from scratch.
---------------------------------------------------------
What took ya so long?!:)

I should have noted that the partition is definitely there and fully accessible via Ubuntu Live. I just need to know how to edit the boot.ini file so that I can return to dual-booting.

Thanks Again. I should have been clearer in my previous post as to what resolution I needed. It's people like you that make Ubuntu shine: A post for help and a reply almost immediately.

---

### Post by DanielHarrisonBergeron on 2008-06-05
> **Oldsoldier2003 said:**
> you can either boot to a live cd and reinstall grub or download the supergrub live cd and have it attempt to repair your grub [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

________________________________________________________________
Hi Soldier,
In following your suggestion and doing a little more investigation, I found this at Supergrub's wiki:

--------------------------------------------------

[www.supergrubdisk.org/wiki/Howto_Boot_Grub_from_windows](www.supergrubdisk.org/wiki/Howto_Boot_Grub_from_windows)

 Classical Final Solution

Once grub has been installed to a partition we need to get its boot sector to a file in order to boot it from Windows.

Let's boot with a live cd and open a terminal.

Identify your Linux partition. In this example the identified partition is sda3.

Plugin your pendrive and open it. Identify your plugged pendrive associated folder.

In this example the pendrive mount folder is: /media/disk

    * sudo su
    * dd if=/dev/sda3 of=/media/disk/linux.bin count=1 bs=512
    * sync
    * Click on your pendrive and umount it. 

Now let's boot into Windows.

Plug in your pendrive and copy the linux.bin file into c:\ folder.
Windows XP/Windows 2000/NT/Windows

Now let's edit boot.ini and add this line at its bottom:

c:\linux.bin="Linux"
--------------------------------------------------

It appears pretty straight forward but I won't have a chance to try it until tonight. I will mark as "Solved" if it works.

Thanks Again,

Dan

---

