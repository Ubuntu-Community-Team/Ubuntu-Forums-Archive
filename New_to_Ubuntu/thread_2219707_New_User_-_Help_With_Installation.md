---
title: "New User - Help With Installation"
date: 2014-04-25
forum: New to Ubuntu
---

### Post by moon2 on 2014-04-25
Morning :) - I am totally new to Linux/Ubuntu but decided to try it on a desktop that was running Windows XP - I had upgraded it to Win 7 but got tired of the activation nonsense.

I have managed to download Ubuntu Desktop 14.04 and rebooted the PC and can choose Ubuntu.  It begins to load but then tells me it is missing files but the only indication of what is /.  Gives me an option to ignore which I did but then says it can't find /tmp.

I don't know what to do from here - I'm not a technical person and don't understand some of the language used when looking at the wiki pages etc.

Can someone suggest what to do next in simple terms (as I'm a very simple soul).

Thanks
Moon

---

### Post by TheFu on 2014-04-25
Welcome to the forums.  For a non-technical person, installing **any** OS can be difficult on some hardware.  The specific hardware involved will be helpful, as some needs "tricks" to get any OS installed.

Also, if you are willing to wipe everything from the old HDD, that makes things easier than trying to co-exist with some other proprietary OS.

Also, many local areas have "LUGs" - Linux Users Groups - which are a great way to get hands-on help.  My LUG meets every Sunday to help people get Linux installed.  We teach HOW-TO, we WILL NOT do an install for you.  I suppose people in the LUG is do the install for a price, but we are officially about teaching and learning, not a tech support store. ;)

Have we met online somewhere else?

---

### Post by WoodenWalker on 2014-04-25
When you say you downloaded Ubuntu Desktop 14.04, do you mean you have it burnt to a disk and are attempting an install? By the way, / is the root directory. It's kinda where everything begins on your system. All other directories reside within root.

---

### Post by moon2 on 2014-04-26
Thanks for your replies.

TheFu - I am running a custom made desk-top with a AMD Athlon(tm) 64 process 3200+ 2.01GHz, RAM 1.50GB, System Type 32-bit OS.  Not having used Ubuntu before I'm a bit scared of getting rid of Win 7 until I can make everything work OK but ultimately I will have to uninstall Win 7 as I have no activation key.  Seeing the demos it seems quite straitforward but if I'm having this much trouble installing it makes me even more warey.

WoodenWalker - I downloaded the iso from the Ubuntu site - I've had to use a USB stick as I can't seem to get the computer to read off a disk.  I ran wubi and it seemed to load the files but I did notice during the installation it was deleting some files as well.

In looking round the web it doesn't look as if I'm not alone in this problem (I've copied the exact wording below) but I can't see that anyone has come up with a solution either:

Serious errors were found while check the disk drive for /.
Press I to ignore, S to skip mounting or M for manual recovery

If I ignore then it says the same thing but /tmp on the first line.

TheFu - not sure if we've met before but I sign into most sites I use as Moonlustie, so you may have come across me before but not to do with Ubuntu.

Cheers
Moon

---

### Post by LastDino on 2014-04-26
You should start by posting partition scheme you're currently using. Depending on that we will be more than happy to guide you for further process. 

Or you can forget about all this and go back and make that Linux bootable again since Win7 is still present by booting into it. This time use this software to make bootable> [http://www.linuxliveusb.com/en/download](http://www.linuxliveusb.com/en/download) or [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
Then boot from it and make following partitions during installation
/        <This is root and keep around 20-24 GB for it.
Swap  <Set this partition in equal amount as you've RAM.
/Home < Give it as much as possible space but you can keep one or two  unassigned partitions just for storing purpose. If you don't know     what I'm talking about just give it rest of your HD.

Go trough installation procedure again and see what happens. Rest is easier than installing Win7 which you seem to be able to do.

---

### Post by moon2 on 2014-04-26
Thanks - ooh no idea about partitions - but if that download gives me step by step instructions I'll give it a go - job for tomorrow though.

Your help is really appreciated.

Thanks
Moon

---

### Post by Mark Phelps on 2014-04-26
>  I ran wubi 

Sorry, but this is a BAD idea!  WUBI has been discontinued and I advise strongly AGAINST using it anymore.

To see what you have on your drive, boot into Ubuntu (LiveUSB if not installed), open a terminal and enter "sudo fdisl -lu" (lowercase L, not a one).  This wil list out the partitions and filesystems on your drive.  Post that information back here.

---

### Post by moon2 on 2014-04-26
Thanks Mark - I've never used Linux/Ubuntu before and I was advised to use Ubuntu Desktop and wubi is what comes in the package from the Ubuntu webpage.

Unfortunately you've lost me in the terminolgy - I start the computer, choose Ubuntu and get this screen: 

[IMG]http://i11.photobucket.com/albums/a176/moonlustie/DSC_00851.jpg~original[/IMG]

What do I do from here - if I let it go to the next screen, this is when I get: Serious errors were found while check the disk drive for /.
Press I to ignore, S to skip mounting or M for manual recovery

I did try c but it didn't recognise sudo - I tried in some of the advanced options but no luck there either

Thanks
Moon

---

### Post by TheFu on 2014-04-26
Looks like Mark misspelled the command.
Boot off a liveCD (or flash drive you made using YUMI), open a terminal and run 
**sudo parted -l**
Please post the output of that command back here using "code" tags.
Or
You can run a slightly more helpful script called **boot-info**.  My signature has more data.

WUBI is a terrible thing and I don't think it has worked since GPT disks came about. It never worked with UEFI systems.  As I mentioned previously, installing ANY OS is hard for some hardware.  You'll need to learn much more about disk partitions to be happy with Linux. That is just the way of the world, I'm afraid.  Er ... unless you can just wipe everything from the current HDD - then the automatic setup stuff sorta "just works", but all current data will be lost.

---

### Post by mastablasta on 2014-04-26
the error is there because you probably used wubi to put it on USB. forget about wubi and use Unetbootin, linuxliveusb or yumi to put ubuntu on USB key

then boot and select USB as boot device. you have a 64bit CPU so you can use the MAD64 image (the 64bit OS).

once you manage to get it to boot select try it and follow the further steps people advised you to take. once you are sure how you want it all setup proceed with install. install can also be done from "try it" (live session). so you can browse internet and such while computer does the install.

btw if you pay to Microsoft a certain amount the annoying messages will go away permanently... :-P

---

### Post by Paulgirardin on 2014-04-26
He meant:   "you have a 64bit CPU so you can use the AMD64 image (the 64bit OS)"

---

### Post by LastDino on 2014-04-26
I'm surprised you tried installing Linux before knowing about partitioning tbh
But not to worry, you can easily learn it in just few minutes.
Read through this> [http://www.howtogeek.com/howto/35676/how-to-choose-a-partition-scheme-for-your-linux-pc/](http://www.howtogeek.com/howto/35676/how-to-choose-a-partition-scheme-for-your-linux-pc/)
[http://askubuntu.com/questions/107599/best-disk-partition-for-normal-users](http://askubuntu.com/questions/107599/best-disk-partition-for-normal-users)

Also, select ''ext4'' as formatting option. It makes life lot easier.

The structure I gave in earlier post is most basic partitioning structure and you can choose to stick with it **unless of course, you want to preserve that Windows partition as well by doing it more thoroughly and for that you'll need to read the links above.**

If you're willing to erase entire disk, you can also choose to stick with default selection just in case what I mentioned earlier is confusing as well. But that will get rid of your Win7 and all the data on HD.

---

### Post by moon2 on 2014-04-27
Hoorah!!! \\:D/I've finally managed it!  Once I'd used the livelinuxsub to create a boot usb and chose the correct option on my boot configuration (thought it was under one section and it turned out to be under another) it just all loaded and it's working.  I just used the options that were already chosen so that it functions.  Am using it as we speak.

I'm sure there is a lot to learn and will have to see if I can find a "Dummies" book but looking foward to getting my head around it all - thank you all for your help and suggestions, I would not have achieved it without your help.

Thank you, thank you thank you :KS

Good night
Moon

---

