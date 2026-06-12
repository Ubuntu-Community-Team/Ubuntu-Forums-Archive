---
title: "Error Trying to Dual Boot"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by rkcjason on 2008-11-27
Hello,
    This is the first time I have tried to install any type of Linux on a computer.  I am trying to dual boot Vista and Ubuntu 8.10.  I was following a tutorial by apcmag.com, and I got everything installed and working correctly, but when I tried to switch Ubuntu and Vista's boot order, the Ubuntu stopped working.  The error I get when trying to boot into Ubuntu says Booting 'Ubuntu 8.10... kernel...ro quiet splash, then it says Error 17: File not found.  I believe the problem could be how I set up the menu.lst file in EasyBCD.  Thank you for any help in advance.

---

### Post by rkcjason on 2008-11-27
Hi, this is my first time installing any type of Linux on any machine and everything was working fine, including Ubuntu, until I attempted to switch the boot order so that Vista would stay in charge of things.  I used EasyBCD to switch them and I put part of the menu.lst file into that program by following a tutorial from apcmag.com.  Now, Vista boots fine but when I attempt to boot Ubuntu it says Booting 'Ubuntu 8.10...kernel /boot/...ro quiet splash Error 17: File not found Press any key to continue.  Thank you very much in advance for any information.

---

### Post by rkcjason on 2008-11-27
Hi, this is my first time installing any type of Linux on any machine and everything was working fine, including Ubuntu, until I attempted to switch the boot order so that Vista would stay in charge of things. I used EasyBCD to switch them and I put part of the menu.lst file into that program by following a tutorial from apcmag.com. Now, Vista boots fine but when I attempt to boot Ubuntu it says Booting 'Ubuntu 8.10...kernel /boot/...ro quiet splash Error 17: File not found Press any key to continue. Thank you very much in advance for any information.

---

### Post by Bucky Ball on 2008-11-27
Do you get the grub menu at boot still? (list of kernels and windoze)

---

### Post by rkcjason on 2008-11-27
Yes, I can still choose Vista or Ubuntu.  Vista works fine but when I try to boot into Ubuntu, I get this error.

---

### Post by Bucky Ball on 2008-11-27
Okay, that is good news. At the grub, select windoze but don't boot it, press 'e' to edit. Have a loot there and see where it is booting from - (hd0,0) if it is first partition, first drive but may be different (hd1,0) for instance (second drive, first partition). As you can figure, 0=1.

Esc a couple of times to get back to grub then 'e' to edit your Ubuntu kernel. What does the (hd?,?) say there? Is the first digit the same as the vista install ie (hd0,?)?

Couple of things; are the two OSs on the same drive, different partitions, or seperate physical hard drives?

If they are on the same drive, the first digit for your Ubuntu kernel should be the same as the windoze one, second number different (different partition, naturally). Edit it that way, esc and 'b' for boot. If this all works we can change it permanently in /boot/grub/menu.lst

---

### Post by rkcjason on 2008-11-27
I tried pressing 'e' on both options and it did not do anything, however I do know that both OS's are on the same physical hard drive, but on separate partitions. Thanks.

---

### Post by Bucky Ball on 2008-11-28
Pressing 'e' at the grub doesn't do anything ???

At the grub screen, at the bottom of that screen, your instructions say press 'e' for edit? Just to make sure we are on the same page.

---

### Post by rkcjason on 2008-11-28
I wanted Vista to still be the primary operating system, so I installed EasyBCD to allow Vista to be the default.  Since I installed that, GRUB is not the bootloader, it is the Windows Boot Manager instead, which does not offer the 'e' to edit option.

---

### Post by Bucky Ball on 2008-11-28
Ouch. Can't really help then as don't even know what that is! Sorry. :(

Hopefully someone else will chime in for you. Not sure what you mean by 'primary operating system' though. Do you mean you want it to automatically boot into Windoze on start up? Windoze is always on a primary partition, Ubuntu doesn't need one, logical fine. But I don't think that is what you mean either.

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by zwygart on 2008-11-28
First, why do you want that Vista loads Ubuntu, it's easier to load Vista from GRUB (the bootloader of Linux).

Second please post th entire error line. Probably it search the kernel and you don't have indicated correctly the boot disk.

To help you, can you post or attach the file menu.lst which you talked about.
I suppose you have installed ms2grub or something like that.
At the boot press C and post the output of the following commands
[HTML]find /boot/grub/menu.lst
find /boot/menu.lst[/HTML]

I hope we will be able help you.

---

### Post by mechanicalturk on 2008-11-28
I had error 17 problems with a previous install on an external USB hard-drive.  I found [this forum page]("http://ubuntuforums.org/showthread.php?t=442945") and [herman's grub page]("http://users.bigpond.net.au/hermanzone/p15.htm#Ubuntu_bootup_problems") to be useful.  In my case, menu.lst was simply pointing to the wrong hard-drive in the Ubuntu entry (hd0 instead of hd1).

You can press 'e' at the grub menu to edit particular entries in the boot menu during boot up, which will allow you to see the commands grub executes.

It may also be helpful to post the contents of the ubuntu entry or the contents of menu.lst here.

---

### Post by confused57 on 2008-11-28
Did you install grub to Ubuntu's root partition, using the live cd?:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Read the tutorial, but it would be something like:
```
root (hd0,2)
setup (hd0,2)
```
of course it would depend on the output of "find /boot/grub/stage1".

---

### Post by falcon61102 on 2008-11-28
Your best bet would be to reinstall the grub as confused57 suggests.  

Editing the Vista Boot loader can be a real pain, GRUB is a much more user friendly enviornment for edits.  And yes, you can still have it boot directly to Windows if you'd like.

---

### Post by ideewoww on 2008-11-28
[img]http://www.ideewomen.com/cn/uploads/200811111137220.jpg[/img]Women's beauty sourses from heart, just like the IDee jewelry reveals unique beauty carelessly, palpitates the will of the people easily. The IDee accessories are all designed uniquely, both elegant and fashion. Especially the series of mounting is matched by luxurious swarovski quartz, pearl, agate and so on, sparkles the eye-catching ray. The intoxicant appearance will let you unfold the graceful makings all the time. How can&#8217;t you be moved?  Wearing the charming IDee jewelry, your mood will be bright everyday. The IDee jewelry is worth possessing!

---

### Post by jgoguen on 2008-11-28
Could you post the relevant portion of your menu.lst?  Open it in Text Editor by pushing Alt+F2 and entering this command:
```
gedit /boot/grub/menu.lst
```

Then, look for the sections near the end, there's a bunch of blocks of text that each start with a line starting with "title".  Copy and paste all of those blocks.  Here's an example from my menu.lst of what I'm looking for:

> title       Ubuntu 8.10, kernel 2.6.27-9-generic
uuid        0b6dd3cc-b4c1-47a4-9794-932abd55ae8a
kernel      /boot/vmlinuz-2.6.27-9-generic root=UUID=0b6dd3cc-b4c1-47a4-9794-932abd55ae8a ro quiet splash
initrd      /boot/initrd.img-2.6.27-9-generic
quiet

---

### Post by caljohnsmith on 2008-11-28
Are you by chance using Ubuntu on a different HDD than Vista? Also, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal), and post:
```
sudo fdisk -lu
```
And please identify your partitions.

---

### Post by overdrank on 2008-11-28
Please do not make multiple threads on the same issue. Threads merged :)

---

