---
title: "Transferring data from iPhone -shotwell"
date: 2018-04-12
forum: New to Ubuntu
---

### Post by chaoticbob on 2018-04-12
I've been trying to solve this problem by looking around on t'internet and have gathered that it's not straightforward, but should be possible via USB using shotwell. I've tried this (it seems to be bundled with Ubuntu) but it's not working for me.
Hardware: PC end Dell Optiplex 780, phone end iPhone 6.
Software: PC end Ubuntu 16.04 LTS, can't see a way a way of finding shotwell revision. iPhone end iOS 11.2.6.

What happens is that shotwell finds the phone, the phone asks if the computer is to be trusted (yes, obviously), then shotwell says "starting import, please wait". But nothing further happens.  

Any advice would be welcome, Robin.

---

### Post by yancek on 2018-04-12
On my Ubuntu 16.04 using an iphone 7, when I plug the iphone into the usb port, I see a smart phone icon in the left panel.  I click on it and it opens nautilus showing Numbers and Pages.  If I click on the Go tab at the top of Nautilus, then click enter location, you will see an entry beginning with afc:// and a UDID after it.  If you go to the end of the UDID you will see a colon and some characters.  In my case it is one number and a forward slash.  Delete the colon and anything after it, then either click the right arrow at the right end of the location box or hit the Enter key.  You should see the various folders on the iphone.

I've only used it to move photos off the iphone so I'm not sure what the limitations are.  If this doesn't work, then another method that I know works is explained at the link below.  It is very long (20+ steps) but explained in excruciating detail.

[https://my30daysoflinux.blogspot.com/2017/07/make-iphone-7-ios-1033-work-on-ubuntu.html](https://my30daysoflinux.blogspot.com/2017/07/make-iphone-7-ios-1033-work-on-ubuntu.html)

---

### Post by 1clue on 2018-04-12
Using android I have problems too. Every time I try to use the "official" way it messes things up. Photos and music gets duplicated over and over. It's a cluster @#$@.

What I wound up doing is this:
[LIST=1]
[*]Install an FTP server on my phone. I use Wifi File Transfer, but again I'm using android so your mileage may vary.
[*]Get a smart ftp client for your Ubuntu box. Filezilla or one of many others that are linux-only.
[*]Copy everything off your phone into a directory just for this.
[*]As I had tons of duplicates I had to:
[LIST=1]
[*]De-duplicate the directory on my linux box.
[*]Delete all the files from my phone
[*]Transfer the de-duplicated folder(s) back to my phone.
[/LIST]

[*]After that all you need to do is copy all files from your phone to that same directory, and tell it to skip files that already exist.
[*]Transferring movies or your wife's pictures from your computer to your phone, you do the same thing in reverse:  Copy everything but skip duplicates.
[/LIST]

---

### Post by duchuymobile on 2018-04-13
Thanks 1clue

---

### Post by 1clue on 2018-04-13
One thing I've been thinking about but hadn't gotten around to yet is this:

Keep the already-transferred files (exclusively photos and video in my case) in a different place than the default. So:
[LIST]
[*]$HOME/phone/toLinux/ is for when you sync from your phone to your Ubuntu box. It mirrors your phone's default directory structure exactly. 
[*]$HOME/phone/fromLinux/ has hand-picked, reviewed photos that you still want to carry around. It has a different directory structure which could include whatever organization you might want to impose. 
[*]Your phone no longer has blurry or irrelevant shots. It's pruned down only to what you actually want to keep, not every last shot. 
[*]Of course you could do this with music too, or whatever else you sync. 
[/LIST]

That process would require that you empty out the default photo/video directories after every sync, and it would also require that you review your photos and organize them before syncing back. This might be the reason I haven't made the change.  :)

---

### Post by chaoticbob on 2018-04-13
Thanks for replies. Further investigation reveals that shotwell gets an error code of -53 from the iPhone when trying to mount the phone's filespace. It seems that this is something to do with Apple's (possibly flawed) security checks. I've tried updating shotwell in case the version bundled with my 16.04 installation is out of date, but still no dice.

I'll go down the FTP route next - as far as I can gather iOS supports the protocol, and it's something that I'm familiar with.

There is an irony (or stupidity) here - I've migrated from MS to open source on my desk/laptops, but gone the other way (Android to iOS) on my phone... 

Robin

---

### Post by 1clue on 2018-04-14
My wife uses Windows 10 and Android. FWIW the "normal" way doesn't work for her either. She also uses filezilla on her pc and an ftp server on the phone.

You would think at some point somebody would develop rsync compatibility but nope. There are some efforts but they all suck on android.

---

### Post by yancek on 2018-04-14
Your problem is not with Shotwell and updating it or getting a newer version will not help.  I never was able to access photos on my iphone with Shotwell but can in Nautilus.  The problem is with Apple.  What worked on an iphone 5 in Linux would not work with 6, 7 or 8.  Even minor version changes in IOS would prevent it from working on Linux due to changes made by Apple.  I seriously doubt if a default install of Ubuntu will have all the software needed to access a current iphone.  If you read through the link I posted earlier, you will see the amount of software needed to accomplish what you want.  Using SSH or FTP might work or even be easier, never tried it myself though.

If you are simply trying to access photos, it might be simpler to use icloud which won't require installing or setting up any software.

---

### Post by 1clue on 2018-04-14
+1 on yancek's post. The sync-to-computer features made by the manufacturer are a moving target and the FOSS product will always trail behind.

I'm sure that if you had a mac you'd be able to sync flawlessly with your iphone, but there is some doubt in my mind that it would work as well even with Windows 10.

There is some change that appened with smart phones in general, all at about the same time. It used to be that pretty much every phone could be synced, or better yet mounted as a USB drive. Suddenly like clock work it all stopped working and has never been good since. For any phone, AFAIK.

The FTP protocol has been the same for decades. It's a known, standard multi-platform protocol, it won't change much, ever. The idea of syncing two directories over ftp has been around almost as long as the protocol. There are lots of ftp clients out there with the ability to sync directories with minimal traffic and maximum convenience, especially on Linux. My favorites have two sessions side by side, usually the left side is "local" and the right side "remote" but some of them allow two different remote sites.

My biggest issue with Android versions of the FTP server is that they all suck huge amounts of power. This is bad programming, not something inherent with FTP. If iPhone is like Android though, you will be able to find a server that only accepts connections from the local LAN, and is free of ads. It will, by its nature, need access to all the files you need to get at.

---

