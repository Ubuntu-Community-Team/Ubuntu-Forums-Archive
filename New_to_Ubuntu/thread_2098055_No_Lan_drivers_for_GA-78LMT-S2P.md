---
title: "No Lan drivers for GA-78LMT-S2P?"
date: 2012-12-25
forum: New to Ubuntu
---

### Post by nubejohn on 2012-12-25
Hello, this problem may have been covered elsewhere but I did not find it on a search.
  I am fed up with windows and looking to move to ultimate edition gamers or gamedrift (I have kids that like their windows games).  I have ultimate edition gamers installed (tried both 32 and 64 bit) with the same problem, no nic recognized.  I am posting using a usb live of fatdog64 which seems to have the drivers I need but I do not know enough about linux to harvest them (can that even be done?)

  All of this for the question, How do I get the drivers for my onbord lan?

MB is GA-78LMT-S2P, lan will depend on the revision which I am not sure of.
  Any help?

  Thanks, ,, 

  John.

---

### Post by candtalan on 2012-12-25
You might like to try a recent ubuntu on live usb as a test? The drivers are usually included. From your live fatdog64 session, to get more information about your hardware:  use a terminal and type
lspci
(return)
the response should include the name of the network chip. For example mine here is
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
hth

---

### Post by nubejohn on 2012-12-25
Thanks for the reply, and Merry Christmas, ,,:)

  I tried the most recent version yesterday, same results.  As for the terminal, crt-T does not bring one up and I do not see an option in the menu either?

> **candtalan said:**
> You might like to try a recent ubuntu on live usb as a test? The drivers are usually included. From your live fatdog64 session, to get more information about your hardware:  use a terminal and type
lspci
(return)
the response should include the name of the network chip. For example mine here is
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
hth

---

### Post by verymadpip on 2012-12-25
Try

ctrl+alt+t

Xubuntu is super (windows)+t

---

### Post by nubejohn on 2012-12-25
Thanks, but that did not do it either.
  The distro is Great as far as functionality, and may even connect if I had a wireless adapter, but the drivers for the onbord nic just does not seem to be present..

  How many choices for drivers can one board have?  Would it be worth my time to try installing drivers for the last few revisions of the board? (I purchased it new from tiger direct only about 4 months ago if that helps)

  If the answer to that question is yes, then I guess the big question becomes; Where do I find those drivers and how do I install them?

  Thanks again, ,  

  John.

> **verymadpip said:**
> Try

ctrl+alt+t

Xubuntu is super (windows)+t

---

### Post by nubejohn on 2012-12-25
Ok, rebooted to Ultimate Edition and ran lspci from there.
  Though the network jack does not light up or work in any way in ultimate, it does seem to recognize the device.  The output for the Ethernet controller is:

Ethernet controller: Atheros Communications Device 1083 (rev c0)

  This being the case, any advice?

---

### Post by candtalan on 2012-12-26
Good, now knowing that your ethernet is controlled by Atheros 1083 means that questions and searches can be very targetted. However, it is still not clear at this stage if the problem is simply lack of driver. 
Latest (Ubuntu) releases usually wrap up and include any previous lack, generally speaking that is. I would re state that it will be useful to specifically try a live session (USB maybe) of ubuntu 12.10 (and also perhaps 12.04.1) to test if the facility is normally present. I cannot say if your current install of ultimate relates accurately to - say - Ubuntu 12.10 - nor if your Ultimate is somehow a problem in this area. The benefit of a live session is that the software is, in a sense, a standard, and is unchanged.

A (rather quick) internet search outside this forum  did not seem to throw up much to suggest that atheros 1083 was an obvious problem for Ubuntu in 2012, but I did not look long.

hth

---

### Post by candtalan on 2012-12-26
Another thought, in case I am away for a time. If push comes to shove, if it was myself and time was short, I would grab another PCI NIC and set to use that. But my experience has been that in -almost- all cases over 8 years, wired ethernet has not had problems with Ubuntu. And any that did come up were later included in next releases.
hth

---

### Post by nubejohn on 2012-12-26
Thanks for the info, gota get some work done but will try to download ubuntu tonight and try that.
  I am guessing Linux is like Windows in that it can be installed side by side, what is the best partition tool to use with Linux so I don't loose what I have while I test?


> **candtalan said:**
> Another thought, in case I am away for a time. If push comes to shove, if it was myself and time was short, I would grab another PCI NIC and set to use that. But my experience has been that in -almost- all cases over 8 years, wired ethernet has not had problems with Ubuntu. And any that did come up were later included in next releases.
hth

---

### Post by candtalan on 2012-12-26
dl Ubuntu 
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
but do not install. Save the .iso image file and arrange to create a bootable USB (or DVD) with it.
This might be useful:
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)
FWIW I always use unetbootin, but  I only use it from Ubuntu, (I don't use any Windows)
Then boot from the ubuntu live usb stick, check the function of the ethernet etc. Good luck.

PS: yes you can install ubuntu alongside other  windows or linux based os.  However, once you move from the 'default' case where the target PC has only Windows on one HD,  the assisted install might get inaccurate. In all such cases I use the manual choice of 'Something else' in the installer. But this supposes you have prepared a system partition and have a linux swap partition to use (or you create one first). Partition changes can be potentially disastrous, ensure excellent backups FIRST! :-)

---

### Post by nubejohn on 2012-12-26
Thanks again, I will check out  the links after feeding the kids.
  I downloaded the new 32bit ubuntu and took the upgrade option and it seems to be working fine (posting  this from it), though the extra's from ultimate seem to be gone, but my documents are still in tact so all is well that ends well.

  Would it profit anything to use the 64bit version?
  Also, 3 of my kids love Diablo 2, which is one of the reasons I was trying to use gamers or gamedrifter (both ubuntu based).  Anyone here have exp with D2 on Ubuntu?

> **candtalan said:**
> dl Ubuntu 
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
but do not install. Save the .iso image file and arrange to create a bootable USB (or DVD) with it.
This might be useful:
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)
FWIW I always use unetbootin, but  I only use it from Ubuntu, (I don't use any Windows)
Then boot from the ubuntu live usb stick, check the function of the ethernet etc. Good luck.

PS: yes you can install ubuntu alongside other  windows or linux based os.  However, once you move from the 'default' case where the target PC has only Windows on one HD,  the assisted install might get inaccurate. In all such cases I use the manual choice of 'Something else' in the installer. But this supposes you have prepared a system partition and have a linux swap partition to use (or you create one first). Partition changes can be potentially disastrous, ensure excellent backups FIRST! :-)

---

### Post by audiomick on 2012-12-26
> **nubejohn said:**
>  what is the best partition tool to use with Linux so I don't loose what I have while I test?

When you get your ubuntu installer CD or USB organised, you can boot into the live environmnt, the "try without installing" option in the boot menu, and use gparted from there.

You should, however, use the windows tool to work on windows partitions, and boot windows a couple of times after you have done that to give it a chance to run the file system repair tool if it wants to.

---

### Post by nubejohn on 2012-12-26
Windows is gone, ,, , :)
  Ubuntu 12.10 is working well, though I miss the extras that was in ultimate.
  

> **audiomick said:**
> When you get your ubuntu installer CD or USB organised, you can boot into the live environmnt, the "try without installing" option in the boot menu, and use gparted from there.

You should, however, use the windows tool to work on windows partitions, and boot windows a couple of times after you have done that to give it a chance to run the file system repair tool if it wants to.

---

### Post by candtalan on 2012-12-27
> **nubejohn said:**
> Windows is gone, ,, , :)
  Ubuntu 12.10 is working well, though I miss the extras that was in ultimate.

You might consider - install into Ubuntu 12.10 an app or two that Ultimate has that you like, it may be possible. Also -both 'wine' and playonlinux might work. both worth a little research. Also of course, consider a virtual machine install of your windows (virtualbox), although unlike in wine etc the VM does give a slower performance. Keep aware that many games are now being written for Ubuntu (steam whatever? I am not a games person).
good luck

---

### Post by nubejohn on 2012-12-27
Thanks for the help.  So far I am loving Ubuntu, and looking into the idea of upgrading the kernel on a ultimate or gamedrift install?
  Right now I am still getting to know 12.10, have wine installed and have the D2 downloader installing D2.  This seems to be the most important part for my kids, LOL.
  I play a bit of Diablo, but these kids love their games.
  Bottom line, Windows changes too often and the last truly stable version imo was 98SE, which no new hardware plays nice with now.  It is just time for a change, ,  :)

> **candtalan said:**
> You might consider - install into Ubuntu 12.10 an app or two that Ultimate has that you like, it may be possible. Also -both 'wine' and playonlinux might work. both worth a little research. Also of course, consider a virtual machine install of your windows (virtualbox), although unlike in wine etc the VM does give a slower performance. Keep aware that many games are now being written for Ubuntu (steam whatever? I am not a games person).
good luck

---

