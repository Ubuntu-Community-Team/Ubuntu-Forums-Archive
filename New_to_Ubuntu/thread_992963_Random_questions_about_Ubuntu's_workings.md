---
title: "Random questions about Ubuntu's workings"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by Barky on 2008-11-25
I've been using Ubuntu since 8.04 came out and I love it. I consider myself an intermediate to advanced windows user and have an udnerstanding of how the under-lying system "works". There are still a things I don't understand about some common functions of Ubuntu though and how it is working under the hood. Hopefully you guys can help me out so I can get a "full picture" view instead of just being a mindless user.

Why on earth do I have to use nautilus when I want to edit any files or folders outside of /HOME? does nautilus just function as root's file browser?

How can I clean up my system? It seems I have so many packages spread out all over the place it would be impossible to find what i don't need anymore. It was easier with Windows because all system files were usually in that specific file. When packages are installed, they get moved all over to usr, docs, etc and there's no way to consolidate them from what I can tell.


Why do I have to set permissions on certain files I download or aquire but not others before I run them? sometimes I need to run chmod on a file to execute it but sometimes I don't, why the discrepency?

How does mounting ISOs work in Ubuntu? I know there's a command to mount ISOs but haven't tried it yet. Does the mounted ISO appear as a new drive to explore? The only experience I have with mounting ISOs is daemon tools which mounted a virtual drive on the system to load ISOs into.

Is there something similar to device manager in Ubuntu? It seems hard to see what devices use what drivers without a consolidated list of devices and the drivers used for them. 

How does USB configuration work in Ubuntu? Windows handled USB devices with file called usbsys (with service pack 3 this has changed). I know there is a way to change the polling of the mouse in Ubuntu but not a way to change the joystick polling.

I think that'll do it for now. thanks for the help

---

### Post by Paqman on 2008-11-25
I'll take a quick stab at a couple of these

> **Barky said:**
> 
Why on earth do I have to use nautilus when I want to edit any files or folders outside of /HOME? does nautilus just function as root's file browser?


Nope, Nautilus is the file browser for the whole system. To check go to Places > Home > Help > About.

When you need to edit files outside /home, you're talking about files *you don't own*. So you need to run Nautilus as root instead of as yourself. The command to launch Nautilus as root is:
```
gksu nautilus
```
Whereas to run it as yourself, it's just:
```
nautilus
```


> 
How can I clean up my system?


Good question. The bottom line is that you don't really need to do as much cleanup to Ubuntu as you do to Windows. For some ideas about what you can do, have a look at [HOWTO: Cleaning up all those unnecessary junk files]("http://ubuntuforums.org/showthread.php?t=140920")

> 
How does mounting ISOs work in Ubuntu? I know there's a command to mount ISOs but haven't tried it yet. Does the mounted ISO appear as a new drive to explore? The only experience I have with mounting ISOs is daemon tools which mounted a virtual drive on the system to load ISOs into.

Take a look at gmountiso, it gives you a nice GUI for mounting ISOs.

---

### Post by m_duck on 2008-11-25
[COLOR=DarkSlateGray]Why on earth do I have to use nautilus when I want to edit any files or folders outside of /HOME? does nautilus just function as root's file browser?[/COLOR]

Answered above. The files outside of your home directory are not owned by your user, but by another user or "root".
[COLOR=DarkSlateGray]
How can I clean up my system?[/COLOR]

Most of the time, when you have installed packages from the repo's (or a .deb file) the packages that have been installed as dependencies will be remembered, and will be removed if no longer in use when the main package is uninstalled. If you install packages from the command line, you will notice it sometimes say that there are packages that were installed but no longer in use, and use ```
sudo apt-get autoremove
``` to remove them. There are other similar commands mentioned in the link posted above.

To completely remove a package, mark for complete removal in synaptic, or use ```
sudo apt-get remove <package-name> --purge
```I don't think the above removes configuration files from your home directory.
[COLOR=DarkSlateGray]
Why do I have to set permissions on certain files I download or aquire but not others before I run them?[/COLOR]

I believe this varies with file type and what it is executed by, but am not sure. The reason you often have to make certain scripts executable before the will execute is for security reasons to make it harder for malicious scripts to be run on your computer (I think).

[COLOR=DarkSlateGray]Is there something similar to device manager in Ubuntu?
[/COLOR]
Three good ways are:```
sudo lshw
lspci
lsusb
```These will let you see what is attached to your computer. In "lshw" it will list all of your hardware, and in the lines that begin "configuration:" there will be an entry of "driver=something" which tells you the driver that is in use for that piece of hardware.

Other questions I am not sure of. Hope this is of some use.

EDIT: Just found a [thread to enable ISO mounting from a right click while in Nautilus]("http://ubuntuforums.org/showthread.php?t=704350"). It also lets you unmount from a right click as well.

---

### Post by corncob on 2008-11-25
Is there any difference in where you use "gksu" and "sudo"?  They seem to do the same thing on my computer.

---

### Post by jakupl on 2008-11-25
> **corncob said:**
> Is there any difference in where you use "gksu" and "sudo"?  They seem to do the same thing on my computer.

gksu is better for gui applications.
sudo is better for command line applications

---

### Post by CatKiller on 2008-11-25
> **corncob said:**
> Is there any difference in where you use "gksu" and "sudo"?  They seem to do the same thing on my computer.

See [here]("http://www.psychocats.net/ubuntu/graphicalsudo") for the rationale.

---

### Post by CatKiller on 2008-11-25
> **Barky said:**
> How can I clean up my system? It seems I have so many packages spread out all over the place it would be impossible to find what i don't need anymore. It was easier with Windows because all system files were usually in that specific file. When packages are installed, they get moved all over to usr, docs, etc and there's no way to consolidate them from what I can tell.

**Packages** aren't spread around. They are quite tidily in /var/apt/cache in case they are needed again. The **files that were contained in the package files** (think of packages as really sophisticated self-extracting archives, if it helps) are put in the appropriate place for the type of file that they are; executable binaries are put in /usr/bin, documentation is put in /usr/doc and configuration files are put in /etc - in keeping with the [Filesystem Hierarchy Standard]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard"). All of these places, and others, could be spread over many different partitions, or different machines, tailored to the types of files that will be put there. As has already been mentioned, your package manager will keep track of which packages installed which files, and when the package is uninstalled, these files will go with them.

> Why do I have to set permissions on certain files I download or aquire but not others before I run them? sometimes I need to run chmod on a file to execute it but sometimes I don't, why the discrepency?

Until a file is made *executable*, it can't be executed. It's just a text file. I'm sure you'd agree that having random things off the Internet being automatically executed would be a Bad Thing. Other files aren't executed at all. Archive files are opened with the Archive Manager, media files are opened with your media player, and so on.

> How does mounting ISOs work in Ubuntu? I know there's a command to mount ISOs but haven't tried it yet. Does the mounted ISO appear as a new drive to explore? The only experience I have with mounting ISOs is daemon tools which mounted a virtual drive on the system to load ISOs into.

There's no such thing as a separate drive in Linux. Every file that you can use is mounted at some point in the filesystem tree, and devices are treated as files, which are also in the filesystem tree. So when you mount an .iso, it becomes part of the tree, the same as an actual CD or DVD would, and the same as your hard drives do.

> Is there something similar to device manager in Ubuntu? It seems hard to see what devices use what drivers without a consolidated list of devices and the drivers used for them.

No. The Device Manager was actually one of the things that I most missed when I stopped using Windows. The Device Manager is only possible because Microsoft is able to rule device makers with an iron fist, and specify exactly how all drivers can interface with the software that Microsoft have written, and how they all will behave for installation and uninstallation. Since Linux has a slightly more ad-hoc approach, there's absolutely no reason why a printer driver should present the same information in exactly the same fashion as a mouse driver, say, or a sound card, or a digital camera. They all do different things, so there's not really any incentive to make them all behave the same way.

There are tools, like **lshw**, that show how device drivers are connected to the kernel, and graphical tools, such as **hardinfo**, that take this information and present it in the graphical style that you're probably accustomed to. You can't modify the drivers that are revealed by this method, since they are configured and installed in ways that play to their particular features.

---

