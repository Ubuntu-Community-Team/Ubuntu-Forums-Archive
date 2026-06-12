---
title: "I have two internal HD's with 2 versions of Ubuntu, how to use both?"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by tahitiwibble on 2008-11-11
I have updated my system to 8.04 by installing it on a second HD that I had and moving /home onto that HD.

I can't for the life of me get wine to work in 8.04 with a very important reference library, or even to work at all for that matter. On my second HD is good old 7.04 and my Windows program in Wine which works perfectly.

How can I use both environments without having to physically unhook one or the other HD to boot from the one that I need to use?

---

### Post by Hospadar on 2008-11-11
You can configure grub to give you the option to boot either kernel.  I'm not sure exactly how to do it with your setup, but I know it would involve plugging both hdd's in and going into whichever ubu your bios picks by default, then configuring grub on that version of ubuntu.

I think your best bet is to start reading up on grub and how to install and configure it.  It's really not so difficult once you get going.

Here's a somewhat wordy page in the community docs on the topic: [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
Googling would turn up all sorts of similar and helpful pages.

Also, I might suggest taking a look at the version of wine you are running in 7.04 vs 8.04, then try grabbing the old version from the wine website and install that in 8.04

---

### Post by tahitiwibble on 2008-11-11
> **Hospadar said:**
> You can configure grub to give you the option to boot either kernel.  I'm not sure exactly how to do it with your setup, but I know it would involve plugging both hdd's in and going into whichever ubu your bios picks by default, then configuring grub on that version of ubuntu.

I think your best bet is to start reading up on grub and how to install and configure it.  It's really not so difficult once you get going.

Here's a somewhat wordy page in the community docs on the topic: [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
Googling would turn up all sorts of similar and helpful pages.

Also, I might suggest taking a look at the version of wine you are running in 7.04 vs 8.04, then try grabbing the old version from the wine website and install that in 8.04

Thanks for the pointers, I'll start looking into grub. I was worried about connecting both HD's and having some horrible conflict occur which may lose me more stuff. I lost a whole HD during the past 4 days of upgrading. My poor tired brain is really frazzled right now.

I did try to install the old version of Wine on 8.04 but got "Error: dependency is not satisfiable: libldap2", and couldn't proceed any further.

---

### Post by cariboo on 2008-11-11
To make things  a lot easier I would have a look here:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

and use Super Grub Disk to help setup grub properly.

Jim

---

### Post by tahitiwibble on 2008-11-12
> **cariboo907 said:**
> To make things  a lot easier I would have a look here:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

and use Super Grub Disk to help setup grub properly.

Jim

Jim,

Thanks, however the Super Grub Disk site is a little involved for someone with my limited knowledge. Is the CD a little more intuitive?

Just what's going to happen if I connect both HD's and boot up as normal?

All the best,

Martin

---

### Post by kattman on 2008-11-12
Do you have a "boot menu" on your computer splash screen? ie "F10".
I did that way untill i just edited Grubs menu.lst.

---

### Post by tahitiwibble on 2008-11-12
> **kattman said:**
> Do you have a "boot menu" on your computer splash screen? ie "F10".
I did that way untill i just edited Grubs menu.lst.

kattman, negative, I don't have the "boot menu".

---

### Post by kattman on 2008-11-12
Here is my menu.lst, Windows in on the first ide port. and the bios is set to boot the second ide port by default.(ubuntu /puppy linux)
Change the Puppy part to match your Ubuntu/windows drive (ie hd1,2)


## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=15122944-09a7-49f9-a606-09b32fa7eeb9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic

title		Puppy linux 4.00
root		(hd0,2)
kernel		/boot/vmlinuz root=/dev/hdb3 pmedia=idehd

title 		Windows XP MediaCenter
map 		(hd0) (hd1)
map 		(hd1) (hd0)
root 		(hd1,0)
savedefault
makeactive
chainloader +1

quiet

---

### Post by skitter.rusty on 2008-11-12
Just connect one to the slave then when it prompts you press the the appropriate button (Usually F10) to get into your BIOS or Boot Order menu and choose the correct drive. Doesn't go through grub though.

---

### Post by caljohnsmith on 2008-11-12
> **tahitiwibble said:**
> I have updated my system to 8.04 by installing it on a second HD that I had and moving /home onto that HD.

I can't for the life of me get wine to work in 8.04 with a very important reference library, or even to work at all for that matter. On my second HD is good old 7.04 and my Windows program in Wine which works perfectly.

How can I use both environments without having to physically unhook one or the other HD to boot from the one that I need to use?
It sounds to me like the crux of your problem is that you are letting 8.04 and 7.04 share the same /home partition, and your Wine directory ".wine" is located in your home directory. It could be that the newer Wine in 8.04 is not compatible with the older one available in 7.04 I think. If you move your .wine directory to back it up, reinstall Wine in 8.04, that might fix your problem getting Wine to work in 8.04. But then when you want to use Wine in 7.04, you would have to move the new 8.04 .wine directory and replace it with the original 7.04 .wine directory. That's one reason why I don't think it is a good idea to share a /home across distros or even different versions of the same distro. :)

---

### Post by tahitiwibble on 2008-11-12
> **caljohnsmith said:**
> It sounds to me like the crux of your problem is that you are letting 8.04 and 7.04 share the same /home partition, and your Wine directory ".wine" is located in your home directory. It could be that the newer Wine in 8.04 is not compatible with the older one available in 7.04 I think. If you move your .wine directory to back it up, reinstall Wine in 8.04, that might fix your problem getting Wine to work in 8.04. But then when you want to use Wine in 7.04, you would have to move the new 8.04 .wine directory and replace it with the original 7.04 .wine directory. That's one reason why I don't think it is a good idea to share a /home across distros or even different versions of the same distro. :)

Hi Mr. Smith,

In fact I haven't hooked up the two drives simultaneously yet.

The scenario is that I have two completely separated HD's that have never been powered up together, for fear of the stuff hitting the fan again. 

The old one contains one partition with 7.04, Wine 0.9.33 and it's own /home directory; on this HD Wine works perfectly with my beloved reference library. 

The new one has two freshly formatted partitions (I thought this to be an improvement), one partition for my 8.04 system files and the other for my /home directory; on this HD I have never been able to install the version of Wine (1.0 I believe) in "add/remove" applications and much less use my reference library.

I'm trying to figure out if I can use them both without having to physically unhook one or the other and going through all the involved shutdown/bootup procedures.

---

### Post by caljohnsmith on 2008-11-12
While you are in 8.04, it's possible to "chroot" into the 7.04 partition as though you had actually booted into the 7.04 partition, and run the wine programs from your 7.04 partition while you are in 8.04. I have done exactly this type of thing myself so that I don't have to install all the programs in my new distro that my old distro has, unless I want to. 

How about going ahead and hook up both your HDDs, boot into 8.04, and then you can set up a chroot environment for running applications from your 7.04 partition like so (change sdXY to your 7.04 partition):
```
sudo mkdir /media/Ubuntu_7.04
sudo mount /dev/[COLOR="Blue"]sdXY[/COLOR] /media/Ubuntu_7.04
sudo mount --bind /dev /media/Ubuntu_7.04/dev
sudo mount --bind /proc /media/Ubuntu_7.04/proc
sudo mount --bind /sys /media/Ubuntu_7.04/sys
sudo mount --bind /tmp /media/Ubuntu_7.04/tmp
xhost +
sudo chroot /media/Ubuntu_7.04 /bin/bash

```
After doing all the above steps, you will be essentially "booted into" your 7.04 install. Next do:
```
su -l [COLOR="Blue"]<username>[/COLOR]
export DISPLAY=:0.0
cd ~/.wine/drive_c/"Program Files"
```
And replace <username> with the user name you use in 7.04. Now you can run wine apps in 7.04, and they will displayed in the 8.04 Ubuntu you are booted into. Just find your Wine apps in that "Program Files" folder above, and then run them with:
```
wine [COLOR="Blue"]<program.exe>[/COLOR]
```
And they should run fine if all goes well. Let me know if you decide to give it a shot; I know it works for me for almost all programs. :)

---

### Post by tahitiwibble on 2008-11-12
Mr. Smith,

I like this approach of yours very much, it looks to be very clever, and I love the idea of being able to leave old versions wholly intact until such time as one decides that they are no longer needed. Please be patient with me for I have a couple of questions/concerns. I seem to follow the logic and actions accomplished by the code, however;

1/ Does this procedure have to be repeated every time that I want to access the 7.04 HD? (for some vague reason, I would assume not)

2/ What are the risks of data loss in trying this out?

3/ What is going to happen when I boot up a computer with two fully functional OS's on two distinctly separate HD's?

---

### Post by caljohnsmith on 2008-11-12
> **tahitiwibble said:**
> 
1/ Does this procedure have to be repeated every time that I want to access the 7.04 HD? (for some vague reason, I would assume not)

Yes, normally you would have to repeat the procedure each time you boot into 8.04; or you could instead put all those commands in a bash script, and then put that bash script in maybe your /etc/rc.local file so that it gets executed automatically on start up. Then I think you could even add menu entries for your 7.04 apps in 8.04 so that everything worked without any extra effort. I haven't actually tried that so there might be a few details we would have to work out to actually get everything working OK. But I know doing it all from the command line like I gave in my previous post works. :)
> **tahitiwibble said:**
> 
2/ What are the risks of data loss in trying this out?

All you are really doing is mounting your 7.04 partition while you are in 8.04, and then running apps from the 7.04 partition. As long as you follow the directions carefully that I gave in my previous post, I don't think there is any significant risk of any data loss at all; one thing you should be careful of is after doing the "chroot" command, immediately do the "su" command I give after that so you aren't the root user. But as I mentioned, I have tested it and know it works for me, so I think you will be fine to. 
> **tahitiwibble said:**
> 
3/ What is going to happen when I boot up a computer with two fully functional OS's on two distinctly separate HD's?
That's not a problem at all, in fact that's the case for at least 90% of the people who use Ubuntu I think; they have multiple OSes on one or more drives, so they either dual boot or multi-boot. That's what the Grub boot loader is meant for; you can have just about as many OSes as you want on any number of HDDs, and you can boot them all from Grub. In your case, just set your BIOS so that the Ubuntu 8.04 drive is first to boot on start up, and then you should be able to boot into 8.04 with no problems. If for some reason you can't change your BIOS and can only boot your 7.04 drive, that's not a problem either, because you can easily add the 8.04 drive as a boot option in the 7.04 Grub menu. Let me know how it goes, or if you run into problems. :)

---

### Post by tahitiwibble on 2008-11-12
Thank you Mr. Smith,

I am going to have to digest and research a few things but will let you know what happens when I try this.

Once again, thank you. :)

---

