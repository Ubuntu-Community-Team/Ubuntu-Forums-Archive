---
title: "How to enable laptop wireless"
date: 2011-10-25
forum: New to Ubuntu
---

### Post by woods050 on 2011-10-25
Hi everyone, 

I'm new to ubuntu world but attracted by its freedom of use thus have installed my desktop with the 11.04 version which I recently upgraded to 11.10 and found very pleasant to use.

I'm tired of using pirated o/s and have decided to install ubuntu to my laptop as well.  Everything looks find at first but the wireless connection could not be established.  I've tried several solution posted by others on the net but to no avail.  My laptop is Lenovo 3000 G230 hope that someone out there is able to help.  Million thanks.

In addition, I'm able to connect to the web via lan cable.

---

### Post by computerandu on 2011-10-25
Welcome to Ubutnu...

It is very normal to have some problems with wireless...happens with the users of all levels...

Have you gone through this post: [http://www.computerandyou.net/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/](http://www.computerandyou.net/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/)
or this: [http://www.computerandyou.net/2011/05/24/how-to-solve-no-wireless-network-in-ubuntu-11-04-centrino-wireless-n-1000/](http://www.computerandyou.net/2011/05/24/how-to-solve-no-wireless-network-in-ubuntu-11-04-centrino-wireless-n-1000/)

Revert back if those post doesn't help...

---

### Post by candtalan on 2011-10-25
As with a number of other laptop models, your model has switches, and software, to control wireless. Have you checked these are on?

Slide the Wireless device switch latch to (enable wireless) - this is likely to be located at the top of the keyboard  near the screen towards the right hand side.

Press Fn + F5, Set Wireless to Enable - this seems to be the key combination for your particular model from some notes I have seen.

Ubuntu: the network icon in the top panel - verify that wireless is checked as 'enabled'

hth

---

### Post by woods050 on 2011-10-25
thanks bro, i've tried what the links suggest but instead solving my problem, it actually deleted my "enable wireless" icon which later I reinstalled the entire Ubuntu 11.10...

I've check all the button on my laptop have pointed to wireless connection.  The real problem I'm facing (in my opinion) is that I'm unable to check the "enable wireless" icon.  I've also tried to configure through "system setting" "network" than "wireless network" but every time I click the on button on the "wireless network" section, it will automatically turn off, really puzzle me now...

Still looking for solution.

P/S:  I'm able to access inter net by the lan cable (through my notebook).

---

### Post by Drowz0r on 2011-10-25
Hey man, welcome to ubuntu.
 
I'm pretty new myself but had some similar issues just recently. I found that after a format to 11.10 I didn't have a working wireless on one of my machines.
 
So I basically ignored it and left it until last thing. Fully upgraded the machine on a wired connection first, then made sure I was in good range of my wireless box before unplugging the cable and trying to connect again.
 
There is a little network manager in ubuntu 11.10 (in the top right somewhere). I did find I had to remove my wireless connection and set it up again but it did work that time.
 
Initially though it totally wouldn't work, before the updates... of which there were like 50.
 
Does your wireless only not work with HDD ubuntu but works on the CD ubuntu? I find that's a driver related issue when that happens.

Oh and make sure your wireless devices are all on. I sometimes forget my wireless card is off, spend 10 minutes raging at no internet connection before turning it on like a fool...

Maybe reboot the wireless router just in case.

---

### Post by woods050 on 2011-10-25
Well I've on/off my router before but it doesn't work, and I tried to connect through my HTC phone's network also not successful, basically I think just check the "enable icon" will solve the problem but the thing is when I checked it, no tick appear...

---

### Post by zynchnod on 2011-10-25
I've had problems with proprietary Broadcom wireless drivers.  I had to disable the proprietary drivers and then install an ndiswrapper to make it work.  That was in an Inspiron.  I have had no problems with Intel chips whatsoever, they fire up with no prob.

---

### Post by computerandu on 2011-10-25
ok...lets see...could u plz post the output of following commands:

ifconfig
sudo lshw -C network

sudo rfkill list all

---

### Post by woods050 on 2011-10-25
Bro, here you go:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

```
woods@woods-Lenovo-3000-G230:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:16:07:67:e0  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:16ff:fe07:67e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:904 errors:0 dropped:0 overruns:0 frame:0
          TX packets:955 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1028976 (1.0 MB)  TX bytes:169519 (169.5 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

woods@woods-Lenovo-3000-G230:~$ sudo lshw -C network
[sudo] password for woods: 
  *-network               
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:16:07:67:e0
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.119 duplex=full firmware=sb v3.04 ip=192.168.1.3 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:46 memory:95500000-9550ffff
  *-network DISABLED
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth2
       version: 01
       serial: 00:21:00:6d:5f:70
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:94500000-94503fff
woods@woods-Lenovo-3000-G230:~$ sudo rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
```
woods@woods-Lenovo-3000-G230:~$

---

### Post by computerandu on 2011-10-25
Now try :

sudo rfkill unblock all

and restart your computer (just to make sure)

---

### Post by woods050 on 2011-10-25
tried before, no luck

---

### Post by computerandu on 2011-10-25
I hope that you tried 
sudo rfkill unblock all sudo rfkill list all
If it did not work then Now try these commands and see if it works:

sudo rmmod -f acer-wmi sudo rfkill unblock all sudo rfkill list all

---

### Post by anewguy on 2011-10-25
It's a Broadcom 4312.  This will probably require the firmware cutter and a couple of other packages, but before going that far:

- while connected to the net via your hard-wire connection:

sudo apt-get update

Wait for this to finish, then go to additional drivers - it may take a while but it will check the net to see if it finds any drivers.  If so, it will show them and you can enable them.  If no driver shows, post back.

This is why your clicking on the enable wireless does nothing:  there is no driver installed for your adapter.  The above will attempt to install a driver.

Post back with any questions or additional problems.

Dave ;)

---

### Post by woods050 on 2011-10-25
woods@woods-Lenovo-3000-G230:~$ sudo rfkill unblock all
[sudo] password for woods: 
woods@woods-Lenovo-3000-G230:~$ sudo rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
woods@woods-Lenovo-3000-G230:~$ sudo rmmod -f acer-wmi
woods@woods-Lenovo-3000-G230:~$ sudo rfkill unblock all
woods@woods-Lenovo-3000-G230:~$ sudo rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
woods@woods-Lenovo-3000-G230:~$ 
 
sorry, I'm very new to ubuntu, is the above what you ask to do?

---

### Post by woods050 on 2011-10-25
woods@woods-Lenovo-3000-G230:~$ sudo apt-get update
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric InRelease
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric-updates InRelease                              
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric-backports InRelease                             
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric Release.gpg                                     
Get:1 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric-updates Release.gpg [198 B]                   
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric-backports Release.gpg                                                            
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric Release                                                               
Get:2 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric-updates Release [32.4 kB]                     
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric-backports Release                                                                                   
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric/main Sources                                                                                        
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric/restricted Sources                                                            
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric/universe Sources                                       
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric/multiverse Sources               
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric/main i386 Packages                                     
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric/restricted i386 Packages                               
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric/universe i386 Packages           
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric/multiverse i386 Packages         
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric/main TranslationIndex                                  
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric/multiverse TranslationIndex                            
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric/restricted TranslationIndex                            
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric/universe TranslationIndex                              
Get:3 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric-updates/main Sources [56.8 kB]                       
Get:4 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric-updates/restricted Sources [14 B]                             
Get:5 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric-updates/universe Sources [4,319 B]
Get:6 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric-updates/multiverse Sources [1,032 B]
Get:7 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric-updates/main i386 Packages [106 kB]                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease                                            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                 
Get:8 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric-updates/restricted i386 Packages [14 B]          
Get:9 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric-updates/universe i386 Packages [21.2 kB]            
Get:10 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages [2,703 B]                 
Get:11 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric-updates/main TranslationIndex [73 B]                        
Get:12 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex [72 B]
Get:13 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex [70 B]
Get:14 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric-updates/universe TranslationIndex [73 B]        
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric-backports/main Sources                             
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric-backports/restricted Sources                       
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric-backports/universe Sources                         
Get:15 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]                                  
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric-backports/multiverse Sources                        
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric-backports/main i386 Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric-backports/restricted i386 Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric-backports/universe i386 Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric-backports/main TranslationIndex
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric-backports/universe TranslationIndex
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric/main Translation-en         
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric/multiverse Translation-en   
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric/restricted Translation-en   
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric/universe Translation-en     
Get:16 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric-updates/main Translation-en [55.3 kB]
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric-updates/multiverse Translation-en            
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric-updates/restricted Translation-en
Get:17 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric-updates/universe Translation-en [14.4 kB]              
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric-backports/main Translation-en                                          
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric-backports/multiverse Translation-en
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric-backports/restricted Translation-en
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric-backports/universe Translation-en
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg [198 B]       
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release [28.2 kB]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources [4,957 B]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources [14 B]
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources [14 B]                                                                   
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources [14 B]                                                                 
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages [12.7 kB]                                                              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en                                                                                     
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages [14 B]                                                           
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages [5,250 B]                                                          
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages [14 B]                                                           
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex [72 B]                                                              
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex [70 B]                                                        
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex [70 B]                                                        
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex [72 B]                                                          
Get:32 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en [8,207 B]                                                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en                                                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en                                                                    
Get:33 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en [4,303 B]                                                         
Fetched 359 kB in 8s (44.0 kB/s)                                                                                                             
Reading package lists... Done

done, should I restart my notebook?

---

### Post by woods050 on 2011-10-25
It works!!!! thank you bro!! million thanks!!!!  the problem have bother me for the last whole night! what a relief!  thank you very much!

---

### Post by unknown user on 2011-10-25
Hi there, I remember that I had a problem like this on my old laptop with an older version of Ubuntu. No matter what I did I was unable to get the wireless to work. So in the end what I had to do was to go into the laptop bios on bootup and change the settings back to default. This was a random thing for me to try, but at this stage I had tried everything. It worked a treat and since then I have had no issues with the wireless.

---

### Post by woods050 on 2011-10-25
new problem arise, each time when i turn off / restart the notebook, the wireless connection is lost and I've to perform the following command before it automatically reactivate.

sudo rmmod -f acer-wmi sudo rfkill unblock all sudo rfkill list all

any idea anyone?

---

### Post by realitykid on 2011-10-25
> **woods050 said:**
> new problem arise, each time when i turn off / restart the notebook, the wireless connection is lost and I've to perform the following command before it automatically reactivate.

sudo rmmod -f acer-wmi sudo rfkill unblock all sudo rfkill list all

any idea anyone?
There should be a way to set it so that Ubuntu will run that automatically when you login, possibly requiring you to enter your password again though.

I'll get back to you on that once I've figured out how to do that, if it all possible in 11.10

---

### Post by realitykid on 2011-10-25
From terminal type in

```
sudo gedit /etc/xdg/autostart/wireless1.sh
```When gedit opens copy and paste the following:

```
gksudo rmmod -f acer-wmi sudo rfkill unblock all sudo rfkill list all
```Now save the file.

In terminal, type:

```
sudo chmod +x /etc/xdg/autostart/wireless1.sh
```That should make the script executable. Reboot and see if it works.

If it doesn't work, or you want to remove it later just go into terminal and type:

```
sudo rm /etc/xdg/autostart/wireless1.sh
```

I really hope this helps.

---

### Post by woods050 on 2011-10-26
nope, it doesn't work, I've still have to input the command in order to activate the wireless connection

---

### Post by realitykid on 2011-10-26
> **woods050 said:**
> nope, it doesn't work, I've still have to input the command in order to activate the wireless connection

Ok, one more trick up my sleeve then.

Click on the dash button on the dock.

In the search field, type "startup" without the quotation marks.

An icon labeled "Startup Applications" should appear. Click that.

Now, in the window, click add.

A dialogue box should appear with the following fields:

Name:
Command:
Comment:


Put whatever you like in the "Name" and "Comment" fields.

In the "Command" field input

```

gksudo rmmod -f acer-wmi sudo rfkill unblock all sudo rfkill list all 

```

Now reboot and tell me if that works.

---

### Post by woods050 on 2011-10-26
thank you bro for your trick but still it doesn't work but nevertheless, thanks for your effort...I'll keep trying

---

### Post by realitykid on 2011-10-26
> **woods050 said:**
> thank you bro for your trick but still it doesn't work but nevertheless, thanks for your effort...I'll keep trying

Darn. Oh well then. Sorry man. Wish I could be of more help. I hope you figure it out soon.

---

### Post by computerandu on 2011-10-26
Hi,

To make the changes (which worked for you) permanent, use the following commands

sudo su

echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf

exit

---

### Post by woods050 on 2011-10-26
thank you bro, it finally work with no problem at all, million thanks!

---

### Post by computerandu on 2011-10-26
> **woods050 said:**
> thank you bro, it finally work with no problem at all, million thanks!

You are welcome ... and please mark the thread solved...

And someone else with similar problem, here are all the steps provided in this post:

[http://www.computerandyou.net/2011/05/how-to-solve-no-wireless-network-in-ubuntu-11-04-centrino-wireless-n-1000/](http://www.computerandyou.net/2011/05/how-to-solve-no-wireless-network-in-ubuntu-11-04-centrino-wireless-n-1000/)

---

### Post by anewguy on 2011-10-27
For some reason I forgot to get back to you after you did the update initially to get it working as per my post.  Thanks computerandu for finishing up with the blacklisting of the bad driver.

Sorry I didn't get back to here sooner - could have saved you a lot of messing around.  I'm glad that my post on the update, etc., got it working.  This is usually the best course of action for someone to take if their wireless isn't working.

Glad it's working for you!

Dave ;)

---

### Post by budmaester on 2011-10-27
Been having the same problem on Latitude D530 and spent hours trying to find proble in blacklist, iwconfig file and researching ndiswrapper. Yes, the fn F5 key worked! But my keyboard F2 key is labeled as the on/off for wireless?  Go figure. Thanks for the nudge and help.:popcorn:

---

### Post by woods050 on 2011-10-27
sorry bro, this is quite embarrassing, how to change this thread to "solved"?

---

### Post by computerandu on 2011-10-27
I too had to struggle to find out how to mark the thread solved. So don't feel embarrassed..
I guess it is already marked as solved. But in case, on the top right corner in the thread tool you have an option of marking it as solved.

---

### Post by candtalan on 2011-10-27
> **woods050 said:**
> sorry bro, this is quite embarrassing, how to change this thread to "solved"?
no probelm, I get exactlty the same question for myself and have to search!
I think it is at the top of the page you see:
Thread Tools 	Search this Thread 	Display Modes 

inside thread tools, as thread 'owner' you should see
Mark thread as solved I think

---

### Post by anewguy on 2011-10-27
Just open this thread in your browser, go to the top of the thread and you'll see a box for "Thread Tools".  Just put your mouse on that and you'll find the "solved" title.

EDIT:  Sorry, didn't see there was a page 4 and all these posts telling you how to do it already.

Dave ;)

---

