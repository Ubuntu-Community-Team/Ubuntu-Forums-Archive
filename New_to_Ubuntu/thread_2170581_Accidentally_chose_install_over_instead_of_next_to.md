---
title: "Accidentally chose install over instead of next to."
date: 2013-08-26
forum: New to Ubuntu
---

### Post by sean-s-bishop on 2013-08-26
So I think I really messed up. I was trying to install Ubuntu 13.04 over 12.04 and accidentally hit install over. It brought me to the next screen where you choose where your located and it wouldn't let me go back. I rebooted my computer and now I only have one partition showing my old entire hardrive capacity. How do I get windows and all my data back. Why would Ubuntu just start rewriting over anything without confirming? There was no warning besides what was written under the option and I wanted to install it over 12.04 but not the entire disk. I am currently stuck using a live usb, but managed to download testdisk and am trying to run it, but it has been an hour and still says please wait. Is there any way to get my data back?

---

### Post by eternal243 on 2013-08-26
Well there are software that can restore data, test-disk is supposed to be able to, but I have never tried it, if you want to do that however you should make sure to not use that hdd for anything until you have done so, since every time you write to the disk you risk corrupting the old data by overwriting it.

---

### Post by sean-s-bishop on 2013-08-26
Thats what I am doing. My only option right now is to run from the live-usb I have.

---

### Post by eternal243 on 2013-08-26
Yep, but live usb and live cd's aren't really that bad, they are actually quite awesome in emergencies like these, where you need to recover lost data and so on. =)

---

### Post by sean-s-bishop on 2013-08-26
Any idea why testdisk is just sitting at the Please wait... screen. It's been going for about 30 minutes right now.

---

### Post by eternal243 on 2013-08-26
Well, it could be it is actually working as intended, although I suspect it is slow since you are running it from a live usb system. Not really sure though since I haven't used it, maybe someone else can give a better answer than me.

How big is your HDD, that you are trying to recover files from? A bigger drive will definitely take quite some time to recover, although CPU speed will have some impact on that as well.

---

### Post by cody4 on 2013-08-26
This may make the recovery process faster as it would avoid the need to run the recovery software from the live usb:
You will need an external hard drive that you don't mind disassembling and a second computer with the recovery software installed.

Remove the casing from the external hard drive and you should be able to unplug the drive itself (external hard drives are simple regular hard drives with a usb adapter). Remove the damaged hard drive from the computer and plug it into the external hard drive case. Now you should be able to plug the damaged hard drive into a computer and it will mount just like an external hard drive. So plug it into your second computer with the recovery software installed and away you go.

---

### Post by sean-s-bishop on 2013-08-26
Edit: Trying a deep scan using testdisk.

---

### Post by sean-s-bishop on 2013-08-27
snip



Can anybody help with this? I'm at a loss.

---

### Post by Elfy on 2013-08-27
drag and drop of images can go horribly wrong and leave text - can you try again with the image using the attach image

---

### Post by sean-s-bishop on 2013-08-27
Thank you Elfy. I was trying to edit it, but it kept freezing on me.

Why is it so difficult to take a screenshot? This stuff used to work flawlessly three years ago and now you click one button and without asking ubuntu deletes your entire hard drive in ten seconds before even asking your timezone . I would have expected this from Apple but good lord, no wonder Canonical is going down so fast.

---

### Post by sean-s-bishop on 2013-08-27
Where are the screenshots even saved?

---

### Post by coffeecat on 2013-08-27
> **sean-s-bishop said:**
> Why is it so difficult to take a screenshot? 

Simply press the PrtScrn key.

> **sean-s-bishop said:**
> Where are the screenshots even saved?

Where you save them. After you press the print key and you hear a camera shutter noise, a window pops up giving you a preview of the screenshot and giving you a choice of saving to the clipboard or to a folder. It defaults to the Pictures folder, but you can change this. You can change the filename too.

---

### Post by sean-s-bishop on 2013-08-27
I had no popup show up, just a white flash like a shutter click and that was it.

---

### Post by sean-s-bishop on 2013-08-28
So I managed to get gpart to run on my lost harddrive and these are the results. 

```
Ok.

Guessed primary partition table:
Primary partition(1)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(2)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(3)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r


```

My original harddrive that I lost had four partitions. Should I attempt to restore it or is this not finding anything?

---

### Post by sean-s-bishop on 2013-08-30
Anyone?

---

### Post by eternal243 on 2013-08-30
> **sean-s-bishop said:**
> So I managed to get gpart to run on my lost harddrive and these are the results. 

```
Ok.

Guessed primary partition table:
Primary partition(1)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(2)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(3)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r


```

My original harddrive that I lost had four partitions. Should I attempt to restore it or is this not finding anything?

> **sean-s-bishop said:**
> Anyone?

Okay, something is certainly messed up, it might be possible to rescue some data, but I have never tried, although there should be some application for it in Linux.

---

### Post by sean-s-bishop on 2013-08-31
I have already considered the data a full loss, so I am not worried about losing it or not retrieving it, but I am curious and would like to try and get it back. That way I can help others if the issue comes up. I am just having trouble seeing how in ten seconds or so 630 gb's could be gone just like that.

---

### Post by eternal243 on 2013-09-01
Well, from a simple google search I found these links. 
**->** [ddrescue recovery tool]("http://www.gnu.org/software/ddrescue/ddrescue.html")
**->** [10 linux rescue tools]("http://www.techrepublic.com/blog/10-things/10-linux-rescue-tools-for-recovering-linux-windows-or-mac-machines/")

---

### Post by newb85 on 2013-09-01
If it's a matter of not even seeing the partitions (as opposed to the data on the partitions), it sounds like you need a tool like gpart.  It's a tool to be used with gparted, and its purpose is to examine the contents of the directory and guess the partition table.  It's in the Universe.

Be warned, like most data recovery tools, it takes a long time.

---

### Post by sean-s-bishop on 2013-09-01
Newb85, I posted my output of gpart earlier in the thread. It guessed four partitions, but that's it. I am not sure if I should try to restore it.

---

### Post by newb85 on 2013-09-01
As I understand it, restoring the partitions really involves nothing more than re-writing the partition table (at the beginning of the drive).  As the partition table there is currently incorrect, it seems to me you have nothing to lose by trying it.  But maybe you should wait for someone else to chime in and confirm that.

---

### Post by sean-s-bishop on 2013-09-04
Is there anybody that has any idea on what my gpart output means?

---

### Post by Quackers on 2013-09-04
Hi sean-s-bishop, have you tried Testdisk? It has recovered partitions and all or some of the data that was in them in the past. If the data is already considered a total loss you really don't have much to lose. Have a look here
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")

EDIT I see you tried Testdisk earlier but it seems to have been taking a long time. Did it finish its search eventually? What output was there.
For free options Testdisk is about the best I've used.

---

### Post by sean-s-bishop on 2013-09-04
Hi Quackers, I did try testdisk and it gave me a funny output too, unfortunately I couldn't post the screenshot. I have since dd my old hard drive the one that was lost to another hard drive that I created a new partition on. Unfortunately, when I run testdisk now it only finds the whole new hard drive instead of the individual partition that is what my lost hard drive used to be. Sorry, that may have been kind of hard to follow.

---

### Post by sean-s-bishop on 2013-09-07
Boy, the help around here is extremely difficult to come by. When I started on Ubuntu around 9.04 on my netbook this was the place to go. What happened? No offence to the few that have tried to help, I really do appreciate it.

---

