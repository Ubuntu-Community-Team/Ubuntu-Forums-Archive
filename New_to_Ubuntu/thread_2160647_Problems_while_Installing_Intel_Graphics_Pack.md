---
title: "Problems while Installing Intel Graphics Pack"
date: 2013-07-07
forum: New to Ubuntu
---

### Post by TynieTinker on 2013-07-07
I'm new to the whole Linux OS scene. I chose to run Ubuntu 13.04, at least thats what I recall. :P The whole purpose of me partitioning my hard drive was to migrate all my games onto Ubuntu, so Window's stops running so hard. So step one, is done. I installed playonlinux along with Wine to start installing my main game, Rift. All that was a success after some minor glitches that I researched and figured out on my own, eventually. I finally go to play my game, the loading screen and videos flash obscenely, but I've read that that was expected, so thats fine with me. So when I finally log in to my character/account I recieved nothing other than disappointment after my days of figuring it all out. I'm staring at a black screen with only the GUI appearing on screen.

So I told a techy friend of mine what happened, and he suggested that it was something to do with the graphics. He sends me a link to install the Intel(R) Graphics Installation Pack. This is where all my problems started. I go to install it and I got some errors and failed to download yada yada. Along with this process I removed playonlinux and wine because  the errors said  something about them... That removed two of the errors. So I searched it all up and tried a solution I thought would work. I posted the gist of it in another thread. 

> **TynieTinker said:**
> I'm new to ubuntu, and I had the same  problem while I was trying to install the Intel Graphics pack. But  instead of being simple for me, I got this when I tried running the  suggested commands:
E: Unable to lock the download directory

So I browsed around online, came across another forum post that solved  my issue. So I thought I'd share it on this thread, to save others  encountering the same problem having to search for more answers. :smile:
 I found out that running this:
```
sudo apt-get autoremove && sudo apt-get clean && sudo apt-get autoclean
```

In a fresh terminal, seemed to solve my issues to be able to run:
```
sudo -i
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
```

With no issues, Like **abhicr **suggested.

Thanks for the help. :smile:


Now, I ran the Intel Graphics Installer again, But I still get an issue, and I'm now calling for help. This is exactly what I get:
Performing Diagnostics, Everythings Okay, But Upgrading System is when it faulters.
> updating package cache failed
W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/raring-security/Release.gpg)  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
, W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/raring/Release.gpg](http://archive.canonical.com/ubuntu/dists/raring/Release.gpg)  Something wicked happened resolving 'archive.canonical.com:http' (-11 - System error)
, E:Some index files failed to download. They have been ignored, or old ones used instead.


Please, Can someone help?!?! SAVE MY SOUL, I don't know what to do!!

I solved one problem, but got another.

PS. Here's all my deets:

tyson@Tyson-Satellite-L650:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Qualcomm Atheros AR8152 v1.1 Fast Ethernet (rev c1)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

---

### Post by mastablasta on 2013-07-07
intel drivers are already installed and come with kernel. i doubt this is a driver's issue. t is porbably the programmes issue workignin wine. depends on what the output is if you run the game from terminal.

furthermore sicne you are running Ubuntu you should knwo that Unity in 13.04 is 3D acelerated. i.e. it's drawing power form your GPU to draw itself. it can also interfere with fullscreen and graphics intensive programmes (such as for example games in wine). there should be an option somewhere to somehow disable the desktop acceleration when running fullscreen games. i know  there is one in Kubuntu. anyway for playsing games you might want to try to install XFCE o LXDE and switch to these two desktops when running your game (these two desktops and a few others are lighter on resources and not 3D accelerated). there is even a distribution based on Ubuntu that does that on the fly. otherwsie it's log out, select different desktop and log back in.


aynway if you want to install intel drivers the easiest way is to add PPA to your sources in software center, refresh the software center so that driver package from PPA appears in the software center and then install the new package from software center. oh and here is the link to Xorg edgers PPA: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

instructions on how to isntall are in the link (both terminal and GUI)

---

### Post by TynieTinker on 2013-07-07
> **mastablasta said:**
> intel drivers are already installed and come with kernel. i doubt this is a driver's issue. t is porbably the programmes issue workignin wine. depends on what the output is if you run the game from terminal.

furthermore sicne you are running Ubuntu you should knwo that Unity in 13.04 is 3D acelerated. i.e. it's drawing power form your GPU to draw itself. it can also interfere with fullscreen and graphics intensive programmes (such as for example games in wine). there should be an option somewhere to somehow disable the desktop acceleration when running fullscreen games. i know  there is one in Kubuntu. anyway for playsing games you might want to try to install XFCE o LXDE and switch to these two desktops when running your game (these two desktops and a few others are lighter on resources and not 3D accelerated). there is even a distribution based on Ubuntu that does that on the fly. otherwsie it's log out, select different desktop and log back in.


aynway if you want to install intel drivers the easiest way is to add PPA to your sources in software center, refresh the software center so that driver package from PPA appears in the software center and then install the new package from software center. oh and here is the link to Xorg edgers PPA: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

instructions on how to isntall are in the link (both terminal and GUI)

I knew that the drivers were already installed, but I figured it wouldn't hurt to give it a try. I did my research before getting Linux, I read online that Ubuntu would be the best platform for games. Right now I'm taking your advice in looking for the option to disable the desktop acceleration while running full screen applications. I'll edit this comment letting you know if I've found it or not. Thanks. :)

EDIT:I found the Unity Tweaker in the software centre.

---

### Post by dannyboy79 on 2013-07-08
> **TynieTinker said:**
>  I read online that Ubuntu would be the best platform for games. .
that's not a very specific statement, it will all depend on what games you're talking about. currently there is NOT a single AAA game title developed natively for Linux or even Ubuntu. So if you're fine with playing indie titles and or playing popular games within WINE then you should be alright assuming your title is supported to run "well" in either of those environments.

Which is intel GPU are you running? You can use this command to check

```
lshw -class display
```

---

### Post by mastablasta on 2013-07-08
> **dannyboy79 said:**
> that's not a very specific statement, it will all depend on what games you're talking about. currently there is NOT a single AAA game title developed natively for Linux or even Ubuntu. 

where have you been living? under a rock? :-P

what about Half life 1 & 2, portal (well these might be beta), team fortress 2, l4d, l4d2 (these 2 are AAA but a bit dated), then there is award winning Minecraft,a couple of really good indie games (psychonauts well and many others in indie bundles...)...plenty work well in wine too (skyrim for example), Wow etc.

well i do not know the latest top titles (other than COD and BF which are indeed windows only), but there is plenty of a bit older games that work well in linux. pelnty of steam ones are getting a port, whiel some were already ported. in fact Valve is planning a linux based console.

edit: there is nothign wrong with installing the latest opensource drivers it is just much easier and safer to do it using a PPA. that was my previous point.

---

