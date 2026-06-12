---
title: "trying to un-lag Ubuntu"
date: 2013-02-16
forum: New to Ubuntu
---

### Post by Sarger001 on 2013-02-16
Help!
Installed Ubuntu via Wubi Installer to my WinXP Device with 5 gigs given. However, Ubuntu lags. I can still boot XP and it doesn't lag but ubuntu takes ages to click a button. If i remove files on XP, will that speed ubuntu up? Can i re-install with another size? HELP!

---

### Post by snowpine on 2013-02-16
Welcome to the forums!

It's meaningless to discuss performance without mentioning hardware. Tell us about your: CPU, RAM, video card, hard drive, etc.

If your computer is from the XP era then it's probably too weak for the full Unity desktop; you might want to try a lightweight desktop such as Xfce or LXDE as described here: [http://www.psychocats.net/ubuntu/xfce](http://www.psychocats.net/ubuntu/xfce)

---

### Post by 3rdalbum on 2013-02-16
Wubi is not good from a speed, flexibility and stability perspective. Try removing it and installing Ubuntu by booting from the Ubuntu CD.

Also, what graphics card do you have? If it is ATI or Nvidia there may be a driver you can install and get snappier performance.

---

### Post by Sarger001 on 2013-02-16
The thing is, it can't be that bad of a PC. It runs minecraft at 40fps smoothly, so a OS should not be a problem. I'll try that now, however.







EDIT:



Just booted into Ubuntu and am met with a purple screen and nothing else. It's been there for 2 mins now.



Rebooted into recovery mode with black screen. Shall reboot again.

3rd Edit:

Booted with success. Shall install XFCE.

---

### Post by Bölvaður on 2013-02-16
> **Sarger001 said:**
> The thing is, it can't be that bad of a PC. It runs minecraft at 40fps smoothly, so a OS should not be a problem. I'll try that now, however.

EDIT:
Just booted into Ubuntu and am met with a purple screen and nothing else. It's been there for 2 mins now.

40 fps is low for a game like minecraft unless if you set that as max fps.
What CPU (processor/core) do you have? (any info like number of cores or hz is sufficient)
Amount of RAM?
Is your harddisk greatly fragmented? (when did you defragment on xp?)
What GPU do you have? (how old is your graphic card?)

Did you do ANYTHING at all (installing software or anything) in ubuntu after installing it?

---

### Post by Sarger001 on 2013-02-16
ATI Radeon Xpress 200 Series. Updated to latest driver.
I think i have about 500mb of ram. Not much, but it suits me.
And no, i did nothing in ubuntu other than surf the web (Which is very fast, actually)

---

### Post by EnigmaticCoder on 2013-02-16
Choice of window manager plays an important role in speed. If you're willing to try a tiling window manager, awesomewm is lightweight and improves productivity.

(I wish I could recommend something without it sounding like an ad, but I hope this helps)

---

### Post by Bölvaður on 2013-02-16
I think you should keep XFCE with 512MB in RAM. The Unity interface is alright on that RAM amount but XFCE is going to be a bit lighter on your CPU and RAM, which looks like you need.


Btw about deleting files in XP. No that wont speed Ubuntu up. When you used Wubi it made a normal file on your XP partition and installed Ubuntu into that file pretending it is a hard disk drive. If you have been using this computer for long it could mean that file is on many different parts on your hard disk, making it slow to read. What you can do then is to degrag XP. If it is very fragmented it could take a long time.


Btw again.. are all problems away (by magic)?

---

### Post by Sarger001 on 2013-02-16
> **Bölvaður said:**
> Btw again.. are all problems away (by magic)?

Nope. It just actually booted up.

Installing the pack now. Might take a while, so i'll get some rest.

EDIT:
Welp. I'm back, still installing. It's about halfway, i give it another hour. Despite how much lag there is, i'm starting to like this OS and it might replace my XP.

---

### Post by Sarger001 on 2013-02-16
When i select xubuntu or xfce it goes to a black screen and takes me back to the login screen. Any help?

---

### Post by Sarger001 on 2013-02-17
Ugh. It's a pain to even open the software centre. Can i somehow boot into windows, shut it down and still run Wubi?

---

### Post by DuckHook on 2013-02-17
There are a number of counts working against you here.

1. WUBI install
2. Low-powered box
3. Wrong flavour of 'buntu

Let's take them in order.

1. WUBI is, in my opinion, a bit of a deal with the devil. It's designed to make it much easier for Windows users to try out Ubuntu because it doesn't require disk repartitioning (a risky venture, especially for new users). It performs this sort of sleight-of-hand by shoehorning a virtual partition into a file in Windows. So, unlike a true partition, your HDD performance suffers because each disk I/O must be journalled and handled twice--first to ext4 which is Ubuntu's default file type, then translated to NTFS which is Windows. Just as bad--if the WUBI file is installed into Windows notoriously fragmented diskspace, then it will be scattered all over heck's half-acre and the read head will be jumping all over your HDD like a cricket on a frying pan for every read or write, but especially during boot or on updates. Last but not least, if your WUBI file is ever corrupted, it's game over. So, a WUBI install is not only a big performance hit, but fragile.

2. You still have not posted your CPU or video RAM, but based on your video chip and system RAM, I am guessing that it is a single-core lightweight mobile-type processor. The combination of these low-powered components mean that your box is barely powerful enough to run Ubuntu, which is designed for higher-powered systems. My minimal recommendation for a happy Ubuntu experience is duo-core CPU, 2GB system RAM, 3D-video chip with 256MB dedicated video RAM. Anything less may still work, but won't be snappy, with performance diminishing rapidly as spec goes down.

3. Therefore, the proper flavour for you is Lubuntu or one of the very lightweight distros outside of the 'buntu family, like Crunchbang. Trying to run Ubuntu on your system is like trying to haul a semitrailer with a motorcycle. It can be done, but not meant to be.

Recommendations:

1. Try Lubuntu on a LiveCD to see how you like it. No need to install it at all.
2. If deciding to install, backup first, then do true dual boot instead of WUBI.
3. You will see instant performance increase and the experience will actually be pleasant.

---

### Post by presence1960 on 2013-02-17
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)

I know a lot of people install wubi intending it to be a permanent installation. However it is not meant to be a permanent installation, but rather a test drive to see if you like ubuntu without having to partition your hard disk. And as wubi inevitably does, it fouls up and then those using it as a permanent installation demand miracles to get it to run. Don't believe me? Read the article in the above link paying attention to the second question and the answer to that question.

+1 for Lubuntu.

---

