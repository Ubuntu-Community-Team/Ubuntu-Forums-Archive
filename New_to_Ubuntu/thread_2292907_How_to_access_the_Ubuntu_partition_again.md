---
title: "How to access the Ubuntu partition again?"
date: 2015-09-01
forum: New to Ubuntu
---

### Post by shalom3 on 2015-09-01
I had installed windows 7 and Ubuntu into my PC, but recently I restored Win7 partition and upgraded to windows 10.

Now I cannot access Ubuntu because somehow the duel-boot is inactive (I apologize for the lack of technical terms)

How can I access duel-boot screen when I turn on the PC so that I can choose between OSs?

Thanks

---

### Post by Double.J on 2015-09-01
Hi there!

What's happened is the windows bootloader is taking preference at start up. 

There's a number of ways to fix this depending on your system - if you have a UEFI system it can be as simple as going into the bios and selecting ubuntu from the boot order.

However most fo the time a bit of configuring needs to be done. Boot with your ubuntu install media, either DVD or USB that you used to install in the first place, and click try ubuntu. 

Then check out [this guide]("https://help.ubuntu.com/community/Boot-Repair") on using boot repair - it's by far the easiest way!

Let us know how you get on, 

JJ

---

### Post by shalom3 on 2015-09-01
Thank you, I followed the instructions and installed Boot-repair. It was a success.
However, I have another issue. 

now the computer boots from GRUB. how can I change this so that I choose the OS from windows dual boot evirionment.

Thank you

---

### Post by dino99 on 2015-09-01
why not using grub as your main bootloader ? i'm not sure that ubuntu will be happy with the windows bootloader (if its possible to do it; who knows ?)

---

### Post by Bucky Ball on 2015-09-01
> **shalom3 said:**
> now the computer boots from GRUB. how can I change this so that I choose the OS from windows dual boot evirionment.



The answer to your question, if I understand correctly, is that you don't. Or do you mean you can't boot into Windows?

---

### Post by yancek on 2015-09-01
The only windows software I am aware of that will boot any Linux is EasyBCD which is basically a modified gui which edits the bcdedit boot file on windows.  It uses something they call neogrub which is a modification of grub4dos which in turn is a modification of Grub.

---

### Post by shalom3 on 2015-09-02
Hello,

I am completely ok with GRUB, but when other family members are using my PC its a little hard for them because of the multiple options in the GRUB.

how can I change to windows boot environment?
Thanks

---

### Post by yancek on 2015-09-03
If your family members usually use windows, you can set it as the default and when the computer is booted, it will boot windows unless you change it.

A second option is easyBCD, basically a GUI front end which edits the windows boot files.  Just google "EasyBCD" and you should get the neosmart site and you should find some documentation there also.

The first option is much easier.   Explained in detail at the site below.

[http://www.howtogeek.com/196655/how-to-configure-the-grub2-boot-loaders-settings/](http://www.howtogeek.com/196655/how-to-configure-the-grub2-boot-loaders-settings/)

---

### Post by Mike_Walsh on 2015-09-03
Would it not be just as easy to install 'grub-customize', and then simply use it to remove the lines you don't want? That's what I've done.....and the only two lines I have showing on the GRUB2 menu are 'Xubuntu 14.04.3 LTS' & 'Linux Mint 17'.

If I understand the OP correctly, I think that's what he wants to do; simply tidy it up, so that he only has the options for Windows and Ubuntu showing; and **nothing **else.

He may have to re-do the entries after a kernel upgrade, however. Once you've done it for the first time, it's really simple the next time.....and only takes a couple of minutes at most.


Regards,

Mike. ;)

---

### Post by mastablasta on 2015-09-04
just use grub customizer to pout windows on first place. set the timer to 5 sec or 7 sec. then when others boot it will automatically boot to windows. 

also you can add some nice pictures into grub and change colours.


btw the boot for windows goes like this now - BIOS/UEFI -> GRUB -> Windows boot loader ->Windows

just in case you ever need to access the windows boot loader.

---

