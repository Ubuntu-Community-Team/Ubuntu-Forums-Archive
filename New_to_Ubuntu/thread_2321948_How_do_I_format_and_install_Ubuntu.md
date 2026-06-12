---
title: "How do I format and install Ubuntu"
date: 2016-04-25
forum: New to Ubuntu
---

### Post by Norman_L_Bliss on 2016-04-25
Hello
I'm going to need some help but you gotta be patient because I new. I have an older computer. 
Memory: 7.9 GIB.
Processor: AMD Phenom II X4955 Processor x4
Graphics: GeForce GT 240/SSE2/3DNOW!
OS type: 32-bit
Disk: 2.5 GB
I had a diagnostic done on it. I have two hard drive, (C:) and (H:). Everything checked out ok but the hard drive (C:) was bad so I removed it. And left the (H:) in.
I have Ubuntu 14.04 on a SanDisk.
How do I format (H:) and install Ubuntu 14.04 on (H:).
Thank You

---

### Post by grahammechanical on 2016-04-25
So, effectively, one hard drive. Is there an existing operating system that you want to keep? So, that you dual boot between the existing OS and Ubuntu? That is important information for us to know.

What version of Ubuntu 14.04 did you install on that USB memory stick? The Ubuntu amd64 ISO image? Is it running? I just want to confirm that the CPU is a 64 bit CPU and that you can run 64 bit Ubuntu (amd64 ISO image).

These instructions are applicable

[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

Note section 3 - Allocate drive space. Think carefully about the option at the top of the dialog box. Erase disk and install Ubuntu. That will do what it says it will do. That is the simplest, less fussy method of installing Ubuntu. We choose that if we do not want to dual boot with an existing OS or save any data that is on the hard disk.

If there is another OS on the disk you should get an option to Install Alongside (the other OS). What specifically do you want to do?

Regards

---

### Post by Norman_L_Bliss on 2016-04-25
No existing operating system. Was removed when I removed the C: hard drive. I started Ubuntu 14.04 32-bit on the SanDisk on the computer. Ubuntu was working fine. I click on clean Install Ubuntu Now and after Ubuntu installed I click on Restart Computer Now and got this error. see picture&#8230;
Would like Ubuntu as the only OS on this computer. Thanks
[IMG]http://www.backyardpit.us/wp-content/uploads/2016/04/IMG_20160425_094559_708.jpg[/IMG]

---

### Post by ian-weisser on 2016-04-25
During boot, several thing occur. This is an oversimplified version:
1) The machine loads GRUB, which teels the machine where to find the kernel, the OS to run on top of the kernel, and where the filesystem is located.
2) The machine loads the kernel from disk.
3) The machine runs a small program called 'init' from a compressed bundle (initramfs) stored on disk.
4) Init runs the kernel and loads the filesystem.
5) Init transfers control to a *different* 'init' program on the freshly loaded filesystem.
6) New-init loads the rest of the OS from the filesystem, and starts showing you pretty pictures and eventually a login prompt.

Everything through step 3 seems succesful. Your error indicates a problem somewhere around 4 or 5. 

At that initramfs prompt, run the command 'blkid' and post a photo of the output here.

---

### Post by ajgreeny on 2016-04-25
Firstly I am assuming that the two disks of which you speak were actual separate hardware disks as Microsoft Windows calls partitions disks, which is very confusing.
Is the disk H: which is now the only one in the computer, the one you show as **Disk: 2.5 GB**?

If so it is not large enough to install any of the *ubuntu family of OSs.

You need a larger drive to install to which you could put into the vacant space of disk C: assuming it was a real separate disk.

---

### Post by Norman_L_Bliss on 2016-04-25
[IMG]http://www.backyardpit.us/wp-content/uploads/2016/04/IMG_20160425_131104_143.jpg[/IMG]

---

### Post by Norman_L_Bliss on 2016-04-25
The H hard drive is 1 terabyte.

---

### Post by oldrocker99 on 2016-04-25
It appears that your computer best needs a reinstallation. If you used the SanDisk to install the apparently failed system you have now, and you can, burn a DVD using any disk burner that will burn a disk image and try reinstalling.

If you can't burn a DVD, boot from your USB again and format the entire drive and reinstall. 

If you can, also, select "Something Else" and create a, say, 128 or even 64 GB / directory (plenty of space, by the way) and the rest of the drive as /home. Then, in case of disaster, you can reinstall without losing all your documents, music, videos etc., by just mounting that partition as /home at installation.

And do ask as many questions as you need to ask. It **is** what this forum is for.:)

---

### Post by Norman_L_Bliss on 2016-04-25
This sounds like it should work. This will take me some time to complete. I will get back with you and let you know how it worked out. Thank you

---

### Post by Norman_L_Bliss on 2016-04-26
No matter what I do this window appears (see picture #1) and if I click on anything this window appears (see picture #2). I've tried everything and this is all I get these two windows. I tried to reinstall Windows XP and the same two windows appear. I call two computer repair shops in town nobody will work on Ubuntu. What do I do from here? 

[IMG]http://www.backyardpit.us/wp-content/uploads/2016/04/picture-1.jpg[/IMG][IMG]http://www.backyardpit.us/wp-content/uploads/2016/04/picture-2.jpg[/IMG]

---

### Post by Norman_L_Bliss on 2016-04-26
it's fixed I guess I kept going in the right direction.

---

### Post by Norman_L_Bliss on 2016-04-26
Thank y'all for your time and help. Norman Bliss

---

### Post by ajgreeny on 2016-04-27
It would be more helpful to others who might have the same problem if you told us what solved the problem for you, and then please mark the thread as SOLVED from the Thread Tools menu up-top.

---

