---
title: "Broken dependencies"
date: 2013-12-29
forum: New to Ubuntu
---

### Post by RbMAC on 2013-12-29
I have just installed Edbuntu 12.04.3 LTS on an older Dell Inspiron 5100 laptop. (Dual boot with Windows XP). In my attempt to fix wireless  Ihave used commands:
Sudo apt-get remove bcmwl-kernel-source
Sudu apt-get install firmware-b43 installer b43-fwcutter
It keeps asking me to "Please insert the CD media disc labled Edubutu 12.04.3 Precise Pangolin Release i386 (20130820). After reinstlling disc and pushing Continue, nothing happens. 
Now my Ubuntu software Center wants me to  repair this and asks me to insert the same disc with same results.
This was my last step. I do not know how to use the -f commands.

```
madison@madison-Inspiron-5100:~$ sudo apt-get update
[sudo] password for madison: 
Ign cdrom://Edubuntu 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820) precise/main TranslationIndex
Ign cdrom://Edubuntu 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820) precise/multiverse TranslationIndex
Ign cdrom://Edubuntu 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820) precise/restricted TranslationIndex
Ign cdrom://Edubuntu 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820) precise/universe TranslationIndex
Ign cdrom://Edubuntu 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820) precise/main Translation-en_US
Ign cdrom://Edubuntu 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820) precise/main Translation-en
Ign cdrom://Edubuntu 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820) precise/multiverse Translation-en_US
Ign cdrom://Edubuntu 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820) precise/multiverse Translation-en
Ign cdrom://Edubuntu 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820) precise/restricted Translation-en_US
Ign cdrom://Edubuntu 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820) precise/restricted Translation-en
Ign cdrom://Edubuntu 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820) precise/universe Translation-en_US
Ign cdrom://Edubuntu 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820) precise/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                    
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [71 B]            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en
Fetched 71 B in 2s (25 B/s)
Reading package lists... Done
madison@madison-Inspiron-5100:~$ sudo apt-get clean
madison@madison-Inspiron-5100:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
madison@madison-Inspiron-5100:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 firmware-b43-installer : Depends: b43-fwcutter (>= 1:015-9) but it is not installed
E: Unmet dependencies. Try using -f.
madison@madison-Inspiron-5100:~$ -f
-f: command not found
madison@madison-Inspiron-5100:~$ sudo apt-get -f
apt 0.8.16~exp12ubuntu10.12 for i386 compiled on Jul 16 2013 18:00:58
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   autoremove - Remove automatically all unused packages
   purge - Remove packages and config files
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies
   changelog - Download and display the changelog for the given package
   download - Download the binary package into the current directory

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to correct a system with broken dependencies in place
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.
madison@madison-Inspiron-5100:~$ 
```

What is my next step?

---

### Post by claracc on 2013-12-29
You are asked to run the following command in xterm:
```
sudo apt-get -f install
```

Then you will be asked for password, introduce it and enter.

And see if the command fix the broken dependencies

---

### Post by Bucky Ball on 2013-12-29
You might need to take your CD out of the Software Sources. It is looking to that as a repository.

Update Manager>Settings button in the bottom left corner>Ubuntu Software tab. Make sure the CD is not included. 

Open Software Centre, search and install the b43 stuff from there and see if that fixes dependencies. Do you have Synaptic Package Manager? Even better, gives an option to fix broken packages.

* And what claracc said. Run that command. Once you're done, in a terminal, run:

```
sudo apt-get update
sudo apt-get upgrade
```

Post back the errors, if any.

---

### Post by RbMAC on 2013-12-29
I did everything and ran updates, cleared depencies and the installer package for the b43 driver and the utility for extracing Broadcom 43xx firmware b43-fwcutter are installed.
Now how do i I use these to enable my wireless card?

---

### Post by Bucky Ball on 2013-12-29
Please show the output of:

```
sudo lshw -C network
```

When you left click on the network icon, do you see any available networks?

---

### Post by RbMAC on 2013-12-29
Left Click on network icon shows no networks. For a test I attached a USB wireless adapter. My local network showed up and I could connect but I could not open a webpage in FireFox.
 sudo lshw -C network produced:
madison@madison-Inspiron-5100:~$ sudo lshw -C network
[sudo] password for madison: 
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:ae:21:7e
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.103 latency=32 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:7 memory:faffe000-faffffff
  *-network:1
       description: Network controller
       product: BCM4309 802.11abg Wireless Network Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:11 memory:faffc000-faffdfff
madison@madison-Inspiron-5100:~$

---

### Post by Bucky Ball on 2013-12-30
When you check in Additional Drivers, do you have the b43 driver and the STA? If so, try the STA and reboot. Also, have a look at this:

[http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers-bcm43xx](http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers-bcm43xx)

Try the second answer down with '33' next to it then under the instructions for 12.04 and below. I'm not sure this:

```
driver=b43-pci-bridge
```

Is the right one for that card.

---

### Post by RbMAC on 2013-12-31
I attempted to load STA driver and resulted in screen dump crash. How can I recover from this. I can boot up to Ubuntu for about 2 minutes before it crashes. Can I resolve this in safe mode and go to root? I tried the fix broken packages option but no go. 
Below is a screen shot of the crash dump. Paste the link into your browser.

[http://s1350.photobucket.com/user/Randall_McFarlane/media/image_zps9087d702.jpg.html](http://s1350.photobucket.com/user/Randall_McFarlane/media/image_zps9087d702.jpg.html)

 Thanks for all of your continuing help. I am brand new in trying to learn ubuntu installations on all of my old pentium 4 laptops.

---

### Post by Bucky Ball on 2014-01-01
When you get to Ubuntu for two minutes perhaps disable that STA driver again for the moment and see if that stops the crashing. Perhaps something is conflicting with that and another driver needs to be blacklisted.

---

### Post by RbMAC on 2014-01-03
When I get back from vacation Jan 6, I'll try that.

---

### Post by RbMAC on 2014-01-07
Unable to remove Broadcom STA Linux driver via Ubuntu software Center. It crashes before the removal process completes. How can I do this in Safemode via root prompt?

---

### Post by Bucky Ball on 2014-01-07
*Deleted duplicate.*

A simple 'bump' every 24 hours hours is fine.

---

