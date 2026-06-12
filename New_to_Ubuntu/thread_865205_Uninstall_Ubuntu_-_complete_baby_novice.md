---
title: "Uninstall Ubuntu - complete baby novice"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by darla1753 on 2008-07-20
I'm sorry of this has been asked before, I've read some other people's replies, but they were too complicated for me!

To give some background:  My laptop hard drive failed so I went a bought a new one.  However, I had lost the windows CD and am broke so decided to see what linux was like instead.  Whilst I can appreciate that it's great for a number of things, I'm simply too much of a novice to make it do what I want it to, I'm afraid, so now want to uninstall it so I can use the hard drive as a portable device.

I tried putting the hard drive in a new case, plugging it into a computer so I could format it.  Whilst the computer recognised that there was new hard ware, I couldn't find it in explorer or anywhere else!  My suspicion is that it is because the HD has linux on it and windows doesn't like that and so can't cope.

So I put it back into the laptop and tried to look around to find out how to uninstall it, but I can't find any button or similar where I can just select the hard drive and click format.

If it is possible to completely format the hard drive through linux (even though linux is running on it), could someone please explain it to me in the most baby steps possible?

I saw on some sites that I should write certain instructions, but I don't even know which program I'm meant to write these in.

I'm sorry to be such a novice over all this and would appreciate any help that can be given!

DARLA

ps: the reason I don't use the windows CD of the other computer to just format the drive is because I onyl have upgrade CDs, not the originals.  Windows, in any capacity, is therefore not an option for this uninstall!

---

### Post by pavel989 on 2008-07-20
do u have the live cd?

the thing is, XP which i assume the other computer was, has a device manager, which will recognize an hard drive and can wipe it. on the other hand, u can't wipe what your using so u can just clean of linux while booted into it. which is why you need a live cd.

also XP doesnt load it because you dont have the driver installed. windows typically uses FAT32 and NTFS formats. Linux uses ext3 usually, and xp doesnt know about that. so you could just get a driver for it and use it to store stuff and still hold linux on it. but as i said before, to completly wipe it, you need either a live cd, or find the device manager in xp/vista, i can help you with both. sorry to hear that you're leaving the linux world

---

### Post by JagDragon on 2008-07-20
OK. I will presume you are on Ubuntu right now, so you can open up a terminal by going to the Applications menu -> Accessories -> Terminal. First of all, we need to install the partitioner. So, type in ```
sudo apt-get install gparted
```Once that is finished, we need to run it by typing ```
gparted
```. This program will start, and you will see all of the hard discs connected to your computer. One will have two partitions, ext3 and swap, and the other will have one partition.

Erase or reformat the other partition and exit.

---

### Post by solwic on 2008-07-20
> **darla1753 said:**
> I'm sorry of this has been asked before, I've read some other people's replies, but they were too complicated for me!

To give some background:  My laptop hard drive failed so I went a bought a new one.  However, I had lost the windows CD and am broke so decided to see what linux was like instead.  Whilst I can appreciate that it's great for a number of things, I'm simply too much of a novice to make it do what I want it to, I'm afraid, so now want to uninstall it so I can use the hard drive as a portable device.

I tried putting the hard drive in a new case, plugging it into a computer so I could format it.  Whilst the computer recognised that there was new hard ware, I couldn't find it in explorer or anywhere else!  My suspicion is that it is because the HD has linux on it and windows doesn't like that and so can't cope.

So I put it back into the laptop and tried to look around to find out how to uninstall it, but I can't find any button or similar where I can just select the hard drive and click format.

If it is possible to completely format the hard drive through linux (even though linux is running on it), could someone please explain it to me in the most baby steps possible?

I saw on some sites that I should write certain instructions, but I don't even know which program I'm meant to write these in.

I'm sorry to be such a novice over all this and would appreciate any help that can be given!

DARLA

ps: the reason I don't use the windows CD of the other computer to just format the drive is because I onyl have upgrade CDs, not the originals.  Windows, in any capacity, is therefore not an option for this uninstall!

Pop the drive back in to your Windows computer, then go to Control Panel -> Administrative Tools -> Computer Management.  In that Window, on the left, under "Storage" you'll see "Disk Management".  Click that, and it'll see the drive as "Unknown Partition" (For instance...my Windows XP sees my Linux partition as:  "425.82GB Healthy (Unknown Partition)").  

Right click, delete partition, then create a new NTFS partition and it'll work with Windows.  

Good luck!  :)

EDIT:  That is, of course, assuming you have a desktop computer with Windows XP installed, and that you're hooking the laptop drive up as a secondary, or slave, drive.  :)

---

### Post by darla1753 on 2008-07-21
Thank you all for your help - wonderfully clear instrucions!  Mwah :)

It's worked :)

When I get a new computer, I'll re-install ubuntu on the old one and have a better play to learn how to use it (hate being ignorant grrr:mad:)


DARLA
xx

---

