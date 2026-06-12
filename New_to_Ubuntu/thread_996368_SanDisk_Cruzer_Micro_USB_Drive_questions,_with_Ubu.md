---
title: "SanDisk Cruzer Micro USB Drive questions, with Ubuntu 8.04...?"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by jweissburg on 2008-11-28
To Whomever Might be of help...  =)

I'm a new user to Ubuntu 8.04 Hardy Heron, who hasn't really worked much with a USB flash drive before, so I'm here asking for help.

I've just recently bought a SanDisk Cruzer Micro USB 2.0 Flash Drive (8GB) on my Ubuntu, but I'm not sure how to use it...  :confused: 

1.) Once you plug in the thumb drive, how do you get access to the USB Flash Drive contents, either through GUI or through Terminal? Normally when you pop in a 3.5 or a CD, there usually is an icon of some sort that pops up, and I think that's the case with most MS Windows based programs. In this case I'm not getting anything.

2.) How do you store and retrieve info on it? Is it anything like a 3.5"?

3.) Does this Flash Drive have cross-compatibility between Linux-based systems and the average everyday Windows system that the everyday person uses? Or is there a better Flash Drive out there that's user-friendly and *goof-ball*-proof?

Also, if/when I can pull up the thumb drive, are there any files on there that I should NOT touch so that way I don't make the Drive unwriteable/unsaveable/et.al, ad infinitium, aut ad nauseam?

Any help would be appreciated. Thanks.

---

### Post by swoody on 2009-01-19
Hi, and Welcome to the forums! :)

1) First off, I have the SanDisk Cruzer 2GB version, and I've had it working beautifully in Ubuntu and Vista. The flash drive should display an icon like any other drive on the desktop, and in the 'Places' menu at the top of your screen. If it's not, then we need to work out some things.

2) I haven't used a 3.5" on my computers so I can't say if it's similar, but when you access your USB drive it will look like any other folder in Ubuntu, and you can copy/paste or drag/drop or anything else you can do to a normal folder.

3) I have had this USB working in Ubuntu and Vista' so yours should as well. For best compatibility you may want to format the drive as a 'fat' file system. You should try reformatting it, and see if Ubuntu will recognize it then. To do this in Windows simply right-click on the drive, and select 'Format' and in the options that pop up make sure to select one of the 'fat' file systems. Try this out, and let me know if Ubuntu still doesn't recognize it.

4) There should be a hidden file on the USB called '.trash' This is the only folder that remains on my USB, but even after deleting it a number of times, it always comes back on it's own. Otherwise I've deleted whatever other folders were on the USB by default.

Hope this helps you out! Please post back and let me know if you encounter any problems! :)

---

### Post by mike555 on 2009-01-19
If your thumbdrive has "  U3  " on it you can uninstall it by going to their site and downloading their  U3 remover , then on a windows machine use it to remove the U3 partition,  then it should work better on linux ........

---

### Post by bumanie on 2009-01-19
I agree with Mikewhatever. That u3 garbage was one of the most annoying bits of proprietary software I've ever come across. It was off my thumbdrive in less than a week. Of course, you may like it - I didn't and I went to sandisks site and used the removal tool. Up to you, it is probably useful for some situations - I guess :confused:

---

