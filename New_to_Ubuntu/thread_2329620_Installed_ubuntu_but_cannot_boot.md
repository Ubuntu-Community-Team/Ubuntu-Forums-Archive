---
title: "Installed ubuntu but cannot boot"
date: 2016-07-03
forum: New to Ubuntu
---

### Post by haydenj96 on 2016-07-03
Hello everyone,

I installed ubuntu alongside windows 8.1 on my Toshiba Satellite Z-30A. Afterwards, the computer simply booted straight into windows. I booted from my USB with ubuntu on it and decided to install ubuntu over windows, removing windows completely.

Now, I can't boot at all without the USB, however when I go to reinstall ubuntu from the USB it tells me it is already installed (presents the option to install Ubuntu 16.04 alongside Ubuntu 16.04). :confused::confused:

I've tried the recommended boot repair option and tried reinstalling a few times and I've also tried a few other settings in boot repair as per some old forum posts on this website with no luck. I also turned secureboot off.

I would greatly appreciate some assistance in getting this working, I just want ubuntu instead of windows now on this laptop.

Here is a pastebin of my bootrepair log as of right now [http://pastebin.com/R2JXJ4DH](http://pastebin.com/R2JXJ4DH)

Thank you

---

### Post by Geoffrey_Arndt on 2016-07-03
Since you already wiped out Windows, maybe best to do your install after setting uefi/bios to "legacy" mode.    Then, during the install, do the custom install instead of the "install alongside" . . . the custom install is done via the "Something Else" option and allows you to install to a specific partition on sda.   Best to install it "over" the existing install, and then just watch for the screen where you're asked where to install grub bootloader.   Be sure to put it on sda (not sda1, 2, 3 or sdb).

---

### Post by haydenj96 on 2016-07-03
> **Geoffrey_Arndt said:**
> Since you already wiped out Windows, maybe best to do your install after setting uefi/bios to "legacy" mode.    Then, during the install, do the custom install instead of the "install alongside" . . . the custom install is done via the "Something Else" option and allows you to install to a specific partition on sda.   Best to install it "over" the existing install, and then just watch for the screen where you're asked where to install grub bootloader.   Be sure to put it on sda (not sda1, 2, 3 or sdb).

Thanks heaps! This solved the problem for me.

---

### Post by Geoffrey_Arndt on 2016-07-04
Great Hayden , , . . glad it worked out for you, as you have a really nice ultra-book and it should run only a 1st Class OS . . . . Ubuntu . . . and IF in the future you require a "Windows Only" program or app, just install Virtual Box and install WIn10 in that VM.    Plus, that way, MS won't be in a position to control your PC (since only you paid for it, . . . not MS.).

To help others, it's suggested that if a problem is solved - - that the original poster edits the thread and shows it solved (I think that option is under the "thread tools").   Thanks . . :)

---

