---
title: "Looking for drivers for my laptop"
date: 2016-02-02
forum: New to Ubuntu
---

### Post by helm10101 on 2016-02-02
**Edit: It's an AMD Radeon R5 M230 GPU in my laptop

Is there an easy way to find drivers for my laptop?
I installed Ubuntu 15.10, and my laptop has also AMD GPU so that my laptop can switch between Intel and AMD when needed.
On Windows it's easy: You see Intel's and AMD's icons on the tray, and also you see Settings of both of them when you right-click the desktop.
Since I am currently using 2 monitors with this Ubuntu, I assume it installed the intel's drivers currectly, but:
How can I open Intel settings in Ubuntu, and, how can I install AMD, or if it's already installed, how can I open AMD graphics settings?

Thanks!

---

### Post by sandyd on 2016-02-02
Install the proprietary drivers by going to System Settings -> Software and Updates -> Additional Drivers.

You should then be able to switch between intel and amd graphics from the ati control panel.

---

### Post by mastablasta on 2016-02-03
after installation you need to initialise adapters and hope it will work otherwise prepare to do the purge. while many of these combos do work sometimes they do not (due to the way it is all wired on motherboard and no firmware made for linux).

[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

---

### Post by helm10101 on 2016-02-03
Thanks,
I checked fglrx in "More drivers", instead of "Using X.Org X server":
[IMG]http://i.imgur.com/yJwEzy4.jpg[/IMG]


But when I open terminal and type "fglrx" or "fglrx-amdcccle" or maybe "sudo fglrx-amdcccle" it says "command not found"

What is the problem?

---

### Post by buzzingrobot on 2016-02-03
Be sure to reboot after installing a new driver.  You can't activate a driver with something like "fglrx". Video drivers are activated as the system boots.

---

### Post by helm10101 on 2016-02-03
> **buzzingrobot said:**
> Be sure to reboot after installing a new driver.  You can't activate a driver with something like "fglrx". Video drivers are activated as the system boots.

Thanks. I rebooted. But than it told me that I'm on low graphic mode and I couldn't reach Ubuntu desktop anymore. Spent two hours and tried all I could find about how to fix this problem on Google. Ended up reinstalling Ubuntu. I just don't get what i did wrong. And now every time I am going to install new driver I should fear the possibility of reinstalling Ubuntu? It takes time. And I followed all the instructions as to how to install those drivers.. What did I do wrong? Are you sure I was supposed to check the amd proprietary option instead of the x.org wrapper?
Doesn't Linux have a protection against installing something that can ruin your whole OS like happened to me?

---

### Post by mastablasta on 2016-02-03
> **helm10101 said:**
> Thanks. I rebooted. But than it told me that I'm on low graphic mode and I couldn't reach Ubuntu desktop anymore. Spent two hours and tried all I could find about how to fix this problem on Google. Ended up reinstalling Ubuntu. I just don't get what i did wrong. And now every time I am going to install new driver I should fear the possibility of reinstalling Ubuntu? It takes time. And I followed all the instructions as to how to install those drivers.. What did I do wrong? Are you sure I was supposed to check the amd proprietary option instead of the x.org wrapper?
Doesn't Linux have a protection against installing something that can ruin your whole OS like happened to me?


you really should have read the link I posted. you need to 
1. install 
2. then initialise the driver/devices, 
3. then reboot. 

if the combo is supported by AMD and laptop manufacturer then all will work. 

if not, you might get text mode at which point you need to uninstall the driver (write down or print out the command from the link I posted) and reboot. and then you can complain to AMD why it is not working or the laptop manufacturer.

you are in full control of the OS. you can do everything you want with it. you can create something new, something lean, something beautiful and of course you can even ruin it. sudo command or entering admin password is there to also notify you that you are doing some major system changes. so make sure you want to changes to happen. in this case it would be good to have restore points like windows and i think there is a plan for something similar. until then there are multiple backup programs that will help restore the OS to previous state. or as in your case you can just purge proprietary and reinstall the x.org driver. 

EDIT2 : removal and reinstall procedure:
> ```


[LIST=1]
[/LIST]
sudo apt-get purge fglrx*
```

[LIST=1]
[/LIST]
Reboot.

[LIST=1]
[/LIST]
You may need to install the linux generic headers ```
sudo apt-get install linux-headers-generic
```

[LIST=1]
[/LIST]



please read the link I posted. looks a bit techy and difficult but it's actually not. **hint: title 3.1; item 6 (you can add hardw. accel. package later I believe)**

---

### Post by helm10101 on 2016-02-03
Thank you, I will be trying this right away.

**Edit: I tried what you did, but now how do I see the Catalyst control panel? again, when I type fglrx nothing happens
I also wrote "amdcccle" and it shows me
"The program 'amdcccle' can be found in the following packages:
 * fglrx-amdcccle
 * fglrx-amdcccle-updates"

As if the steps I did (in your guide) did nothing



Btw I tried another thing before I saw your reply, it's directly from AMD website:
[http://www2.ati.com/relnotes/amd-catalyst-graphics-driver-installer-notes-for-linux-operating-systems.pdf](http://www2.ati.com/relnotes/amd-catalyst-graphics-driver-installer-notes-for-linux-operating-systems.pdf)
followed every step, but again, every step gets its own errors so I just gave up. why can't they make it simple to install this on Linux / Ubuntu?
I just want to see the Catalyst control panel again ](*,)

---

### Post by grahammechanical on 2016-02-03
> Doesn't Linux have a protection against installing something that can ruin your whole OS like happened to me?

No. Linux is no different from Microsoft Windows this respect. A computer operating system is stupid thing. It is more stupid that we are. It cannot stop us from doing stupid things. 

The reason why things are easier on Windows is because for business reasons there is cooperation between Microsoft and the manufacturers of the motherboard as well as manufacturers of video adapters. There is little financial gain from Linux for hardware manufacturers and so that cooperation does not happen with Linux developers. This is why we sometimes need video drivers from the manufacturer and then it all depends on how interested the manufacturer is in keeping Linux users contented. Believe me, Linux developers would rather not depend on commercial corporations for software of any kind when they cannot get access to the code without breaking the law.

Also, add in the fact that Windows comes pre-installed with the supplier making sure that everything works. With Linux we are our own supplier. But it is a lot cheaper this way. My advice would be to get things working with one monitor first. And then try to set up both monitors.

During loading Linux will access a chip in the monitor (digital) and read the EDID (Extended Display Identification Data) and use that to set up the optimum screen resolution. Having 2 monitors might be a factor in this.

There should be an AMD/ATI settings utility and you will see an icon for that in the Dash. In System Settings there will be a Screen Display utility. Both should have options to detect displays. You may need to set up a profile peculiar to your system.

From Additional Drivers

> A proprietary driver has private code that Ubuntu developers cannot review or improve. Security and other updates are dependant on the driver vendor. 

Welcome to Linux! It is free, even in the sense that it does not cost us a penny. But it can be costly, in the sense that we have to be our own technical support department.

Regards

---

### Post by helm10101 on 2016-02-03
Thanks graham for the help :KS

I just unplugged my other monitor and left with only with my laptop's monitor.
I do not see anything in the Dash.

What are the steps from scratch I should follow in order to see that icon?

---

### Post by mastablasta on 2016-02-04
hmmm I would need to check this at home, but what does fglrx-amdcccle run?

---

### Post by Mark Phelps on 2016-02-04
> **helm10101 said:**
> Doesn't Linux have a protection against installing something that can ruin your whole OS like happened to me?

This is an entirely different world from Windows -- and it was invented by folks who were accustomed to doing work that would frighten Windows users.  So, Linux presumes you know what you are doing.

My suggestion, if you want to experiment with stuff, is to become familiar with using something like Clonezilla to image off your install to an external drive.  That way, if you make a serious mistake, it only takes a few minutes to restore your previously working system.

---

### Post by helm10101 on 2016-02-04
> **mastablasta said:**
> hmmm I would need to check this at home, but what does fglrx-amdcccle run?

I had to reinstall Ubuntu, because everytime I do mistake with fglrx, when I boot Ubuntu it tells me I'm on low graphics mode and I don't know how to fix it and I just reinstall Ubuntu.
So I see this now: fglrx-amdcccle: command not found, because I'm quite afraid to get the "Low graphics mode" again :D


> **Mark Phelps said:**
> This is an entirely different world from Windows -- and it was invented by folks who were accustomed to doing work that would frighten Windows users.  So, Linux presumes you know what you are doing.

My suggestion, if you want to experiment with stuff, is to become familiar with using something like Clonezilla to image off your install to an external drive.  That way, if you make a serious mistake, it only takes a few minutes to restore your previously working system.

Thanks, is Clonezilla easy to use or it's made to frighten Windows users too? :p

---

### Post by helm10101 on 2016-02-04
This is unbelievable (I'm going to do copy-paste on my other thread ](*,)) : 

I stopped installing unknown drivers, all I did now was to go to Software Center, searching for "AMD Catalyst", and I installed it like any other program (No driver!), I clicked it, and it told me that I do not have AMD driver installed, so I simply clicked "remove" via the Software Center it self, but guess what happened when I rebooted my laptop?
You guessed right:

[IMG]http://i.imgur.com/mwydvXy.jpg[/IMG]

Please, I'm tired of reinstalling Ubuntu. is there a way to fix that low graphics things? I didn't even install any driver. 
Maybe I should install Ubuntu 14.04 instead of 15.10?

---

### Post by howefield on 2016-02-04
> **helm10101 said:**
> Thanks, is Clonezilla easy to use or it's made to frighten Windows users too? :p

I'll second what Mark said, Clonezilla is a very useful tool to have, the description of which you can find on the [website]("http://clonezilla.org/").

I have literally just made a fresh USB Live media as a new version has just been released. Easily done by downloading the zip file from the website and extracting the contents to a freshly formatted USB stick, navigate to /media/*user*/Clonezilla/utils/linux/ and run the command sudo bash makeboot.sh /dev/sdb1 assuming that the flash disk is sdb - very important to get the disk name correct.

```
hugh@xenial-laptop:~$ cd /media/hugh/CLONEZILLA/utils/linux/
hugh@xenial-laptop:/media/hugh/CLONEZILLA/utils/linux$ sudo bash makeboot.sh /dev/sdb1
[sudo] password for hugh: 
This command will install MBR and syslinux bootloader on this machine
--------------------------------------------
Machine: Inspiron N5010:
Model: SanDisk Cruzer Facet (scsi)
Disk /dev/sdb: 8004MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  8004MB  8003MB  primary  fat32        boot

--------------------------------------------
Are you sure you want to continue?
[y/n] y
OK! Let's do it!
--------------------------------------------
File system of /dev/sdb1: vfat
--------------------------------------------
Do you want to install mbr on /dev/sdb on this machine "Inspiron N5010" ?
[y/n] y
OK! Let's do it!
--------------------------------------------
Do you want to install the SYSLINUX bootloader on /dev/sdb1 on this machine "Inspiron N5010" ?
[y/n] y
OK! Let's do it!
A filesystem supporting Unix file mode for syslinux is required. Copying syslinux from FAT to /tmp/...
'/media/hugh/CLONEZILLA/utils/linux/syslinux' -> '/tmp/syslinux_tmp.Rg14T6/syslinux'
Running: /tmp/syslinux_tmp.Rg14T6/syslinux -d syslinux -f -i /dev/sdb1 
done!
//NOTE// If your USB flash drive fails to boot (maybe buggy BIOS), try to use "syslinux -d syslinux -fs /dev/sdb1", i.e. running with "-fs".
hugh@xenial-laptop:/media/hugh/CLONEZILLA/utils/linux$ 
```

Boot from it and most likely by taking the default options through the *wizard* will give you good results. It looks more intimidating than it really is but as this is a different topic I won't say any more.

---

### Post by helm10101 on 2016-02-04
Thank you, but as you can see from my post above you, I've already done a mistake before installing clonezilla.
Ah, there has to be a way to rescue Ubuntu from this dreaded "Low Graphics Mode" rather than installing Ubuntu again.

---

### Post by howefield on 2016-02-04
> **helm10101 said:**
> Thank you, but as you can see from my post above you, I've already done a mistake before installing clonezilla.
Ah, there has to be a way to rescue Ubuntu from this dreaded "Low Graphics Mode" rather than installing Ubuntu again.

Yes, we posted at the same time, you could boot into Recovery mode and uninstall the graphics card packages that you installed to cause the error. Do you know how to do that.

---

### Post by helm10101 on 2016-02-04
> **howefield said:**
> Yes, we posted at the same time, you could boot into Recovery mode and uninstall the graphics card packages that you installed to cause the error. Do you know how to do that.

I know how to boot into recovery mode, but not how to uninstall the graphics card packages.
Also, the only thing I installed was from the Software Center and it was named "amdcccle" , which I also removed before rebooting, so why it still caused problems? I don't know..

BUT, I can't boot into recovery because earlier I customized GRUB to automatically start Ubuntu :),
so I just reinstalled again.

By the way, is there another way to maybe fix the low graphics mode? maybe through editing the configuration file? Which is my last resort.. (In the next time that it will happen?)
The file looks like that:
[IMG]http://i.imgur.com/t7QiKLi.jpg[/IMG]

[IMG]http://i.imgur.com/WYgj0nm.jpg[/IMG]
But not sure it can work.
Do you think that my issue was recover-able without reinstalling?

---

### Post by mastablasta on 2016-02-05
it will be hard for us to help you if you are not prepared to read what we post. I already posted how to remove the drivers and get back to previous state without reinstalling the whole system: [http://ubuntuforums.org/showthread.php?t=2312180&p=13433532#post13433532](http://ubuntuforums.org/showthread.php?t=2312180&p=13433532#post13433532)  

also I already posted what you need to do.

the link I provided also offers a manual install mode under title 4.2 in case of hybrid graphics and in case the default install doesn't work. and do read all the warnings.
> 
This method is NOT RECOMMENDED in general, but has been found by some users to make the chore of getting Intel/AMD hybrid graphics to work less difficult.

edit: one more thing - if you find clonezilla too complicated you can try RedoBackup. it does almost the same thing (less options) but with a nice GUI.

---

### Post by helm10101 on 2016-02-05
Thanks mastablasta,
I did follow the manual, I installed, initialized and rebooted, but it got me to the Low Graphics Mode nonetheless. 
You said to "install, initialize, reboot" and in case it doesn't work I should remove by "sudo apt-get purge fglrx*", the problem is that the first time I install any of the fglrx packages I get stuck at Low Graphics Mode!

But now I went to the tutorial you posted, and tried section 4.2, to manually install on a dual graphics laptop.
So I just realized, after following section 4.2, that AMD does not support my R5 M230 for Ubuntu 15.10:
[IMG]http://i.imgur.com/37nqu2m.jpg[/IMG]

That's taken from their drivers page :(.
So I guess there is no other way to make the R5 M230 work with my Ubuntu 15.10?
Or there is something I can do?
Maybe there are 3rd party drivers that work (that include a GUI to work with) ?

Thank you for your patience :)

---

### Post by mastablasta on 2016-02-05
sudo apt-get purge fglrx* and you may need to reinstall the kernel headers that should get you back to previous mode.

R5M230 is relatively new. Ubuntu 15.10 is likely still supported. so what happens if you continue manual install?

as mentioned before it is quite possible that it still won't work due to some firmware on the motherboard. I rmember there was a thread where similar specs laptops once worked and the other time not. probably due to the way motherboard and UEFI was setup.

if it still doesn't work then use windows. with enough ram you can install Linux in virtualbox or similar.

---

### Post by helm10101 on 2016-02-05
> **mastablasta said:**
> sudo apt-get purge fglrx* and you may need to reinstall the kernel headers that should get you back to previous mode.



So I must use sudo apt-get purge fglrx* and reinstall kernel header before I reboot right? (I tried to install fglrx so many times I don't know if I already did that in this order, but next time I will check and tell)

What exactly is the meaning of reinstalling kernel headers? (I'm new to Linux).

And, what is the meaning of adding "*" in "purge fglrx*" , the "*" means that it uninstalls evertyhing related to the word "fglrx"?

Also, since I'm new to Ubuntu, I want to know, is it possible to uninstall packages in a way different than "purge"? 

Thanks

---

### Post by howefield on 2016-02-05
> **helm10101 said:**
> So I must use sudo apt-get purge fglrx* and reinstall kernel header before I reboot right? (I tried to install fglrx so many times I don't know if I already did that in this order, but next time I will check and tell)

What exactly is the meaning of reinstalling kernel headers? (I'm new to Linux).

Just what it said, use something like..

```
sudo apt-get install --reinstall linux-headers-$(uname -r)
```  

> And, what is the meaning of adding "*" in "purge fglrx*" , the "*" means that it uninstalls evertyhing related to the word "fglrx"?

purge meaning completely remove any trace of the named package and fglrx* meaning any package starting with the letters fglrx.. the asterisk being a wild card.

> Also, since I'm new to Ubuntu, I want to know, is it possible to uninstall packages in a way different than "purge"? 

You could use "remove" instead of "purge" but purge also removes configuration files. If not using the terminal I use Synaptic package manager, not installed by default but available in the Software Centre. The Software Centre can be used to remove packages also.

---

### Post by monkeybrain20122 on 2016-02-05
> **howefield said:**
> 


purge meaning completely remove any trace of the named package and fglrx* meaning any package starting with the letters fglrx.. the asterisk being a wild card.

.

My understanding is that unlike in bash * is a not a wildcard but a regular expression in apt-get , in this case it may not matter but some people have apt-get removed a lot more than they intended with * So maybe OP should be warned. [http://askubuntu.com/questions/210976/apt-get-remove-with-wildcard-removed-way-more-than-expected-why](http://askubuntu.com/questions/210976/apt-get-remove-with-wildcard-removed-way-more-than-expected-why)

---

### Post by helm10101 on 2016-02-05
> **monkeybrain20122 said:**
> My understanding is that unlike in bash * is a not a wildcard but a regular expression in apt-get , in this case it may not matter but some people have apt-get removed a lot more than they intended with * So maybe OP should be warned. [http://askubuntu.com/questions/210976/apt-get-remove-with-wildcard-removed-way-more-than-expected-why](http://askubuntu.com/questions/210976/apt-get-remove-with-wildcard-removed-way-more-than-expected-why)

:-# I hope I didn't delete some extra stuff, although I don't believe that there are any more files / packages containing the string "fglrx", but I will be careful next time

---

