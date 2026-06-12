---
title: "Live CD boots [doesn't do much else]"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by Ricorich196 on 2008-07-03
Okay, so I've decided to make the jump into Ubuntu but before going in head first I decided I'd just try it without any change to my computer. 

I downloaded the ubuntu-8.04-desktop-i386.iso checked the md5 hash (everything was good), and burned it using Infra Recorder (as per the directions) at the lowest speed I could (1x) to a Memorex CDRW (700 MB) fresh out of the packaging.

I put it in my drive and reboot, it boots to the screen that says Ubuntu followed by [try without any change to your computer] [install] [check cd for errors] [memory test] ect. No matter what I click nothing happens at all, I let it sit there for 5 mins, 20 mins, an hour, and nothing.

My computer is a Dell Dimension 4600 w/ a Pentium 4 - 2.66Ghz and 1 GB of RAM. 

I've been trying to find an answer to my dilemma for the past 3 days and decided maybe it'd be a better idea to post here, hopefully someone can provide some insight.

Thanks in advance.

---

### Post by bluepowder7 on 2008-07-03
1 - does that menu even respond to mouse-clicks?  i've always just used the up/down arrows and hit enter to select the menu item

2 - do you have a normal cd-r (not an -rw) that you can try?  i've never tried to burn an iso image to an -rw.  also, you DID burn it as an iso image, right?  you didn't just dump the .iso file onto the cd as if it was a data file.

---

### Post by KenBW2 on 2008-07-03
Your specs are more than enough for the LiveCD

I know it doesn't help you wanting to try it out, but you could try the alternate install CD.

---

### Post by dodle on 2008-07-03
Sounds like your computer is plenty fast enough to handle the liveCD.  You might need to re-download the iso and burn it to a new cd.  This happened to me once before.

---

### Post by bcn17 on 2008-07-03
You might try burning again and manually choose a slow speed- Also, when I first tried ubuntu I had to use an alternate cd although I was able to select install on the screen you are talking about. 
*keep in mind that when you try ubuntu rather than a real install it will be the exact same except for much slower because It has to read from a cdrom rather than a harddrive. Keep us up to date with whats happening. I'll subscribe to this thread- GL!

---

### Post by bodhi.zazen on 2008-07-03
> **Ricorich196 said:**
> Okay, so I've decided to make the jump into Ubuntu but before going in head first I decided I'd just try it without any change to my computer. 

I downloaded the ubuntu-8.04-desktop-i386.iso checked the md5 hash (everything was good), and burned it using Infra Recorder (as per the directions) at the lowest speed I could (1x) to a Memorex CDRW (700 MB) fresh out of the packaging.

I put it in my drive and reboot, it boots to the screen that says Ubuntu followed by [try without any change to your computer] [install] [check cd for errors] [memory test] ect. No matter what I click nothing happens at all, I let it sit there for 5 mins, 20 mins, an hour, and nothing.

My computer is a Dell Dimension 4600 w/ a Pentium 4 - 2.66Ghz and 1 GB of RAM. 

I've been trying to find an answer to my dilemma for the past 3 days and decided maybe it'd be a better idea to post here, hopefully someone can provide some insight.

Thanks in advance.

Use the keyboard Luke ....

Hit "Enter" to select your language.

Hit "Enter" to boot.

Use the up and down arrow keys to select other options.

After selecting a language and hitting "Enter" you can select additional options with the F1 - F6 (Function) keys.

If that fails, it could be a problem with your videocard. Select "Safe graphics mode"

---

### Post by Ricorich196 on 2008-07-03
Sorry what I meant to say was, when it first boots I use the keyboard (not mouse clicks)  to select english and I am able to manuever through the menu by pressing up/down on the keyboard (as well as using the Function keys] however selecting anything on that menu (whether its check cd for errors or try without any change) it just hangs.

Brand new CDRWs were all I had hanging around. I burned it as an iso image (as per the directions on the ubuntu site) and I've tried burning it again with no difference. I burned both times at 1x (it doesn't get much slower than that =/) and I know that using the livecd will be slower but I really just want to give Ubuntu a "test drive".

I'm at my wits end. Thank you all so far for the speedy replies!

Also I've tried the safe graphics mode option and it didn't do anything as well =(.

---

### Post by bluepowder7 on 2008-07-03
do you have another computer on which you can try the CD?  even just to "try without making changes" to see if it really is the CD you made or if it's the DELL machine being difficult.

---

### Post by Ricorich196 on 2008-07-03
I'll only be able to try it on a dfferent computer later tonight.

---

### Post by Ricorich196 on 2008-07-03
Okay I just tried out the LiveCD on a different computer which had an AMD athlon xp 2400+ (2 ghz) and 1 GB of ram and instead it hung for a while (when i chose try without any change) and then have me an error saying I/O error Error reading boot cd [reboot] . Ugh this is gonna give me an aneurism (sp?)

---

### Post by bodhi.zazen on 2008-07-03
I wonder if you have a bad burn.

---

### Post by dodle on 2008-07-03
It sounds like maybe what bluepowder7 was saying; maybe it's the cd-rws.

---

### Post by bcn17 on 2008-07-04
It sounds like if you were to install ubuntu on the other computer you would need the alternate cd- This doesn't allow the test drive option you wanted though. There are ways to install from the harddisk from a usb drive but that may very well be more trouble than it's wort without a linux os to make the usb drive with.

To install from an usbdrive to harddisk-
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

To install onto a usbdrive and have a full ubuntu installation on a usb drive you can use unetbootin (there is a entry of unetbootin under the above link) although I tried this once to no avail from a windows partition to a free partition. 

If you try and install on a flash drive understand you should back up anything on it and that before you try you should format it with something like partition magic ( a bootable cd that is a linux environment) to be a fat32 or fat16 filesystem.

---

