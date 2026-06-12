---
title: "Kubuntu wont start, etc.,"
date: 2014-05-06
forum: New to Ubuntu
---

### Post by Robin_Perrett on 2014-05-06
First of all it was my understanding that the Kubuntu operating system would need approx. 4Gb+. My Kubunto ISO file only took up IGb of space on the DVD. After inserting the disk and re-booting, all I got was the word Kubuntu (and its trademark). After another 10 minutes another line appears reading: "Booting system without full network configuration.. . . ." Maybe something else will appear with time. I am really eager to use Linux, but this isn't a very good start. Please reply with SIMPLE advice, I am a real beginner. Thank you kindly.
 Kubuntu 14.04

---

### Post by coffeecat on 2014-05-06
You can ignore the difference between the approx 1GB DVD and the 4GB or so needed for an installation to hard disk. The image on the DVD is highly compressed.

A live DVD should only take a couple of minutes or so to boot up. The first thing to exclude is a bad ISO download. Did you check the md5sum? If not, a howto is here:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

And the md5sums for Kubuntu 14.04 are here:

[http://www.kubuntu.org/getkubuntu](http://www.kubuntu.org/getkubuntu)

Click on the arrow in front of "Kubuntu 14.04 LTS (Latest Release and Long Term Support)" to get the dropdown. The md5sums are at the bottom of the dropdown.

The second thing to exclude is a bad burn. I notice that you were having difficulty burning an ISO in your (now closed) earlier thread. With the Ubuntu live DVD, a screen with two small icons at the bottom appears a few seconds after it starts to boot. If you tap any key at that point you are presented with an old style menu and the third (or so) choice on the menu is a disc integrity check. I don't know whether the Kubuntu live DVD has the same. Perhaps someone who uses Kubuntu can confirm whether it does or not. If you do see a screen with two icons at the bottom a few seconds after starting to boot, try that.

If your md5sum is OK and you still get problems with the DVD I would advise burning the ISO to a USB flash drive, so long as your machine supports booting from USB. Useful howto for Windows here:

[https://help.ubuntu.com/community/Installation/FromUSBStick#Creating_a_bootable_Ubuntu_USB_flash_drive_from_Windows](https://help.ubuntu.com/community/Installation/FromUSBStick#Creating_a_bootable_Ubuntu_USB_flash_drive_from_Windows)

---

### Post by ibjsb4 on 2014-05-06
And what are your computer specs (cpu, ram, video)?

---

### Post by SeijiSensei on 2014-05-06
If the DVD boots, you'll eventually be placed in the GUI desktop with a "Try Kubuntu" and an "Install Kubuntu" option.  Choose the first one so you can run off the DVD and make sure everything works as advertised.  

Unless you're really short on disk space I'd give Kubuntu at least 10 GB of space.  It will consume disk over time for things like logs and any files you store.

---

### Post by Robin_Perrett on 2014-05-07
Thanks fellows. I'm checking now. I will get back to you.
 I'm back again. When the 2 small icons appeared I held down a Key and the menu popped up. I selected the 'check disk for defects' and it checked all the files. when "Check Finished'. it stated: 'errors found in 1 file'. ' Press any Key to reboot your system.' when the 2 small  icons appeared again, I pressed a key and the main menu opened. I selected "Start Kubunto". Now all I have on the screen is the Kubuntu title & trademark. After 10 minutes the addition of: "Booting system without full networkconfiguration.... So it appears I have to fix this one error. How do I do that? Should I burn another disk?

---

### Post by mastablasta on 2014-05-07
yeah that means there is a small error that was made either during DVD burning or download. it is important that image is exactly as on server. a good way to avoid these issues is to download using torrent and to use USB instead of DVD.

does the system still boot? otherwsie while kubuntu logo is on you should be able to press esc and see what is oging on under it. that too can give clues to errors etc.

having some specs here would also be nice.  that way people can advise if your PC is compatible with Kubuntu or not.

---

### Post by coffeecat on 2014-05-07
> **Robin_Perrett said:**
> "Check Finished'. it stated: 'errors found in 1 file'.

That means that the DVD is faulty. Don't use it. As mastablasta said, either an error during download or during burning.

Did you check the md5sum? It is important to do so before trying to burn another DVD. If the md5sum is correct then you could try to burn another DVD. (Or use a USB flash drive as I suggested earlier.) If the md5sum is incorrect, then the ISO you downloaded should not be used and you need to do another download.

---

### Post by Robin_Perrett on 2014-05-08
Windows XP, X86 based PC, System 32, 1,920Mb memory, 60Gb HDD, ATI Radeon Xpress 200m, Service Pack 2.
 I downloaded the Kubuntu 14.04 from your advised links. I compared the MD5sum figures, they both  were correct. I inserted the newly  burnt disk, re-booted, nothing. I shut down and re-started the laptop, nothing again. I did everything according to your instructions and now I don't even get the Kubuntu and its trademark. It just starts with Windows as if I didn't have a disk inserted. Very frustrating!!
 I just checked the disk in My Computer, it's empty. Start again!

---

### Post by mastablasta on 2014-05-08
emtpy disk is of no use :)

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Robin_Perrett on 2014-05-09
I don't think Linux wants me! I burnt a new disk, re-booted, Kubuntu 14.04 started. I selected to try it out. I was perusing the desktop for about 10 minutes and the screen went black with the exception of  7 lines of text in the top left corner. 5 lines of hardware error, 1 referring to a Kernel panic, and the last line saying: panic occurred, switching back to text console.
 And that's where the saga ends!

---

### Post by heidi3 on 2014-05-09
Would it be worth trying a different flavour? I'm VERY new to Linux and tried Kubuntu on a clapped out 12 year old pc. It was very slow even after I got it going so I tried Lubuntu. Loaded like a dream on the ol' gal. It may not be a solution but it was mine albeit a work in progress.

Good luck anyhow :) Hope you find what you looking for?! :)

---

### Post by SeijiSensei on 2014-05-09
When machines boot properly, then act up after use, it's often an indication of problems with hardware. Try booting the Kubuntu disk again and running the memory tester overnight.  Another possibility is overheating, especially if this is a laptop.  Have you blown out any accumulated dust from the machine with a can of compressed air?

---

### Post by buzzingrobot on 2014-05-09
> **Robin_Perrett said:**
> First of all it was my understanding that the Kubuntu operating system would need approx. 4Gb+

That's pretty minimal. While the files that comprise the OS may take 4GB, anything you add will increase the space requirement.

> After another 10 minutes another line appears reading: "Booting system without full network configuration.. . . ." 

That likely is the result of several minutes of repeated unsuccessful attempts to establish an internet connection.  That might be related to the unidentified hardware issues you seem to have (since you report one successful boot off the ISO), or it might be related to something wonky or unusual with you net connection.  Wired ethernet connections typically pose no problem. Certain wireless chip/cards that target Windows can be problematic.

---

### Post by Robin_Perrett on 2014-05-10
I decided to burn a new DVD  and everything went ok. Kubuntu opened up fine and I got onto the desktop. I looked at a few of the items and then tried to connect to my network. I am completely baffled as to how to get online. Is there a tutorial as to how to connect to my network? I rested the laptop for a while and to prevent it going to sleep I hit one of the keys, the spacebar. The screen went black and I had to do a hard shutdown. I rest !

---

### Post by drac-noc on 2014-05-10
Hi Robin. 

When you boot into Kubuntu, you should see a small series of icons next to the clock. One of them is your network manager. Click on it and it should automatically find wireless networks in your area. Pick a suitable one and provide the password if necessary. 

If something is wrong at this point, it might be a compatibility issue with your wireless card, but using a wired connection for a few minutes should allow you to install additional drivers as needed. 
If you need to do this, Press Alt and F2 together, and a little box should appear at the top of the screen. Type in *drivers* into the box and you should see an "Additional Drivers" entry appear. Tap on that and it'll find any extra drivers you need, you'll be walked through installing this software, but bear in mind you'll need to repeat this each time when booting from a LiveCD/LiveUSB. It's only done once when Kubuntu is permanently installed. This is pretty common for wireless cards and graphics cards.

As for the black screen on sleep, I'm sorry I can't help you with that, but sometimes laptops can be a little sluggish when coming back out of sleep, I know my wife's netbook does that but it does return intact. Perhaps a little patience is required, but it could be something else. 

I hope some of that helps. As heidi3 mentioned, it might be worth looking at a different version such as Lubuntu or perhaps Xubuntu to ease some of the load on older hardware.

---

### Post by Robin_Perrett on 2014-05-10
Thanks for that drac-noc, I'll give It a go tomorrow.

---

