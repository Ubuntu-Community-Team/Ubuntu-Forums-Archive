---
title: "How to Remove Ubuntu?!"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by mbarvian on 2008-05-12
Hi guys, I just installed Ubuntu on my Toshiba satellite laptop, but the wi-fi wasn't working on it, so I want to remove it, but can't see how.  I am running the latest version: 8.04, but do not have the Windows Vista disc that should have came with my computer.  Is there any way to fully remove it?

---

### Post by tamoneya on 2008-05-12
the way you remove ubuntu is by installing over it.  There is no other way around it.  Since you dont have the windows disk that is a bit more difficult.  Post the output of ```
sudo fdisk -l
```Maybe the manufacture left a recovery partition on your harddrive.

---

### Post by Inxsible on 2008-05-12
Put the live CD in and then use GParted on the live CD to simply erase the Ubuntu partition and then re merge it to Vista if you want.

You will have to fix the mbr or you can also use SuperGrub to fix your grub entries again.

---

### Post by tjwoosta on 2008-05-12
well if you were to just delete the ubuntu partition, GRUB would stop working and you wouldnt be able to boot into vista.

i have heard of people restoring the default vista bootloader without the original vista cd but i cant remember how (it is definatly possible though)


EDIT: oops, i should have refreshed the page before responding

---

### Post by john91 on 2008-05-12
woah, woah.  completely removing ubuntu is not the best way to go about things.  why not let us help you fix wifi?  my guess is you just have to do some config with your wifi system to get it to work, and besides, if you don't have the vista disk on hand, then you'll have to download the iso and burn it to a disk anyway, which will require internet access on ubuntu (unless you have another computer set up, which I assume you do since you're posting on this forum).  

if you can, run these commands in the terminal (applications > accessories > terminal, if you don't know), and post the output, and we can start helping you fix your wifi.

```
lshw -C network
``````
ifconfig
``````
dmesg | tail -n 50
```

EDIT: this is all assuming that you would want to fix your wifi instead of erase your system.

---

### Post by ugm6hr on 2008-05-12
> **mbarvian said:**
> Hi guys, I just installed Ubuntu on my Toshiba satellite laptop, but the wi-fi wasn't working on it, so I want to remove it, but can't see how.  I am running the latest version: 8.04, but do not have the Windows Vista disc that should have came with my computer.  Is there any way to fully remove it?

Yes.  You can remove it.

Do you still have Vista on the HD (i.e. dual-boot)?

If yes - install EasyBCD ([http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1))

This will restore the Vista bootloader.

Then you can just boot from the Ubuntu LiveCD and use Partition Editor (GParted) to delete the Ubuntu partition.

If no - then you can still remove Ubuntu, but Vista won't be there either.

PS: This assumes you did a full install, and did not use Wubi to install within Windows.

PPS: Did you want to try to get wifi working in Ubuntu?

---

### Post by mbarvian on 2008-05-12
OK, I guess I shouldn't jump to conclusions trying to remove it instantly (although it would be nice).  This is the wi-fi problem: when I click on the two computers at the top right, it opens up a Connections manager thing (again, very new to Ubuntu).  However, everything is listed as it should be there is no Wireless tab.  How do I fix this?

---

### Post by SunnyRabbiera on 2008-05-12
well firstly dont expect to learn a brand new OS right away, secondly have patience.
I am sure we may have a solution to your wireless issue if you give us time

---

### Post by john91 on 2008-05-12
It's really hard to diagnose the problem without knowing some info about your hardware.  if you could post the output of the commands I placed in my last post, it'll help us help you.

---

### Post by ugm6hr on 2008-05-12
> **mbarvian said:**
> OK, I guess I shouldn't jump to conclusions trying to remove it instantly (although it would be nice).  This is the wi-fi problem: when I click on the two computers at the top right, it opens up a Connections manager thing (again, very new to Ubuntu).  However, everything is listed as it should be there is no Wireless tab.  How do I fix this?

We need a bit more info...

Is it a USB or internal wifi card?

In Terminal (see link below if you don't know how), copy / paste the commands john91 suggested, and post results back here.

Also:```
lspci
```

---

### Post by mbarvian on 2008-05-12
> **john91 said:**
> It's really hard to diagnose the problem without knowing some info about your hardware.  if you could post the output of the commands I placed in my last post, it'll help us help you.

I can't, because I keep on having to restart into Vista just to be in this forum, sorry.

---

### Post by amaroKer on 2008-05-12
What kind of wireless card do you have?

Post terminal output of
```
lspci
```
or just look for something that mentions 'Wi-Fi', 'WLAN', '802.11', 'Wireless', or the like.  Write that entry down and tell us what it says.

To narrow it down, you could try
```
lspci | grep 802
``` The line character is a PIPE (that is SHIFT + BACKSLASH).

I find that it makes life much easier to plug into your router when dealing with wireless issues, so that you can still access the internet.

Have you tried using the Restricted Drivers Manager under System>Administration?  Your wireless card may show up there for you to enable with just one check mark.

On a side note, I can't believe that you will have any better luck with Vista if you would uninstall your entire OS just because the network widget doesn't work.  You must be patient with all technology that you are not familiar with.

---

### Post by hyperair on 2008-05-12
You can paste the outputs into a text file or something and then save it in a thumbdrive or hard disk that is accessible from Vista. Then upload it here.

---

### Post by Inxsible on 2008-05-12
> **mbarvian said:**
> I can't, because I keep on having to restart into Vista just to be in this forum, sorry.Well you can always connect the machine to a wired network(ethernet cable) so that you can be on the internet through Linux. Or am I missing something else?

---

### Post by john91 on 2008-05-12
hmmm...that does tend to make things difficult...  is there any way you can get a grounded connection? or do you have a second computer that you can use for the forums while working in ubuntu?  or maybe a usb drive you can use to save a file with the outputs of those commands?

of course, you could always just write out the outputs of the command by hand and then retype them on vista :lolflag:



EDIT: oh well, my internet connection cuts off at 1am, so i won't be able to help in about ... 3 minutes.

---

### Post by HunterThomson on 2008-05-12
You can also just.

Download super grub live cd form;

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

bun the iso

then boot into the live ubuntu cd and go to the partitioner
then just stretch the NTFS win partition to cover the whole harddrive effectively deleting ubutnu

then you will need to boot into the super grub live cd and install it
Then super grub will boot you up into windows.

but yes we can get your wireless working too if you want.

---

### Post by mbarvian on 2008-05-12
> **amaroKer said:**
> What kind of wireless card do you have?

Post terminal output of
```
lspci
```

Have you tried using the Restricted Drivers Manager under System>Administration?  Your wireless card may show up there for you to enable with just one check mark.

On a side note, I can't believe that you will have any better luck with Vista if you would uninstall your entire OS just because the network widget doesn't work.  You must be patient with all technology that you are not familiar with.

No, I haven't tried that, but I think I will now... hold on

---

### Post by SunnyRabbiera on 2008-05-12
> **hyperair said:**
> You can paste the outputs into a text file or something and then save it in a thumbdrive or hard disk that is accessible from Vista. Then upload it here.

or do what I did: use a pen and paper :D

---

### Post by ugm6hr on 2008-05-12
> **mbarvian said:**
> I can't, because I keep on having to restart into Vista just to be in this forum, sorry.

Can you find out what type of wifi card you have in Vista?

It should be somewhere in the Control Panel...  something like Hardware Profile maybe?

Also - you should be able to tell us if it is USB or internal!

---

### Post by HunterThomson on 2008-05-12
Ya,

you can do what I said to delete ubuntu. we all jsut know we can get your wireless working that is why we think it is not a good reson to delete ubuntu you could just tell us the exact model of lap top you have and we can google it.

---

### Post by mbarvian on 2008-05-12
> **ugm6hr said:**
> Can you find out what type of wifi card you have in Vista?

It should be somewhere in the Control Panel...  something like Hardware Profile maybe?

Also - you should be able to tell us if it is USB or internal!

OK, I think this is it:
Realtel RTL8187B Wireless 802.11b/g 54 Mbps USB 2. Network Adapter

---

### Post by SunnyRabbiera on 2008-05-12
> **mbarvian said:**
> OK, I think this is it:
Realtel RTL8187B Wireless 802.11b/g 54 Mbps USB 2. Network Adapter

Hmm, well I do think that model does work albeit with some tweaking.
I know I had a heck of a time getting my wireless adapter to work in ubuntu, but I know it is not ubuntu's fault...
keep in mind most drivers and devices have only windows in mind, we can only do so much without support from those companies that make those said drivers and devices.
Always keep in mind this is a community driven OS asnd not a corporate driven one, and we can only do what we can.

---

### Post by ugm6hr on 2008-05-12
Unfortunately, USB wifi devices are trickier than internal...

This can be made to work, according to this: [http://ubuntuforums.org/showthread.php?t=765671](http://ubuntuforums.org/showthread.php?t=765671)

However, it may not be straightforward.  Depends how much you want to give Ubuntu a go.

If you do decide to remove Ubuntu, I would strongly recommend EasyBCD over any of the other options (including SuperGrub), since it does not require any Linux partitions to work (Ref: [http://ubuntuforums.org/showpost.php?p=2668386&postcount=14](http://ubuntuforums.org/showpost.php?p=2668386&postcount=14))

---

### Post by HunterThomson on 2008-05-12
> **ugm6hr said:**
> I would strongly recommend EasyBCD over any of the other options (including SuperGrub), since it does not require any Linux partitions to work (Ref: [http://ubuntuforums.org/showpost.php?p=2668386&postcount=14](http://ubuntuforums.org/showpost.php?p=2668386&postcount=14))

EasyBCD I have never hard of that looks cool

---

### Post by mbarvian on 2008-05-12
> **ugm6hr said:**
> Unfortunately, USB wifi devices are trickier than internal...

This can be made to work, according to this: [http://ubuntuforums.org/showthread.php?t=765671](http://ubuntuforums.org/showthread.php?t=765671)

However, it may not be straightforward.  Depends how much you want to give Ubuntu a go.

If you do decide to remove Ubuntu, I would strongly recommend EasyBCD over any of the other options (including SuperGrub), since it does not require any Linux partitions to work (Ref: [http://ubuntuforums.org/showpost.php?p=2668386&postcount=14](http://ubuntuforums.org/showpost.php?p=2668386&postcount=14))

OK, that worked, now all I need to do is delete the Ubuntu partition.  Any ideas?

---

### Post by Inxsible on 2008-05-12
> **mbarvian said:**
> OK, that worked, now all I need to do is delete the Ubuntu partition.  Any ideas? See post number 3. Since you have already fixed MBR, you simply need to use Gparted to erase the Ubuntu partition, re-format it as NTFS and merge it or create a new partition

---

### Post by SunnyRabbiera on 2008-05-12
but please, next time consider a dual boot as you will thank us later...

---

### Post by mbarvian on 2008-05-12
> **Inxsible said:**
> See post number 3. Since you have already fixed MBR, you simply need to use Gparted to erase the Ubuntu partition, re-format it as NTFS and merge it or create a new partition

is there a way to do this inside vista?

---

### Post by tjwoosta on 2008-05-12
in vista go to Administrative Tools-Computer Management then find disk management on the left and click it  (this is the vista partitioner)

---

### Post by mbarvian on 2008-05-12
> **tjwoosta said:**
> in vista go to Administrative Tools-Computer Management then find disk management on the left and click it  (this is the vista partitioner)

OK, I'm there. Now what do I do?

---

### Post by tjwoosta on 2008-05-12
> OK, I'm there. Now what do I do?
uhhh...     delete the unwanted ext3 partition,  maybe even expand your vista ntfs partition back to normal size

---

### Post by mbarvian on 2008-05-12
> **tjwoosta said:**
> uhhh...     delete the unwanted ext3 partition,  maybe even expand your vista ntfs partition back to normal size

[IMG]http://i231.photobucket.com/albums/ee240/mbarvian/screenshot.png[/IMG]

This is what I have listed.  Now what do I do and how?

---

### Post by mbarvian on 2008-05-12
anyone?

---

### Post by Inxsible on 2008-05-12
First of all remove the Ubuntu Live Cd from the cd drive. The D drive you see is your CD drive.

Ubuntu was probably installed in one of the above 3 partitions. The one which says EISA Configuration.... is probably your recovery partition and you dont wanna mess with it.

You may want to delete the other 2 partitions which were probably your root install and swap.

---

### Post by tjwoosta on 2008-05-12
at the top, the two that are directly above the NTFS partition and below the EISA Configuration are your linux partitions (one is ubuntu and the small one is the linux swap partition)

---

### Post by mbarvian on 2008-05-12
Great, now how do I remove them and expand the Vista partition?

---

### Post by mbarvian on 2008-05-12
Great, I've figured out how to delete the two partitions.  It seems that all I have to do now is to get these two partitions:
[img]http://i231.photobucket.com/albums/ee240/mbarvian/screenshot.png[/img]
to merge somehow.  How do I do this?

---

### Post by tjwoosta on 2008-05-12
when you delete them, dont format (just leave unallocated)  this should make them become one partition 
then you should be able to resize your vista partition to fill the unallocated space, if not then just right click the unallocated space and format the whole thing to NTFS, then resize vista 
if thats what you wanted to do

---

### Post by mbarvian on 2008-05-12
> **tjwoosta said:**
> when you delete them, dont format (just leave unallocated)  this should make them become one partition 
then you should be able to resize your vista partition to fill the unallocated space, if not then just right click the unallocated space and format the whole thing to NTFS, then resize vista 
if thats what you wanted to do

So I delete the free space and then expand Vista?

---

### Post by mbarvian on 2008-05-12
anyone?

---

### Post by ugm6hr on 2008-05-12
> **mbarvian said:**
> So I delete the free space and then expand Vista?
Yes.
Delete the Ubuntu partitions and expand Vista to fill the space.

---

### Post by tamoneya on 2008-05-12
you should be able to right click on it and select resize.  The vista partition manager should support resizing as far as I remember.

---

### Post by mbarvian on 2008-05-12
OK, great, I did it and it worked.  Thanks a ton guys!

---

### Post by ugm6hr on 2008-05-12
> **mbarvian said:**
> OK, great, I did it and it worked.  Thanks a ton guys!

If you liked Ubuntu, consider investing in a supported wifi card for when you give it another try.

It's particularly good for resurrecting old PCs if you're concerned about messing up your main system.

Thanks for visiting :)

---

### Post by amaroKer on 2008-05-12
I recommend the D-Link WDA-1320 for wireless.  It even works from the LiveCD.

Looks like the Ubuntu community is better at supporting Vista than it's own is... since he came here.

---

### Post by mbarvian on 2008-05-13
yeah.  BTW, I've decided that I liked ubuntu too much to get rid of it, so I reinstalled it, but I still can't get the wi-fi to work.  Any free solutions?

---

### Post by ugm6hr on 2008-05-13
> **mbarvian said:**
> yeah.  BTW, I've decided that I liked ubuntu too much to get rid of it, so I reinstalled it, but I still can't get the wi-fi to work.  Any free solutions?

Start a new thread with a more appropriate title, and include details about the wifi device.

---

### Post by tamoneya on 2008-05-13
> **mbarvian said:**
> yeah.  BTW, I've decided that I liked ubuntu too much to get rid of it, so I reinstalled it, but I still can't get the wi-fi to work.  Any free solutions?

yeah vista tends to make people say that fairly often.  You wouldnt be the only one.

---

### Post by mbarvian on 2008-05-13
> **tamoneya said:**
> yeah vista tends to make people say that fairly often.  You wouldnt be the only one.

Yeah, I noticed that

---

