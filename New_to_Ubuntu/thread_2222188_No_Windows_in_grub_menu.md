---
title: "No Windows in grub menu"
date: 2014-05-05
forum: New to Ubuntu
---

### Post by michael150 on 2014-05-05
Hi 
I am new to ubuntu too. I downloaded ubuntu to work alongside Windows 7 but Wut windows 7 disappeared. I did a boot repair and rebooted but 
still no windows. Here are my results from the boot repair: [http://pastebin.ubuntu.com/7398687/plain/](http://pastebin.ubuntu.com/7398687/plain/)
Imay need to create space at the beginning of the 1st partition (???) but want to take it very slowly and not make mistakes.
Advice would be most welcome.

Thanks.

---

### Post by michael150 on 2014-05-05
I have a similar problem. I installed Ubuntu and windows 7 has disappeared from the boot option list (it was there for a day or two)
I have done a boot repair and here are the results: [http://pastebin.ubuntu.com/7398687/plain/](http://pastebin.ubuntu.com/7398687/plain/)
But still no windows 7 showing up
Any advice on what to do next would be very welcome
Thanks

---

### Post by oldfred on 2014-05-05
@michael150
Yours is not at all like the thread you posted in. That was UEFI, yours is BIOS. Please do not hijack another thread.
Also merged other post. Only one new thread per issue, please, we all are volunteers and need to know what others may have posted, so we do not dupliate effort.

You are missing bootmgr. Grub2's os-prober looks for the Windows partition with boot files, both bootmgr and BCD.
You still have BCD, but somehow lost bootmgr. 
If you have a copy somewhere copy it back into your Windows sda1 partition. Boot-Repair can only do minor fixes to Windows. If you do not have a copy then you need to use your Windows repair CD or flash drive to fix it.

You also show a wubi install. If not using it and have copied or backed up all data from it, it probably is best to delete it. You should just be able to delete like any other Windows program. You may have to manually edit BCD to remove wubi boot entry.

---

### Post by michael150 on 2014-05-22
Sorry about that. I am a newbie and don't know much about ubuntu. What is BCD? I have no Windows discs either.

---

### Post by oldfred on 2014-05-22
Your issue is all Windows related.

BCD is where Windows keeps the info on what systems to boot.
Bootmgr is its boot file that loads BCD.

You need Windows tools, you can usually only fix minor Windows issues from Linux.

Windows may have a copy of Bootmgr somewhere on system, you can try searching. If you fully backed up system, it should have a copy.
Script only looks for a copy in the location it is supposed to be in.

If you have access to another system with same version of Windows either 32 bit or 64 bit
 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)


 [http://www.sevenforums.com/](http://www.sevenforums.com/)

 Repair install
[http://www.sevenforums.com/tutorials/3413-repair-install.html](http://www.sevenforums.com/tutorials/3413-repair-install.html)
[https://windowssecrets.com/top-story/win7s-no-reformat-nondestructive-reinstall/](https://windowssecrets.com/top-story/win7s-no-reformat-nondestructive-reinstall/)

---

### Post by michael150 on 2014-06-08
Hi I only have access to an xp os on another computer. Would that be able to assist?

---

### Post by michael150 on 2014-06-08
Hi, I have managed to access Windows 7 using a recovery disc. After a 12.10 update problem I am going to delete all of Ubuntu and upload the 14.04 version. Thank you Oldfred for your cogent advice.

Michael150

---

