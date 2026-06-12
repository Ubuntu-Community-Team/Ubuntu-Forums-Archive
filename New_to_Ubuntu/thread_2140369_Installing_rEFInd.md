---
title: "Installing rEFInd"
date: 2013-04-29
forum: New to Ubuntu
---

### Post by Spency on 2013-04-29
Hi Everyone! :p

I have a black Macbook 1,1 which I installed the latest Ubuntu onto, but I'm having terrible difficulty installing rEFInd. 

I managed to install rEFInd via Mac OSX when it was still installed, which allowed me to install ubuntu via usb; however, after intentionally wiping OSX during ubuntu installtion, to my surprise, rEFInd was stripped with it. I know ubuntu comes with grub, but it's not entirerly clear to me whether it's simply for ubuntu and memtest or for other operating systems as well; but more importantly, I much prefer rEFInd for Mac computers for native boot menu integration.

Installing rEFInd on OSX was a piece of cake, but the same method does not seem to work through ubuntu. 

I downloaded the binary zip fil via [http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)
and in OSX terminal ran the install.sh, which worked like a charm.

When I try the same operation in ubuntu I get this error: 

```
:~$ sudo '/home/xxxxx/Downloads/refind-bin-0.6.9/install.sh'
Installing rEFInd on Linux....
//boot/efi doesn't seem to be on a VFAT filesystem. The ESP must be
mounted at //boot or //boot/efi and it must be VFAT! Aborting!
```

I've been digging around for hours but have had little success.

I used this [thread]("http://forums.linuxmint.com/viewtopic.php?f=46&t=97221&start=60") to try to figure it out, but some of the steps they're taking are a bit bewildering for me at my level of knowledge.
I really don't know what to do except reinstall OS X and partition the system via OSX, reinstall rEFInd and then reinstall ubuntu onto a partition. I would rather just partition through linux and add OSX. 

Sorry if this is a very stupid question, any and all advice would be greately appreciated. 

Thank you in advance,
Spency

--EDIT--

I made some progress with this guide: [http://www.rodsbooks.com/refind/installing.html#linux](http://www.rodsbooks.com/refind/installing.html#linux)

Probably should have looked there to start with instead of googling error messages, but now I've hit a rock with step 6. 

When I type in: 
```
** efibootmgr -c -l \\EFI\\refind\\refind_x64.efi -L rEFInd** 
```

I get back this error:
```
 Fatal: Couldn't open either sysfs or procfs directories for accessing EFI variables.
Try 'modprobe efivars' as root.
```

I get the same error if I only type efibootmgr. 

```
 sudo modprobe efivars 
``` 
Seems to do nothing. 

Any ideas?

---

### Post by Spency on 2013-04-29
Well, it looks like I bricked by computer following that guide. :-( Guess I'll have to reformat with mac os and try again.

---

### Post by Kopkins on 2013-04-29
That efibootmgr command is know to brick the mac firmware. You'll probably have to go back to an apple store and have them reflash it. The official documentation for refind also says that on macs it should really only be done on the mac side or else there's a pretty big chance of things turning out poorly. There are different processes for installing on linux and on mac. That is in the official documentation. 

Good luck, Sorry about your apparent bad luck so far.

When I was doing it, i remember I was very cautious after reading all the things that could go wrong on a mac. Be sure to read the offical documentation thoroughly before trying. I spend 3 days reading the documentation before I was comfortable continuing.

Kopkins.

Arch Linux, Mac OSX and Ubuntu 12.04 on MPB 8.1 with rEFInd.

---

### Post by Spency on 2013-04-30
Ah thanks for the Sympathy! :) The mac origional boot loader was still intact so was able to boot Leopard off a usb. I then partitioned the drive inside osx for linux and am now reinstalling. Fingers crossed this time I don't screw up.

---

