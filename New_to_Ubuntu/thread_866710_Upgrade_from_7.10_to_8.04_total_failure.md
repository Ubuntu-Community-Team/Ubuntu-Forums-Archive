---
title: "Upgrade from 7.10 to 8.04 total failure"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by bryanp on 2008-07-22
This is my first foray into Linux. No previous Linux experience, although my computer days go back to DOS 3.1.  Running an HP Pavillion A509.uk. 2.6Ghz celeron, 512 mb ram 40gb HD, with second 20Gb drive on second drive cable. 250 KB/s internet. Previously working great on 7.10. Upgrading from 7.10 to 8.04.was a nightmare!  Backed everything up, including Evolution to a USB HD. Just in case, I downloaded an 8.04 install CD from Ubuntu site. Upgrade went well, then an error message (which told me to consider a bug report) that APCID wasn't upgrading properly and probably wouldn't work. using second PC, found a workaround for this on a Forum. Then the same for PulseAudio. Then the same for Gnome Desktop. At 9 minutes remaining, it was configuring locales, "en AU.UTF-8". 20 mins later, sporadic HD activity and clearly hung, although some functionality available on the main system. Couldn't shutdown from the main system so I pulled the plug (literally) and tried a boot off the ISO image CD. The system hung up. Tried twice more, no joy. Reinstalled 7.10 from CD and all working fine. Reinstalled 8.04 from the CD and all worked fine, all home files and Evolution reconfigured. After 4 hours, all is well. Not sure what I did wrong, or what is weird about my system - any comments?? All seems to be working OK, although I haven't had time to check much yet. Lesson learnt is that backup's are essential on an off-line device. Linux is definitely not for the timid or for a main machine, if my experience is anything to go by, but I stand to be corrected.

---

### Post by muteXe on 2008-07-22
Upgrading went horribly wrong for me when trying to go from Feisty to Gutsy (7.10).  I'd backup and do a clean install to be honest.  

mute

---

### Post by waspbr on 2008-07-22
well, as far as i can tell those glitches are very random, I have upgraded from gutsy on two machines, a desktop and an hp laptop, and all went smooth, though yeah, every now and then you will hear something like what happened to you, good thing you thought ahead and backed up everything. 

normally the safer way to do things is to do a fresh install, but I can see how inconvenient that can be...

tap yourself in the back and go get yourself a cold beer.

---

### Post by bryanp on 2008-07-22
Thank you folks for taking the trouble to reply. To be honest, from the forums I read, I half expected problems in the early days of 8.04, so didn't upgrade when it first came out (lesson learnt from M$ days - never be the first to upgrade!) I decided that 8.04 had been out long enough for the glitches to be sorted so went for the upgrade rather than clean install. Memo to self: don't be tempted to hit the upgrade button when next LTS upgrade appears!

---

### Post by ramjet_1953 on 2008-07-22
With any install, hardware plays large part in success.

Many people have had no joy with Pulse Audio.

For me, the only problem was that Hardy didn't recognise, or configure my laptop's on-board WinModem, which was recognised and configured automatically under Gutsy, after asking if I wanted to use a restricted driver.

A tip also. When writing on these forums for help, don't write a long, unbroken diatribe.

It is very hard for us to read.

Break each point up into a paragraph and you will get more responses, as some people refuse to wade through one long paragraph.

Regards,
Roger :cool:

---

### Post by MrWES on 2008-07-22
I got the same error when upgrading via the upgrade manager. Hung forever on locales. Luckily, I had setup my machine with a separate /home partition and ended up doing a clean install from the CD. Worked fine after that.

Bill

---

### Post by bryanp on 2008-07-22
Roger, thanks for the tip. Any tips to help a newbie like myself are much appreciated!

---

### Post by kostkon on 2008-07-22
In two days I upgraded from *7.04* to *8.04* (i.e. *7.04 -> 7.10*, *7.10 -> 8.04*) and it went well, without any problems at all. In a few cases, during the upgrades, the system seemed to had stuck, but obviously it was doing its work configuring the packages. 

During an upgrade, it may take the system a lot of time to configure some packages, that is my personal experience anyway.

---

### Post by sharks on 2008-07-22
try upgrading without a cd. type in terminal:

sudo apt-get dist-upgrade

---

### Post by SlappyPappy on 2008-07-22
I've read about people who upgrade and it all went great, some who had a small problem here and there, and then I've heard the horror stories. 

I'm the cautious sort because I'm actually doing work in Ubuntu. I'm still using Gutsy and I got a second hard drive where I've done a clean install of Hardy and I'm slowly building it up to the same level of efficiency, programs etc that my Gutsy install has. I'm in no rush and testing everything thoroughly. 

So far no problems with hardware and software choices. Best of all, no pain and slow down with my work because I'm still working in Gutsy.

Hope you get to sort out all your issues.   :)

---

### Post by bryanp on 2008-07-28
The saga continues....
I spent the rest of the week trying (unsuccessfully) to mount and display a second internal hard drive - which had worked OK under 7.10.

I tried every command I could find in the various forums, to no avail. The device was mounted, but would not display, eventhough the "display volumes" was ticked in nautillus editor. Spent a lot of time reading many forums - thanks to all for the various tips and tricks.

I also found my Sony NWZ 818 wouldn't mount (but it had in 7.10) and other folk, according to the forums have found the same. And I can't find anyone who has got the beast to work yet. 

So decided to go Back to 7.10. However, trying to boot into Live CD mode made the PC hang. Tried all sorts of thisngs but...
Long story short: 
Delete all but the primary partition
Reformat using partition magic to FAT32. The install then reformats to ext3. (Tried many other combinations, but this is the only one that worked).
Boot into Safe Graphics mode on 7.10 CD (Nothing else worked)
Run Live CD, then install.
Update all 228 7.10 updates
Mount and display 2nd HD (hooray)
Restore Evolution files
Drink copious quantities of a cheeky Autralian Merlot

As a newbie to Linux, I don't know what I have done wrong, nor have an understanding of what I need to do to make 8.04 do what 7.10 does. 
However. 7.10 works, and does all I (currently) need to do. So I shall leave well alone and simply accept that unless you know what you're doing at quite an advanced level, the moto of "If it Works - Don't fiddle with it" is one I need to follow.

---

