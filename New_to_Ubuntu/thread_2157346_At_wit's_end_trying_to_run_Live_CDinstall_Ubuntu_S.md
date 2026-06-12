---
title: "At wit's end trying to run Live CD/install Ubuntu Studio or Xubuntu"
date: 2013-06-25
forum: New to Ubuntu
---

### Post by Bolwerk on 2013-06-25
So I downloaded and burned DVD's of Ubuntu Studio and Xubuntu to take them for a spin.  

Initially tried to use the built in dual boot help included with Ubuntu Studio.  That brought up the Windows failed start-up screen every time I selected Ubuntu from Window's dual boot screen.  

I tried doing it without the dual boot screen; just booted from the DVD via changing the boot order via the BIOS menu.  Got some sort of "security header" message (I forget the exact message, but it was something in that vein) in the top left corner of my screen.  So I do some research, find out about the secure boot debacle, and thus promptly go into the BIOS and disable secure boot.  No more message, just a black screen.... forever.  
 
Then I find out that it's probably a video card/driver issue (especially since my video card is an AMD Radeon); so I press e when selecting an option from the GRUB 2 boot menu, and try the nomodeset suggestion after quiet splash and also deleting quiet splash.  I also try adding pci+noacpi based on a suggestion from another post I've read in these forums.....nothin'.  (of note, is that the GRUB 2 editing menu options for Ubuntu Studio and Xubuntu seem rather small; i.e. only 2 lines of code/settings/options in comparison to the paragraphs of options I've seen from screenshots of other Ubuntu distros)

So................. due to the fact that most other posts and tutorials that are tangentially related to this issue seem geared towards experienced Linux users, I'm officially at my wit's end.

Any help would be greatly appreciated.

---

### Post by mastablasta on 2013-06-25
have you checked the md5sum of the downloaded file before burning it on DVD?: [https://help.ubuntu.com/community/HowToMD5SUM?highlight=%28%28HowToMD5SUM%29%29](https://help.ubuntu.com/community/HowToMD5SUM?highlight=%28%28HowToMD5SUM%29%29)

have you verified the burned files?

looks like your downloaded image is not the same as the one on server. and yet it has to be exactly the same for it to work.

graphics card will be supported (at least some basics) with default opensource drivers. but you might need the nomodeset boot parameter.

---

### Post by Bolwerk on 2013-06-25
Just checked the md5sum of both files and they are identical to the originals.

---

### Post by halevuli on 2013-06-25
I have an AMD Radeon card and I'm using Ubuntu right now so I doubt it's your video card.

---

### Post by holycow131415 on 2013-06-25
Is this a laptop?

Does the dvd appear to be spinning when it is a black screen (do you hear it loading the livecd) ? If so, use your keyboard shortcut to change the brightness. There was a recent kernel bug that makes screens black.

---

### Post by Bolwerk on 2013-06-25
No, it's a Windows 8 tower that I bought recently.

I'm going to try again to see if the DVD is spinning.  Btw, what's the keyboard shortcut to alter the screen brightness?  I'm checking here:  [https://help.ubuntu.com/community/KeyboardShortcuts](https://help.ubuntu.com/community/KeyboardShortcuts)  but no luck; or are you referring specifically to laptop shortcuts?

---

### Post by Bolwerk on 2013-06-25
Okay, so I burned a DVD of a different flavor of Ubuntu (Linux Mint) to try out.  Same GRUB 2 screen; same black screen after pressing enter on the option to start it; but I can hear the DVD spinning like a hurricane.

---

### Post by Bolwerk on 2013-06-25
Also tried the "install from Windows" option with Linux Mint; goes to 'windows failed startup screen' at boot and whenever I select Linux Mint from the Windows 8 dual boot screen; just like when I performed a similar function with Ubuntu Studio.

---

### Post by ty74 on 2013-06-25
Windows 8 has its own bois sometimes try startings windows 8 going into that under general in settings

---

