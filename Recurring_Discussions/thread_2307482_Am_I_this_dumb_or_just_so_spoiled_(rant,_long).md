---
title: "Am I this dumb or just so spoiled? (rant, long)"
date: 2015-12-25
forum: Recurring Discussions
---

### Post by kiklo on 2015-12-25
I'm sorry if this doesn't belong here, but I don't know where else to go.

Ok, so I got a new laptop that came with win10. After seeing Microsoft's new "experience enhancements" like sharing my browsing history with Microsoft, along with 10h of bootup time, I decided to go for Ubuntu Linux and double-booted my laptop.

Now, people have been telling me that the learning curve is steep, but really! After the initial loading Ubuntu logo went flickering all over the screen(probably because I don't have proper graphics drivers installed, dunno), I got to the desktop screen and actually managed to enable multiple workspaces, and crashed the system by choosing too many workspaces.
But that's ok. The only thing I planned to install was Opera, the web browser. I tried about 5 "official" installation packages. Most of them didn't setup properly, I started getting system errors on Ubuntu start up, all the time my wifi was randomly disconnecting, even though the router is 3 meters away from me, then opera tells me that it can't access a folder in /home, which could be fixed by running it with sudo, but caused that you couldn't see anything but glitching text inside the app window.
Then I tried to install Steam from the software center. But after it told me that I need 3 additional packages of some sort and the wifi didn't feel like doing anything, I gave up as well.

I expected to encounter difficulties, people had told me. But I can't install a browser without my head exploding. I won't describe the specific errors, there were just too many.


All I want to know is if it's normal that I feel like the OS is half baked, non functional, glitchy and fragile, as opposed to the clean, independent, free, optimised and stable OS I was promised. I've wasted a whole day and achieved nothing.

So is it really worth it? Will it be become easier over time? Or should I just go back to windows? Maybe Linux is intended for other people who don't need Opera nor Steam.

---

### Post by jeremy31 on 2015-12-25
Start by posting the result of ```
inxi -Fxz; lspci -nnk | grep -iA2 net; lspci -nnk | grep -iA2 vga
```

Sounds like hardware issues that may be resolved if people know what the hardware is

---

### Post by matt_symes on 2015-12-25
No a support request.

Thread moved to **Recurring Discussions.**

Why didn't you ask for help when you where having problems ?

You may want to start a support thread for each problem you've been having.

Having a rant will not fix your system, although it may make you feel better.

---

### Post by kiklo on 2015-12-25
Lol, you guys are determined. Of course I'll have to resolve all of the issues individually. I guess the answer is "Yes, it's worth it" then. Hopefully I'll make it all work till I die.

---

### Post by buzzingrobot on 2015-12-25
> **kiklo said:**
> 

Ok, so I got a new laptop that came with win10... along with 10h of bootup time...

Exceptionally long boot time on a new Win10 system, especially if it's been slow from the start without user tinkering, might point to some non-OS related issues.  Win10 is actually reasonably speedy to boot.

 
>  After the initial loading Ubuntu logo went flickering all over the screen(probably because I don't have proper graphics drivers installed, dunno)...

Linux will determine which video card, and other hardware, is active as it boots and it will use the best available (i.e., installed) driver without user intervention. For video cards, it will use an open source driver.  Because open source developers are prevented from having access to complete details and data for video cards from AMD and Nvidia, some cards have less than perfect support from their open source drivers. Many have excellent support.

Proprietary drivers from Nvidia and AMD, however, are available and can be installed easily from within Ubuntu,.

The newest video cards -- like you find in a new laptop --  are the most likely to be inadequately supported by open source drivers simply because it takes some finite time before developers acquire (buy) machines with those cards and can learn enough about them to write some code.

You should post a separate thread detailing your hardware specs, including your video card, and ask for help on this problem.

> The only thing I planned to install was Opera, the web browser. I tried about 5 "official" installation packages.

What repositories?  It is not included in Ubuntu's repositories, but Opera provides an installable package for Ubuntu here: [http://www.opera.com/computer/linux](http://www.opera.com/computer/linux)


> All I want to know is if it's normal...

No, it isn't.

Linux is not Windows.  It's made differently and it works differently.  Distributions like Ubuntu maintain large repositories of software that is packaged specifically that version of that distribution. These are always your first resort for software.  These packages are not simple archives as you might be used to from Windows. They are archives plus scripts that are executed to ensure all the software components -- there can be hundreds -- are installed in the right locations throughout the file system. (Linux software is seldom unarchived into a single directory and executed from there.) Part of the installation is determining if the software being installed requires -- is dependent on -- other packages that need to be installed.  If you use the Software Center or one of the other similar tools available in Ubuntu's repositories *and* if you are acquiring the packages from the Ubuntu repos or some other repository you have correctly configured your system to use, all this will happen automatically.

But, if you follow typical Windows practice and simply download an archive you found someplace on the web and try to install it, it very likely will fail.

---

### Post by stalkingwolf on 2015-12-26
>  I guess the answer is "Yes, it's worth it" then. Hopefully I'll make it all work till I die.  or 5 yrs when the version hits its end of life.

---

### Post by gordintoronto on 2015-12-26
Only you can decide if it's worth it. I can install a new version of Xubuntu on a dreadful old netbook in 20 minutes, and everything works perfectly.

One small suggestion: if you have a new laptop, you should try the latest version of Ubuntu (15.10), not the LTS (14.04). New hardware, old OS, poor combo.

---

