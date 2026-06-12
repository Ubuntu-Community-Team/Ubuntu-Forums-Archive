---
title: "Problems with Installing Ubuntu"
date: 2015-04-24
forum: New to Ubuntu
---

### Post by dariussan on 2015-04-24
Hey Guys, I have a really big problem at the moment.
I had Linux Mint 17 before and wanted to install Ubuntu again on my netbook. However the installation failed somehow ( probably the usb stick had some issues ) and the installation was aborted. Ever since that I can not boot anymore since I chose to erase everything. Now I am really concerned about how I can fix it again. I am a really noob when it comes to Linux however I want to reinstall Ubuntu. I tried already to make a bootable Ubuntu USB stick , but it just does not boot even after I changed the bootorder in BIOS. Can someone help me out? I am constantly getting a black screen ... nothing happens when I plug in the Usb stick and try to boot... just a  bar pops up...
Thanks in Advance!

Mike

---

### Post by yancek on 2015-04-24
More details are needed.  What hardware do you have, how old/new is the computer on which you are trying to install.  Your post indicates you have no operating system on this computer.  How are you creating the bootable usb, what software are you using to create it?  When you are installing it is always useful to pay attention to what is happening because things might fail as they have in your case.  "Failed somehow" doesn't tell anyone trying to help you much.  Are you able to access another machine to see if they usb boots on it to eliminate that as a possible problem?  Are you using UEFI/GPT or the old MBR to boot?

---

### Post by dariussan on 2015-04-24
Thanks Yancek for your replay

I am currently using an ASUS F200CA. I bought this netbook around 1 year ago.
Yes I know , but I did have Linux Mint 17 before. Then I installed the Unetbootin and created a "bootable" usb stick of Ubuntu. Then I rebooted and started the installation. But during the Installation ( note that I chose the option to delete everything from my harddrive ) it failed. It said something about that a few files were not correct and then I restarted my netbook and again and suddenly it was just the black screen with a bar.

"Are you able to access another machine to see if they usb boots on it  to eliminate that as a possible problem?  Are you using UEFI/GPT or the  old MBR to boot?" Sorry but I do not clearly understand , I am really new to this one, could you please elaborate on it or try to explain it to me in a more easier way?

---

### Post by sandyd on 2015-04-24
> **dariussan said:**
> Thanks Yancek for your replay

I am currently using an ASUS F200CA. I bought this netbook around 1 year ago.
Yes I know , but I did have Linux Mint 17 before. Then I installed the Unetbootin and created a "bootable" usb stick of Ubuntu. Then I rebooted and started the installation. But during the Installation ( note that I chose the option to delete everything from my harddrive ) it failed. It said something about that a few files were not correct and then I restarted my netbook and again and suddenly it was just the black screen with a bar.

"Are you able to access another machine to see if they usb boots on it  to eliminate that as a possible problem?  Are you using UEFI/GPT or the  old MBR to boot?" Sorry but I do not clearly understand , I am really new to this one, could you please elaborate on it or try to explain it to me in a more easier way?
Try creating another USB drive on another computer, and then try to boot using the USB drive.

If it does not boot (your computer manual doesn't seem to have an option for a boot menu), press F2 and go to the boot section of your BIOS

Your computer uses UEFI, so manually move the USB drive priority to the top. (See picture of boot section at [http://www.manualslib.com/manual/547670/Asus-F200ca.html?page=79#manual](http://www.manualslib.com/manual/547670/Asus-F200ca.html?page=79#manual)) and try booting again.

---

