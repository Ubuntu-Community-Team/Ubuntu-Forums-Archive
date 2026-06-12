---
title: "Can't install Ubuntu on my laptop"
date: 2014-03-12
forum: New to Ubuntu
---

### Post by andrea24 on 2014-03-12
Hi everyone, my laptop is an Acer Aspire 5750G. I've tried many times to install Ubuntu as second partition. So i run the dvd from windows then it restarts and select ubuntu. It starts with a screen like command line and then after a while it freezes with the cursor that keeps blinking. It stays like that for ages but never progresses from that point.
Did anyone else have this problem? Can you think of any solution?
Thanks everyone :)

---

### Post by zircon_34 on 2014-03-12
I once had an acer aspire, I had to turn acpi=off in bios mode at startup to make it work, maybe this may work for you...?

---

### Post by zircon_34 on 2014-03-12
> **andrea24 said:**
> So i run the dvd from windows then it restarts and select ubuntu. 

not sure I understand correctly, are you trying to install Ubuntu on a second partition by starting the Ubuntu dvd in win? 

You have to boot your computer with the Ubuntu dvd and then make the install on the second partition.

---

### Post by JeQhdMD on 2014-03-12
Currently am running Ubuntu 13.10 on Acer Timeline Aspire 4830T (it runs great).   Just a couple questions, . . when you say you run the dvd from windows, are you saying you do a "restart" so the laptop will boot up from the DVD?  Or are you running the DVD from some windows application or the windows file manager?   Another question, what graphics system do you have on your laptop?  nVidia graphics, ATI, or Intel?   Out of the box, Intel based systems will work best (without needing adjustments).   Zircon's advise is good also, to use that advice, are you seeing the normal pre-startup screen (see this link for more complete info:  [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Mark Phelps on 2014-03-12
>  I've tried many times to install Ubuntu as second partition. So i run the dvd from windows

Do NOT do this!  This will attempt to install Ubuntu from INSIDE MS Windows, something known as Wubi.  Due to problems with Win8, Wubi support has been discontinued.  I strongly advise against using it anymore.

---

### Post by andrea24 on 2014-03-17
I apologize for the late reply, it's been a busy week/weekend.
By start the dvd from windows (win7) I mean that I turn on my laptop and log in to windows, run the dvd and an installer starts. When it finishes preparing the partition for the installation it automatically restart the computer and continues the installation from that point on, this time outside of windows. I've also tried by turning on the computer with the dvd already in so it boots from there and it installs ubuntu but didn't make any difference.
As for the graphic card it's a NVIDIA GeForce GT 520M, but it also have some kind of Intel technology that works as graphic card (don't really know how it works, I suppose it automatically switches between integrated card and nvidia depending on the resources it needs. Tonight I'll check if I can disable it via BIOS).
I'm asking this because my company is thinking about switching to Ubuntu. We have a few new laptops and we'll also need to install it on these machines here: [http://www.ecom-ex.co.uk/products/mobile-computing/intrinsically-safe-notebooks/](http://www.ecom-ex.co.uk/products/mobile-computing/intrinsically-safe-notebooks/) (for out technicians) but I didn't have time to try it on those yet so hopefully it will be easier.
thanks for your suggestions, I'll get back to you as soon as I can
A

---

### Post by Thexisback on 2014-03-17
I have a cheap Delium iBuddie 10.1" it had the same issue, it wouldnt even load into the usb to install or an external DVD writer, I ended up taking the HDD out and putting it into my Friends Acer Aspire One and installing ubuntu on it and then switching the HDD back in. 

It had some issues to start with but a few updates and patches later it works fine.[URL="http://www.google.co.uk/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&sqi=2&ved=0CC4QFjAA&url=http%3A%2F%2Fwww.hotukdeals.com%2Fdeals%2Fdelium-ibuddie-y10s1-uk10-1-netbook-10-1-screen-1-gb-250gb-hd-159-99-del-comet-946437&ei=M_kmU5KsJtKThQfI84HoBg&usg=AFQjCNHaY21W0J7wY8Tib5NbV9wQBm_qZA&bvm=bv.62922401,d.ZG4"]
[/URL]

---

### Post by oldfred on 2014-03-17
See post #5, if you have booted Windows then  you are installing wubi.

If system is a new Windows 8 system with gpt partitioning, wubi will not work. Wubi has been discontinued and the last version is 12.04 since all new computers are now Windows 8 systems with gpt partitioning.

Also dual video adds a bit of complication, you have to know which video is used to boot with. nVidia requires nomodeset, but Intel needs different boot parameters for video to work.

What version of Windows do you have?

---

### Post by andrea24 on 2014-03-19
I'm using windows 7...
I'll try downloading the latest version and install it when I get some time during the weekend :)
Thanks, A

---

### Post by Korkel on 2014-03-19
You want make a dual boot?

Boot from the CD/DVD or USB and choose the option **Install Ubuntu next to Windows**. It will work for you.

---

