---
title: "Ubuntu 12.04 Installer Fails"
date: 2012-04-26
forum: New to Ubuntu
---

### Post by doppel.ganger on 2012-04-26
I'm trying to install Ubuntu 12.04 on my HP Mini 5101. The installer seemed to be running fine until... Well, see the screenshot. How do I check (and/or fix) the hard drive? I would really appreciate any help I can get.

EDIT: I'm not using a CD or DVD, but a flash drive.

Thanks,
DG

---

### Post by HeroOfCanton on 2012-04-26
There's a bit of info [here]("https://help.ubuntu.com/community/TestingStorageMedia") on checking the drive(s). More info available in the [manpage]("http://manpages.ubuntu.com/manpages/hardy/man8/fsck.8.html") for fsck.

Not to accuse the installer of lying, but are you sure you have a good "burn" there? If you haven't experienced issues with these drives before you may want to first verify the md5 of your iso and/or try clearing and rebuilding the USB installer. (Maybe download the iso again too just to be sure)

---

### Post by houseworkshy on 2012-04-26
The first thing to do is to check the integrity of the image, this explains how [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
For checking the harddrive, assuming it has linux on it read the man pages for fsck,  "man fsck" entered in the terminal will get you to them.  You could also try looking at the man pages for the commands listed at the bottom of that page, "man...{whatever-it-is-you-want-to-look-at}"  I'd recomend looking at only the diagnostic stuff rather than trying to fix things until you know how.
Was typing the above while the previous reply was posted.

If you decide to download again there is a firefox addon called downthemall which lets you paste the md5 to verify before you pull the file in.  Very handy.

---

### Post by doppel.ganger on 2012-04-26
The md5 is OK. I'll try putting it on the flash drive again.

---

### Post by Bender2k14 on 2012-04-27
I have had this error message before from installing a previous version of Ubuntu. While I may be remembering the solution to a different problem, the following may help.

The issue was that I was installing Ubuntu without a swap partition.  I had previously installed Ubuntu successfully without a swap since I have enough RAM.  I realized that this was the problem by simply trying to install Ubuntu using all of the default settings (which for the partition selection meant the "default" clean install).

---

