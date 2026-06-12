---
title: "Hang on Boot up"
date: 2012-08-05
forum: New to Ubuntu
---

### Post by JerryC on 2012-08-05
I installed gnome 3 a couple days ago and it seemed to do a clean install.  Everything worked fine.  Did 2 or 3 re-boots and 2 or 3 log offs.  The next day when I booted, it hung right after the purple screen and the 5 dots displayed.  It didn't get to the log-in screen.  The last two entries displayed are:

Checking battery state    [OK]
Stopping System V runlevel compatibility   [OK]

After that I have to Ctrl-Alt-Del.

What's next?  Uninstall Gnome?  Re-install 12.04?  Something else?

Thank you for your time.

JC

---

### Post by Bashing-om on 2012-08-05
Jerry;
 hi, ... can you get a terminal login by ctl-alt-F1 ???I expect a grub trouble can be fixed from the command line or from the install live cd ...
      talk to us ... 
see ya

---

### Post by JerryC on 2012-08-06
Ctrl-Alt-F1 does work.. I was surprised.  I didn't think it had booted far enough.  I am new to linux but am comfortable working in a terminal.  I don't know many commands yet, so be gentle with me.

Sorry the reply took so long.  We're spending the summer in our RV and today was moving day.

Thanks for your help and what's next?

JC

---

### Post by JerryC on 2012-08-08
Anybody else have any ideas?  If I re-install over the current installation, will I lose anything I have added?

---

### Post by brodedra on 2012-08-08
> **JerryC said:**
> Anybody else have any ideas?  If I re-install over the current installation, will I lose anything I have added?

Jerry, there seems a problem with the boot loader - Grub. Since you are able to access terminal the indications fine & system is responsive - hence not in a circular dead loop. However, any hardware hiccup might be causing the issue else, it could be a start-up program.

I have had a similar problem on a ThinkPad. I did a fresh clean installation. Doing so would erase your old programs though.

---

### Post by JerryC on 2012-08-08
Brodera -

That seems reasonable.  How do I look at Grub?  What am I looking for?

JC

---

### Post by Bashing-om on 2012-08-09
Jerry; my apologies too in taking so long in getting back with you.
ok... you can get a CLI (command line interface) ... try this:
```

sudo grub-install /dev/sda 

```
you will be prompted for password; enter the PW you entered in the installation. You will not get the PW echoed back to you ... you will see no response. 
 now as to the above code; the sda at the end is assuming (KEEP in mind the ole cliche') that the this device is a) the only disk on your system or b) it is the device you installed all your system on... 

 Enter the above and advise on what results.
                              we will take it from there.

---

### Post by JerryC on 2012-08-10
I ran gparted and found that my C: drive is sda3, my D: drive is sda5, my ext4 partition is sda6 and the swap is sda7.  So which one to use?  I'm thinking sda6?

JC

---

### Post by mwl128340 on 2012-08-10
when you install grub you want to install it to the disk with the os on it. do not use a specific partition. since you can get a terminal prompt boot into that and run the code bashing provided exactly as it is in the post. dont forget to update grub after the installation.```
sudo update-grub
```

---

### Post by JerryC on 2012-08-10
Thank you for the info about updating afterward.  Do you mean I should ignore the fact of partitions?  I have Win7 and linux installed on the same disk.  Doesn't grub have to be in the boot record on C:?

JC

---

### Post by mwl128340 on 2012-08-10
your not really ignoring partitions. you will be in your linux partition when installing which is why you have to boot into your semi working linux and go to the terminal prompt. that will take care of the partition aspect because you are installing grub to the mounted linux partition and during the installation, grub will take care of chainloading the windows partition. by only specifying the /dev/sda, grub is gonna point the mbr to look for grub in the linux partition and write the info at the begining of the drive.

---

### Post by JerryC on 2012-08-10
So do I use /dev/sda or not?  Just don't want to trash Win7.

JC

---

### Post by mwl128340 on 2012-08-10
yes , use sda and not sda6.

---

### Post by JerryC on 2012-08-10
I have done the two grub commands.  When I re-boot, it still hangs, but at a different place.  The messages are:

* Starting the Winbind daemon winbind      [OK]
saned disabled; edit /etc/default/saned


Anymore ideas?

JC

---

### Post by mwl128340 on 2012-08-10
how did you install gnome3 in the first place

---

### Post by JerryC on 2012-08-10
Through the terminal.  Not sure what I typed.  Seems like there were two commands.

JC

---

### Post by JerryC on 2012-08-10
I found what I typed:

sudo apt-get install gdm gnome-shell

One suggestion was to add "synaptic deborphan" on the end of it, but I didn't do that.

Hope this helps.

JC

---

### Post by Bashing-om on 2012-08-10
Jerry, we are making progress!
  Ok ... lets do this ,,,, //the winbind file is a part of the file sharing package to share files with windows... at this time let us say it is not needed, and get rid of it ... we can re-install it later for file sharing iffen ya want//
so remove winbind
 ```

sudo dpkg --purge winbind

```
remember will require password..get no response...
then:
```

sudo dpkg --configure -a

```
this should fix any other broken packages..
maybe at this point will boot up... if not try to install grub again as advised.

see ya!

---

### Post by JerryC on 2012-08-11
Did the purge on winbind and a dependent didn't like it, so I purged the dependent and then purged winbind OK.  Did the configure on dpkg and still wouldn't boot, so I  installed grub again.  Still won't boot and we're back to the original errors of:

Checking battery state [OK]
Stopping System V runlevel compatibility [OK]

This all started the day after I installed the gnome desktop.  And, even though gnome worked for the first day, should I uninstall gnome?  Also, grub always has worked.  The menu comes up and lets me make menu choices.  How does it help to re-install grub?  Just trying to have a learning experience here.

I have to attend a 50th wedding anniversary party today, so I won't be able to respond til later this afternoon.

JC

---

### Post by mwl128340 on 2012-08-11
i know what ya mean jc. i had installed gnome 3 on a previous version of ubuntu and found it was pretty unstable, at least on my machine. i recall just doing a reinstall of ubuntu but that was with 11.04 or .10. i will look into what i did to get gnome 3 in 12.04 and get back at ya in a lil. i may not be the most help with this but hopefully get started on the right path and see if anyone else can jump in. did you remove unity when you installed gnome 3? and any other info about anything that you did during or after installation would be very helpful. i will go into ubuntu and do some research about what i have done in the meantime. it doesnt sound like a grub issue cuz your able to get a command prompt so grub has done its job and booted the OS. but removing gnome may not be as easy as just purging it because of dependancies.

---

### Post by JerryC on 2012-08-11
I did not remove Unity.  It is on the list to remove if I can sometime.

---

### Post by mwl128340 on 2012-08-11
we can try and see if there are any broken packages. this may see something, may not. one thing about apt is that before and after doing anything in apt, i like to update the repos list to keep it fresh and up to date.```
sudo apt-get update
```shouldnt take more than a min to complete and you will see a whole list of sources follewed by done. then to check for broken dependacies use ```
sudo apt-get check
``` if there are broken packages youll probably have to use ```
sudo apt-get -f install
``` to fix them

---

### Post by mwl128340 on 2012-08-11
also ```
sudo apt-get upgrade
``` might be useful for it will get all packages up to date

---

### Post by mwl128340 on 2012-08-11
and as far as the synaptic and deborphan, synaptic i find very useful for it gives apt a gui frontend that use to be installed by default in ubuntu but for some reason is not anymore it is the package manager if you used ubuntu in the past. and deborphan finds orphaned (not used anymore but was installed at an earlier time) and can list them. i dont use the orphan but find synaptic to be very useful.

---

### Post by Bashing-om on 2012-08-11
Jerry; I am surprised above procedure was non-productive.
  Out of curiosity and see what the system status is .. can you log into your system from the CLI ? If so what do you get when you run the command "startx"
also, your attention is invited to the this post[HTML]http://ubuntuforums.org/showthread.php?t=1850641[/HTML].
 
 By the way thanks for your patience and follow through!

---

### Post by JerryC on 2012-08-11
I ran apt-get update and a ton of stuff was listed followed by a listing of web sites it couldn't find.  Then I ran apt-get check and everything was OK, so I didn't run -f install.  Next I ran apt-get upgrade and it didn't work.  This is when I slapped my forehead and said "Duh!".  I'm guessing not enough stuff has been loaded to put me online.  Then I ran "startx" and, lo and behold, I came up to my gnome2 desktop which is where it was the last time I saw a desktop.  However, I had no menu bars nor could I find a way to make them appear.  All I had visible was a windows program which I had on the desktop of my home screen.  It seems like progress.  Right?  Anything else to try?

JC

---

### Post by Bashing-om on 2012-08-11
Hey Jerry ....
 My last shud have worked!
 OK, seems your system is for the most part intact ..maybe only gdm has some holes. How bout we use synaptic package manager and re-install UNITY ? Get your system back in shape then see bout getting Gnome3 on it ...
by the way this site makes the switch look easy 
[http://www.filiwiese.com/installing-gnome-on-ubuntu-12-04-precise-pangolin/](http://www.filiwiese.com/installing-gnome-on-ubuntu-12-04-precise-pangolin/)
but I have not read all of it ...see what haps with the current UNITY desk top manager...
  My way for problem resolution ... 1-step-at-a-time, huh?? <==BDQ

---

### Post by Bashing-om on 2012-08-12
Jerry;
  Instead of doing my last (I did some more thinking/looking) at this time;
I found this on askubuntu:
[http://askubuntu.com/questions/129120/i-lost-unity-desktop-when-i-uninstalled-nautilus-how-to-get-it](http://askubuntu.com/questions/129120/i-lost-unity-desktop-when-i-uninstalled-nautilus-how-to-get-it)
Try this from terminal
```

Reinstall unity.

sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get install unity

```
This looks to be the solution !

---

### Post by JerryC on 2012-08-12
Don't you think I have to be online to do those things?  Are there some commands we can run to make a wireless connection work?

JC

---

### Post by mwl128340 on 2012-08-12
you can run ```
iwconfig
``` to see what the connections are. wireless is probably wlan0 or wlan1. then ```
sudo ifconfig wlan0 up
``` or if it is wlan1 replace wlan0 with 1. hopefully this works to get you online.

---

### Post by JerryC on 2012-08-12
iwconfig shows no wireless.  Which is odd because it shows the ethernet adapter and the laptop has both.  I'm in an RV park, so I have no access to ethernet.

JC

---

### Post by mwl128340 on 2012-08-12
hmm, is your wireless turned on on the laptop. there should be a light or some indication if the adaptor is on or off and should be a button to toggle power to the adaptor

---

### Post by JerryC on 2012-08-12
There is a keyboard toggle but no lite.  I toggled it both ways than ran iwconfig.

JC

---

### Post by mwl128340 on 2012-08-12
im assuming its an internal adapter does ```
lspci | grep Wireless
``` return anything.

---

### Post by JerryC on 2012-08-12
We get a return of:

08:00.0 Network Controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)

JC

---

### Post by Bashing-om on 2012-08-12
Jerry:
  I do not know much about wireless ... but I am here .. will continue

---

### Post by JerryC on 2012-08-12
I really appreciate the help from both of you folks.  Thank you so much.  I'll hang in there as long as you do.

JC

---

### Post by Bashing-om on 2012-08-12
Hey;
  we are here to help. (all of usuns are in this together )/
OK, let me regroup ... I was thinking your system is intact with the exception of your desktop ( for which I have found a solution)... is this not the case ...or do we back up and regroup ? 
[INDENT]kind regards <==BDQ
[/INDENT]

---

### Post by JerryC on 2012-08-12
I'm not sure I'm qualified to answer that since I don't know anything about the sequence of how things load.  It loads far enough that I can get to a terminal (Ctrl-Alt-F1).  I don't believe it starts the wireless connection.  Startx starts a form of desktop, but does not give me access to any menus or a toolbar.

JC

---

### Post by mwl128340 on 2012-08-12
hey im back, no prob on the help. its a learning experience for me as well. would you mind printing what the iwconfig spits back.

---

### Post by JerryC on 2012-08-12
The sum total of the output for iwconfig is:

lo   no wireless extensions
eth1   IEEE 802.11 Access Point: Not Associated
           Link Quality: 5  Signal Level: 0  Noise Level: 0
            Rx invalid  nwid:0 invalid  crypt:0 invalid misc:0

eth0  no wireless extensions

Hope this formats properly

JC

---

### Post by mwl128340 on 2012-08-12
ok, looks like eth1 is your 802.1x connection. lets try and see if it will scan for networks.```
iwlist scan
```

---

### Post by JerryC on 2012-08-12
You do know the ethernet jack is not plugged into anything, right?  So I'm betting no network will be found.

---

### Post by Bashing-om on 2012-08-12
Jerry/IM ;
 Excuse me for interrupting wireless issue....but..how bout this?
 	Quote:
 	 	 		 			 				If the network adapter supports a power management option, the following check box may be selected:
Allow the computer to turn off this device to save power
If the network adapter supports this option, it is available on the  Power Management tab of the network adapter properties dialog box. To  resolve this issue, disable this option on the Power Management tab. For  more information about how to disable this power management option,  click the following article number to view the article in the Microsoft  Knowledge Base: 			 		 	 	 
If you have this power-save function on in Windows, it will turn  the network card off before shutting down, leaving it unavailable to  Ubuntu.  So check that in Windows, and make sure you don't have  power-save on.
bt
 I am assuming that you are accessing the net from the same box as the ubie problems only on the windows installation.

---

### Post by JerryC on 2012-08-12
This is a Dell PC and the only power setting I can find for the wireless adapter does not shut the adapter down for any reason.  But what I did do was change the setting to max performance for both battery and plugged in.  I accessed the power settings through the little battery down on the task bar.

JC

---

### Post by mwl128340 on 2012-08-12
i see where your coming from. it sounds like your loading the linux kernel and then it stops. being that you have to manually start the x and you dont get the taskbar and gnome wont load. this is just me thinking out loud. do you still have a live cd for the exact operating system you have.

---

### Post by Bashing-om on 2012-08-12
As we certainly need to get your network interface up ....
see if the network card is alive and well with the following terminal command from the ubie install:
```
ifup eth1
```
```
ping -c3 74.125.227.135
```
that pings a google server .... see what responds (if any) we get.
 If nothing we will look at the hardware/software interfaceings .

---

### Post by JerryC on 2012-08-12
I tried something.  I ran the command "sudo iwlist scan".  I thought it might turn on the wireless adapter, but I got a surprise.  It listed three wireless nodes here in the RV park after the eth1 adapter.  Seems odd to me.  Anyway ...

Bashing-om -
Running sudo ifup eth1  returns ignoring unknown interface eth1=eth1.  Seems odd.

MWL128340 -

Yes I do have a live install on a USB drive.  Seems like that install didn't work for me so I used a live CD.  I don't have that CD with me.

JC

---

### Post by Bashing-om on 2012-08-12
Jerry;
 I may have given you a inappropriate command (if up eth1) that maybe for wired access ....mw, can you confirm ??//
try ```
sudo ip link set eth1 up
```
this is for wireless access.
then see what the command
```
nm-tool
```
yields.
then for device recognition:
```
lshw -C network
```

I hope this helps!

---

### Post by JerryC on 2012-08-12
The if up command (is that one or two words?) returned ignoring unknown interface eth1=eth1.

"sudo ip link set eth1 up" returned me to a prompt.  I assume no errors.

"nm-tool" returned, among other things, State disconnected, Device eth0, Type wired.
Device eth1, Type 802.11 wifi, State disconnected, Wireless access points (listed for close access points here).

"sudo lshw -C network " returned a long list listing details for the wireless interface and the ethernet interface.  (I wish I new how to copy and past in a way to get the info back to windows.

Just for fun, I tried to ping that IP address but it didn't go.

Thank you both for hanging in there with me.  I am old and it is 10:40 PM where I am, so I am going to bed.  I will be available most of the day tomorrow from about 8AM CSDT.

Nite,

JC

---

### Post by Bashing-om on 2012-08-13
Jerry;

 I had expected "lshw -C network" to tell us what is going on ... look in the output for one of these ..claimed, unclaimed, enabled, or Disabled.
That will determine our next procedure.
bt
for copy and past ... just highlight the text you want to transfer, choose copy from the right click, (that copies to clipboard in the background) in the forum thread clink on the '#' at the top of the post, position the cursor between the 2 code brackets, right click with cursor so positioned and "paste" ...

[INDENT]HTH   
[/INDENT]

---

### Post by JerryC on 2012-08-13
Guys, I am so sorry I haven't been around today.  The wife's PC won't go online (it did a week ago) and I had to work on that and we ended up going to Best Buy which is 20+ miles away.  Now we have to leave for the evenings activity in about 10 minutes.  I will try to get back later this evening.

JC

---

### Post by Bashing-om on 2012-08-13
Jerry;
 Time is not an essence in this case. 
 Sorry to hear about the wife's PC . Hope the trip to Best Buy was not replacing!

 Anyway I been looking and I found these guides ... Take a looksee at them; get back with us for any questions and additional assistance.
 This is a puzzle, and I like working puzzles that have meaning! 

[help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic]("http://ubuntuforums.org/help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic")
[help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html]("http://ubuntuforums.org/help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html")
[help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("http://ubuntuforums.org/help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

As we have no GUI at this time the first URL will be the more relevant.

Hope this helps. BDQ

---

### Post by JerryC on 2012-08-14
> **Bashing-om said:**
> Jerry;

 I had expected "lshw -C network" to tell us what is going on ... look in the output for one of these ..claimed, unclaimed, enabled, or Disabled.
That will determine our next procedure.
bt
for copy and past ... just highlight the text you want to transfer, choose copy from the right click, (that copies to clipboard in the background) in the forum thread clink on the '#' at the top of the post, position the cursor between the 2 code brackets, right click with cursor so positioned and "paste" ...

[INDENT]HTH   
[/INDENT]

I will get the output of this command in more detail and get back to you.  About copy & paste.  I know how to do it, but I remind you that I am working on one PC here.  I read this forum in windows, write down your commands, restart the laptop into linux, do the command(s), write down the result, boot back into windows, and show the result in this forum.  I'm thinking a copy & paste won't live through a reboot.  If you know some way to make that work, I'll buy ya a beer.  Now I'm off to record the output of lshw.

PS: My plan is to work on this all day.

---

### Post by Bashing-om on 2012-08-14
Jerry ...
 Copy/paste difficulties noted ... I often  get my cart before the horse...

I have a cheap thumb drive that really comes in handy in cases such as this.
Make me a document/file I copy and paste to/from.

I will be in and out this day ... so will check back later on the progress/status..

---

### Post by JerryC on 2012-08-14
The return from lshw is as follows:

*-network
  description: wireless interface
  product: BCM 4313 802.11b/g/n Wireless LAN Controller
  vendor: Broadcom Corp
  physical id: 0
  bus info: pci@0000:08:00.0
  logical name: eth1
  version: 01
  serial: 78:e4:00:b6:fd:41
  width: 64 bits
  clock: 33MHz
  capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
  configuration: broadcast=yes driver=w10 driverversion=5.100.82.38 latency=0         multicast=yes wireless=IEEE 802.11
  resources: irq:17 memory:f0500000-f0503fff
*-network
  description: Ethernet interface
  product: RTL 8111/8168B PCI Express Gigabit Ethernet Controller
  vendor: Realtek Semiconductor Co.
  physical id: 0
  businfo: pci@0000:20:00.0
  logical name: eth0
  version: 03
  serial: 00:26:b9:e1:81:8c
  size: 10Mbit/s
  capacity: 1Gbit/s
  width: 64 bits
  clock: 33MHz
  capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical ip mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcsast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rt8168d-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbits/s
  resources: irq:41 ioport:4000(size=256) memory:f0a04000-f0a04fff memory:f0a00000-f0a03fff memory:f0a20000-f0a3fff

Hope this helps.

JC

---

### Post by Bashing-om on 2012-08-14
That tells us a lot ... wireless module (driver) is loaded; lemme see what it will take to get connections. 
[INDENT] CUL
[/INDENT]

---

### Post by Bashing-om on 2012-08-14
OK; looking good so far! 
 do these and lets see:
**3. Check Driver**

 *If you ran [lshw -C network]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Commands#lshw") and saw a driver bound to the device then let's test to make sure it's communicating with the kernel.* [edit:which we do]

[LIST=1]
[*]Run the command [lsmod]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Commands#lsmod") to see if driver is loaded. (look for the driver name that was listed in the output of lshw, "configuration" line).
[LIST]
[*]If you did not see the driver module in the list then use the [modprobe]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Commands#modprobe") command to load it.
[*]If you see two modules (usually ndiswrapper and a native Linux driver) blacklist one of them (see below).
[/LIST]
 
[*]run the command [sudo iwconfig]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Commands#iwconfig").  If you see output like in the example in the command section then the  driver is at least identifying the device as a wireless device to the  kernel.
[LIST]
[*]Opening  networking in system>administration> and seeing the device in the  list is how to identify through a gui if the driver is at least  communicating with the kernel.
[/LIST]
 
[*]run the command [sudo iwlist scan]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Commands#iwlist")  to scan for a router. If an access point is identified this shows that  the card is probably working properly as it can complete a wireless  interface task. (note not all cards support scanning)
[/LIST]

---

### Post by Bashing-om on 2012-08-14
Hey Jerry;
  While awaiting your response I have been investigating the initial problem further.
It is possible the initial and ongoing problem could stem from a lack of disk space.
Wont take but a moment to check this with terminal command du -h to make sure we have some overhead on the disk. Also the newer SSD devices could be too fast in loading up the system before Upstart can get a handle on things ... are you running the newer SSD device ?

---

### Post by JerryC on 2012-08-19
I am so sorry.  I either never got notified of this post or I missed. it.  I ran du -h and got several pages of stuff very quickly but no errors.  Don't know what I was looking for.  I doubt if I am out of space.  If I remember right, I allowed a hundred gig.  Just have the one hard drive in this laptop.

JC

---

### Post by Bashing-om on 2012-08-19
Hey Jerry;

 I am enheartened to hear from you... How is it going ? Have you completed post #58 ? (have not looked at other thread yet) ....
[INDENT]regards <==BDQ
[/INDENT]

---

### Post by JerryC on 2012-08-19
I'm sorry, but I don't know how to get to post #58.  I search for my subscribed threads, then after that I can't get them all to display on one page and they don't show the page count at the beginning and end of the thread any more.  What is #58?  I probably did it.

JC

---

### Post by Bashing-om on 2012-08-19
Jerry;
 In reference to your lshw response: my reply was as follows:


OK; looking good so far! 
 do these and lets see:
**3. Check Driver**

 *If you ran [lshw -C network]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Commands#lshw") and saw a driver bound to the device then let's test to make sure it's communicating with the kernel.* [edit:which we do]

[LIST=1]
[*]Run the command [lsmod]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Commands#lsmod") to see if driver is loaded. (look for the driver name that was listed in the output of lshw, "configuration" line).
[LIST]
[*]If you did not see the driver module in the list then use the [modprobe]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Commands#modprobe") command to load it.
[*]If you see two modules (usually ndiswrapper and a native Linux driver) blacklist one of them (see below).
[/LIST]
[*]run the command [sudo iwconfig]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Commands#iwconfig").   If you see output like in the example in the command section then the   driver is at least identifying the device as a wireless device to the   kernel.
[LIST]
[*]Opening  networking in system>administration> and  seeing the device in the  list is how to identify through a gui if the  driver is at least  communicating with the kernel.
[/LIST]
[*]run the command [sudo iwlist scan]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Commands#iwlist")   to scan for a router. If an access point is identified this shows that   the card is probably working properly as it can complete a wireless   interface task. (note not all cards support scanning)
[/LIST]

---

### Post by JerryC on 2012-08-19
I may have mentioned this before, but we are in a fifth wheel trailer in West Bend, Wisconsin.  The wifi has been excellent.  But tomorrow is moving day.  We will be headed fo Kankakee, Illinois, where we will spend one night (wifi unknown and we won't unhitch) and then the next day we will head to Monticello, Indiana, meeting relatives.  I will do these things and get back to you as soon as I can, hopefully tomorrow night.

JC

---

### Post by Bashing-om on 2012-08-19
jc;
  Roger the moving ... have fun!
still time is not of essence ...I stay on this to insure you are a happy ubutunite !
(and to solve a puzzle)... I will be around when you get back to this little matter,

[INDENT]regards <==BDQ
[/INDENT]

---

### Post by JerryC on 2012-08-26
We were in two campgrounds that had crap for wifi.  We are now in Elkhart, IN and the wifi is wonderful.  I have run the commands listed in msg #63 with the following results.


sudo iwconfig

lo	no wireless extensions
eth1	IEEE 802.11  ESSID:””
	Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
	Bit Rate:72Mb/s  Tx-Power:24 dBm
	Retry min limit:7  RTS thr:off  Fragment thr:off
	Power Management:off
	Link Quality=5/5  Signal level=0 dBm  Noise level=-12dBm
	Rx invalid nwid:0  Rx invalid crypt:0 Rx invalid frag:0	
Tx excessive retries:0  Invalid misc:0  Missed beacon:0
eth0	no wireless extensions






sudo iwlist scan

lo	interface doesn’t support scanning
eth1	Scan completed
	Cell01 – Address:  00:02:6F:DA:B0:A0
		ESSID:”Campground-AP3”      (I use this one)
		Mode:managed
		Frequency:2.442 GHz (channel 7)
		Quality:4/5  Signal level:-63 dBm  Noise level:-98 dBm
		Encryption key:off
		Bit Rates: 1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
			     9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
			     48 Mb/s; 54 Mb/s

(There are 3 more cells listed)
Eth0	interface doesn’t support scanning

Looks to me like we only have to run a command or two to connect to that router.

JC

---

### Post by Bashing-om on 2012-08-26
JC;

  Hope it has been happy trails ! To my wife's irritation, i dislike travel, Subsequently, we stay home too much!

To the situation at hand. Catch-up: no GUI and no connect with wifi ?

wifi: run the command ```
lsmod
```
and lets see what driver is loaded ... see if we can then ping your router (when we can get an ip address.

[INDENT]regards <==BDQ
 
[/INDENT]

---

### Post by JerryC on 2012-08-26
I forgot to mention, I figured out why I was having so much trouble finding postings.  I had been experimenting with the setting on how forum postings are displayed.  I have now restored that so all should go much better now.

Ran the lsmod command and got a long list which includes:

r8169   size=62099  used by: 0

We determined earlier this is the driver for the wireless card in this laptop.

JC

---

### Post by Bashing-om on 2012-08-26
JC; --I am still learning this interface too---->

  I did some little amount of research...... r8169 has been fixed for linux in later kernel releases..and in dual booting with windows; this fix:
[http://ubuntuforums.org/showthread.php?t=1937956](http://ubuntuforums.org/showthread.php?t=1937956)

step 12 applies.

  Apply that and we see where we are at.

[INDENT]BDQ
[/INDENT]

---

### Post by JerryC on 2012-08-26
I have applied step 12.  The steps were slightly different than detailed there, but I believe I accomplished both steps.  I have not re-booted yet but I will shortly.

What's next?

JC

---

### Post by Bashing-om on 2012-08-26
JC;

  Reboot and let's see wifi workin' ,,,fingers crossed....

[INDENT][INDENT]BDQ
[/INDENT][/INDENT]

---

### Post by JerryC on 2012-08-26
I got to thinking as windows was shutting down.  Various commands have listed available routers in my campground.  That would tell me the adapter is working.  After the re-boot back to Ubuntu, I ran nm-tool which lists the wireless access points in this park.  I also ran iwlist which didn't list any routers but has in the past.

I am at the point of confusion in that my notes tell me what I have done, but not what the correct order is to do commands.  I have the sense that if I can see a list of routers, I should be able to issue a command to connect to a router.  True?

We may have a different problem here.  This RV park has the wifi set up so that when you sign on the first time in the morning, you need to enter a password in a web browser.

So, do I need to issue a series of commands in a specific order to get online?

JC

---

### Post by Bashing-om on 2012-08-26
Yeah, that does complicate things somewhat . (I ran across the command string in the past for the rv park router, can find it again if needed).

ok, lets see if the router responds to us with terminal command:
```
sudo iwconfig
```
look for eth1's "inet addr".

then scan with sudo to gain any additional info:
```
sudo iwlist scan
```

if you get good responses try !!
```
sudo ifup eth1
```
---------------------------
if you still do not connect ..we look to see what is blocked:
```
rfkill list
```

---

### Post by JerryC on 2012-08-26
What do I do with "inet addr"?  Or does it just need to be there?  How do I tell if I connect?  I ask because I have done these commands before.

JC

---

### Post by jibawakee on 2012-08-26
Try this 


```
sudo su
```

```
lspci
```

---

### Post by Bashing-om on 2012-08-26
inet addr ....if you see an address (example 192.168.0.100).. that indicates interface is working all good ... just need to do some configurations.
and, we may need this address for the rv park router for the later command string.

 we know the driver is loaded (lshw and lsmod tells us so)// the wireless interface should be up! ...sudo ifup eth1 should activate it!

by the way speaking of routers// do you have an in-house router to interface all your in-home computers ?

@jibawakee ..appreciate any assist // we are past that stage.
[INDENT]BDQ
[/INDENT]

---

### Post by JerryC on 2012-08-27
Thank you for jumping in.

sudo su
appeared to change to a different directory

lspci
lists controllers and chipsets one of which is the wireless LAN controller

JC

---

### Post by JerryC on 2012-08-27
iwconfiig
eth1 shows no "inet addr"

iwlist scan
shows 4 routers

sudo ifup eth1
shows ignoring unknown interface eth1=eth1

rfkill list
shows 0: brcmwl-0: Wireless LAN
       Soft blocked: no
       Hard blocked: no
1: dell-wifi: Wireless LAN
        Soft blocked: no
         Hard blocked: no

Yes, I do have a router at home and we will be heading that way tomorrow.  We're stopping in Davenport, IA for a couple nights to visit friends, and then will head home (West Des Moines, IA) on Thursday.

---

### Post by Bashing-om on 2012-08-27
JC;

    in-house router was referring if you employed one at this time in your present establishment.
 The wifi card apparently works, just cannot get connection. It is getting time to look at the logs and see what the system errors are. 
  First though, lets see if we can force and ip address with :
```
sudo dhclient  eth1/CODE]
if you get "no dhcp offers received" then try this:
[CODE]
sudo invoke-rc.d networking restart
    After running the invoke-rc.d command try dhclient eth1 again

```lastly (before looking at the logs )..see if you can decipher and apply this code: try connecting manually from a terminal using the iwconfig command
The syntax looks like this:
sudo iwconfig <ath0> essid <essid> ap <xx:xx:xx:xx:xx:> key <XXX> mode <> commit

edit1: the smilies to be replaced with colons (\ :  ), ath0 with eth0 and the brackets are inplace for syntax usage  to be removed when the options are employed. All of the options may not be required (ATT I do not know).[INDENT][LEFT] I will keep trying <==BDQ
[/LEFT]
[/INDENT]

---

### Post by JerryC on 2012-08-27
Just about to leave for site seeing.  Will do this this evening.

We do not have a router here in the trailer.  Wonder if we will have better luck when I get home.  No security to get around. Like we do here.

JC

---

### Post by Bashing-om on 2012-08-27
security is one of my weakest points; never having had to utilize it..

  I will await further developments.


[INDENT]BDQ
[/INDENT]

---

### Post by JerryC on 2012-08-27
Sudo dhclient eth1 
Takes a couple minutes thinking and returns to the prompt with no display.

sudo invoke-rc.d networking restart  returns
* Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
* Reconfiguring network interfaces ...
(I'll have to look up that word)

Sudo dhclient eth1 
Takes a couple minutes thinking and returns to the prompt with no display.

I will have to study the syntax on the iwconfig command.  As I mentioned earlier, tomorrow is moving day again and I don't know what kind of wifi service we will have, so I may not be able to get back to you til Friday.

JC

---

### Post by Bashing-om on 2012-08-28
JC;

  as " /etc/init.d/networking restart" is deprecated (system V) do this:

```
sudo service networking stop
sudo service networking start
```this is the upstart way.

and we look at the dmesg ring buffer for info/errors and go from there.
[INDENT]BDQ
[/INDENT]

---

### Post by JerryC on 2012-09-01
BOY!, HAVE I GOT GOOD NEWS.
Sorry it took so long to get back to you. 
I ran nmtool and it said my wireless adapter was connected to my home router!  So I ran apt-get update and it actually updated.  Big step forward.
What's next?  Uninstall gnome?  Or re-install Unity?

JC

---

### Post by Bashing-om on 2012-09-01
Outstanding! .... I was pulling my hair on this (seems should work, no workie) ... my next was see if we had uninstalled  the wpasupplicant/// as we are now good to go, not necessary!

Ok, back to problem: How bout we reinstall unity and install gnome3, I am under the impression that they live side-by-side in harmony. Choose the desktop manager at login screen. What do you want to do?

[INDENT]BDQ
[/INDENT]

---

### Post by JerryC on 2012-09-01
> **Bashing-om said:**
> Ok, back to problem: How bout we reinstall unity and install gnome3, I am under the impression that they live side-by-side in harmony. Choose the desktop manager at login screen. What do you want to do?

[INDENT]BDQ
[/INDENT]

I am game to do that.  I did have them installed side by side and I was looking over gnome2 when everything crashed.

JC

---

### Post by Bashing-om on 2012-09-01
ok; let's do this:
executing the code one-line-at-a-time;
 re-install unity:
                   ```
sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get install unity

```reboot to see where we stand.
If all good then:
install gnome:
                  ```
sudo apt-get install gnome-shell

```reboot again ... 
Should have both desktop managers available.
[INDENT]awaiting results <==BDQ
[/INDENT]

---

### Post by JerryC on 2012-09-01
> **Bashing-om said:**
> 
                   ```
sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get install unity

```
reboot to see where we stand.

[INDENT]awaiting results <==BDQ
[/INDENT]

Unfortunately the unity, ubuntu desktop reinstall did not work.  The commands are good and they appeared to do what they were supposed to do, but on re-boot I ended up at the same place I always do.  Perhaps there needs to be another command or two in that series?

JC

---

### Post by Bashing-om on 2012-09-01
ok here goes the last I presently have in my bag-of-tricks;


"But what if at some point you want to revert all the changes so you have the default packages reinstalled again?
Running :sudo apt-get install --reinstall ubuntu-desktop
does not reinstall its dependencies. So the solution is" :
```

sudo apt-cache depends ubuntu-desktop | awk -F ":" '{print $2}' | \
sed '/^$/d' | xargs sudo apt-get \
install --reinstall --install-recommends --yes

```(yes this is one line :))


and again my fingers are crossed. <==BDQ

---

### Post by JerryC on 2012-09-01
Entering that command did not allow me to enter the sudo password.  Instead it said: No command ' sed' found, did you mean:
command 'ssed' from package 'ssed' (universe)
command 'sed' from package 'sed' (main)
command 'psed' from package 'perl' (main)
command 'ksed' from package 'keysafe' (universe)
sed: command not found
[2]+ stopped             sudo apt-cache depends ubuntu-desktop | awk -F ":" '{print $2}' | \ sed '/^$/d' | xargs sudo apt-get \ install --reinstall --install-recommends --yes

JC

---

### Post by Bashing-om on 2012-09-02
jc;

 I ran that code on my 12.04 system/// ran just fine. I was amazed at the resulting conditioning, in that it totally rebuilt my system.
1. This code is to be executed as a single instance.
      open a terminal, and copy/paste the three lines in its entirety to the cli,
      hit "enter"
      submit your pass word.
       a. This will take no small bit of time...
        b. will get a running percentage of completion of the downloads.
         c. will get a readout of the rebuilding processes. Just kick back and watch it //see   if  any errors pop up.. be patient, watch, some steps take some time to complete.
in the end it had totally rebuilt my system.
prior to reboot for peace of mind I ran:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub

```(as I am triple booting)

2. Run the code again and advise.
[INDENT]BDQ 
[/INDENT]

---

### Post by JerryC on 2012-09-02
I wish I could copy and paste but I have that re-boot to contend with.  I suspicion I'm having a problem with 'space' characters.  Is there some way you can show where the spaces are in that string?

JC

---

### Post by Bashing-om on 2012-09-02
well... let's try this:
remember this is all one instance to be implemented one time.
sudo(sp)apt-cache(sp)depends(sp)ubuntu-desktop(sp)|(sp)awk(sp)-f(sp)":"(sp)'{print(sp)$2}'(sp)|(sp)sed(sp)'/^$/d'(sp)|(sp)xargs(sp)sudo(sp)apt-get(sp)install(sp)--reinstall(sp)install-recomends(sp)--yes    

now (sp) = space ;this code is all one input from start to end. Compare the two and note that the / (new line) character is not needed for the one-line typing input vice copy/paste input.  Type all this into the terminal as a single string.

```

sudo apt-cache depends ubuntu-desktop | awk -F ":" '{print $2}' | \
sed '/^$/d' | xargs sudo apt-get \
install --reinstall --install-recommends --yes

```I have proof read this three times (I am left brained)so I may have still missed a type-o.
it is difficult to perceive the pipe (|) symbol.
and (install(sp)2dashesreinstall(sp)2dashesinstall-recommends(sp)2dashesyes)

I do not know for sure if there is a limit on the length of a string in terminal input ..(we may find out!)///[INDENT]BDQ
[/INDENT]

---

### Post by JerryC on 2012-09-02
I finally got the command line to work without error.  However I did not notice we were off line when I did it.  It said reading package lists...done.  Building dependency tree.  Reading state information ... done.  The following extra packages will be installed ... lists several.  Suggested packages ... lists many.  The following new packages will be installed ... lists a lot.  The following packages will be upgraded .. lists even moree.  And then it figured out it was off line and couldn't do any of that.  My question is: Is it safe to run it again?  I ask because you were emphasizing only run it once.  I think I can because it never actually did anything, it only told me what it was going to do.

JC

PS: We're having a lot of trouble with the online provider today.

---

### Post by Bashing-om on 2012-09-02
Jerry, You are correct in your assumption, run the code again(real pleased ya got it workin) !!!

BUT, wait for a secure time to do so, problem in networking at this stage would be catastrophic and would require a re-install from source.

[INDENT]BDQ
[/INDENT]

---

### Post by JerryC on 2012-09-02
Will do. Have no confidence in the net connection now so this may take a while. 

JC  (from my phone)

---

### Post by Bashing-om on 2012-09-02
roger, it has been this long ......a bit longer should not be a big deal.

will await results <==BDQ

---

### Post by JerryC on 2012-09-02
Well, I managed to get everything to run without incident.  Unfortunately it didn't help.  I'm guessing it's time to do a re-install from CD.  It was a practice installation, so it's not like anything will be lost.  Any further ideas?

JC

---

### Post by Bashing-om on 2012-09-02
JC;

  I can not imagine what is preventing re-installing the desktop. Perhaps others can suggest something, but; I am at a loss as we have attempted all the methods I know of (and some I dug up)// There are times when it is best to just bite the bullet and re-install the operating system .. Re-installing a new install ...welp ...20 minutes and back in business.  

[INDENT]I dislike not having a solution....period!

Let us know how things work out... 
thanks <==BDQ 
[/INDENT]

---

### Post by JerryC on 2012-09-02
I will do a re-install.  If not tonight, then tomorrow.  Will post the results here.

JC

---

### Post by JerryC on 2012-09-03
I have successfully re-installed 12.04 and done an upgrade.  Should I also apply your command line?  What does that command line do?  I am skeptical of Gnome3.  What is your experience with it (if any)?

JC

---

### Post by Bashing-om on 2012-09-03
Hey ----Outstanding/// things looking brighter alla-the-time !
negative on the long command code. It just rebuilds the operating system resulting from broken dependencies.....

Now if all looks good and you want to install gnome3.4 ,,,, It is available in the repositories. Download it direct with the software center utility.

And, no I have not used/seen the gnome DE in 12.04. At this point I would not be skeptical at all of gnome 3.4 .... Seems the bugs have been worked out and it is deemed to peacefully co-exist with unity. Which DE to boot with is optional at the login.


[INDENT]Do Enjoy <==BDQ
[/INDENT]

---

