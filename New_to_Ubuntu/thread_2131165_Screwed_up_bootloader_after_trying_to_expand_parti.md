---
title: "Screwed up bootloader after trying to expand partion"
date: 2013-03-31
forum: New to Ubuntu
---

### Post by Chuckn2x on 2013-03-31
After trying to expand my Ubuntu partion of my dual boot Windows 7/ Ubuntu through Gparted, I restart my computer and Ubuntu won't load up, but instead, gives me some error about not being able to mount or something. I then go through Startup repair using the Ubuntu live USB, restart, and from what was in Grub: Ubuntu, Ubuntu Advanced Options, and Windows 7, I now only see GNU/Linux and GNU/Linux advanced options. I can't boot into Ubuntu, it just stays at a purple screen, and Windows 7 isn't an option any more. I am now stuck using the Live USB. 
-Edit: I managed to get into Windows 7 by reinstalling the Windows boot manager. Still cant access Ubuntu, gonna try startup repair again.

---

### Post by daslinkard on 2013-03-31
> **Chuckn2x said:**
> After trying to expand my Ubuntu partion of my dual boot Windows 7/ Ubuntu through Gparted, I restart my computer and Ubuntu won't load up, but instead, gives me some error about not being able to mount or something. I then go through Startup repair using the Ubuntu live USB, restart, and from what was in Grub: Ubuntu, Ubuntu Advanced Options, and Windows 7, I now only see GNU/Linux and GNU/Linux advanced options. I can't boot into Ubuntu, it just stays at a purple screen, and Windows 7 isn't an option any more. I am now stuck using the Live USB. 
-Edit: I managed to get into Windows 7 by reinstalling the Windows boot manager. Still cant access Ubuntu, gonna try startup repair again.

Welcome to the forums!!  My very first question would be whether or not you need Windows 7 on your machine?  Personally I dumped Windows a little over a year ago and have not looked back.  However, I know that each situation is different for each individual.  What version of Ubuntu are you running?

---

### Post by Chuckn2x on 2013-03-31
Yes, I stick with windows just because some stuff I'm too lazy to transfer over, and I like gaming, and know there are still some issues with that with Linux. I have Ubuntu 12.10. Things were working smoothly until I started screwing around, trying to expand the partion. I just felt like I'd be using linux more and more often so I wanted to give it some more space.

---

### Post by daslinkard on 2013-03-31
> **Chuckn2x said:**
> Yes, I stick with windows just because some stuff I'm too lazy to transfer over, and I like gaming, and know there are still some issues with that with Linux. I have Ubuntu 12.10. Things were working smoothly until I started screwing around, trying to expand the partion. I just felt like I'd be using linux more and more often so I wanted to give it some more space.

Obviously you have a couple of different options here....the first would be reinstalling Ubuntu all together.  Some could say this is the most painful simply because you'd be starting over from scratch.  The other thing that you could try would be to fix your Grub.  I have a [link]("http://www.howopensource.com/2012/05/reinstall-recover-grub-from-ubuntu-12-04-live-cd-usb/") here that hopefully helps you repair your Grub from your live cd.  Let me know if this helps!

---

### Post by Chuckn2x on 2013-03-31
I already tried the Startup repair, but I'll give it one more go. Whenever I try to boot into Ubuntu, it just gives me a bunch of error messages. I can't give you those error messages right now, because it's not accessible using Windows Boot loader, but I will try once I reinstall grub again.

---

### Post by black veils on 2013-04-01
maybe the ubuntu partition needs to have an equivalent of check disk.

the disk utility application, which shows smart status, has another option for filesystem check.

---

### Post by Chuckn2x on 2013-04-01
How would I do that? I looked at it, ran the SMART drive thing, and it said my hard drive was okay.

---

### Post by black veils on 2013-04-01
once the drive is selected from the left pane, the right will show options. click the ubuntu partition on the right side. at the lower area there is a button saying "check file system", click it.

---

### Post by Chuckn2x on 2013-04-01
no option for that from what I'm looking at.

---

### Post by black veils on 2013-04-01
[COLOR=#000000]this can be done from the command line then. so boot the live usb, and make sure you know the location of your ubuntu partition. open terminal application, paste the following in ```
sudo fsck /dev/sdaX
``` replace the X with your partition number. [/COLOR][COLOR=#000000]press the enter key[/COLOR][COLOR=#000000].

fsck will check the file system and ask which problems should be fixed  or corrected. If you don't want to type y every time then you can use this command instead ```
sudo fsck -y /dev/sdaX
```

Please note if any files are recovered then they are placed in */home/lost+found *directory[/COLOR][COLOR=blue]

[/COLOR][COLOR=#000000]source: [/COLOR]
[COLOR=#0000cd]http://linuxpoison.blogspot.tw/2009/04/how-to-checkrepair-fsck-filesystem.html[/COLOR]

---

### Post by Chuckn2x on 2013-04-01
okay, then just run the Startup repair again?

---

### Post by black veils on 2013-04-01
your ubuntu live usb, like what you must have used for the disk utility application

---

### Post by Chuckn2x on 2013-04-01
Tried it, and no luck. The error messages I got where along the lines of corrupted file system, unable to launch, etc.etc. I just got fed up with it, deleted the entire partion, and am now reinstalling ubuntu. Thank you for your help. One more question, if WIndows 7 doesn't appear in grub, how do I add it in? It was just kind of an automatic thing before.

---

### Post by black veils on 2013-04-01
its always best to install ms.windows before a linux, but you can do it this way.

in gparted, in your new ubuntu install, create a new ntfs partition to the right of ubuntu. then boot the ms.windows disc to install on that partition.

afterwards boot the ubuntu usb and do the following

- choose "Try Ubuntu" 
- connect internet 
- open a new Terminal, then paste in: 
```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
```
- Press Enter. 
- Then paste in: 
```
sudo apt-get install -y boot-repair && (sudo boot-repair &)
```
- Press Enter
- launch **boot repair** then choose recommended repair option.
this should work.

source: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


Edit: i realised you dont need to do any of this, you didnt remove the ms.windows partition. oh well it might be useful for someone.

---

