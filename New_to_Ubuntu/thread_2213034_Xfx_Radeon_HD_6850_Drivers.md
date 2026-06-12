---
title: "Xfx Radeon HD 6850 Drivers"
date: 2014-03-24
forum: New to Ubuntu
---

### Post by fluctuatinganomaly on 2014-03-24
I'm posting this in the newbie section, becuase I still have no clue about most things and this seems like the right place for me :p

So I've just installed 12.04 LTS on my desktop, have a thread about all this on this forum.#

Any ways, once I got back on and stuff, I figured I'd need drivers for my graphics card, now, when I got to the desktop some were suggested, and being silly, I accepted them. So I've installed some form of graphics driver, but I do not believe it is the right one.

I've been and downloaded a .run file from the website for my card, and I have tried to install it with failure everytime, something about no permission. Any ways, looking at other threads there are alot of apt-get purge ******** commands, and I'm not sure which I need to be runnig to uninstall what ever it was I installed. And I don't know how to find out either :/

I dont want to go running alot of different purge commands incase at some point I remove something I'd actually need

If any one could help me with this I would appreciate it, finding out what I installed and what I need to remove and on whether I have the right file downloaded and how to actually install it. Would be great :)

~Matt

---

### Post by Mark Phelps on 2014-03-24
I've used the AMD .run files successfully but to do that, I had to make them executable.  You do this by opening a terminal and entering "sudo chmod +x <filename.run>", substituting the actual name of the run file for "<filename.run>".

---

### Post by fluctuatinganomaly on 2014-03-24
> **Mark Phelps said:**
> I've used the AMD .run files successfully but to do that, I had to make them executable.  You do this by opening a terminal and entering "sudo chmod +x <filename.run>", substituting the actual name of the run file for "<filename.run>".

I've tried that and I get some run out of it. It opens with:

Install Driver 13.251 on X.org 6.9 or later

Generate Distribution Specific Driver Package

Not sure which I need. But the top option ends in error, this is the install log file

> Supported adapter detected.

[Error]A previous installation of fglrx driver detected to be loaded.
User must uninstall existing fglrx driver 
or run install with force option. 
Forcing the installation is not recommended.

the generate distribution specific driver package option brings a list of packages SuSE Packages and RedHat Packages and at the bottom, Build Package for detected OS: Ubuntu/precise

this last option ends with:

> Package build failed!
Package build utility output:
./packages/Ubuntu/ati-packager.sh: 294: ./packages/Ubuntu/ati-packager.sh: debclean: not found
./packages/Ubuntu/ati-packager.sh: 295: ./packages/Ubuntu/ati-packager.sh: dpkg-buildpackage: not found
[Error] Generate Package - error generating package : Ubuntu/precise

~Matt

---

### Post by Yellow Pasque on 2014-03-24
Use this to clean up a previous failed install:
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
```
Make sure you have the dependencies needed to build a package:
```
sudo apt-get install build-essential cdbs dh-make dkms execstack dh-modaliases fakeroot libqtgui4
```

This is a pretty good guide: [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

---

### Post by monkeybrain20122 on 2014-03-24
Why don't you just install the flgrx driver in the repo? You do understand that if you install with the .run file everytime you have a kernel update you have to recompile the driver, don't you?

---

### Post by Yellow Pasque on 2014-03-24
> **monkeybrain20122 said:**
> Why don't you just install the flgrx driver in the repo?
It's probably older than a downloaded one.

> You do understand that if you install with the .run file everytime you have a kernel update you have to recompile the driver, don't you?
False. That's what dkms is for...

---

### Post by monkeybrain20122 on 2014-03-24
> **Temüjin said:**
> It's probably older than a downloaded one.
.

Then get one from xorg-edgers. Still a lot easier than installing from the .run file and OP is not very experienced.

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

> False. That's what dkms is for... 		 

I don't know, but it seems that you do have to recompile kernel module if you install a Nivida driver from the .run file. Maybe my info is outdated, haven't done it for a while.

---

### Post by fluctuatinganomaly on 2014-03-24
> **monkeybrain20122 said:**
> Why don't you just install the flgrx driver in the repo? You do understand that if you install with the .run file everytime you have a kernel update you have to recompile the driver, don't you?
I didn't realise this, no. I had seen it had been mentioned by someone else briefly in another post somewhere


> **monkeybrain20122 said:**
> Then get one from xorg-edgers. Still a lot easier than installing from the .run file and OP is not very experienced.

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)


Its true, I'm not. I figured once I found the correct file, it would simply be a case of running the file to install to get it installed. I don't get what the xorg it or anything :/


I have run the 
sudo sh /usr/share/ati/fglrx-uninstall.sh

but it says : sh: 0: Can't open /usr/share/ati/fglrx-uninstall.sh

I've had a look on the wiki, and as much as it makes sense, I don't know where or how the wget comes into it?
where does the link come from? what about the file I have, how can I find which is the most recent and up to-date?

The one I had "Activated" was "ATI/AMD proprietary FGLRX graphics driver" in the additional drivers dialog.
I have de-activated this one now, as well as run 
```
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*
```

But after running my .run file, I still receive a message saying there is an old version still installed that I have to remove before installing.
Unless I run with the --froce command.

I'll run through the wiki page from the beginning, hopefuly that will sort things out. But I'm not entirely sure on
everything thats been done with the commands

~Matt

---

### Post by monkeybrain20122 on 2014-03-24
You should just use the one from the Additional Driver dialogue. That is the one in the official repo. Never mind xorg-edgers because it seems that you just want to get the thing running but don't really care if you get the latest driver.

In any event, forget about the .run file unless you are looking for a learning experience (xorg-edgers has the latest if that is what you want)

---

### Post by fluctuatinganomaly on 2014-03-24
A learning experience is what I'm looking for, I do want to get it working, which I have I guess, but I also want to be using my hardware to its full extent. Maybe I'm wrong in thinking this, but I have deduced that the reason I can't increase my monitor screen size is related to my drivers?

I could increase the resolution on my main monitor to max while in windows, but now I cannot make it more than 1024 x 768 (4:3) as I receive these errors

> The selected configuration for displays could not be applied
requested position/size for CRTC 148 is outside the allowed limit: position=(800, 0), size=(1920, 1080), maximum=(1920, 1920)

> Failed to apply configuration: %s

GDBus.Error:org.gtk.GDBus.UnmappedGError.Quark._gnome_2drr_2derror_2dquark.Code3: requested position/size for CRTC 148 is outside the allowed limit: position=(800, 0), size=(1920, 1080), maximum=(1920, 1920)

I've just attempted a run through of the wiki page, and come into more errors any way, package build failed...

theres alot more, but it may be too much to post here unless absoloutely neccesary?

~Matt

-------EDIT

I have run 
```
sudo dpkg -i fglrx*.deb > dpkgError-Outlog.txt 2>&1
```
and
```
sh amd-catalyst-13.12-linux-x86.x86_64.run --buildpkg Ubuntu/maverick 2> errorlog.txt
```

to get the errors only into a file, error wise there isn't as much text, most is just output. But I have the errors available

---

### Post by Yellow Pasque on 2014-03-24
> **fluctuatinganomaly said:**
> I've had a look on the wiki, and as much as it makes sense, I don't know where or how the wget comes into it?
If you already have the file, then you don't need to use a wget command to download another one.

> But after running my .run file, I still receive a message saying there is an old version still installed that I have to remove before installing.
If you can't run the fglrx-uninstall program and you're still receiving this message, my best guess is that you have leftover cruft in /etc/ati
```
sudo rm -r /etc/ati
```

[QUOTE=monkeybrain20122]I don't know, but it seems that you do have to recompile kernel module if you install a Nivida driver from the .run file.[/QUOTE]
Installing from Nvidia's .run file is a bad idea because it doesn't generate packages, but you can still use dkms to avoid manual rebuild for new kernels.

---

### Post by fluctuatinganomaly on 2014-03-24
> **Temüjin said:**
> If you already have the file, then you don't need to use a wget command to download another one.

I was mainly just curious about where this link comes from with this :p

any ways,
```
 sudo rm -r /etc/ati 
```

returns: 
rm: cannot remove `/etc/ati': No such file or directory 

I'm gonna apologise for being a pain in the **** :p 

Also, I have edited some more info onto my previous post, mainly just that I have directed error text out into a seperate file for easy location of the errors I ran into during following the wiki

~Matt

---

### Post by fluctuatinganomaly on 2014-03-25
Making this post to bump the topic incase any one can provide any help.

I have de-activated the ATI/AMD proprietary FGLRX Graphics driver in the additional drivers dialoug and I can increase my screen resolution to maximum size no issues. I'm sure at this point I'm running with no drivers though?
If I activate the driver and reboot, my screen res drops again and if I try to increase it I get the error messages I have already posted.

I did install my graphics card drivers in windows, but I can't imagine they would work cross platform!?

I have tried to find more detailed information on my drivers, but I don't think I've found much.
I've run:
```
lshw -C video
lshw -C display
```
and got 
> *-display
       description: VGA compatible controller
       product: Barts PRO [Radeon HD 6850]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       **_configuration: driver=radeon latency=0_**
       resources: irq:95 memory:d0000000-dfffffff memory:fea20000-fea3ffff ioport:e000(size=256) memory:fea00000

I also ran lspci found the VGA line and then used 'grep -i' to search through the Xorg.0.log for any matches. I got ALOT of stuff, alot that I don't think is neccessary to this, but one thing I did get

```
grep -i radeon var/log/Xorg.0.log results
-------------


[    13.886] (II) LoadModule: "radeon"
**_[    13.886] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so_**
[    13.898] (II) Module radeon: vendor="X.Org Foundation"
**_[    13.925] (II) RADEON: Driver for ATI Radeon chipsets:_**
```

I know I'm new at this and probably don't have a clue what I'm doing, But the Underlined and Bold text suggests to me that the driver I have installed for my graphics card is "radeon"??

(all these commands were out put to a text file with cat >> file.txt so I have the info saved)

I'm just looking for some information on whats happening with my graphics drivers? whether I have any installed? if so, are they up-to-date? and again, if so, am I utilising my cards full capabilities? 
If I have none installed, why do the ATI/AMD proprietary drivers prevent me from utilising my maximum screen resolution?

~Matt

---

### Post by verymadpip on 2014-03-26
Hi Matt.
If you had no drivers you'd have nothing to look at :)

I expect you're  using the open source driver that comes with the kernel.
Have a look in synaptic package manager for "radeon" & see what stuff has a little green square next to it. You may, however, have to install synaptic.  It's in software centre or run 
```
sudo apt-get install synaptic
```

Is there a reason why the open source driver is not suitable for your needs? i.e. Can you do all that you want or need to do with the graphics working as they are without installing another driver?  If "yes, I can", then why install anything more?

As an aside; I had to install a proprietary AMD driver when I was messing about with the native Linux Steam client.  The one from the additional drivers dialogue worked okay for me though.
(I now use an Nvidia card BTW).

---

### Post by fluctuatinganomaly on 2014-03-26
Hey, thanks for the advice, I've installed synaptic and had a look, I have 4 green marked boxes related to the search "Radeon"
> 
libdrm-radeon1
Userspace interface to radeon-specific kernel DRM services -- runtime

radeontool
utility to control ATI Radeon backlight functions on laptops

xserver-xorg-video-ati-lts-raring
X.Org X server -- AMD/ATI display driver wrapper

xserver-xorg-video-radeon-lts-raring
X.Org X server -- AMD/ATI Radeon display driver

I guess I am running on the open source driver you mentioned??

And no, although this one does work for me in regards to my screen resolution. I do intend at some point to maybe play some games and such (after looking into if thats possible) from the steam client and others like Minecraft. I'm not sure if this current driver will give me the best display options for games and the likes, and like I said, really, I just want to try and get the most out of my card :/

~Matt

---

### Post by verymadpip on 2014-03-26
Hi Matt.
Yup, they'll be the open source drivers.

As far as I am aware your HD6xxx card should still be supported.  However, there seemed to be some weirdness around 12.04 & AMD drivers which involved AMD dropping support for HD2xxx (?), 3xxx, 4xxx series cards & an X server update.  It made the whole thing a bit of a minefield (for me at least).

I can't comment on Minecraft, & you will almost certainly need the proprietary driver if you're going to install the native Steam client.
I have no idea why the proprietary drivers are misbehaving for you & would like an answer to that myself out of sheer curiosity.

I think the person we need here is QIII.  He's very knowledgeable regarding AMD graphics.  I don't want to suggest a course of action in case I make matters worse for you.

There's always the "just wait for 14.04 & try again" option, or the "have a crack at 13.10 & see how you go on" option, but I'm fairly sure you'd rather not reinstall another OS, given that that seems to be what we've had you doing for the last few days.

---

### Post by fluctuatinganomaly on 2014-03-26
> **verymadpip said:**
> 
There's always the "just wait for 14.04 & try again" option, or the "have a crack at 13.10 & see how you go on" option, but I'm fairly sure you'd rather not reinstall another OS, given that that seems to be what we've had you doing for the last few days.

Honestly, not for the point of "try again" no. But I will hopefuly be upgrading to the new release when it comes out. Minecraft is working okay for me actually. No issues, other than getting it installed and installing mods etc :p

I guess for now, I'll leave it how it is and just see how I go with it. I'll leave the thread open, hopefuly this QIII will put his two cents in and be able to explain why the proprietary drivers are acting up.

Thanks for the info though, its nice to know that technology doesn't just hate me :p

~Matt

---

