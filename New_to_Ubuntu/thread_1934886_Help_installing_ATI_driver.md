---
title: "Help installing ATI driver?"
date: 2012-03-03
forum: New to Ubuntu
---

### Post by cv5903 on 2012-03-03
Hi, fairly new to Ubuntu and have been searching for a solution all night. I have a Radeon 5570, downloaded the latest driver from ATI, did sudo chmod +x (paraphrasing from memory), but when I try to run the file in terminal it says there is an existing driver in place that needs to be removed first unless I force an overwrite (not recommended). My question is how do I force overwrite? Or should I not? Here is the end of the log from the attempted install.

find arch \
        etc \
        lib \
        module \
        usr \
        xpic     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
        arch/x86/usr/X11R6/bin \
        usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# set the permissions on the pxpress scripts
chmod 744 debian/pxpress/switch*
dh build
make: dh: Command not found
make: *** [build] Error 127
dpkg-buildpackage: error: debian/rules build gave error exit status 2
[Error] Generate Package - error generating package : Ubuntu/oneiric

I found something about removing proprietary drivers and tried that, they still show up and it won't install. Thanks in advance for any help...Running Ocelot with radeon 5570 and intel core 2 quad Q8300.

---

### Post by mastablasta on 2012-03-03
you need to remove the one you have installed first. 
here is how : [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

check under purge fglrx.

---

### Post by cv5903 on 2012-03-03
Yeah that's the one I found, still no dice. Anybody know if it would be worth it to change to the proprietary Catalyst 11.12, or if the one that came on Ocelot is better/the same?

---

### Post by ahrar25 on 2012-03-03
System Settings<Additional Drivers<update your Graphics card driver... 
i faced the same problem before..... then update your ubuntu after updating your card driver

---

### Post by cv5903 on 2012-03-03
So...I feel like a real winner here. I finally got the old driver deleted, then got the brilliant idea to reboot before installing the new driver. SMH. This is what I get for doing this at 4 in the morning. I tried setting my BIOS to integrated graphics but still can't see anything but the BIOS. Any ideas other than fresh install? Luckily I just play with this partition, I have dual boot w/ 7.

---

### Post by Mark Phelps on 2012-03-03
You didn't mention that you have Hybrid Graphics.  That was designed to work with MS Windows and presents serious problems running Linux:

[https://help.ubuntu.com/community/HybridGraphics]("https://help.ubuntu.com/community/HybridGraphics")

---

### Post by cv5903 on 2012-03-03
Well, I went ahead with the fresh install. I needed to do some cleanup anyway. When I installed 11.04 somehow I ended up with three different Linux partitions and 1 Windows 7. At least this gave me a reason to merge those 3 and utilize more disc space. Thanks for the links, they were helpful.

---

### Post by mastablasta on 2012-03-04
installing latest catalyst should solve the hybrid graphics problem: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

or look here for succesfull how to made by one user: [http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

---

