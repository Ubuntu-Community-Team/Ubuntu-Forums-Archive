---
title: "Gparted will boot from cd but not ubuntu"
date: 2014-01-28
forum: New to Ubuntu
---

### Post by Joel_ on 2014-01-28
I am a noob to linux so please be easy on me. 
I recently got a raspberry pi and I love the raspian system. So I grabbed an old dead laptop and I am trying to install ubuntu, or any linux distro at this point. The laptop is a toshiba M45. It is ancient and slow. I copied ubuntu 12.04 onto a usb and tried to boot, no joy. So I copied it to a dvd, no joy. I did to the md5sum to check its validity and it checks out. I did get the drive fitness tester to boot, and it said the hdd was good. So i tried the puppy distro on a cdrom. It loaded the first line which said "isolinux 4.05 0x50328bd7 etcd copyright (c) 1994-2011 H. peter anvin et al"  and then it just sat there. So i made a bootable gparted disc, it booted up fine and I formatted the entire drive to ext4 and it all seemed fine. Again I tried puppy, ubuntu, and even a ubuntu minimal with no success. Now I am fairly sure that this could very well be another hardware problem but why can I boot some cd's and not others. I have looked through the help files on ubuntu, checking all the md5sum hashes and they all are good. I checked that the Iso was burned correctly on all of the disc's. I have gone through the bios (pheonix 1.5) and set the cd to boot first. no joy. If I restart the computer with nothing in the drive it loads to a command prompt that reads 1234F: but I can't write anything. 

Is there anything that I can try or should I gut this thing for the lcd and make a rpi laptop!

Thanks for the help

---

### Post by whitesmith on 2014-01-28
First, welcome to the forum! Have you tried lubuntu? That distro is intended for older systems like yours. As to why gparted would boot and not Linux, keep in mind that the two are doing different things. An operating system is vastly more complex than any utility, and makes different BIOS calls as well. Also, are you saying you can't change  the boot order to make CDs boot first? This setting should be made standard so you can boot from a CD without standing on your head. Regards.

---

### Post by Joel_ on 2014-01-28
Thanks for the quick response! I have not tried lubuntu, but I am downloading it now. 

I was able to change the boot order on my bios, sorry that I did not make that clear. I will let you know how lubuntu works shortly.

Thanks again

---

### Post by Joel_ on 2014-01-28
Lubuntu is downloaded and the image is made on a cd. Now it is doing something new. When the computer boots up it spins up the cd and it thinks for about 15 seconds, then it reboots again, over and over. 

I think the computer is a lost cause. Is there anything else I should try?

---

### Post by Bashing-om on 2014-01-28
Joel_; Hi !

Two things pop to mind.
Did you verify the .iso file's integrity ? 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

How much ram do you have installed ? There is a minimum amount even Lubuntu must have in order to operate (even load).

In the event that Lubuntu is not install-able, there exist many even lighter versions, for instance DSL impresses me.

hey
[INDENT][INDENT]where there is a will there is a way[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2014-01-28
Puppy Linux and Bodhi are also possiblilies. The eternally spinning disk seems like problematic hardware, though.

PS: If it is a dead optical drive, install from USB. You can use something like UNetbootin to create the install media.

---

### Post by coldraven on 2014-01-28
> I copied ubuntu 12.04 onto a usb and tried to boot, no joy. So I copied it to a dvd, no joy
You cannot just copy the .iso you have to make the media bootable.
For a CD or DVD you must use the "Burn Image" setting of the disc burning software.
For a bootable USB stick or SD card* use Unetbootin, Get it here: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Oh! I forgot to say Welcome :P

*I use a 1GB SD card for all my installs, it works every time.

---

### Post by Joel_ on 2014-01-28
Thanks for all the advice. I am currently writing the lubuntu iso on a thumb drive and trying that. I would assume that the optical drive is working as it booted gparted and the drive tool. I have been running the md5sum on all of the iso's except for the lubuntu one. Im sure i was just being lazy but I did not see the hash listed on the lubuntu.net site. I will revisit that idea if this does not work. 
I have tried puppy on a cd, and could not get that to load either. I am burning the image correctly, just as found on the ubuntu web site. 
Thanks for telling me about unetbootin, im using that now for my thumb drive. 

I'll let you know shortly how it works.

---

### Post by Joel_ on 2014-01-28
I finally got something to work! Puppy is running off of a usb currently. I still might see if it is possible to install one of the ubuntu copies that I have to the hard drive through puppy. not sure if this is possible, but I will do some research.

Thanks to all who helped me with this!

---

### Post by Bashing-om on 2014-01-28
Joel_; Great;

Making progress -> sounds like this may be a lack of installed ram. Might see if you can install more, then see if Lubuntu will load up.

[INDENT][INDENT]just my thought
[/INDENT][/INDENT]

---

### Post by whitesmith on 2014-01-28
And don't forget to use Thread Tools (top of page) to mark the problem as solved...if and when. All of us were glad to help, by the way. Best regards to you.

---

### Post by Joel_ on 2014-01-28
I think your right Bashing-om, on both my bios and on puppy it lists something around 440mb ram. This seems like a non conventional amount. Could it be damaged, or is this common?
Is puppy going to be about as good as it gets for this old laptop, or is there a possibility of me installing a more capable os now that I have something running. I would rather get something running off of the hard drive, if for no other reason than to see that it is truly a functioning hard drive. Right now I am working on installing puppy to the hard drive to see how that works. 
One more question, I formatted the entire drive into on ext4 partition. Is that a good all around linux file system or should I reformat it to something else?

Thanks again!

---

### Post by Joel_ on 2014-01-28
I should also mention that I am not doing this expecting something great from this old pos laptop, but only to get a feel for linux and get my hands dirty.

---

### Post by Joel_ on 2014-01-28
will do whitesmith! thanks for pointing a noob in the right direction.

---

### Post by Bashing-om on 2014-01-28
Joel_; Hey;

440 is an odd number, but believable as that memory may be shared out to other things, say video cards .
Yeah a lack of ram for 'buntu, best I recall ( and I can be mistaken) one wants a minimum of 512K.
As noted I am impressed with DSL - Damn Small Linux . It will install to hard drive and will fly on that hardware.
Partitioning: minimum is a "/" partition and a swap partition. and yes the installer will format the "/ = root" partition as ext4 format and swap as file type "swap".

How big is the hard drive ? There also exist minimums for the size of the hard drive for operating systems to install onto.
Once you start looking around, you will find other flavors you can install. Installing and (re-)installing different flavors will certainly teach you a lot, long about the 5th install I expect your hands will be real "dirty" !
If the drive is big enough, and you have developed the skill, one can boot several operating systems on the same hardware.

The install wizards will take care of formatting, as you gain experience, you may do that partitioning/formatting manually. Only you can know what you want in your operating system. Once you have mastered manual partitioning the linux world is your oyster !

[INDENT][INDENT][INDENT]it ain't nothing but a thing
[/INDENT][/INDENT][/INDENT]

---

### Post by king.of.random on 2014-01-28
That lack of RAM is your main problem. Is it possible to increase this amount. You'd need to research the maximum it can take and see if it is still available though. You should also make sure you have a swap partition as explained above. This will handle (very slowly) processes when the RAM is maxed out. The usual formula for calculating the size of your /swap partition is to double the amount of RAM.

Chrunchbang is a debian based distro that uses the openbox desktop (super light weight desktop manager) and may be more suitable to your needs. This link describes it in more detail and offers the link to download it: 

[http://distrowatch.com/table.php?distribution=crunchbang](http://distrowatch.com/table.php?distribution=crunchbang)

I wish you luck in getting that laptop up and running to your requirements.

---

### Post by Joel_ on 2014-01-28
Just a little update. Puppy was super simple to get installed on the hd, but I wanted more.. I tried ubuntu 12.04, booting it off of the usb instead of dvd, and it would get half way through and freeze. So I tried ubuntu minimal 12.04, half way through I would get stuck at a purple screen. Each of these times I gave it about an hour to work out its problems with no joy. Then I tried lubuntu and IT WORKS!! I am typing this very post on it. I packed up my windows compy and now I am doing my online classes on the old crappy laptop. So far it has given me no problems, I even managed to get spotify on it! 

Thanks a ton!

---

### Post by Bashing-om on 2014-01-28
Joel_; Great !

enjoy

[INDENT][INDENT]feels good all over, huh ?
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2014-01-29
I know you're set now but just a tip with the minimal install. Yes, it goes to a purple screen and looks like it is doing nothing for ages ... then springs to life and it is finished! Bit of an oversight that there is no spash to tell you things are in progress. Reason? It is downloading the entire kernel, it is not on the disk to start with, so depending on your connection and hardware specs, an hour is not out of the question before it springs back to life again. 

The minimal install is smaller than Lubuntu so no reason that shouldn't have booted from USB. ;)

---

