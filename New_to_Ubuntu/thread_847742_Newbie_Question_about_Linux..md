---
title: "Newbie Question about Linux."
date: 2008-07-02
forum: New to Ubuntu
---

### Post by Jay03 on 2008-07-02
Should be an easy one.  Can Ubuntu or any Linux OS do any harm or damage to hardware?  I just upgraded my PC a few months ago and was thinking about trying Ubuntu out.  If Ubuntu doesn't load correct drivers will it damage any hardware?  I would like to get away from Windows.  I downloaded the x32 Ubuntu and have it on cd.  Figured i'd ask the above question before booting up with the live cd.  Thanks 

My specs are 

M2N32-SLI Deluxe with Wifi
AMD 64 x2 6000+
2GB of ram
250GB SATA hard drive
Nvidia Geforce 8600gt

---

### Post by paul101 on 2008-07-02
well unless the cd EXPLODES INTO A MILLION PIECES... its not going to harm your system ;)

---

### Post by acidsolution on 2008-07-02
I dont think it does any harm to ur hardware unless u r cd is broken . if it is so than it may damage your cd rom

---

### Post by iaculallad on 2008-07-02
Ubuntu or Linux in general does not damage your hardware when installed, not even when you use open-source drivers.

Do the installation and see it for yourself.

---

### Post by untermensch on 2008-07-02
> **paul101 said:**
> well unless the cd EXPLODES INTO A MILLION PIECES... its not going to harm your system ;)

Even then most of the shrapnel would be caught by your cd driver. So even then all you've lost is a cd/dvd player. But you'd have to spend the cd at like 20k+ rotations a min.

---

### Post by Jay03 on 2008-07-02
That was a quick reply.  Thanks.  Just wasn't sure if Linux drivers would run the hardware differently leading to damage.

Think I will give it a whirl. Thanks to all that replied.

---

### Post by untermensch on 2008-07-02
You might need to update some drivers at most, but they would affect your system no more than updating your drivers for windows.

---

### Post by bhadotia on 2008-07-02
> **paul101 said:**
> well unless the cd EXPLODES INTO A MILLION PIECES... its not going to harm your system ;)
HA HA HA HEE!
Don't take anything personally just kidding around .:)

---

### Post by ChameleonDave on 2008-07-02
There are two ways in which software can render hardware useless.  They both take some effort.

Firstly, via the operating system you can install the latest version of the firmware (software which is directly installed onto a specific bit of hardware rather than just onto the hard drive) for something like your motherboard or your modem.  If the firmware is corrupt or the installation is aborted halfway through, then the device will no longer work.  If that device is the motherboard itself, then you won't be able to boot in order to correct the problem.

However, there are three reasons not to worry about this:
[LIST=1]
[*]No operating system will install firmware without you specifically deciding to do so;
[*]There is no reason to think it will fail or be corrupt;
[*]There is virtually always some sort of reset button you can press or some battery you can remove, in order to force a device to go back to its factory settings.
[/LIST]

Secondly, via the operating system you can run applications that overclock or overpower various bits of hardware, typically processors and video cards.  This will force them to work faster or with greater amounts of electric current, in order to get more performance.  This will shorten the lifespan of the piece of hardware, making it burn out in five years instead of eight (for example).

However, there are three reasons not to worry about this:
[LIST=1]
[*]No operating system with overclock your hardware without you specifically deciding to do so;
[*]It's not a failure but rather the price you pay for an advantage received;
[*]It's not an immediate failure, but a slow degradation.
[/LIST]

In summary: stop being paranoid, and just use Linux.  Windows viruses are far more likely to screw you up than anything discussed here.

---

### Post by tjwoosta on 2008-07-02
i have heard of some very rare occasions where ubuntu can wear down harddisks  very fast 
look here
[http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear]("http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear")
(this can be diagnosed before any damage occurs by using smartmon tools to monitor the wear of your harddisk)
(also if it happens there is a fix somewhere i just dont remember where)

also there is some very rare problems people have with there fans not running properly with linux
(you can monitor temperatures with lm-sensors)

just keep an eye on temperatures and stuff after installing (youl know if theres a problem before any damage occurs)

---

### Post by ledzeppelin on 2008-07-03
If they say it wont harm your harware they are wrong and right at the same time. If you don't take precautionary steps to be able to dual boot, then your system recovery partition will be destroyed by ubuntu so make sure you go to linux.com and check out the precautionary steps to be able to dual boot.

---

### Post by bhadotia on 2008-07-03
> **ledzeppelin said:**
> If they say it wont harm your harware they are wrong and right at the same time. If you don't take precautionary steps to be able to dual boot, then your system recovery partition will be destroyed by ubuntu so make sure you go to linux.com and check out the precautionary steps to be able to dual boot.
It will be your fault that you did not take the precautionary steps and not ubuntu's . Ubuntu won't harm anything unless you tell it to.:)

---

### Post by tjwoosta on 2008-07-03
> Ubuntu won't harm anything unless you tell it to

99% of the time this is true (read my last post)

---

### Post by raf952 on 2008-07-03
> **ledzeppelin said:**
> If they say it wont harm your harware they are wrong and right at the same time. If you don't take precautionary steps to be able to dual boot, then your system recovery partition will be destroyed by ubuntu so make sure you go to linux.com and check out the precautionary steps to be able to dual boot.
To dogpile on the previous answers, I would say that Linux isn't any more dangerous to hardware than any other computer operating system. If you provide a hardware driver or load software that is configured improperly it may have an effect, but I would not blame the OS, per se. If you continually drive your monitor at the wrong frequencies and cause it to melt, the fault is your misconfiguration, not the OS--it was just following orders.

That being said, running fdisk and trashing a windows partition isnt' a hardware problem in my way of reckoning. It sucks, and I've accidentally formatted a windows partition when I wasn't careful, but no harware was harmed in the process (except the hole I punched in my wall).

---

