---
title: "Upgrading from 10.04 to 12.04--would like some advice"
date: 2012-11-05
forum: New to Ubuntu
---

### Post by traces09 on 2012-11-05
Okay...all I have is a 9.10 disk. I installed that with no problem, then upgraded to 10.04. The Update Manager said that I could upgrade to 12.04, so I tried. The upgrade aborted mid-install and suddenly I had all kinds of problems, including the inability to download anything, and repeated messages of "unmet dependencies."  I researched and tried every fix possible to no avail.

So...I reinstalled 9.10, then upgraded to 10.04 again. Everything is working fine in this version now.

My question is: In order to upgrade to 12.04 without a problem, do I need to update 10.04 as much as possible? And if so, where can I get all the 10.04 updates, since Ubuntu, of course, no longer provides them?

Tracy

---

### Post by Wim Sturkenboom on 2012-11-05
10.04 is a LTS release and supported till april 2013.

But to be honest, I would download 12.04, burn it on disc and do a fresh install.

---

### Post by 2F4U on 2012-11-05
> My question is: In order to upgrade to 12.04 without a problem, do I  need to update 10.04 as much as possible? And if so, where can I get all  the 10.04 updates, since Ubuntu, of course, no longer provides them?

Ubuntu 10.04 is still supported and you still can get updates for it because it LTS. However, to be honest, the safest way to get from 10.04 to 12.04 would be to do a fresh installation.

---

### Post by traces09 on 2012-11-05
Okay, I installed the updates for 10.04 that were available in Update Manager. I'm using an older computer that only has a DVD Rom, so I can't burn 12.04 to disk. I downloaded the 12.04 iso and was looking for a free Ubuntu-friendly program that would allow me to install without having to burn it to disk. Are there any?

Obviously I am new to Ubuntu. Any suggestions or explanations need to take that into consideration. :)

Tracy

---

### Post by verymadpip on 2012-11-05
There's a decent application named Unetbootin which will let you install to a USB flash drive.
You could try with that, provided your rig will boot from a USB stick.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by traces09 on 2012-11-05
Thank you for the USB flash drive suggestion. In case the computer won't do that (I don't have a USB stick right now so would have to buy one) are there any other suggestions?

---

### Post by ajgreeny on 2012-11-05
Judging by your comment about the computer being "older" it is very possible that it will not run 12.04 very well, or at least not run the unity desktop in 3D, which is needed to get the best from it.

Have you considered Xubuntu or even Lubuntu?

What hardware is in the machine, particularly the graphic card and size of ram?

---

### Post by ibjsb4 on 2012-11-05
Yes, another consideration.

Ubuntu has put on some weight.  Two of them, Gnome2 has been replaced with Gnome3; the old desktop has been replaced Unity.

Maybe its a little heavy for your computer.  Im lazy right now and not going to look it up, but I think minimum ram required is now one gig.  I have heard some say that it will run on one core just fine and others say no.

May want to take a look at Xubuntu, depending on your computer specs.

---

### Post by traces09 on 2012-11-05
Graphic card: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)

Mem:   2569624k total

---

### Post by verymadpip on 2012-11-05
I think on that amount of RAM Lubuntu may be your best bet. (I may have my decimal point in the wrong place but I think that's 256Mb, which is not much).  What CPU is in there?  Lubuntu is a sweet little operating system IMO :)

As far as installing goes; you're going to need an image of some sort, on either a CD or a USB stick.  If you can get a friend or family member to download one & stick it on a disc or USB for you, that'd be very helpful.
I don't know if you can do an install over the internet from a Live CD, but I've never heard of it.
Obviously you don't want o do an upgrade again.

Installing on that little RAM will also mean working from the alternate (text based) installer.  It's pretty straightforward, trust me :)

---

### Post by ibjsb4 on 2012-11-05
Mem: 2569624k total

I read that as 2.5GB of ram

Intel Corporation 82915G/GV/910GL looks like the drivers are there

[http://ubuntuforums.org/showthread.php?t=2029486](http://ubuntuforums.org/showthread.php?t=2029486)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Intel+Corporation+82915G%2FGV%2F910GL&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Intel+Corporation+82915G%2FGV%2F910GL&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

### Post by verymadpip on 2012-11-05
> **ibjsb4 said:**
> Mem: 2569624k total

I read that as 2.5GB of ram


Excellent, I am not the bearer of badish news news :)

---

### Post by newb85 on 2012-11-05
Your RAM should be sufficient to run Ubuntu.  Nonetheless, if you're going to buy a flash drive to create a Live USB, it's not a bad idea to use it to test drive Ubuntu, Xubuntu, and Lubuntu.

---

### Post by Wim Sturkenboom on 2012-11-06
Ubuntu 10.04 contains a startup disk creator that can be used to create bootable USB drives; no need for unetbootin.

---

