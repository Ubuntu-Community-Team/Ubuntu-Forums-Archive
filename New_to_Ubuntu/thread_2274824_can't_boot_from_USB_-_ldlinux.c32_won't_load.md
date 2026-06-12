---
title: "can't boot from USB - ldlinux.c32 won't load"
date: 2015-04-22
forum: New to Ubuntu
---

### Post by cameron25 on 2015-04-22
Hi,
I thought I would take the plunge and try Linux for the first time.  I have many years of tech experience doing this and that with pretty good success.  But sheesh I have never had so much trouble doing a "simple" install.  And even hours on the forums don't give a solution.

I have an old Toshiba Satellite M100 bought in China.  Been a great workhorse since 2007.  But I am giving up XP.

I have a CD drive but the install is too large to fit on a CD.  Got those errors and rejections.  Meow.  So I move onto USB.
I've tried various aids that create USB bootables including Rufus.
I've seen various posts about versions of SysLinux versus the Lubuntu install version.  Really?  Don't have time to sift through all that.  I thought LUBUNTU was the lite and easy way to get started.

SYSLINUX ver 6.03 EDD 2014-10-06
lubuntu-14.10-desktop-i386.iso

"Failed to load ldlinux.c32"

But I can't beat this error.  What a pain in the caboose!  Can someone hold me hand and send me a link or combo links that will push through all this??

Thanks!

---

### Post by RobGoss on 2015-04-22
I think DVD ' are recommended for this process, make sure the DVD's you're using have sufficient disk space in order to fit the complete installation of the iOS file. 

I usually get my DVDs with about four gigabyte of disk space. If you do this you should not have any problems burning the ISO file to that DVD.

Remember to burn the iso file at a slower rate so it will give you better results.

---

### Post by sandyd on 2015-04-22
Hi, have you verified that the ISO had been downloaded correctly?

See [here]("https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows") for instructions

---

### Post by Rex Bouwense on 2015-04-22
I am assuming that you have already downloaded the ISO.  Some things to consider Lubuntu 14.04 is a LTS version and will be supported for an additional 2 years.  It appears that you have downloaded Lubuntu 14.10 which only has 3 months of support remaining.  You of course can use it.  However, Lubuntu 15.04 is do to be released tomorrow but it will only be supported for 9 months.  Your choice on which ISO that you use.  Whichever one that you choose, you need to check the md5sum (hash) to make sure that you have a good download.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
Once you are sure that you have a good download you can burn the ISO to a CD (in the case of Lubuntu 14.04) or a DVD (in the case of 14.10).  Since Lubuntu 15.04 hasn't been released we don't know whether it will fit on a CD yet.  As has already been stated you need to burn it at the lowest possible speed to make sure that you get a good burn.
After you have completed that task you can boot from the CD or the DVD.  Then "take Lubuntu for a test drive".  See if everything works.  You will choose Try Lubuntu without making any changes to your computer.

---

### Post by yancek on 2015-04-22
Are you able to test the flash drive on another computer to see if it boots to eliminate that as a problem?
Is the computer capable of booting from a flash drive, have you done it previously?

---

### Post by cameron25 on 2015-04-22
Hey.  Thanks for all the suggestions.  I'll take a look at the ideas and see if I can get it going.  I did pick up a blank DVD as my first solution and ran into trouble with that, too.  I'll check my install file and go from there.  Stay tuned.  ;-)

---

### Post by kunitoki2 on 2015-04-23
Don't know exactly how to solve your problem yet, but let me share my experiences I so far collected over the last 10 years:
USB booting is still a matter of luck in the end because there are no real standards the industry agreed upon.
Booting from CD and DVD is better standarized and should be last resort because it's very slow compared to USB but works most of the time if burned correctly.
The problem with USB booting is there are more than one potential candidates causing trouble.
Sticks are different ALL THE TIME - some 'behave' like external storage devices, some 'emulate' CD drives, some behave like external hard drives, depending on the controller built in.
And of course the mainboards - since no real standard emerged over the years every (BIOS) manufacturer implements own routines to deal with USB booting - some offer a lot of options (USB HDD, USB media, USB CD, USB Floppy) and sometimes even the ability to treat a stick as one of those and the 'emulate' some kind of hardware that's not really connected but wouldn't work at all if not being treated as something else.
Long story short: I played with A LOT OF different sticks and mainboards slash BIOSs over the years, and of course different apps to create bootable sticks (unetbootin, rufus, even made them myself and from scratch with syslinux and or grub and and and...) and the result: There's ALWAYS a bit of luck left and if you just happen to have the 'wrong' (most of the time wrong means cheap) hardware (stick and bios slash board) then it just doesn't matter which app you use, the damn stick and board will just refuse to work together.
Sticks that didn't work (refused to be booted from) were ALWAYS cheap noname sticks. That doesn't mean ALL noname sticks don't work. I have nonames that work. But the ones that didn't were always cheap noname (cheap built-in controller and slow (and probably soon dying) flash memory). 99% of the time Verbatim sticks and the Unetbootin app create sticks that work almost everywhere, but even then I sometimes encounter mainboards that refuse to work with them. Sadly there's nothing out there that is guaranteed to work - it's try and error in the end.

---

### Post by cameron25 on 2015-05-05
Hey there.  Thanks very much for the help.  I ended up packing the laptop for a trip in a container ship until July.  Will try things again then.  Cheers!

---

