---
title: "[SOLVED] Installed GRUB on an external hard drive."
date: 2008-05-31
forum: New to Ubuntu
---

### Post by yatesl on 2008-05-31
As said in the topic title, I foolishly installed the boot loader on my external USB hard drive (SATA drive, connected to USB via a docking station).  I have Ubuntu installed on a 20GB partition of the hard drive, and Windows installed on my internal hard drive.

With GRUB being installed on the external, it means I can't even boot in to Windows without the hard drive being connected and on.  

Which would be the best way of correcting this?  Is there a way to move the GRUB loader on to my C:\ (internal), so I can boot Windows even if the Linux drive isn't connected?

Thanks. :oops:

---

### Post by Frak on 2008-05-31
I would download the [Super Grub Disk]("http://supergrub.forjamari.linex.org/"), burn it, and then start up the computer with the USB drive in. Assuming that it will see your USB drive, you should be able to install GRUB onto a different drive with the same menu.lst.

Be aware that this is a big assumption, but it wouldn't hurt to try.

---

### Post by kansasnoob on 2008-05-31
Frak has it right. Actually you can restore GRUB either with the Super GRUB Disc (instructions below):

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_To_Use_Super_Grub_Disk](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_To_Use_Super_Grub_Disk)

or you can use the Ubuntu Alternate Install CD:

[http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub](http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub)
(just click on: "Re-install GRUB....................................with the Alternate CD Rescue mode."

---

### Post by yatesl on 2008-05-31
Cheers guys.  Will the Super Grub USB thing work even if I don't have access to the external hard drive with GRUB/Linux on?  

If not, what are my choices?  I'd happily reinstall Windows/Linux, but I don't want to do that only to find it still won't boot, because something in my BIOS (or whatever) is pointing to this absent drive.

---

### Post by Frak on 2008-05-31
You may want to go into your BIOS and make sure that your HD is a higher boot priority than your USB HD.

---

### Post by meierfra. on 2008-05-31
Just to make sure:
 When the external drive is attached, you are able to boot into Ubuntu and into Windows from the Grub menu. 
But if the external drive is not attached you get a grub error?
Do the bios allow you to boot from the external drive?


You  need to do the following

1)  Install grub the MBR of your external drive.
2)  Edit the file "menu.lst"
3)  Put Windows back in charge of the MBR of the internal drive.
4)  Change your the boot order in the bios: The external drive needs to come before the internal drive. 


If you post the output of


```
sudo fdisk -l
```

and 

```
cat /boot/grub/menu.lst
```


I can give you detailed instruction how to carry out Steps 1,2 and 3.

---

### Post by meierfra. on 2008-05-31
> With GRUB being installed on the external, it means I can't even boot in to Windows without the hard drive being connected and on.


Grub comes in two parts. You can choose where to install the first part.  The second  part is usually on the ubuntu partition. Since you cannot boot without the external drive, it means that the second  part got installed to the MBR of your internal drive.  Now then you boot without the external drive attached, the part of grub in the MBR of your internal drive is looking for the part on the external drive.  Of course it fails and  gives you an error message.

> Will the Super Grub USB thing work even if I don't have access to the external hard drive with GRUB/Linux on?

???? You don't have the external drive available right now?

Then you can still  use SuperGrub or a WindowsCD to fix the MBR of your internal drive.(Click on FixMBR in my signature) This will let you boot into Windows. But it will make it slightly more difficult to fix the booting problem for the  external drive (Basically you then  will have to fix things from the Ubuntu LiveCD, which is a little bit of a hassle, but not much)


> I'd happily reinstall Windows/Linux, but I don't want to do that only to find it still won't boot, because something in my BIOS (or whatever) is

No need to reinstall Windows or Linux.

---

### Post by julianpitt on 2010-03-03
Ok here's what im trying todo, i want to create a bootable hard drive with ubuntu mac snow leopard and also use it for storage on windows.
What ive done so far used mac setup to format the drive and partition it into 3 sections, one was to use for windows storage so i formatted that partition with dos, the next thing i did was create a partition of empty space (later for ubuntu), and the last partition was for mac which i formatted with g something tables, after the instillation i was perfectly able to boot mac from my external drive, i then went into windows and reformatted the space for storage from fat32 to ntsf.
Then my problem arose, i installed ubuntu on my external drive using my laptop with the hard drive still in, and selected install ubuntu on the free space option in the ubuntu setup partitioner.
When i restated i was able to load mac and ubuntu perfectly but not windows vista (on laptop hdd) with or without the external drive in so i had to use my vista disc to restore the vista boot loader but now grub wont appear when selection boot from external drive.

so my problem is grub installed on my laptops hdd and not my external, is there anyway of re installing grub onto my external drive without affecting my laptop?
if it helps i also have a desktop that i can easily remove the hdd from but i dont want to start the process over again

---

