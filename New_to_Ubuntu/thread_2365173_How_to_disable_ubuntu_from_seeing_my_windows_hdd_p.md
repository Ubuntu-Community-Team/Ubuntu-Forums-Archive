---
title: "How to disable ubuntu from seeing my windows hdd partitions?"
date: 2017-07-03
forum: New to Ubuntu
---

### Post by jebi on 2017-07-03
hi

how do i disable ubuntu from seeing ntfs, fat, fat32, exfat partitions?

or disable sata support? (ubuntu on usb hdd)

Please complete idiot here step by step idiots guide please?

I dont want ubuntu to write something to other partitions maybe do something in ubuntu to ubuntu so that it does not see, read or write them?

thx

---

### Post by QIII on 2017-07-03
Hello!

It would be very helpful if you would describe what end state you are trying to achieve and why.

---

### Post by leunam12 on 2017-07-03
You have not given a lot of information on what you are trying to do, so, just guessing here... If your system is already installed Ubuntu won't read and/or write your Windows partitions unless you mount them first. If you are trying to install, then you have to create separate partitions for your Ubuntu installation and tell the installer to install on those partitions; all the other partitions will remain untouched. Please provide more specific information.

---

### Post by oldfred on 2017-07-04
If it is just the Windows c: "drive" partition, you have to mount it using fstab to hide it.
As then you can set to read only.

 Set windows boot partition Read only - Morbius1
[http://ubuntuforums.org/showthread.php?t=2043862](http://ubuntuforums.org/showthread.php?t=2043862):
UUID=xxxxxxxxxxxxxxx /WinC ntfs defaults,noauto,ro,umask=227 0 0
After Ubuntu has done it's thing, go in and change the umask to 227 which will make the C Drive read only. 

  If you want to prevent all access then change the umask value to: umask=777. That will prevent all access - except for root. 

 #any time you edit fstab run this to verify everything is correct. Its ok if it does not give any messages.
sudo mount -a 


 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)

---

### Post by jebi on 2017-07-04
hi

ok, so to be sure

on [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

sudo blkid

to get list of hdds?

then


sudo mkdir /media/windows

what do you do here?  i dont want ubunbu to see, read or write to anything on C:\ D:\ or hidden windows 10 partitions(ie system reserved 500mb)?

thx

could someone do an example, i know nothing of ubuntu, i need a step by step show and tell example, i am not computer literate. i could use dos but not linux's dos equivalent.

thx

---

### Post by Morbius1 on 2017-07-04
oldfred showed you an example and gave you a link to the the last time you asked this question - 5 years ago - with step-by-step instructions..

---

### Post by oldfred on 2017-07-04
@Morbius1
I did not notice that your instructions I linked to, was the same user.

---

### Post by jebi on 2017-07-05
> **Morbius1 said:**
> oldfred showed you an example and gave you a link to the the last time you asked this question - 5 years ago - with step-by-step instructions..

I have asked again as i tried that and could not get it to work.

I dont understand the mount point

mkdir winC?  i dont want any mount point?

I think this a problem with asking linux users questions.

Linux users are very knowledgeable whereas i am a windows user with no training at all.

I might as well have asked an astrophysicist about Yang-Mills Theory and how to solve it.

I guess simple idiots guide means different things to different mindsets.

[CENTER][COLOR=#333333][FONT=&amp]**O.o**[/FONT][/COLOR][/CENTER]

---

### Post by deadflowr on 2017-07-05
You can always use Disks to do what you want
Open Disks from Ubuntu menu.
On the left there will be a list of devices, find your hard drive with windows and click on that.
Then in the main window area it will show the parttion layout for that hard drive, click on the Windows partition.
Then below the main window area will be a few icons ( a playback arrow icon and a few others)
One of those icons will be a cog-like icon.
Click on the cog icon to show a dropdown menu.
In the dropdown menu click on Edit Mount Options.

In edit mount options first change the settings from On to Off
(This will allow you to edit the settings.)

Then you can add the entry shown above to the line that shows those options.
(I am not sure the line has a name in Disks)

Food for thought is I would simply uncheck the top two settings which are Mount at startup and show in user interface.
(This will stop it from both ever mounting at login and prevent it from ever showing in any location like the file manager)

Then click OK when you have set what you want and enter your Password to save the changes.

The show in user interface will have an automatic affect.
Not sure about the mount at startup, since you've already started up...

Hope that makes sense, or helps.

---

### Post by barrywhyte on 2017-07-06
You can use "Disks", it's preinstalled. Select the physical drive, the partition, then the gear wheel > edit mount options > automatic off > show in interface off. It that's what you wanted to do.

edit: for whatever reason I didnt see the other answers

---

### Post by yetimon_64 on 2017-07-06
> **jebi said:**
> ...I dont understand the mount point

mkdir winC?  i dont want any mount point?...

The mount point is required purely for use in the /etc/fstab entry, the noauto option used in the /etc/fstab entry actually stops any data being mounted to it. It will always be a blank/empty directory.

I have used the method Morbius1 posted and oldfred linked to very effectively to block the mounting of Windows drives in the ubuntu OS as they are already technically "mounted" by /etc/fstab (although NO data is EVER mounted, due to the "noauto" option in use).

I have never tried the "Disks" method myself, it may be worth a try if you still feel uncomfortable with having a blank/empty mount point being created to block all other automatic/easy mounting of the partition/s in question. With a windows 8 install I had to create three blank "mount points" to ensure none of my windows install could be accessed easily in Ubuntu; I found it worked very effectively in blocking windows mounting.

---

