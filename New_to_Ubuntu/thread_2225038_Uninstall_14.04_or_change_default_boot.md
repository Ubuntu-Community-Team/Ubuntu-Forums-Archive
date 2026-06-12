---
title: "Uninstall 14.04 or change default boot ?"
date: 2014-05-19
forum: New to Ubuntu
---

### Post by Greg Mueller on 2014-05-19
I've installed 14.04 in a partition and have now decided that I like 12.04 better.

At this point in time I want to do one of two things.

**Uninstall Kubuntu 14.04**
**or** if I can't do that
**Change the the default boot so it is 12.04**

If I could change the boot so it default boots 12.04 then I could leave 14.04 and play with it once in a while.

How to ?

Thanks

---

### Post by LastDino on 2014-05-19
You can use grub customization to change your default boot selection and if you need to uninstall the OS (by clean method) you can use Linux Rimix version of Ubuntu which has tool to remove OS from your system.

---

### Post by Greg Mueller on 2014-05-19
> **LastDino said:**
> You can use grub customization to change your default boot selection and if you need to uninstall the OS (by clean method) you can use Linux Rimix version of Ubuntu which has tool to remove OS from your system.


I'm looking at the Grub Customizer but I'm not finding a button (etc) to change the boot default from 14.04 (which it is now) to 12.04.
As you can probably tell, this is the first time I have messed with this.

Thanks

---

### Post by LastDino on 2014-05-19
> **Greg Mueller said:**
> I'm looking at the Grub Customizer but I'm not finding a button (etc) to change the boot default from 14.04 (which it is now) to 12.04.
As you can probably tell, this is the first time I have messed with this.

Thanks

You should be able to see that in general settings tab, there are two options; predefined and previously booted one, use whatever that suites your needs. There are other ways like editing the file manually but I wouldn't suggest that.

Here is link to something similar to what you want to do.
[http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order](http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order)

---

### Post by anakai on 2014-05-19
You could install kde-config-grub2 package if you are using Kubuntu. Then from the settings you choose Start and finishing?? tab....Form there you can customize grub in many way's...

I'm not sure what Start and finishing tab is called in English, but you should find it easily.

---

### Post by grahammechanical on 2014-05-19
Are these two installations on one hard disk? Is it sda? Boot into Kubuntu 12.04, open a terminal and run

```
sudo update-grub
sudo grub-install /dev/sda
```

Now reboot and Kubuntu 12.04 will be at the top of the Grub menu. When we run those commands, then whatever install of Ubuntu or its flavours or any distribution that uses Grub we are in at the time we run those commands gets put to the top of the Grub menu. And this is because Grub is getting its configuration from a Grub file in that installation and not from the other installations.

Regards.

---

### Post by Greg Mueller on 2014-05-19
> **grahammechanical said:**
> Are these two installations on one hard disk? Is it sda? Boot into Kubuntu 12.04, open a terminal and run

```
sudo update-grub
sudo grub-install /dev/sda
```

Now reboot and Kubuntu 12.04 will be at the top of the Grub menu. When we run those commands, then whatever install of Ubuntu or its flavours or any distribution that uses Grub we are in at the time we run those commands gets put to the top of the Grub menu. And this is because Grub is getting its configuration from a Grub file in that installation and not from the other installations.

Regards.


[SIZE=4]**Hooray!**[/SIZE]
That worked perfectly
Thank You

---

### Post by pfeiffep on 2014-05-19
Please mark thread [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

