---
title: "Installing applications"
date: 2020-08-15
forum: New to Ubuntu
---

### Post by brdmartin on 2020-08-15
Hello,
Just installed Kubuntu 2 days ago, and working on getting things set up. I want to install some additional applications, such as GIMP and Musescore. Finally figured out that the included application to install software is called Discover Software Center. However, when I try to start it up, only the outline of a window appears before the program crashes. On a daemon program referencing the crashed program, it made reference to a version 16.xx. I ran across a post somewhere that said that this application has often been problematic. So my question is - how do I install applications? It would be nice if Discover or some sort of equivalent program could be used. I found the KDE's Applications website, but haven't had a lot of luck with that so far.
Thanks!
Brian

---

### Post by fragglebliss on 2020-08-16
Just use apt from the command-line.

---

### Post by drpjkurian on 2020-08-16
I suggest you reinstall 'Discover' using the muon package manager.
Another alternative is to reinstall the software using the command line. Open the Konsole and type the command
> sudo apt-get update
sudo apt-get install plasma-discover
Let us know whether it helped you.

---

### Post by monkeybrain20122 on 2020-08-16
Discover works well here, however muon is kind of broken (search not working at all and it appears to be a long standing bug), so I uninstalled muon and installed synaptic. Discover is a good software store application for new users, I think it is better than gnome software. IMO it is not very helpful to tell new users to use apt command exclusively to install software. How do they know the name of the software in the first place without more cryptic commands? I am setting up kubuntu 20.04 for a friend who is not a geek, I want to make everything easy and simple for him.

---

### Post by CelticWarrior on 2020-08-16
Before reinstalling stuff and/or installing new stuff, make sure the system is up-to-date:

```
sudo apt update
sudo apt full-upgrade
```

Please post here any error messages.

---

### Post by Impavidus on 2020-08-16
It may help if you told us which version of Kubuntu you installed (and don't say "the latest version", because you wouldn't be the first who installed an old version thinking it were the latest). CelticWarrior's commands will actually tell that. Now, I could give you one command with apt that will install both gimp and musescore, but that won't help you the next time you want to install something.

---

### Post by brdmartin on 2020-08-16
Good point on not saying "the latest version" I know that there are new versions all the time. It's 20.04, as far as I can tell, though I don't know how to verify this. I ran the scripts you suggested DrPJ & Celticworrior. on the "sudo apt upgrade" it looks like it might have done something, but on the other ones the result was 0 installed and 0 upgraded. Tried to run discover again after doing these, and got the same result.
Thanks for the help so far :-)

---

### Post by brdmartin on 2020-08-16
This can kinda be confusing. I know I installed a 20.xx version, but now I'm getting a message "Upgrading Ubuntu 16.04.7 to version 18.04. I'll put in an update once this finishes installing.

---

### Post by CatKiller on 2020-08-16
> **brdmartin said:**
> It's 20.04, as far as I can tell, though I don't know how to verify this.

```
cat /etc/lsb-release
```

---

### Post by TheFu on 2020-08-16
**lsb_release -a** is the command
```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04.1 LTS
Release:        20.04
Codename:       focal
```

On a different machine, 
```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.7 LTS
Release:        16.04
Codename:       xenial
```

It is best to use a fresh install for each LTS, not an upgrade install. This cleans out a little cruft and ensures that deprecated settings aren't carried forward ... then broke in 2 yrs when the deprecation becomes unsupported. With 16.04, systemd-resolved was introduced along the .2 - .3 - .4 upgrades and it broke DNS on most of my systems. The ones where it broke were those upgraded from 10.04 --> 12.04 --> 14.04 --> 16.04.  Best to do a fresh install with each new LTS.

```
sudo apt update
``` needs to be run within about 6 hrs of any software upgrade or installation tasks. This ensures the repository on each system knows the current information for each package in each of the configured repositories.  For .rpm-based distros, the update is automatic.  By default, the Ubuntu system should update that list daily, automatically, if there is an internet connection.  It is possible to disable that through settings in both config files or through a GUI.  Because each "flavor" of Ubuntu tends to have slightly different software GUIs, it is hard for us to guess what you may be seeing with knowing the DE and specific release being used.

**inxi -bz** is the easiest way to provide that data that I know.
```
$ inxi -bz
System:    Host: hadar Kernel: **4.15.0-112**-generic x86_64 (64 bit)
**           Desktop: Openbox 3.6.1 Distro: Ubuntu 16.04 xenial**
Machine:   Mobo: ASUSTeK model: ROG STRIX B450-F GAMING v: Rev 1.xx
           Bios: American Megatrends v: 2801 date: 09/18/2019
CPU:       Hexa core AMD Ryzen 5 2600 Six-Core (-HT-MCP-) speed/max: 1342/3400 MHz
Graphics:  Card: NVIDIA GP108 [**GeForce GT 1030**]
           Display Server: **X.Org 1.19.6** driver: **nvidia** Resolution: **1920x1200@59.95hz**
           GLX Renderer: GeForce GT 1030/PCIe/SSE2 GLX Version: 4.6.0 NVIDIA 430.64
Network:   Card: **Intel I211 Gigabit** Network Connection driver: **igb**
Drives:    HDD Total Size: 1012.2GB (58.2% used)
RAID:      Device: 1: /dev/md127 - inactive
Info:      Processes: 559 Uptime: 21 days Memory: 18658.8/32160.7MB
           Client: Shell (bash) inxi: 2.2.35 

```
It tells the most important things. I've bold'ed the usual trouble items. There are options to get much more data using that same command. It is worth having install now, before you need it for troubleshooting.  Same of **lshw**.  Install both using **sudo apt install  lshw inxi** in any terminal.

---

### Post by Impavidus on 2020-08-16
> **brdmartin said:**
> ... I don't know how to verify this. I ran the scripts you suggested DrPJ & Celticworrior. on the "sudo apt upgrade" it looks like it might have done something, ...If you show us the output from those commands, we may be able to tell. It's text, you can copy-paste it to the forum.

> **brdmartin said:**
> This can kinda be confusing. I know I installed a 20.xx version, but now I'm getting a message "Upgrading Ubuntu 16.04.7 to version 18.04. I'll put in an update once this finishes installing.
Yeah, that must be confusing. If you installed 20.04 (which is indeed the latest version), you can't upgrade from 16.04 (which is the oldest supported version) to 18.04.

---

### Post by brdmartin on 2020-08-16
The update took quite a while, and now discover works just fine. Learned some useful things here though, thanks to ya'all.
Brian

---

### Post by math492m on 2020-08-18
sudo apt install [PROGRAMNAME]
or
sudo apt-get install [PROGRAMNAME]

both in terminal

---

### Post by drpjkurian on 2020-08-18
Happy to hear that the issue is resolved. Please mark the thread solved.

---

