---
title: "Help: ubuntu live USB to recover data from windows 7 PC with blue screen issue."
date: 2015-06-14
forum: New to Ubuntu
---

### Post by ansh2 on 2015-06-14
Hello, 

I got the dreaded blue screen on my Windows PC :(. it has 4GB RAM on it.  
The PC never came with a Windows 7 recovery CD. Hence I am hoping to use Live Ubuntu USB to recover data on to an external hard drive, post which I will do a clean install of Windows 7 (OR get an iMAC :lolflag:)

I used a 16GB pen drive, and pendrivelinux.com to create Ubuntu 64bit live Ubuntu pen drive. then I changed bios settings to boot from usb stick. so far so good. 

The issue is I get the following error when I select "Install Ubuntu" option on the screen, "Not enough memory to load specified image". 
I tried to resolve this issue by highlighting the "install" option, before hitting enter, pressing tab. This brought up a line of code at the bottom of my screen. Added a space to the end, and then inserted "mem=1024m" option. I used "mem=1536m" option as well. 

This however did not resolve the issue but threw another error with a screen full of code which looks gibberish to me. and at the end says "end kernel panic - not syncing : VFS : Unable to mount root fs on unknown-block(2,0)"

Where do i go from here? I also tried reformatting pen drive (using another PC of course) and re--installing ubuntu. But I keep getting same sequence of errors while booting. 

Would really appreciate help on resolving this issue. Many thanks!

---

### Post by yancek on 2015-06-14
The major manufacturers which sell computers with windows pre-installed rarely provide and installation disk nor do they provide a recovery disk.  There is usually a Recovery partition and when you initially boot windows, you are prompted to create the recovery disk.  Did you not do this?  I think it may be possible to get a recovery disk as you will not be able to create one yourself if you can't boot windows.

If you want to use Ubuntu to try to recover data from the computer, you do not need to install it just select the option to "Try Ubuntu" and see if that boots.  Have you tried booting the flash drive on another computer to see if it is good, just to eliminate that as a possibility?  Also, did you check the Ubuntu iso download.  Sometimes the download is not corrrect and if that is the case, it probably will never work.  At the Ubuntu download page below, in the extreme lower left is a link "View Ubuntu md5 hashes" which explains how to do this.

 [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

---

### Post by Bucky Ball on 2015-06-14
*Thread moved to **New to Ubuntu**.*

Welcome. As above. 'Try Ubuntu' not 'Install Ubuntu'. You don't want to install it. You only want to rescue your files with it (thus the post move).

So. Try Ubuntu> when at a desktop open a file manager> locate your Win partition (you may need to mount it, ask if you can't do that)> locate your external drive partition> drag and drop your Win files/folders to the external drive partition.

Once you have your valuable data safe go about sourcing Win recovery media. Good luck.

(Who knows, you might like what you see, forget the iMac and Win and learn about Ubuntu! What do you do in Win that you couldn't do in Ubuntu? Sorry, disregard, off-topic and the stuff of another thread, but worth a thought ... ;))

---

