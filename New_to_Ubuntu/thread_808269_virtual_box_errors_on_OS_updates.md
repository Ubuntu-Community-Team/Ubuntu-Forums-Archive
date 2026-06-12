---
title: "virtual box errors on OS updates"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by taith on 2008-05-26
hey everybody :)

annoying problem here, whenever ubuntu has an OS update(in which a reboot is required... like this morning) virtual box keeps giving me errors when trying to boot... it was working this morning before the updates were installed, and after, i get the following error:

> VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}


all of the vbox components are still installed... anyone know how to fix? and/or why it keeps going out?

---

### Post by taith on 2008-05-26
*shameless bump*

---

### Post by Michaelg14 on 2008-05-26
I don't know what causes it but the easiest way to fix it is just re-install Virtualbox, you won't lose anything doing it.

---

### Post by taith on 2008-05-26
nope... i reinstalled, as well as uninstall->reboot->install->reboot and it still gives me the same errors :(

---

### Post by starcannon on 2008-05-26
I have the same error here.

---

### Post by lizzard on 2008-05-26
You need to recompile the VirtualBox kernel modules:
```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by taith on 2008-05-26
sudo /etc/init.d/vboxdrv setup
* Usage: /etc/init.d/vboxdrv {start|stop|restart|status}


sudo /etc/init.d/vboxdrv restart
 * Stopping VirtualBox kernel module vboxdrv                             [ OK ] 
 * Starting VirtualBox kernel module vboxdrv                                    
 * No suitable module for running kernel found.



sudo /etc/init.d/vboxdrv status
 * VirtualBox kernel module is not loaded.

---

### Post by lizzard on 2008-05-26
OK, seems to be an issue with the open-source-edition. Try to install/reinstall the virtualbox-ose-modules.

---

### Post by Gallienus on 2008-05-26
I'm no expert, having only installed VirtualBox a few days ago, but I believe that the VirtualBox kernel driver is specific to the version of the Linux kernel that you are using. Today's updates gave us the new 2-6-24-17 Linux kernel, but I'm guessing that an updated compatible VirtualBox kernel driver is not yet available in the repositories. Hopefully this will be offered as an automatic update when it's ready.

When I boot up my system, I'm given the option of choosing to use 2-6-24-17 or the old 2-6-24-16 kernel. So in the meantime, when I want to use VirtualBox, I'll just use the old Linux kernel. (Hope this made sense, I don't completely understand it all myself. :) )

---

### Post by lizzard on 2008-05-26
> **Gallienus said:**
> I'm no expert, having only installed VirtualBox a few days ago, but I believe that the VirtualBox kernel driver is specific to the version of the Linux kernel that you are using. Today's updates gave us the new 2-6-24-17 Linux kernel, but I'm guessing that an updated compatible VirtualBox kernel driver is not yet available in the repositories. Hopefully this will be offered as an automatic update when it's ready.

When I boot up my system, I'm given the option of choosing to use 2-6-24-17 or the old 2-6-24-16 kernel. So in the meantime, when I want to use VirtualBox, I'll just use the old Linux kernel. (Hope this made sense, I don't completely understand it all myself. :) )

I think, you're right. :)

---

### Post by taith on 2008-05-26
> **Gallienus said:**
> I'm no expert, having only installed VirtualBox a few days ago, but I believe that the VirtualBox kernel driver is specific to the version of the Linux kernel that you are using. Today's updates gave us the new 2-6-24-17 Linux kernel, but I'm guessing that an updated compatible VirtualBox kernel driver is not yet available in the repositories. Hopefully this will be offered as an automatic update when it's ready.

When I boot up my system, I'm given the option of choosing to use 2-6-24-17 or the old 2-6-24-16 kernel. So in the meantime, when I want to use VirtualBox, I'll just use the old Linux kernel. (Hope this made sense, I don't completely understand it all myself. :) )

thanks! i assumed as much, didnt know if there was an easy/quick fix :) i hopes they hurrys up with that new patch!!

---

### Post by bodycoach2 on 2008-05-26
I'm having the same issue after the update. Booting into the older kernel works, but that's not very convenient. I hope the provide a fix/patch/update soon.

---

### Post by adyroman on 2008-05-27
Any idea what's the usual delay between a new kernel release and a patch for the virtualbox kernel modules? The kernel modules package is maintained by the Ubuntu MOTU team, but how can we get them to reply on this thread? :p

---

### Post by Glucklich on 2008-05-27
I have exactly the same problem. And I was using AutoCAD 2007 and have a project delivery for tomorrow. So, how do I do that "get back to the last version" thing?

---

### Post by Glucklich on 2008-05-27
I got it. Was on that GNUB loader thing. But I agree with the previous posts, this is not very convenient and I hope the Ubuntu team provides the stuff for the new version soon. Unfortunately I don't know how to get their attention to this issue.
Edit: For some reason they made the update, and for this reason we can't use it. At least me, that is stuck on this issue for professional reasons.

---

### Post by buntunub on 2008-05-27
Same issue here. Hope this gets fixed soon!

---

### Post by nike984 on 2008-05-27
Type the following command in the terminal

sudo aptitude install linux-headers-$(uname -r);sudo dpkg-reconfigure virtualbox;sudo /etc/init.d/vboxdrv setup

It's one line, so just copy and paste every thing.

---

### Post by BoyMike on 2008-05-27
That didn't work for me, I get the following output in /var/log/vbox-install.log:
> 
/etc/init.d/vboxdrv: 311: /usr/lib/virtualbox/src/build_in_tmp: not found


Any ideas?

// Mike

---

### Post by sgtkeum on 2008-05-27
If you really need Virtualbox snd can't wait for OSE version update, try getting the non-ose version from SUN. (You'll have to first remove all ose version of Virtualbox).

I removed VirtualBox OSE version and installed 1.6 version from Sun website. It works O.K. with pre-existing VDI's (You may want to reinstall guest OS plugin). But then the Virtual box consumes my CPU at very high rate, around 60~70%, even with one single internet explorer in the guest machine (Win XP). I'm not sure why this upgrading degrades the performance. At least now it's running.

---

### Post by buntunub on 2008-05-27
> **nike984 said:**
> Type the following command in the terminal

sudo aptitude install linux-headers-$(uname -r);sudo dpkg-reconfigure virtualbox;sudo /etc/init.d/vboxdrv setup

It's one line, so just copy and paste every thing.

 K. did this and noticed a couple things:

```
sudo aptitude install linux-headers-$(uname -r);sudo dpkg-reconfigure virtualbox;sudo /etc/init.d/vboxdrv setup
[sudo] password for dave: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are unused and will be REMOVED:
  ant antlr libbcel-java libcommons-collections-java 
  libcommons-collections3-java libcommons-configuration-java 
  libcommons-io-java libcommons-lang-java libcommons-logging-java 
  libjdom0-java liblog4j1.2-java liblogkit-java libregexp-java 
  libservlet2.3-java libswt3.2-gtk-java libswt3.2-gtk-jni 
  libwerken.xpath-java [B]linux-headers-2.6.24-16 
  linux-headers-2.6.24-16-generic[/B] velocity 
0 packages upgraded, 0 newly installed, 20 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 88.8MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 182176 files and directories currently installed.)
Removing velocity ...
Removing ant ...
Removing libwerken.xpath-java ...
Removing antlr ...
Removing libbcel-java ...
Removing libcommons-collections-java ...
Removing libcommons-collections3-java ...
Removing libcommons-configuration-java ...
Removing libcommons-io-java ...
Removing libcommons-lang-java ...
Removing libcommons-logging-java ...
Removing libjdom0-java ...
Removing liblog4j1.2-java ...
Removing liblogkit-java ...
Removing libregexp-java ...
Removing libservlet2.3-java ...
Removing libswt3.2-gtk-java ...
Removing libswt3.2-gtk-jni ...
[B]Removing linux-headers-2.6.24-16-generic ...
Removing linux-headers-2.6.24-16 ...[/B]
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
[B][I]Package `virtualbox' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: virtualbox is not installed
 * Usage: /etc/init.d/vboxdrv {start|stop|restart|status}[/I][/B]
```

First, it removed the old Linux headers for the -16 kernel. Sounds promising, but where are the headers for the -17 kernel?.. No headers for the new kernel = no vboxdrv!

btw, 

```
 which virtualbox
/usr/bin/virtualbox
```

---

### Post by Delever on 2008-05-27
Or you could simply enable pre-release (proposed) updates in Software sources, update only virtual box, then disable pre-release updates.

---

### Post by buntunub on 2008-05-27
> **Delever said:**
> Or you could simply enable pre-release (proposed) updates in Software sources, update only virtual box, then disable pre-release updates.

What good would that do for us?

Is the fix committed but not released?

---

### Post by Delever on 2008-05-27
> **buntunub said:**
> 
Is the fix committed but not released?

Yes.

---

### Post by JayBee808 on 2008-05-27
> **Delever said:**
> Or you could simply enable pre-release (proposed) updates in Software sources, update only virtual box, then disable pre-release updates.

This worked for me.  Vbox is up and running without even rebooting.  Is it a good idea to leave proposed updates enabled, or should I turn it back off now.  I'm just wondering how many other bugs might be fixed already...

---

### Post by Delever on 2008-05-27
> **JayBee808 said:**
> This worked for me.  Vbox is up and running without even rebooting.  Is it a good idea to leave proposed updates enabled, or should I turn it back off now.  I'm just wondering how many other bugs might be fixed already...

Proposed means that they are being tested, and are not released until checked. They are usually 1-2 days ahead. You should not enable them, unless life is not exciting enough :lolflag:.

---

### Post by JayBee808 on 2008-05-27
> **Delever said:**
> You should not enable them, unless life is not exciting enough :lolflag:.

Life is not exciting enough without vbox!:)

Thanks for the tip, you got me back up and running.

---

### Post by buntunub on 2008-05-28
I got the fix with the latest round of updates, so all is right with the world again. :)

---

