---
title: "Avoiding Kernel Updates"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by mcse37 on 2008-06-22
Every time I agree to install a kernel update, something breaks.  I just upgraded to 2.6.24-19-generic, and now VirtualBox is broken.  How important are kernel updates & would avoiding them give me a more stable desktop?

Thanks!

---

### Post by niyonk on 2008-06-22
kernel updates are for fixing not breaking ;)
It has also happened to me a number of times.
but soon after that no more problems. 
Just make sure u install the kernel updates on their own time first.
what i mean is...ignore the other packages. coz i think they sometime interfere, then when u restart i do not think u will have such troubles...thats how i do my updates(most of the time)
Hope it helps :)

---

### Post by drs305 on 2008-06-22
Install and use Startup-Manager. You can select (or change) whether or not your boot menu is updated when a kernel is installed. This means that you can update and see the new kernels but you won't boot to a new one until you decide to take the plunge. When you are ready, you can change StartUp-Manager to start using the new kernel.

To install it:
```
sudo aptitude install startupmanager
```

To open it and change settings: System, Settings, StartUp-Manager.

To make the changes I've discussed or to ensure the new kernel won't be used until you tell it to: 
Advanced, leave 'Automatically update default boot option' unchecked. On the first tab you can select the default kernel or operating system.

You can also use StartUp-Manager to hide extra kernel displays:
[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by Oldsoldier2003 on 2008-06-22
> **mcse37 said:**
> Every time I agree to install a kernel update, something breaks.  I just upgraded to 2.6.24-19-generic, and now VirtualBox is broken.  How important are kernel updates & would avoiding them give me a more stable desktop?

Thanks!

Virtual box uses kernel modules, so when you update your kernel you need to update the vbox modules. Its a lot easier if you use the puel version of virtualbox.

If you are dead set on locking down your kernel version you can "pin" or "hold" it in synaptic or apt. [https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto) , pay special attention to the section on holding packages using synaptic

---

### Post by ramjet_1953 on 2008-06-22
Every time that you have a kernel update, you will need to set-up VirtualBox for that kernel.

When you do a kernel update and try to run VirtualBox, it will pop up a message that you need to run a configure script for the new kernel.

It even gives you the script, so all you have to do is copy and paste it into a terminal.

Not that hard at all.

Many people get a warning pop-up and don't bother to read and digest what it is saying, even when the answer is right there in front of them.

Regards,
Roger :cool:

---

### Post by bigtel on 2008-06-27
I have problems after updates too. 

What is the difference between the Virtual and Generic options in the Grub menu.??

My system has problems if I boot with the virtual, so I am looking at disabling that option.

---

### Post by sdennie on 2008-06-27
It's best to keep the kernel up to date.  However, if you are using the version of virtualbox from [www.virtualbox.org](www.virtualbox.org), you can avoid having to recompile the drivers after every update with this script:

```

#!/bin/bash

echo "Building VirtualBox driver for $1" >&2
cd /usr/share/virtualbox/src
make clean 2>&1 > /dev/null
make install KERN_DIR=/lib/modules/$1/build KERN_INCL=/lib/modules/$1/build MODULE_DIR=/lib/modules/$1/misc 2>&1 > /dev/null

depmod -a $1

```

Name it update-vbox and install it with:

```

sudo mkdir -p /etc/kernel/postinst.d
sudo install update-vbox /etc/kernel/postinst.d

```

Now every time you install a kernel update, it will build the virtualbox driver for the new kernel before you boot into it.

---

### Post by ChameleonDave on 2008-06-27
> **mcse37 said:**
> Every time I agree to install a kernel update, something breaks.  I just upgraded to 2.6.24-19-generic, and now VirtualBox is broken.  How important are kernel updates & would avoiding them give me a more stable desktop?

Thanks!

If you are using SCIM fpr language input, then you need to install *scim-bridge-client-qt* for keyboard capture to work properly.  That's a problem many people have had.

One way you can avoid risky updates is to use the Mint Updater.

---

### Post by bigtel on 2008-06-27
..what is the 'Mint Updater'..??

---

### Post by ChameleonDave on 2008-06-27
> **bigtel said:**
> ..what is the 'Mint Updater'..??

It's a program.  It's not available in the standard Ubuntu repositories though, so maybe just forget about it.

---

### Post by Vishal Agarwal on 2008-07-26
After the Kernel Update, What (and how) to do with the earlier one ? I saw the list of kernel is added to the menu.lst.  

How do it can be deleted/Uninstalled.
How risky it is ?

---

### Post by drs305 on 2008-07-26
> **Vishal Agarwal said:**
> After the Kernel Update, What (and how) to do with the earlier one ? I saw the list of kernel is added to the menu.lst.  

How do it can be deleted/Uninstalled.
How risky it is ?

The easiest and safest way is to use StartUp-Manager. Each time a kernel is introduced it is added to grub's menu.lst but there are advantages to removing older kernels with synaptic. In either case, unless you do something, the kernel list displayed during boot will continue to grow each time a new kernel comes out.

I'd recommend you always keep 2 kernels, the one you are currently using plus one that worked in the past. If you want to remove older unused kernels from the machine use synaptic and do a search for "linux-image". You will find a list of all the kernels installed on your machine. If you remove a kernel via synaptic it will also be removed from your boot menu.lst

Another way is to use StartUp-Manager to control what you see on your boot menu. Refer to post #3 for more information and read the link at the bottom of the post to see the advantages of using StartUp-Manager vs editing grub's menu.lst manually.

---

### Post by bigtel on 2008-07-26
My laptop will not even boot up after this new kernal update. This is frustrating, it just 'hangs' there. I have got to revert back to using version 19 generic.

---

### Post by drs305 on 2008-07-26
I think I've avoided a lot of grief over the years by keeping the 'proposed' and 'backports' repositories disabled unless I need something specific. 

I've selected 'linux-image' in synaptic which automatically updates to the latest stable kernel but even then have grub set to keep using the last kernel used until I decide to change it.

---

### Post by stmiller on 2008-07-26
Ubuntu does not update the main kernel version in a distro release. They stay with one version. There are, however, kernel security updates which could trigger a need to recompile virtualbox modules.

So the updates are security related and very important to do:

[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

---

### Post by drs305 on 2008-07-26
> **stmiller said:**
> Ubuntu does not update the main kernel version in a distro release. They stay with one version. There are, however, kernel security updates which could trigger a need to recompile virtualbox modules.

So the updates are security related and very important to do:

[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

By version are you referencing 2.6.24? I've had -16 through -19 already and people are having problems with -20. Perhaps my terminology regarding 'kernels' and 'versions' is not precise.

---

### Post by shellback84 on 2008-07-26
I am having problems with the -20 kernel as well and I have tried everything suggested here at this forum with no luck. So all I do is use my Grub loader during start up, select the older -19 kernel and my joy is good, along with all the other updates I downloaded. Like everything else wonderful with this OS, they will come out with a fix and I will wait till then and live with the slightly older kernel. So is life.

---

### Post by YaroMan86 on 2008-07-26
I don't use StartUp manager. Directly editing the menu.lst is EASY. And you can remove any entries.

Keeping the older kernels is actually a good idea in case something goes wrong.

---

### Post by ibuclaw on 2008-07-26
> **shellback84 said:**
> I am having problems with the -20 kernel as well and I have tried everything suggested here at this forum with no luck. So all I do is use my Grub loader during start up, select the older -19 kernel and my joy is good, along with all the other updates I downloaded. Like everything else wonderful with this OS, they will come out with a fix and I will wait till then and live with the slightly older kernel. So is life.

Then why do you have hardy-proposed enabled in your sources list then?

It's called hardy-proposed for a reason, comment it out in your /etc/apt/source.list file it and purge the 2.6.24-20 kernel :)

Regards
Iain

[EDIT]
If you installed the Binary-Only version of VirtualBox (from Sun's Site)
Then you have to run
```
sudo /etc/init.d/vboxdrv setup
```
After every kernel update.

---

### Post by pandan on 2008-07-28
I think the newer kernel in Hardy 8.04 doesn't like my p3's motherboard completely and gives some IDE recognition errors.

As such I want to stick with Gutsy 7.10 when I install on p3's and avoid kernel as well as distro upgrades.

I know there are settings to keep current version of packages- including the kernel packages,

But...

Is there a way of removing the distro upgrade button in update-manager when I give the computer away??

---

### Post by dakkar9999 on 2010-05-06
> **sdennie said:**
> It's best to keep the kernel up to date.  However, if you are using the version of virtualbox from [www.virtualbox.org](www.virtualbox.org), you can avoid having to recompile the drivers after every update with this script:

```

#!/bin/bash

echo "Building VirtualBox driver for $1" >&2
cd /usr/share/virtualbox/src
make clean 2>&1 > /dev/null
make install KERN_DIR=/lib/modules/$1/build KERN_INCL=/lib/modules/$1/build MODULE_DIR=/lib/modules/$1/misc 2>&1 > /dev/null

depmod -a $1

```

Name it update-vbox and install it with:

```

sudo mkdir -p /etc/kernel/postinst.d
sudo install update-vbox /etc/kernel/postinst.d

```

Now every time you install a kernel update, it will build the virtualbox driver for the new kernel before you boot into it.


Sorry, complete newbie here.  Will this work with the current release (Lucid and virtualbox 3.1.6)?

And it's not clear to me where that script needs to be put.

Thanks!

---

