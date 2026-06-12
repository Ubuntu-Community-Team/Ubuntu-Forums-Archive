---
title: "Can't direct connect on ubuntu."
date: 2015-11-29
forum: New to Ubuntu
---

### Post by trevor28 on 2015-11-29
Hello everyone, I am new to the community and just recently installed ubuntu and this is the first time I have ever used a non-windows operating system. So far everything is going pretty well and I really love it. Especially I was having major problems on windows 10, and 8 causing my computer to almost be unusable when I just bought it a few months back. With Ubuntu on it everything works great. Now to the point, I tried searching the forums here looking for similar posts, however, I wasnt able to find anything on the subject. So I apologize if I made a mistake by making this post. My laptop is an Asus F555LA-AS51. This is my first time using linux and I was unsure about how to download drivers etc. However since installing it last night everything really appears to be working great on it. But recently I connected it to my ethernet connection and it worked for about 10 minutes before disconnecting/dropping and throwing my back on wifi and not allowing me to reconnect. I am just assuming this is a driver issue since I havn't installed any yet. If anybody has any knowledge of asus computers and can help me/point me in the right direction it would be greatly appreciated.
Thank you for any help/advice in advance.

---

### Post by Geoffrey_Arndt on 2015-11-29
Very rare to need driver install for an ethernet connection . . . (99.9% of time connection is automatic) . . . . are you sure ethernet cable securely attached to laptop?   

Have you tried connecting ethernet before booting up laptop?    Does the network manager applet show a wired connection (via edit connections)?

---

### Post by trevor28 on 2015-11-29
I suppose it could have been lose last time, I just now tried direct connecting before booting my pc. So far so good no problems. But we will see. It does show the connection currently yes, and it also did last time until it randomly disconnected. so far it seems to be working though. I was assuming I would have to install some drivers in order for everything to work so that was my first guess.

---

### Post by Bucky Ball on 2015-11-30
> **trevor28 said:**
> I was assuming I would have to install some drivers in order for everything to work so that was my first guess.

Welcome. Drivers for lots of hardware, graphics and wireless, are included right there in the Ubuntu kernel. Unlike Win, you don't need to manually install drivers for lots of them. You got lucky by the sounds and the drivers for your wifi are already in the kernel.

Just out of curiousity, please open a terminal and post the output of this command:

```
sudo lshw -C network
```

That will give us an idea of what you have and which drivers Ubuntu has installed for you.

There can sometimes be a bit of a conflict between wired and wireless. If one is up, the other can't connect, etc. If ethernet dropped, system would have automatically dropped to wifi and possibly blocked any other connections until a reboot. Booting with the cable in will give the cable priority. :)

---

### Post by trevor28 on 2015-11-30
wow that is awesome, I guess I am just used to windows. I have been told with the field I am going into I need to get some linux experience, I just havn't had the chance yet I guess. But I bought a new laptop about 5 months ago and after upgrading to Windows 10 I had an issue with 100% Disk Usage, and I spent months and months reverting back to windows 8, reinstalling the OS, trying multiple fixes in every direction... before I finally got frustrated and made the switch to ubuntu. After my experience here so far, I don't think I am ever going back.Anyways thank you for the help here, last night I did boot with the ethernet cable connected and it worked the entire time perfectly. As long as it works I am happy, Here is the information

---

### Post by Bucky Ball on 2015-11-30
Thanks for sharing, but sorry, trevor28, the 'wall of text' approach is beyond me so I didn't get far into it. Please use paragraphs when posting. Thanks. :)

As for terminal output, please use code tags so it is readable. See the last link in my signature.

---

### Post by trevor28 on 2015-11-30
I apoligize that was unreadable... for some reason even when in advanced reply or edit I don't see the little hashtag to click so I can post my code.

---

### Post by trevor28 on 2015-12-01
I just wanted to give an update im not sure why I have no options for posting, however, after all day yesterday trying it out booting my pc with the ethernet already connected it works great so I guess I was too quick to jump to a conclusion that something was wrong. However, while I am here I would like to get some advice on another issue if you don't mind lately the last few times when booting my computer I get an error message which I never have a chance to read fully but it says something about my hard drive not mounted and gives me options to wait or do it manually. Have you ever seen this before? or have any idea what this may be? I looked around a little bit and seen people who had this issue with external hard drives etc. However I only have one internal main hard drive. Any advice is greatly appreciated thank you

---

### Post by sandyd on 2015-12-01
> **trevor28 said:**
> I just wanted to give an update im not sure why I have no options for posting, however, after all day yesterday trying it out booting my pc with the ethernet already connected it works great so I guess I was too quick to jump to a conclusion that something was wrong. However, while I am here I would like to get some advice on another issue if you don't mind lately the last few times when booting my computer I get an error message which I never have a chance to read fully but it says something about my hard drive not mounted and gives me options to wait or do it manually. Have you ever seen this before? or have any idea what this may be? I looked around a little bit and seen people who had this issue with external hard drives etc. However I only have one internal main hard drive. Any advice is greatly appreciated thank you

If it vanishes after a while, it should be fine - vanishing means that it has mounted the partition correctly. Sometimes the messages show up briefly while the system is booting.

Do you have an encrypted system by the way (i.e. chose full disk encryption during setup)?

If you do, that message is normal. The swap file is encrypted, and needs cryptswap to be setup before it is usable. Sometimes cryptswap is a bit slow to get up and running which is why you see the messages.

---

### Post by trevor28 on 2015-12-01
ok yeah it has been happening all day today and I have restarted my pc about 3 times. After the message my pc boots up just fine and works just fine other than my wallpaper reverting back to the stock ubuntu wallpaper once. I will say i was trying to uninstall a program via terminal earlier and for some reason it couldnt find the program no matter how many times I double checked and slowly typed out the program name not sure if that means anything either. I don't have a full disk encryption no. I do have my home folder encrypted though.

---

### Post by sandyd on 2015-12-01
> **trevor28 said:**
> ok yeah it has been happening all day today and I have restarted my pc about 3 times. After the message my pc boots up just fine and works just fine other than my wallpaper reverting back to the stock ubuntu wallpaper once. I will say i was trying to uninstall a program via terminal earlier and for some reason it couldnt find the program no matter how many times I double checked and slowly typed out the program name not sure if that means anything either. I don't have a full disk encryption no. I do have my home folder encrypted though.

Home folder encryption should create a cryptswap too, so that is likely what the message it is.

If you post the messages you get, we should be able to help further.

---

### Post by trevor28 on 2015-12-01
Okay so just a quick update on this issue shortly after my last post I noticed on my Unity Dock my hard drive was showing, and next to it was an eject symbol like there would be if it were a usb flash drive or something. Anyways I went in to settings and seen under disks that automatic was off and realized that it was supposed to be on. I am not sure how that happened. Anyways after doing so it disappeared from my dock but like an hour later I got an error message saying "Ubuntu 14.04 had an internal error" and it told me I needed to restart my pc so I did. When doing so I got a new error message during the boot screen that was similar to the last one except this time it said "the disk drive for /dev/mapper/cryptswap1 is not ready yet or not present"

---

### Post by sandyd on 2015-12-01
Post output of the following:
```

sudo fdisk -l
sudo blkid
cat /etc/crypttab
cat /etc/fstab
```

---

### Post by scoutchorton on 2015-12-02
> **trevor28 said:**
> lately the last few times when booting my computer I get an error message which I never have a chance to read fully but it says something about my hard drive not mounted and gives me options to wait or do it manually. Have you ever seen this before? or have any idea what this may be?

trevor28, a mounted drive is just a drive readily available to use.

[ATTACH=CONFIG]265892[/ATTACH]

This is my Windows partition (I have a Ubuntu dual boot), and it is just a quick link on the sidebar to it. If you go to the file browser and the sidebar looks something similar to this:

[ATTACH=CONFIG]265893[/ATTACH]

The Computer part is the Ubuntu files (/ and subdirectories). The Windows is the, well, Windows files. So, if you don't have the Windows on the Ubuntu sidebar, it's ok. But if it isn't on the Files (like the second screenshot), then you might not be in the best boat.

Anyways, good luck! :D

---

