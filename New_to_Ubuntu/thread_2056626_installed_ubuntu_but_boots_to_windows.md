---
title: "installed ubuntu but boots to windows"
date: 2012-09-11
forum: New to Ubuntu
---

### Post by BenTaeubel on 2012-09-11
hello i am brand new to the linux/ubuntu world.  i just installed ubuntu 12.04.1 aside win 7 using a CD.  i did install the 32-bit version.  i have an intel core i5 processor which, to my understanding, is 64-bit.  do i NEED the 64-bit version of ubuntu? 
anyways, i finished installation and when i rebooted, there is no prompt to boot windows or ubuntu.  
i need some babying here as i am new. i know a tad bit, but i will probably be asking questions along the way if i don't understand so bear with me
i am on an asus k55a laptop, if it helps.

any help appreciated, thanks!

---

### Post by Bashing-om on 2012-09-11
ben; Hi !  Welcome to the forum. 
 ...no boot options indicates grub (grand unified boot loader) is not installed onto the booting drive.

Easily fixed.
If you are at a ubuntu command line: Log in with user name and pass word. Your password will echo nothing back to the screen (security reasons).
from this command line next enter:
```

sudo grub-install /dev/sda  
sudo update-grub

```This is assuming you only have one disk drive installed.

else:
          advise what type of prompt are you seeing (> grub )(???)

Here are links for grub info/instructions:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/](http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/)

As to 32/64 bits ..32 bit will run just fine on the 64 bit hardware.

Questions are a way to learn ...ask away ![INDENT]warm regards <==BDQ
[/INDENT]

---

### Post by Bucky Ball on 2012-09-11
Welcome.

32bit will run fine, 64bit better.

Fire away with all questions; post in appropriate sub-forums; always use descriptive titles and give as much info as poss about your issue; *always* do some searching before posting here. ;)

Your title here says it boots to win but your post says it boots to neither. If it is booting to win, then hit the shift key when you boot the machine and just after the BIOS screen and that should take you to a list with Ubuntu and Win listed. Take your pick. Try this before reinstalling grub as it is unclear what you are getting; Win or a blank screen at boot. 

If the latter, and you are staring at a cursor, try simply:

```
startx
```

That should get things kicking regardless of whether grub is installed or not. Try these things before reinstalling grub. It may already be there. ;)

---

### Post by BenTaeubel on 2012-09-11
thanks both for the welcome!

> **Bashing-om said:**
> ben; Hi !  Welcome to the forum. 
 ...no boot options indicates grub (grand unified boot loader) is not installed onto the booting drive.

Easily fixed.
If you are at a ubuntu command line: Log in with user name and pass  word. Your password will echo nothing back to the screen (security  reasons).
from this command line next enter:
```

sudo grub-install /dev/sda  
sudo update-grub

```This is assuming you only have one disk drive installed.

else:
          advise what type of prompt are you seeing (> grub )(???)

Here are links for grub info/instructions:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/](http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/)

As to 32/64 bits ..32 bit will run just fine on the 64 bit hardware.

Questions are a way to learn ...ask away ![INDENT]warm regards <==BDQ
[/INDENT]

how can i use command prompt if i cannot boot ubuntu? can i do it using a live cd? one of the links shows how to reinstall grub2 using a live cd should i go with that?

> **Bucky Ball said:**
> Welcome.

32bit will run fine, 64bit better.

Fire away with all questions; post in appropriate sub-forums; always use  descriptive titles and give as much info as poss about your issue; *always* do some searching before posting here. :wink:

Your title here says it boots to win but your post says it boots to  neither. If it is booting to win, then hit the shift key when you boot  the machine and just after the BIOS screen and that should take you to a  list with Ubuntu and Win listed. Take your pick. Try this before  reinstalling grub as it is unclear what you are getting; Win or a blank  screen at boot. 

If the latter, and you are staring at a cursor, try simply:

```
startx
```That should get things kicking regardless of whether  grub is installed or not. Try these things before reinstalling grub. It  may already be there. :wink:

sorry  for being unclear, but it boots straight to windows, without allowing  me to choose between win or ubuntu. also, i have accessed the BIOS  (pressing esc) and i can't seem to find any selection regarding OS  choices.

---

### Post by oldfred on 2012-09-12
Post link to BootInfo from this:

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by BenTaeubel on 2012-09-12
ok i ran boot repair. it reinstalled grub2 (i think) but when i rebooted i got a message saying to select boot source (since i took out live cd) and could not load windows nor ubuntu!!  i got a url paste.ubuntu.com/1199940/

---

### Post by Wim Sturkenboom on 2012-09-12
UEFI might be in the way :) See e.g. [http://ubuntuforums.org/showthread.php?t=1974392](http://ubuntuforums.org/showthread.php?t=1974392)

What worked for me
[LIST]
[*]burn ISO to pendrive
[*]boot system with pendrive inserted and press the key required to select the bootdevice; this is a BIOS action
[*]in my case, the pendrive was recognized twice, once as USB and once different (can't remember the wording)
[*]I choose the USB one and installed Ubuntu
[/LIST]
and that was it. Dual boot ready to go ;)

PS the motherboard is an Asrock H61M-VS

---

### Post by YannBuntu on 2012-09-12
Hello

> **BenTaeubel said:**
> ok i ran boot repair. it reinstalled grub2 (i think) but when i rebooted i got a message saying to select boot source (since i took out live cd) and could not load windows nor ubuntu!!  i got a url paste.ubuntu.com/1199940/

Your PC is EFI, so you should definitely use a 64bit disk. See [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by BenTaeubel on 2012-09-12
> **YannBuntu said:**
> Hello



Your PC is EFI, so you should definitely use a 64bit disk. See [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

you were absolutely right! i installed a 64-bit ubuntu via flash drive and it works! thank you very much.

---

### Post by YannBuntu on 2012-09-13
Good! :)

Please could you indicate your new [Boot-Info]("https://help.ubuntu.com/community/Boot-Info") URL?
Also you can login to your Launchpad account (create one if you haven't yet) then mark yourself as affected by this bug:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555)

---

