---
title: "wth am i doing wrong?  belana etcher installation on 20.04"
date: 2024-10-06
forum: New to Ubuntu
---

### Post by cryofreeze666 on 2024-10-06
System:
  Kernel: 5.15.0-122-generic x86_64 bits: 64 Desktop: Gnome 3.36.9 
  Distro: Ubuntu 20.04.6 LTS (Focal Fossa) 
Machine:
  Type: Desktop Mobo: Gigabyte model: GA-78LMT-USB3 6.0 v: SEx 
  serial: <filter> BIOS: Award v: F2 date: 11/25/2014 
CPU:
  6-Core: AMD FX-6300 type: MCP speed: 1401 MHz min/max: 1400/3500 MHz 
Graphics:
  Device-1: NVIDIA driver: nvidia v: 470.256.02 
  Display: x11 server: X.Org 1.20.13 driver: nvidia 
  unloaded: fbdev,modesetting,nouveau,vesa tty: N/A 
  OpenGL: renderer: NVIDIA GeForce RTX 3060/PCIe/SSE2 
  v: 4.6.0 NVIDIA 470.256.02 
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  driver: r8169 
Drives:
  Local Storage: total: 1.14 TiB used: 57.42 GiB (4.9%) 
Info:
  Processes: 278 Uptime: 9h 46m Memory: 23.45 GiB used: 2.23 GiB (9.5%) 
  Shell: bash inxi: 3.0.38 



i am trying to install balena etcher 

1st i went here [https://phoenixnap.com/kb/etcher-ubuntu](https://phoenixnap.com/kb/etcher-ubuntu)

2nd i went here [https://askubuntu.com/questions/1520383/how-to-run-balena-etcher-on-ubuntu-20-04](https://askubuntu.com/questions/1520383/how-to-run-balena-etcher-on-ubuntu-20-04)

3rd i came here and only found a post about an error thats not the same as mine

this is how the installation from curl went:
a@a-GA-78LMT-USB3-6-0:~$ sudo apt install curl
[sudo] password for a: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
curl is already the newest version (7.68.0-1ubuntu2.24).
curl set to manually installed.
The following packages were automatically installed and are no longer required:
  gir1.2-goa-1.0 libfwupdplugin1 libxmlb1
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
a@a-GA-78LMT-USB3-6-0:~$ curl -1sLf 'https://dl.cloudsmith.io/public/balena/etcher/setup.deb.sh' | sudo -E ba
sudo: ba: command not found
a@a-GA-78LMT-USB3-6-0:~$ curl -1sLf 'https://dl.cloudsmith.io/public/balena/etcher/setup.deb.sh' | sudo -E 
usage: sudo -h | -K | -k | -V
usage: sudo -v [-AknS] [-g group] [-h host] [-p prompt] [-u user]
usage: sudo -l [-AknS] [-g group] [-h host] [-p prompt] [-U user] [-u user]
            [command]
usage: sudo [-AbEHknPS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p
            prompt] [-T timeout] [-u user] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p
            prompt] [-T timeout] [-u user] file ...
a@a-GA-78LMT-USB3-6-0:~$ sudo apt update
Hit:1 [https://repo.steampowered.com/steam](https://repo.steampowered.com/steam) stable InRelease
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal InRelease                      
Hit:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates InRelease              
Hit:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-backports InRelease            
Hit:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease       
Ign:2 [https://dl.bintray.com/etcher/debian](https://dl.bintray.com/etcher/debian) stable InRelease            
Err:7 [https://dl.bintray.com/etcher/debian](https://dl.bintray.com/etcher/debian) stable Release
  404  Not Found [IP: 18.232.172.199 443]
Reading package lists... Done
E: The repository 'https://deb.etcher.io stable Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
a@a-GA-78LMT-USB3-6-0:~$ sudo apt install balena-etcher-electron
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package balena-etcher-electron

using the debian repository.:

a@a-GA-78LMT-USB3-6-0:~$ echo "deb [https://deb.etcher.io](https://deb.etcher.io) stable etcher" | sudo tee /etc/apt/sources.list.d/balena-etcher.list
[sudo] password for a: 
deb [https://deb.etcher.io](https://deb.etcher.io) stable etcher
a@a-GA-78LMT-USB3-6-0:~$ sudo apt-key adv --keyserver hkps://keyserver.ubuntu.com:443 --recv-keys 379CE192D401AB61
Executing: /tmp/apt-key-gpghome.9I4BRsCBlY/gpg.1.sh --keyserver hkps://keyserver.ubuntu.com:443 --recv-keys 379CE192D401AB61
gpg: key 379CE192D401AB61: "Bintray (by JFrog) <bintray@bintray.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
a@a-GA-78LMT-USB3-6-0:~$ sudo apt update
Hit:2 [https://repo.steampowered.com/steam](https://repo.steampowered.com/steam) stable InRelease                   
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal InRelease                    
Hit:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease             
Hit:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates InRelease            
Hit:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-backports InRelease
Ign:1 [https://dl.bintray.com/etcher/debian](https://dl.bintray.com/etcher/debian) stable InRelease
Err:7 [https://dl.bintray.com/etcher/debian](https://dl.bintray.com/etcher/debian) stable Release
  404  Not Found [IP: 18.214.194.113 443]
Reading package lists... Done
E: The repository 'https://deb.etcher.io stable Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
 

i mean have i forgotten how to copy and paste?  what is going on that i am missing because of lack of experience?

---

### Post by yancek on 2024-10-06
I've never used Etcher so don't have any experience downloading and installing it but have you gone to the Etcher site and selected to download and install the .deb file for version 1.19.21`?

[https://github.com/balena-io/etcher/releases/](https://github.com/balena-io/etcher/releases/)

There are some improper/incorrect usage of the sudo command as you can see in your output.  Not sure where those came from, the links you posted?  A starting point would be to review your /etc/apt/sources.list file, particularly anything related to etcher.  If you are not familiar with the use of this file, you could post its contents here for other members to review.

---

### Post by TheFu on 2024-10-06
Let's step back a bit.

Seems like you want to install a new Ubuntu OS. Great!

20.04 standard support ends in 6 months, so that is NOT the release to be installed today.  Go with 22.04 or 24.04 to have at least 2 more years.  Also, don't bother with the different DE flavors of 20.04. Support for those ended in 2023.  So - pick a newer LTS release that will have more than 6 months of support remaining and stay away from non-LTS releases.  Do yourself a favor.  

BTW, DE Flavors of 22.04 support will end in 2025, so only the Gnome DE of 22.04 should be installed today, not KDE, LXQt, Mate, or XFCE ubuntu flavors.  Only the bloated Gnome DE version of 22.04 will have 3 more years of standard support.  Perhaps 24.04.1 flavors are your best option today?  Only you can decide.

Why bother with **Etcher** at all?  It is bloated due to Electron.  Just download the ISO you want directly then use any tool already on the system to copy the bits exactly from  file.iso to the exact USB flash device you want to use to install from.  **cp** can be used.  **dd**, **ddrescue**, **cat** can all be used.  **Rufus** is popular, but you'll need a new version to handle new ISOs.  Or you could install **Ventoy** onto the flash drive, then simply copy the different ISO files to the Ventoy ISO directory (as many as will fit) to have 1 - 100 different distro ISO flavors to try or install.

Don't get hung up on Etcher, if that is too complicated for your needs or isn't working.  There are lots of other possible options to achieve the goal.  In business, don't they call that a "pivot"?

---

### Post by cryofreeze666 on 2024-10-06
> **TheFu said:**
> Let's step back a bit.

Seems like you want to install a new Ubuntu OS. Great!

20.04 standard support ends in 6 months, so that is NOT the release to be installed today.  Go with 22.04 or 24.04 to have at least 2 more years.  Also, don't bother with the different DE flavors of 20.04. Support for those ended in 2023.  So - pick a newer LTS release that will have more than 6 months of support remaining and stay away from non-LTS releases.  Do yourself a favor.  

BTW, DE Flavors of 22.04 support will end in 2025, so only the Gnome DE of 22.04 should be installed today, not KDE, LXQt, Mate, or XFCE ubuntu flavors.  Only the bloated Gnome DE version of 22.04 will have 3 more years of standard support.  Perhaps 24.04.1 flavors are your best option today?  Only you can decide.

Why bother with **Etcher** at all?  It is bloated due to Electron.  Just download the ISO you want directly then use any tool already on the system to copy the bits exactly from  file.iso to the exact USB flash device you want to use to install from.  **cp** can be used.  **dd**, **ddrescue**, **cat** can all be used.  **Rufus** is popular, but you'll need a new version to handle new ISOs.  Or you could install **Ventoy** onto the flash drive, then simply copy the different ISO files to the Ventoy ISO directory (as many as will fit) to have 1 - 100 different distro ISO flavors to try or install.

Don't get hung up on Etcher, if that is too complicated for your needs or isn't working.  There are lots of other possible options to achieve the goal.  In business, don't they call that a "pivot"?


1) actually no, i want to be able to burn minerstat o.s. direct to my m2 ssd, for my crypto miner.  so i purchased an enclosure in order to do so.  been using ubuntu 20.04 for about 3 months now even upgraded to 22.04.  after problems with work stations "magically" opening and attaching my web browsers to them and never returning, i went back to 20.04.  i've never had anything but trouble with beta programs since my knowledge of linux is so infinitesimally small.  

2) i still don't know which flavor i like best, this version is the only flavor i can currently stomach out of all the flavors and different versions mostly because i'm a huge sudoku and mahjong nut. 

3) why etcher, because i'm a dumb ass noob who typed something like best image burner for linux in google, read a few of the reviews.  and here i am. everything in that paragraph about iso, went clean over my head, and bein bald and wearing sneakers didn't help me any either.

4)  a) hung up on etcher, not really, but i am trying to learn haven't used it ever, don't know if i even like it, i was a huge imgburn fanso all the iso's of ubuntu are on disks.  
     b) if i can't solve the problem i'm having with etcher, what happens if the same problem happens with a different program?   that's the reason i posted this.  what i had copied and pasted, to find       out what was wrong with the coding i had copied to the terminal.

5) this particular computers job will be this quite simply, accessing dashboards of crypto programs, crypto exchanges, and gaming (rom rpg's  (dungeon lords and pool of radiance) to strategy (original starcraft) shooters (unreal tournament series) on disk mostly  so if you have any recommendations of flavors of linux that i have yet to hear of and try, recommend away.  so far all i know about ubuntu is i'm not completely sure about it yet.  i had found a version of debian i liked but forgot which one it was, and it was one of the first i tried. it had so many skins.

---

### Post by grahammechanical on 2024-10-07
> E: The repository 'https://deb.etcher.io stable Release' does not have a Release file.

This is a third party repository and the maintainer of the repository has not updated it to be used with the version of Ubuntu you are using. The instructions you followed to install Etcher refer to Ubuntu 18.04. You are using Ubuntu 20.04. It seems that the Etcher developers have not updated their repository to work on Ubuntu 20.04. See this link.

[https://etcher.balena.io/](https://etcher.balena.io/)

I do not see any download applicable for Ubuntu. There is this link:

[https://github.com/balena-io/etcher?d_id=4b1368e7-b4e5-49e8-b8fa-f41926b29a37&s_id=1728300973962#debian-and-ubuntu-based-package-repository-gnulinux-x86x64&d_id=4b1368e7-b4e5-49e8-b8fa-f41926b29a37&s_id=1728300973962](https://github.com/balena-io/etcher?d_id=4b1368e7-b4e5-49e8-b8fa-f41926b29a37&s_id=1728300973962#debian-and-ubuntu-based-package-repository-gnulinux-x86x64&d_id=4b1368e7-b4e5-49e8-b8fa-f41926b29a37&s_id=1728300973962)

Now scroll down.

It is at this point that I would give up as seeing the process too complicated, But let us continue. Under the heading **Installers** I see this:

> Refer to the [downloads page]("https://balena.io/etcher") for the latest pre-made installers for all supported operating systems.

I click the downloads page link and I am back to where we started from. Not very user friendly.

I have found Ubuntu's Startup Disk Creator to be easier to use. I have also found MK-USB to be excellent and quick. Mk-USB is multi-functional and that does make it complicated.

[URL="https://help.ubuntu.com/community/mkusb"]https://help.ubuntu.com/community/mkusb

[/URL]I have found the Startup Disk Creator would not even recognise the existence of a Debian ISO image but MK-USB had no problem burning the ISO image to USB drive.

Regards

---

### Post by Holger_Gehrke on 2024-10-07
If you go to the github page for balena etcher you'll find an AppImage on the [releases page]("https://github.com/balena-io/etcher/releases"). I personally like AppImages for programs that are not officially part of the distribution I run. Just make the file executable and put it in a directory where the system will look for executables - ~/.local/bin/ is a good option - and you're done. The only disadvantage I can see for AppImages is that they are not updated by the package manager.

Holger

---

### Post by Norm24 on 2024-10-07
Etcher can be found here:
[https://github.com/balena-io/etcher/releases/](https://github.com/balena-io/etcher/releases/)

---

### Post by TheFu on 2024-10-07
+1 for using AppImages.
Download, run. Be happy.

Just be certain to get the AppImage file from a reputable source, typically the team behind the software.  Though there are lots of sketchy software around mining and crypto-stuff.  I consider all of that to be high risk activities like spending time on the darkweb looking for illegal services and drugs.  I'd never mix anything related to crypto-stuff with anything else.  As The Offspring say - "Gotta keep them separated." Ref: [https://www.youtube.com/watch?v=1jOk8dk-qaU](https://www.youtube.com/watch?v=1jOk8dk-qaU)

---

### Post by cryofreeze666 on 2024-10-07
i like that song, 

ok, so if etcher hasn't been updated to this version, which isn't supported any longer.  i still need to be able to load the operating system that was recommended as middle of the road for beginners (i have experience mining in windows but no experience with debian)  that computer has m2 drivesa 250 gig for o.s. and a 2 tb for files and any cache related usage.  so i need a iso burner that will burn to thumb drives so i can load the os directly onto the m2 in the enclosure.  

so ubuntu 2.24 is ubuntu 18.04?  wait what, why?

fu, you recommended some flash drive burners before, i'm looking for the post, i think it was in this thread.

also, thefu, i went to look at rufus, that you recommended above.  it looks like what i actually need, but the main page is full of windows downloads, and i'm not sure how to identify the linux distros for the program on github or fosshub, is there a way?  i'm not really interested in portable, i will also use this particular computer for burning the os's for the 2 new computers i plan to schedule building this year (within next 12 months), after i get the miner os system up and running make sure it's stable, then wipe windows out of the other 8.  so might as well have a permanent program.  ts rufus going to need to be loaded with wine?

---

### Post by cryofreeze666 on 2024-10-07
SOLVED BECAUSE it seems belana etcher is only compatible with 18.04, so i intend to try a different iso burner.

---

### Post by 1fallen on 2024-10-07
Not so, I'm running 24.10 now with 1.19.21, but with zip file.
The code to use on Zip file is:
```
./balena-etcher --no-sandbox

```

If you need help just ask.
BTW The Appimage will run as:
```
sudo '/home/me/balenaEtcher-1.19.21-x64.AppImage' --no-sandbox --disable-gpu-sandbox --disable-seccomp-filter-sandbox

```
Using these switches is not recommended though.  Frankly, I trust my  AppImage and I just need the tool to work... so, no sandbox for me!

Canonical like to keep us on our toes, and the fact Etcher is running an outdated Electron.

---

### Post by grahammechanical on 2024-10-07
Now you are confusing me.

>  i still need to be able to load the operating system that was recommended as middle of the road for beginners

You are using Ubuntu 20.04, are you not? I started using Ubuntu 17 years ago because it had a reputation as being friendly to beginners. I am even more convinced that Ubuntu is designed for the beginner whilst making it possible for the expert to do expert things.

You had problems trying to install a program from a private software repository because the maintainers of that repository had not migrated the repository from Ubuntu 18.04 to 20.04. You want to burn an ISO image to a USB memory stick. Ubuntu 20.04 has such a utility. It is called Startup Disk Creator.

If you are still decided on installing Etcher on Ubuntu 20.04 then install it as an Appimage. The developers of Etcher offer an Appimage. I am guessing that it is their chosen distribution neutral method for distributing Etcher.

Every two years the developers of Ubuntu release a version that has 5 years support for security updates and other stuff. They are called Long Term Support (LTS) releases. Versions of Ubuntu released every 6 months in the intervening 2 years only get 9 months support. We do not recommend installing those releases. They are called standard releases. There is nothing wrong with them. They are fully functional. It is that after 9 months a user will have to upgrade to the next release of Ubuntu. And so on until they reach an LTS version.

Ubuntu 18.04 was LTS. Next came 20.04 LTS. That was followed by 22.04 LTS and now the latest LTS is 24.04.

It is all your decision to make. Decide which utility to use to burn an ISO image to USB memory stick and then think about backing up your data and planning to do an online upgrade to Ubuntu 22.04 LTS. It is possible to get a 5 year extension of support for Ubuntu 20.04. Help doing that is a different question for a different Ubuntu Forum thread.

[https://ubuntu.com/pro](https://ubuntu.com/pro)

It is free for the user with up to 5 machines. More than that and we have to pay for a subscription.

By the way, some of us recommend not doing an online upgrade but a fresh install instead. Again, it is all down to user choice.

Regards

---

### Post by TheFu on 2024-10-07
> **cryofreeze666 said:**
> 
fu, you recommended some flash drive burners before, i'm looking for the post, i think it was in this thread.

also, thefu, i went to look at rufus, that you recommended above.  it looks like what i actually need, but the main page is full of windows downloads, and i'm not sure how to identify the linux distros for the program on github or fosshub, is there a way?  i'm not really interested in portable, i will also use this particular computer for burning the os's for the 2 new computers i plan to schedule building this year (within next 12 months), after i get the miner os system up and running make sure it's stable, then wipe windows out of the other 8.  so might as well have a permanent program.  ts rufus going to need to be loaded with wine?

The ideas that we "burn" and iso to a flash drive is left over from when we "burned" ISOs to empty optical media like CDROM and DVDs.  It isn't really a "burn". It is just copying the bits from A ---> B unmolested.  Any program that will copy bits from A ---> B unmolested can be used. These specialized "ISO burning" programs are there just to protect noobs from accidentally picking the wrong storage.  I haven't used any of them in over 5 yrs, perhaps 10. Hard to remember.  I use **cp** myself.  Yes, the basic Unix cp program that is on every Unix/Linux/OSX machine in the world. That 'cp' program.  The only difficult part is knowing the correct target device.

I haven't used Rufus since, maybe, 2010. IDK.  I don't really create ISO boot flash drives all that often.  I make one every 2-3 yrs and use that same one for all my physical system installs, which I do seldom.  Most of my installs are into virtual machines, which expect the ISO file directly.

I find all those "ISO flash drive burning tools" overly complex for the task.  I'm easily confused by GUI programs. Sorry.

Anyway, none of this really is helpful to you.  Probably best if you read what others in this thread suggest, pick one, and follow their suggestions.

---

