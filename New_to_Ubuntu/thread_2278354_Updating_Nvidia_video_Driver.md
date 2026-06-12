---
title: "Updating Nvidia video Driver"
date: 2015-05-15
forum: New to Ubuntu
---

### Post by aidan8 on 2015-05-15
Hello, I've been using Ubuntu 14.04 for awhile now and I like it a lot and would like to stick with it. I've customized it to how I like, but have come up with a concerning thought. How do I update the Nvidia video driver? I've tried searching for it, but everything I find is a guide on how to install the nvidia video drivers, not update. I know that in Windows you no longer have to uninstall the old video driver, you can simply download the latest version and install it from there (or run the update from the Geforce experience software.) Is this the same case for Ubuntu as well? Can I simply run    apt-get install nvidia-XXX and expect it to properly install the new version, or should I uninstall the current driver before installing the next version?

If I have to uninstall the driver, could someone recommend a proper guide on doing so, that way I won't total my install due to _out dated information_. The [community Nvidia Manual]("https://help.ubuntu.com/community/NvidiaManual#Uninstalling_the_Driver-1") and [BinaryDriverHowTo/Nvidia ]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")really doesn't say much for uninstalling, and I don't really care to install 3rd party tools to do the job for me.

Fyi, I'm using the mamarley ppa for my nvidia drivers.

Thanks! :p

---

### Post by sandyd on 2015-05-15
As long as you install updates, driver updates for the series of drivers (340/349/etc) would be installed.

However, this is dependent on the PPA maintainer on keeping the latest driver version in the PPA.

---

### Post by aidan8 on 2015-05-15
Yes, the 349 drivers are available. I just didn't imagine it being that simple.

So no prior adjustments to the current video driver? Just install the new version and it removes the old?

---

### Post by grahammechanical on 2015-05-15
Why do you think that you need to update the nvidia driver? Are you needing a newer version to fix some compatibility problems? Ubuntu has System Settings>Software & Updates>Additional Drivers tab which will offer us 4 versions of the proprietary video driver and install it for us.

Also in Additional Drivers we can use Ubuntu Software tab and tick the box Proprietary drivers for devices (Restricted) to get updates to the proprietary video driver. Keep in mind that stability is the difference between what we get in Ubuntu and what is available on the manufacturer's web site.

I cannot use the latest drivers from the Nvidia web site as they do not support my older Nvidia adapter. In some cases the latest is not always the greatest.

Regards.

---

### Post by aidan8 on 2015-05-16
I was going to update the driver over a period of time for better performance in new game releases that I'll may buy. Or is that the wrong mentality with Linux? I've always tried keeping everything up-to-date.

The drivers provided in the Software & Updates Additional Drivers are out of date (331.) The last I had used that version, game performance wasn't very good. Since then I decided that I didn't like the Unity environment and reinstalled Ubuntu with just the Gnome DE so there wouldn't be any conflicts in having both. I also installed a newer version of the nvidia drivers (346) outside of the Software & Update tool. The performance was far better in games like Team Fortress 2, CS:GO, and Euro Truck Simulator.

---

### Post by dino99 on 2015-05-16
then move to a newer ubuntu version to get newer drivers by default; the dist-upgrade will not change your custom settings

---

### Post by monkeybrain20122 on 2015-05-16
Up to date driver here [https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa)  

Pretty easy to do, just add the source and do normal update. Some people here have a thing against ppas and would rather tell you to blow your whole system by upgrading the OS,  I have no such hang ups. :)

Read the instructions carefully if you are new to this and install ppa-purge just in case, upgrading graphic driver always has a little risk,--but worst thing would be a reinstall, which you would have to do if you install a new Ubuntu release anyway. ;)

Edited: If you don't have optimus, make sure that bumblebee doesn't get installed. If it is just remove it from package manager before you run 
sudo nvidia-xconfig and reboot.

---

