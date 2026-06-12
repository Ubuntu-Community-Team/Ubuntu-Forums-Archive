---
title: "HOWTO: Set up wireless internet (Desktop or laptop)"
date: 2006-01-04
forum: Outdated Tutorials &amp; Tips
---

### Post by HokeyFry on 2006-01-04
**[SIZE="7"][COLOR="Red"]WIRELESS CARD HOWTO: ANY DISTRIBUTION OF LINUX (DESKTOP OR LAPTOP)[/COLOR][/SIZE]**

Although I run Xubuntu, the following steps should still work with any distribution of Linux. If you run into any trouble with the GUI apps, I will be providing the terminal commands soon as soon as the network admin at my school reminds me how to do it. They will be posted at the end of this HOWTO. Also, don't ever hesitate to PM me about this, because I am always happy to help, although I am a student so bear with me if I don't respond right away.

Also keep in mind that this only deals with wireless devices that are not compatible with Linux out of the box. If you are using a device that is Linux-compatible, refer to the manual for the device, or look for online documentation on how to install it.

For a WPA Encyryption HOWTO, look [here]("http://ubuntuforums.org/showthread.php?t=318539")

I have tested this in the following (K/X)Ubuntu distros.
-5.10
-6.04
-6.10
-7.04
-7.10
-8.04

This should also work with any other Linux distribution.

**[SIZE="6"][COLOR="Blue"]Sections:[/COLOR][/SIZE]**

1. Pre-requisites
2. Installing "build-essential"
3. Installing NDISwrapper from source
4. Installing your wireless driver
5. Activating your wireless card via terminal
6. Credits
7. Other methods


**[SIZE="6"][COLOR="Blue"]1. Pre-requisites[/COLOR][/SIZE]**

1) Working internet connection or method on getting new packages onto your computer (e.g. second computer & thumb-drive). I STRONGLY suggest you try to get a LAN or dial-up connection as it gets tedious without one.

2) The package "build-essential". I will explain how to get this in the tutorial if you do not already have it.

3) Make sure the wireless driver you have is made for your architecture. 32 bit drivers do NOT work on 64 bit systems and vice versa!


**[SIZE="6"][COLOR="Blue"]2. Installing "build-essential"[/COLOR][/SIZE]**
NOTE: If you have the package "build-essential", or you have the gcc compiler (3.4 or newer), you may skip to Section 3. If you do not use Ubuntu, Kubuntu, or Xubuntu, I recommend you try to install the gcc compiler that is available to your distribution, as this section will only accommodate those who can utilize the "apt-get" function or "dpkg" function of the terminal. 

1) Type the following into the terminal (if you have an internet connection).
```
sudo apt-get install build-essential
``` Proceed to the next section.

2) If you do not have an internet connection, use another computer to download the "build-essential" package from [packages.ubuntu.com]("http://packages.ubuntu.com"). Use the search function there to find the package, or [click here]("http://packages.ubuntu.com/search?searchon=names&keywords=build-essential").

3) Once it is downloaded, transfer the file to the computer you are trying to configure wireless on. Put it in its own directory (folder).

4) Run this in a terminal. Make sure you are in the same directory as the "build-essential" package is.
```
sudo dpkg -i *.deb
```

5) If this works, you may safely delete these packages, and go to the next section. 

If not, the there are probably dependency issues. The only thing I can suggest is to write down the names of the packages it says you need, download them and transfer them into the same directory as you are in now, and run the code again. If there are still issues with dependencies, do the same thing. This is why it is MUCH easier to have a working internet connection while doing this.

[B][SIZE="6"][COLOR="Blue"]
3. Installing NDISwrapper[/COLOR][/SIZE][/B]

NOTE: If you have *ever* tried to install your card via ndiswrapper before, type these into a terminal, each separately.
```
sudo rmmod ndiswrapper
sudo ndiswrapper -l
sudo ndiswrapper -e nameofdriver
sudo apt-get remove --purge ndiswrapper*
```
If you don't have Ubuntu, Kubuntu, Xubuntu, or 'apt-get', instead of using the last line, remove the package 'ndiswrapper*' via however it was you installed it.


1) Download the NDISwrapper source code from [here]("http://sourceforge.net/project/showfiles.php?group_id=93482"). Choose the latest stable version. The reason I am having you install from source is that I (along with others I know) have had issues with the 'ndiswrapper' package provided with Ubuntu. Not to discourage their packages, but I have had greater success with compiling from source. Also keep in mind that when there is a kernel upgrade, you may have to recompile ndiswrapper from source in order to make sure it keeps working.

2) Extract the archive with whatever archive extractor you wish. To do it from the terminal, though, here is the command.
```
tar -zxvf nameOfArchive.tar.gz
```

3) in the terminal, type this in
```
cd pathToFolder
```
where 'pathToFolder' is the directory created from extracting the archive in the last step.

4) Now, type in the following exactly, each separately
```
sudo make uninstall
sudo make uninstall
make
sudo make install

```
If you get no errors, you are good to proceed to the next section.

If you get any errors, make sure your gcc compiler is up to date. If you still get errors, or don't want to upgrade, type this into the terminal.
```
sudo make uninstall
sudo make uninstall
```
Then try to use the Ubuntu provided packages.
```
sudo apt-get install ndiswrapper*
```
And proceed to the next section, though it is possible it won't work.

If you do not have an internet connection, you will once again have to transfer the packages from another computer to this one, and use 'sudo dpkg -i *.deb' again, and fix the dependencies yourself.


**[SIZE="6"][COLOR="Blue"]4. Installing your wireless driver[/COLOR][/SIZE]**

You got this far. The hard part is OVER!!! Be happy:mrgreen:

This tutorial DOES assume you have the driver for your wireless card. If you bought the card in a store, it will be on the CD provided. If you for whatever reason do not have a CD (e.g. internal wireless) the website of your computer should have it or the site of the maker of the card should have it on their site. If the driver is inside an EXE file, you should be able to extract it with an archive manager, such as file-roller.

Also, consider this a "Step 0". Paste this into your terminal.
```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```
The bcm43xx driver is a linux proprietary driver that will make *some* wireless cards with a Broadcom chipset work, but it is only "okay", and it may conflict with your wireless hardware and prevent your wireless from working with ndiswrapper.

1) Via the terminal, change to the directory where the driver is. It will have to have the .inf and .sys file in there. Remember, the command to change directories is 'cd'. If the driver is on a CD, the CD is usually mounted at '/media/cdrom0' or somewhere in the '/mnt' directory.

2) Once in the directory, type this into a terminal.
```
sudo ndiswrapper -i *driver*.inf
```
'driver' would be the name of the driver you need to use. And the accompanying .sys file MUST be in the same directory. If it discerns between which Windows driver, use the 2000 or XP one, never Vista, as Vista drivers are not yet supported (but will be in the near future, hopefully).

3) Now type in this
```
sudo ndiswrapper -l
```
If it says no hardware is present, then you have the wrong driver. If that happens here is how to uninstall the driver
```
sudo ndiswrapper -e *driver*
```

4) Type these into a terminal
```
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```

5) Now open up /etc/modules with the text editor of your choice. Make sure you have super-user priveleges, a.k.a. use 'sudo'. Add
```
ndiswrapper
``` to the bottom of the file. You should probably reboot here.

6) If this works, congrats, your wireless is installed. You can either configure it using the network manager that came with your distribution, or you can use a handy program called Wifi-Radar, which effectively manages your wireless. If you choose to install Wifi-Radar, make sure you have Python installed as well. If you do not have a GUI interface, I will be providing the necessary code to bring up your wireless and scan for SSIDs (network names) thru the terminal.

If you are doing this on Hardy, and this did not work, follow the steps in [this]("http://ubuntuforums.org/showthread.php?t=734003") guide for a workaround until whatever bug this is is fixed. This may be fixed by the time Hardy's release comes around, though, so let me know if this is not an issue for you.

**[SIZE="6"][COLOR="Blue"]5. Activating your wireless card via terminal[/COLOR][/SIZE]**

Here is everything you should need to know for bringing up a wireless (or any internet connection) from the terminal. Keep in mind that your wireless connection may not always be called wlan0. For example, my interface is eth1. the command "iwconfig" should give you the interface name.

To scan for a **wireless** network (essid)
```
sudo iwlist wlan0 scan
```

To bring up the interface
```
sudo ifconfig wlan0 up
```

To bring down the interface
```
sudo ifconfig wlan0 down
```

To connect to a router
```
sudo iwconfig wlan0 essid ID key k
```
where "ID" is the name of the router you want to connect to (returned by iwlist scan wlan0), and "k" is the network key to connect to the router

Now that you know what each command does, here is what most people should have to type into their terminal
```
sudo iwlist wlan0 scan
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid ID key k
```

I am unsure if this terminal method works with WPA encryption, so keep that in mind, as I use WEP because of the difficulty I have had with WPA in general. In theory it should work, but I don't know if thee are any extra steps to it.

**[SIZE="6"][COLOR="Blue"]6. Credits[/COLOR][/SIZE]**

While I largely did learn on my own how to use NDISwrapper, I must thank trubblemaker for showing me how to compile ndiswrapper from source, how to purge it from my system, and how to stop the bcm43xx driver from loading. I also want to thank Jim for showing me the commands to bring up a wireless interface from the terminal, even though I forgot them and had to re-ask :roll: Also thanks to Mazza558 for the Hardy workaround.

**[SIZE="6"][COLOR="Blue"]7. Other Methods[/COLOR][/SIZE]**

If this guide does not work for you, but you are able to get your wireless card working some other way, outline what you did or link the walkthrough you followed, along with your wireless hardware or laptop model. I will put that information in this section.

Atheros AR5007 wireless device- [http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)

Also, please vote in the poll at the top, I'd like to know how helpful this has been to you. If anything is unclear or not straightforward, please tell me so I can fix it. In the words of GLaDOS, "thank you for helping me help you help us all."

Good luck and Godspeed

---

### Post by maxwellhouse on 2007-07-17
Great steps and I will be sure to follow them.  I have a dell latitude d610 laptop.  How do I tell what this has in terms of a chipset?  Can you tell me where in the directory tree to look for this?  I do not know at this point whether I need a pcmcia wireless nic or whether my wireless capability is built in.   

Any info is appreciated. 

Thanks
M

---

### Post by antoniogarciaiii on 2007-07-17
I got as far as System -> Administration -> Network

It didn't show the wireless connection.  What can I be doing wrong?:(

---

### Post by HokeyFry on 2007-07-18
> **maxwellhouse said:**
> Great steps and I will be sure to follow them.  I have a dell latitude d610 laptop.  How do I tell what this has in terms of a chipset?  Can you tell me where in the directory tree to look for this?  I do not know at this point whether I need a pcmcia wireless nic or whether my wireless capability is built in.   

Any info is appreciated. 

Thanks
M

it sounds like you are thinking the chipset is in the computer. the chipset has to do with the wireless cards. as for finding out the chipset, i really dont know what to say, other than look at the box, manual, or search online (e.g. google name of wireless card followed by broadcom) or something.


as for your laptop model, looking at it on the dell website it doesnt seem to have built in wireless so you probably need to buy a wireless card or wireless usb pen



if you need any other help dont hesitate to ask again

---

### Post by fitzbag on 2007-09-23
hey was wondering if you would be able to help. I've got a Dell Inspiron 6000 with an Intel Pro/Wireless 2200. I can't for the life of me work out how to install the driver for the card for the life of me. Any help would be great. Thanks in advance.

---

### Post by ayed on 2007-10-06
I don't know why none of this is working, when I put this in the follwoing turns out:

ayed@Ayeds-Laptop:~$ sudo apt-get install build-essentials
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essentials

---

### Post by ayed on 2007-10-06
This turns out from the first step and I don't know why!
ayed@Ayeds-Laptop:~$ sudo apt-get install build-essentials
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essentials

---

### Post by HokeyFry on 2007-10-06
do you have a working internet connection? if you dont then you need to follow the non-internet instructions

---

### Post by woodslanding on 2007-12-13
Okay:

I got stumped on the very first step(I have no LAN...)  Where is 'build essentials' on the ubuntu package page???

Okay, I looked in the gutsy subdirectory, and no mention of 'build essentials' there either.

What are 'backports'.

I'm constantly amazed at the amount that is (okay, has to be ;)) taken for granted when you move to a new OS universe....

Thanks!
eric

---

### Post by woodslanding on 2007-12-13
Well, the search function on the package page doesn't turn up 'build essentials' either.....

---

### Post by Vadi on 2007-12-13
Here you go: [http://packages.ubuntu.com/gutsy/devel/build-essential](http://packages.ubuntu.com/gutsy/devel/build-essential)

And backports are packages that have been avialable in newer versions of ubuntu, and in the older versions too.

Like, let's say a new package becomes avialable in 7.10, that wasn't in 7.04. If you enable backports in your 7.04, and there is a backported copy of that 7.10 package, you'll be able to get it.

---

### Post by HokeyFry on 2007-12-13
im sorry, that was a typo on my part. its just "build-essential", and make sure there is a hypen in there when you type it in. I will change the walkthrough right now too. Thanks for spotting that.

---

### Post by AngelAir on 2007-12-18
I do not know about anyone else, but this was one of the best ***HowTo*** postings that I have seen so far.  It explained everything step by step and not only that IT FIX MY PROBLEM:guitar:

---

### Post by Eberulf on 2007-12-20
It didn´t fix mine.  It is very frustrating.

I do not show wireless network as an option under Administration-Network.  The driver is installed.

---

### Post by HokeyFry on 2007-12-21
Did you run "sudo modprobe ndiswrapper" and reboot?

---

### Post by Ttech on 2007-12-26
Would this by chance fix a network light on my Inspiron 6000 to work?

---

### Post by HokeyFry on 2007-12-30
What do you mean the light? Like is your wireless working and the WiFi light isnt on? Or is your wireless flat out just not working?

---

### Post by 5of0 on 2008-01-17
I agree, this is one of the best tutorials I've seen - very straightforward, and well-described.  Plus it worked!  Well done! :KS:KS:KS:KS:KS
It didn't work the first time, but it turns out I had downloaded the wrong driver from Dell (I'm on a Vostro 1500).  NDISWrapper said that the hardware was installed, but had an alternate driver in parentheses.  The wireless card didn't show up at all, even in iwconfig.
BUT I uninstalled the first driver (assisted by a helpful [post]("http://ubuntuforums.org/showthread.php?t=201902") on another [thread]("http://ubuntuforums.org/showthread.php?t=201902")):
```
sudo ndiswrapper -l
sudo ndiswrapper -e *drivername*

```
Rebooted, reinstalled the correct driver per the instructions on this tutorial, rebooted, and my network manager applet picked it up and worked flawlessly, even with the WPA wifi.  Awesome!  My two issues (sound and wireless) are now taken care of.  Thanks again!

---

### Post by xanderh on 2008-01-25
I'm running into errors while trying to install ndiswrapper.  At the point when I enter
```
make
```
I receive the following error
```
make -C driver
make[1]: Entering directory `/home/alex/Desktop/ndiswrapper-1.51/driver'
Makefile:35: *** Cannot find kernel version in /lib/modules/2.6.15-51-386/build, is it configured?.  Stop.
make[1]: Leaving directory `/home/alex/Desktop/ndiswrapper-1.51/driver'
make: *** [all] Error 2

```

Then, when attempting
```
sudo apt-get install ndiswrapper*
```
I receive this:
```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ndiswrapper.8

```

Can you help?

---

### Post by karl-arthur on 2008-01-27
Dude, Ive been fighting with my laptop for three days now, turns out the only thing missing from the other HowTos was to add 'ndiswrapper' to /etc/modprobe. So I'm extremely happy I read your post carefully, thanks a million!

---

### Post by alzwded on 2008-03-21
um... might <a href="http://packages.ubuntu.com/gutsy/build-essential"> this </a> be what you're looking for?

---

### Post by HokeyFry on 2008-03-21
Noted, thanks.

---

### Post by khumbo on 2008-03-23
it worked from me. i have a bcm94311mcg driveron an HP 530 laptop. initially had problems getting my wireless fixed on ubuntu gutsy. had to download the driver though by following the link on [http://www.linuxquestions.org/questions/linux-wireless-networking-41/help-needed-with-broadcom-bcm94311mcg-617483/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/help-needed-with-broadcom-bcm94311mcg-617483/)

---

### Post by HokeyFry on 2008-04-08
Update: I added a spot if you are having issues with Hardy. If you use Hardy and the normal method works fine, please let me know, since I don't have a spare hard drive to test Hardy out on at this moment in time.

---

### Post by Karnach on 2008-04-08
Similar situationas to others: Dell Inspiron 1520 with 1 gig ram 120 GB hd and Dell 1395 Wireless card. I am dual booting with win xp home. have tried numerous solutions posted on the forums (ndiswrapper foremost) and am hitting a wall. my wifi light is on but no one is home My question is this: one step of the procedure is blacklisting the broadcom bcm43xx driver by typing "echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist" should'nt that result in the driver no longer being listed in system>preferences>hardware information? if so, why is it still showing up? and as long as it is showing up, the rest of the fix doesn't seem to work. HELP!!! Complete noob to Ubuntu so go really slow and basic with any suggestions please.

Kent "K'Arnach" Schmidt
Nameless Extra/ Clapper/ Production Assistant
Star Trek: Phase II

---

### Post by HokeyFry on 2008-04-08
I'm having a hard time understanding your issue. Can you describe it again for me please? What steps have you tried already?

And also, just because you blacklist a certain driver from loading doesn't mean that the system won't detect the hardware. It's not like Windows where you NEED the driver for the operating system to know what the device is. Linux can tell that for the most part on its own.

---

### Post by Karnach on 2008-04-08
Sorry if I wasn't clear.  I have a Dell Inspiron 1520 (a real headache causer from what i am reading on the boards) and it has the Dell 1395 wireless internal card.  Wireless, to this point is not working.  I am running Ubuntu 7.10 and dual booting win xp home.  I have downloaded ndiswrapper, and the win xp drivers from Dell.  I have unzipped the drivers into their own folder and have blacklisted the broadcom 43xx.  I have loaded the driver.  The Wifi light is on but there is no listing of the hardware in the hardware information screen, no wlan listing under network manager and if i unplug the cat 5 network cable, i lose network and internet.  I have tried this procedure  


[http://www.ubuntu1501.com/2007/11/wireless-in-gutsy-gibbon-with.html](http://www.ubuntu1501.com/2007/11/wireless-in-gutsy-gibbon-with.html)

substituting the appropriate driver file for the 1520 as opposed to the 1501.  I have now hit a brick wall and have no idea how to proceed.  I am a 30 year computer user/ builder/etc but all in wintel arena (some cp/m and dos decades ago)  Thanks in advance for any help or ideas.

Kent "K'Arnach" Schmidt
Nameless Extra/ Clapper/ Production Assistant
Star Trek: Phase II

---

### Post by HokeyFry on 2008-04-08
Can you run
```
iwconfig
```
in the terminal and post the output? Here is a sample output from mine
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"WIFINET"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:17:0C:62:54   
          Bit Rate=48 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:35/100  Signal level:-73 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by Karnach on 2008-04-08
I will this evening.  I am currently at work and forgot to bring the laptop.

Sorry
Kent

---

### Post by Sav98 on 2008-04-08
hey have a problem with the ndiswrapper.

```
charlie@charlie-laptop:~$ tar -zxvf ndiswrapper-1.52.tar.gz
```

results in 

```
tar: ndiswrapper-1.52.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
```

can anybody help?

---

### Post by HokeyFry on 2008-04-08
try
```
tar -xvzf ndiswrapper-1.52.tar.gz
```

I don't know if the order of the flags would matter, but I'm guessing it does.

---

### Post by Sav98 on 2008-04-08
no luck, tried this

```
charlie@charlie-laptop:~$ tar -zxvf /home/charlie/Desktop ndiswrapper-1.52.tar.gz

```

and got this reply 

```
tar: /home/charlie/Desktop: Cannot read: Is a directory
tar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now

gzip: stdin: unexpected end of file
tar: Child returned status 2
tar: ndiswrapper-1.52.tar.gz: Not found in archive
tar: Error exit delayed from previous errors
charlie@charlie-laptop:~$ tar -xvzf ndiswrapper-1.52.tar.gz
tar: ndiswrapper-1.52.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

```

only got ubuntu yesterday so this is all a bit confusing

---

### Post by HokeyFry on 2008-04-08
You forgot the slash after Desktop

Change to the directory that the archive is in, then copy/paste the code I wrote a few posts back.

---

### Post by Sav98 on 2008-04-08
sorry to do this to ya but like i said im very new to linux so how would i do that?

---

### Post by HokeyFry on 2008-04-08
Where did you download the archive to?

*EDIT* Actually, just right click the archive and click "Extract Here..." or something of that nature.

---

### Post by Sav98 on 2008-04-08
the desktop, should i just copy it to my docs or somthing like that?
home/charlie/desktop

---

### Post by HokeyFry on 2008-04-08
No, right click the archive and then click "Extract Here..."

---

### Post by Sav98 on 2008-04-08
done no change :(

---

### Post by HokeyFry on 2008-04-08
Hmm... well, I don't really know much about tar errors... is your laptop connected to the internet via LAN right now?

---

### Post by Sav98 on 2008-04-08
yes im using it to post this

---

### Post by HokeyFry on 2008-04-08
Okay, then follow my guide at the beginning of this topic, but instead of compiling from source, use the NDISwrapper binaries from the repository. It outlines what to do fairly well, my friend who is completely computer illiterate was able to follow it with little assistance.

---

### Post by SkonesMickLoud on 2008-04-08
Sav98, try moving the file from your desktop into your home folder.  To do this, simply go:

Places --> Home Folder

Then, simply drag and drop said file into your home folder.

Open up a terminal (terminals usually open in your home folder by default) and run the code again.  (Hit the "up" arrow until it reappears.)

---

### Post by Sav98 on 2008-04-08
try and no such luck im afraid got the exact same error.

ok im having no luck tonight but have to get up early tomorrow so will call it a night, thanks for the help you have given me so far and i shall hopefully have more success when i try again.

---

### Post by SkonesMickLoud on 2008-04-08
> **Sav98 said:**
> try and no such luck im afraid got the exact same error.

Ok, could be that you're typing in the wrong filename.

In Terminal, navigate to whatever directory the file is in and type:

```
ls -a
```

See anything with ndiswrapper-*-*.tar.gz?  If so, that's what you're actually looking for.  (*'s being numbers)

---

### Post by Karnach on 2008-04-08
Here is results of iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

Kent

---

### Post by vishinator on 2008-04-08
does this work with x64 edition too?

---

### Post by HokeyFry on 2008-04-09
> **Karnach said:**
> Here is results of iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

Kent

Honestly, I have no idea what could be wrong. Which distro are you using? And if it's not Hardy, I suggest reinstalling and trying from scratch because I am honestly stumped.



And also yes, this should work in the 64 bit version, but I can't guarantee it since I've never used the 64 bit version. It worked on my friend's laptop and he has a 64 bit system, but that's just one system.

---

### Post by Karnach on 2008-04-09
I'm using Ubuntu 7.10 (Gutsy Gibbon? I Think)  Should I upgrade it to 8.04 (hardy)  I thought that wasn't stable yet.  Which other forums should I post this problem in do you think?  Its my sons laptop and he needs both environments (win and Lin)  in order to develop for them at college.  

Thanks again for the help so far.

Kent "K'Arnach" Schmidt
Nameless Extra/ Clapper/ Production Assistant
Star Trek: Phase II

---

### Post by HokeyFry on 2008-04-09
No, I don't recommend upgrading to Hardy just yet. My rule of thumb is to stay one release behind (though usually I'll wait until three months into the release due to my impatience lol).

I would format the system partition and reinstall Gutsy, then follow my guide from the ground up.

And if he needs it for school, but can't get the wireless to work, I would use VirtualBox (a virtual machine) to install Ubuntu for now, and use that until you get your wireless working. And if he needs if for school, I'm willing to bet that some of his classmates/teachers would be able to help him better than I can, since they can work with the physical machine.

---

### Post by Superthommy on 2008-06-12
Help me: it goes all ok unile I tipe> sudo ndiswrapper -i driver.inf
it gives me this error:> No such file or directory at /usr/sbin/ndiswrapper line 219.
     Thankyou

---

### Post by HokeyFry on 2008-06-12
In the terminal, type in
```
whereis ndiswrapper
```
Then, everywhere in my walkthrough where I say to type in 'ndiswrapper', replace ndiswrapper with the full path to it, which is what 'whereis ndiswrapper' will return for you. If in the event that 'whereis' doesn't return anything for you, try typing in ```
locate ndiswrapper
```
This code may return more results but if ndiswrapper is on your system, the 'locate' will definitely find it.

---

### Post by dishere2003 on 2008-07-05
how do i find out the driver file name that i use to type in... i have the PRO/Wireless 4965 AG(N) intel card in my system.  I downloaded the iwlwifi 1.2.25 thing that the website said to download.  I think this is the driver i am not 100% positive.  I just don't know what name i need to type in for the terminal to get it to work.
All help appreciated

---

### Post by HokeyFry on 2008-07-06
Actually, I have a laptop that uses the Intel PRO/Wireless software to maintain a wireless connection in windows. This usually means that the driver is somewhere in the setup executable. From what I remember those drivers are a pain in the *** to extract. If you can post a download link to the file, I can take a look at it for you.

---

### Post by cmpunk on 2008-07-07
I have a question, i was playing around with my wireless connection icon on my toolbar, and i accidentally changed it to manual configuration and now instead of seeing how many bars I have, i only see the network icon. and also, when i want to search for a wireless connection on the go, instead of just left-clicking and showing me all the connections in range, i have to manually type it in.

How do I change it back to the automatic configuration?

btw, my internet still works.

---

### Post by jAtFhIm on 2008-07-19
Hi,

I'm new to linux. I'm using Ubuntu 8.04.1 64-bit on an HP Pavilion dv9720us.  I was able to install the driver, and when I did sudo ndiswrapper -l it said the driver was installed and it recognized the device, but Ubuntu doesn't see any networks.  The driver I installed was a Vista driver (apparently the wireless card is only for Vista computers), but since it installed I figured it would be okay.  Is that why it's not working?

Thanks

---

### Post by HokeyFry on 2008-07-19
> **cmpunk said:**
> I have a question, i was playing around with my wireless connection icon on my toolbar, and i accidentally changed it to manual configuration and now instead of seeing how many bars I have, i only see the network icon. and also, when i want to search for a wireless connection on the go, instead of just left-clicking and showing me all the connections in range, i have to manually type it in.

How do I change it back to the automatic configuration?

btw, my internet still works.

To change it back, click on the NetworkManager icon in the system tray and go to Manual Configuration. Unlock the menu and then click Wireless Connection, then Properties. Make sure Enable Roaming Mode is checked. That should fix it for you.


> **jAtFhIm said:**
> Hi,

I'm new to linux. I'm using Ubuntu 8.04.1 64-bit on an HP Pavilion dv9720us.  I was able to install the driver, and when I did sudo ndiswrapper -l it said the driver was installed and it recognized the device, but Ubuntu doesn't see any networks.  The driver I installed was a Vista driver (apparently the wireless card is only for Vista computers), but since it installed I figured it would be okay.  Is that why it's not working?

Thanks

Ndiswrapper does not currently support Vista drivers. Use an XP x64 driver if one is available. If not, then you may be SOL with 64-bit Ubuntu unless you buy an external wireless device that supports either Linux out of the box or XP x64.

```
From NDISwrapper's install instructions

Important: Not all Windows drivers are tested / stable. If the Windows driver that you
use is problematic, try alternate Windows drivers that others have tested, especially
those in List. Always, try Windows XP drivers and if Windows XP drivers are not
available, try Windows 2000/2003 drivers. Windows Vista drivers are not supported (yet)
- using Windows Vista driver will result in many &#8216;unknown symbol&#8217; error messages when
loading ndiswrapper.
```

---

### Post by RensD on 2008-07-19
Hi,

I just installed ubuntu hardy heron on my computer (64-bit edition). Now before I found your tutorial I already tried to install the driver myself with ndiswrapper from the package but it didn't work out.
I'm giving your tutorial a shot now and I'm getting stuck again. When I tried to install ndiswrapper from downloading it and then installing it with the terminal myself (I'm not proficient in the linux jargon yet ;)) I got an error.

```
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.

```

I tried doing that for a while but it didn't give me any results. So I installed ndiswrapper as the tutorial suggested from the packetmanager.

When I got to the step of typing
```
sudo ndiswrapper -l
```
Terminal replied that hardware was present and driver installed.

```
sudo ndiswrapper -m
```
Terminal replied:
```
module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

```

I figured that's a bad thing but gave the next step a try as well just to see what would happen.

```
sudo modprobe ndiswrapper
```
Terminal replied:
```
FATAL: Could not open '/lib/modules/2.6.24-19-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko': No such file or directory

```

So... could you please try to help me out. It'd be appreciated a lot.

---

### Post by HokeyFry on 2008-07-19
Try uninstalling ndiswrapper using Synaptic, then go about reinstalling it again from source like you did the first time. When you get to the part where it gives you this

```
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
```

you only need to run make uninstall two or three times. Then move on to running 'make' and 'sudo make install'. Once make and sudo make install are finished running, you can go about installing your driver using ndiswrapper again. Keep in mind that the messages you have seen are normal to see when installing your wireless adapter with ndiswrapper. However, that FATAL error is not. If you install ndiswrapper properly and you still recieve that message, let me know.

Good luck

---

### Post by jAtFhIm on 2008-07-20
Well, I didn't want to be SOL, so I did some more searching for drivers and came upon this:  [http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html) and was able to successfully set up my wireless card.  The only additional thing I had to do was set up my router again, for some reason.  So if anyone else is trying to set up an Atheros AR5007 wireless card with Ubuntu, that site should help you out.

---

### Post by rxxuor on 2008-07-28
> **HokeyFry said:**
> Try uninstalling ndiswrapper using Synaptic, then go about reinstalling it again from source like you did the first time. When you get to the part where it gives you this

```
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
```

you only need to run make uninstall two or three times. Then move on to running 'make' and 'sudo make install'. Once make and sudo make install are finished running, you can go about installing your driver using ndiswrapper again. Keep in mind that the messages you have seen are normal to see when installing your wireless adapter with ndiswrapper. However, that FATAL error is not. If you install ndiswrapper properly and you still recieve that message, let me know.

Good luck
Hey so I had the same problem i keep getting 

FATAL: Could not open '/lib/modules/2.6.24-19-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko': No such file or directory

I uninstalled ndiswrapper using Synaptic, then installed it again using the .tar.gz file. Im using an old HP Pavilion, everything works fine even the LAN. Thanks in advance.

---

### Post by pytheas22 on 2008-08-01
This is a thorough how-to that seems to have helped a lot of people.  But I just wanted to point out a couple of things that you may want to mention (as far as I can tell, you don't):

1. this won't work with any Linux distribution; it will only work with Ubuntu, Debian and possibly other Debian-based distributions.  Some of the steps would work in Red Hat, Fedora, Mandriva, Suse and so on, but in particular, Step 1 won't, because those distributions don't use apt-get.  Users of non-Debian-based distributions would have to figure out how to get kernel headers and gcc installed using whichever package managers those distributions use (yum on Fedora; I think Mandriva uses something called urpmi; et cetera).  It may help to note this for the sake of people who find this thread but aren't using Ubuntu or a related distribution.

2. if you compile ndiswrapper from source, I think that it will break when you update your kernel, which happens once every month or two if you apply the normal Ubuntu updates regularly.  This isn't a big problem--users just need to compile ndiswrapper again ("make; sudo make install") after the kernel upgrade, but it would be useful to mention.  If you install ndiswrapper using apt-get, it gets automatically updated when the kernel changes...but I realize that the apt-get version doesn't always work well.

3. if you're on a 64-bit Linux kernel, the Windows drivers that you load into ndiswrapper need to be built for 64-bit Windows--no exceptions.  If you load 32-bit Windows drivers on a 64-bit kernel, ndiswrapper won't work, even though it will still give you the "driver installed, device present" message.  I've seen a lot of people frustrated by this, so it might help to point it out in the tutorial.

Also note that in some cases (the Netgear WPN111 is an example), wireless-card manufacturers never released drivers for 64-bit Vista.  If you can't find 64-bit drivers for your card, your only option is to switch to 32-bit Ubuntu if you want your wireless to work using ndiswrapper.

Anyway, the how-to is great and seems to be useful for a lot of people, but I thought that the points above might help avoid some confusion in certain cases.

---

### Post by HokeyFry on 2008-08-02
I have made the above fixes since you are right, though, I already mentioned that installing ndiswrapper will differ depending on the distribution you are using.

---

### Post by sendblink23 on 2008-08-09
I'm in a BUMP...

my hardware does show *Present..

```
sendblink23@sendblink23-desktop:~$ sudo ndiswrapper -l
bel6001 : driver installed
	device (1799:6001) present
sendblink23@sendblink23-desktop:~$ 

```


here where i have my problem during your Method:

```
5. Activating your wireless card via terminal

Here is everything you should need to know for bringing up a wireless (or any internet connection) from the terminal. Keep in mind that your wireless connection may not always be called wlan0. For example, my interface is eth1. the command "iwconfig" should give you the interface name.

To scan for a wireless network (essid)
Code:

sudo iwlist wlan0 scan

To bring up the interface
Code:

sudo ifconfig wlan0 up

To bring down the interface
Code:

sudo ifconfig wlan0 down

To connect to a router
Code:

sudo iwconfig wlan0 essid ID key k

where "ID" is the name of the router you want to connect to (returned by iwlist scan wlan0), and "k" is the network key to connect to the router

Now that you know what each command does, here is what most people should have to type into their terminal
Code:

sudo iwlist wlan0 scan
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid ID key k

I am unsure if this terminal method works with WPA encryption, so keep that in mind, as I use WEP because of the difficulty I have had with WPA in general. In theory it should work, but I don't know if thee are any extra steps to it.
```


Well how can i get "Keep in mind that your wireless connection may not always be called wlan0. For example, my interface is eth1. the command "iwconfig" should give you the interface name."

I tried that and this is what it shows for me:
```
sendblink23@sendblink23-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sendblink23@sendblink23-desktop:~$ 

```


Any help there?

---

### Post by HokeyFry on 2008-08-10
Can you post the output of
```
sudo ifconfig
```

---

### Post by sendblink23 on 2008-08-10
> **HokeyFry said:**
> Can you post the output of
```
sudo ifconfig
```

This is my Output

```
sendblink23@sendblink23-desktop:~$ sudo ifconfig
[sudo] password for sendblink23: 
eth0      Link encap:Ethernet  HWaddr 00:11:d8:f2:07:16  
          inet addr:10.0.0.64  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:fef2:716/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:702 errors:0 dropped:0 overruns:0 frame:0
          TX packets:734 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:650028 (634.7 KB)  TX bytes:140028 (136.7 KB)
          Interrupt:21 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2244 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2244 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:112200 (109.5 KB)  TX bytes:112200 (109.5 KB)

sendblink23@sendblink23-desktop:~$ 

```

Just incase by the way....

```
sendblink23@sendblink23-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 10
       serial: 00:11:d8:f2:07:16
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=10.0.0.64 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: Wireless PCI Card - F5D6001
       vendor: Belkin
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64 maxlatency=64 mingnt=32
sendblink23@sendblink23-desktop:~$ 
```

---

### Post by HokeyFry on 2008-08-10
It looks like for some reason your wireless device wasn't assigned a device name. Did you compile ndiswrapper from source or did you install it from the repositories?

Also, are you running 32 or 64 bit?

---

### Post by sendblink23 on 2008-08-10
> **HokeyFry said:**
> It looks like for some reason your wireless device wasn't assigned a device name. Did you compile ndiswrapper from source or did you install it from the repositories?

Also, are you running 32 or 64 bit?


From repositories, the last one was during that method I mentioned on my first post here, running 64 bit

---

### Post by sendblink23 on 2008-08-10
I've decided to change forget about my current Wireless Card (I've read around too many problems, and no successful way to get it to work) ...  and well I've decided to buy a "Netgear 802.11g 54Mbps Wireless USB 2.0 Adapter WG111", because I've seen around that it works... well also found it around Ebay $10 with free shipping  ;) hehe  what a bargain, and well i shall expect getting it around by this Tuesday or Wednesday...

I'll try this method you have in here, or maybe this one to get it to work:
[https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111](https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111)

Well you tell me which one will fit me better for installing it me using "Ubuntu 8.04 Hardy Heron" 

you let me know thnx

---

### Post by HokeyFry on 2008-08-11
That is the same wireless USB I got, and I had issues with it in 64-bit Ubuntu, though 32-bit Ubuntu works fine. The problem is that the inf file contains info for both the 32 bit and 64 bit drivers, and I had to use Ubuntu 32-bit for the device to work properly. If you are looking to use it with 64-bit Ubuntu, I would shop around more.

Also, before spending money on a new device, follow my guide again but this time compile ndiswrapper from source.

---

### Post by sendblink23 on 2008-08-11
> **HokeyFry said:**
> That is the same wireless USB I got, and I had issues with it in 64-bit Ubuntu, though 32-bit Ubuntu works fine. The problem is that the inf file contains info for both the 32 bit and 64 bit drivers, and I had to use Ubuntu 32-bit for the device to work properly. If you are looking to use it with 64-bit Ubuntu, I would shop around more.

Also, before spending money on a new device, follow my guide again but this time compile ndiswrapper from source.

no worries..  I have no problem.. deleting my current Ubuntu .. and changing to 32 bit, (i have it totally new so I wont be losing anything), i know how to erase the current partition through the Ubunto Live CD and through Gparted Live CD  ;) thanx

---

### Post by sendblink23 on 2008-08-15
> **HokeyFry said:**
> That is the same wireless USB I got, and I had issues with it in 64-bit Ubuntu, though 32-bit Ubuntu works fine. The problem is that the inf file contains info for both the 32 bit and 64 bit drivers, and I had to use Ubuntu 32-bit for the device to work properly. If you are looking to use it with 64-bit Ubuntu, I would shop around more.

Also, before spending money on a new device, follow my guide again but this time compile ndiswrapper from source.

I've got it to work, with your instructions, under 32 bit Ubuntu, yes using the wireless USB .. thanx

---

### Post by BamaBob on 2008-09-17
Hello All,

It appears procedures outlined are for using a Windows driver in K/Ubuntu.  What if when you visit the manufactures site, you see a Linux driver for your card (Linksys WPC 11 ver. 3)?  What are the steps to install a Linux driver and give it a try?

If all else fails, I can follow the steps outlined for a Windows driver.  It seems to me it would be in my best interest to use a Linux based driver before using a Windows driver with ndiswrapper.  

I'm still stumbling around; please use the KISS method of instruction.  

Thanks,


Bob

---

### Post by HokeyFry on 2008-09-17
The linux driver on the manufacturer's site should have instructions on how to install it (a.k.a. i have no idea lol). Honestly, though, I have had better luck with using ndiswrapper than using native linux drivers.

---

### Post by pytheas22 on 2008-09-17
> It appears procedures outlined are for using a Windows driver in K/Ubuntu. What if when you visit the manufactures site, you see a Linux driver for your card (Linksys WPC 11 ver. 3)? What are the steps to install a Linux driver and give it a try?

Yes, as HokeyFry says above, usually there are instructions either on the manufacturer's site or in a README file bundled with the source code for the driver.  Be careful, though; a lot of the drivers for Linux that you find on manufacturers' sites are not easy to compile.  The instructions are usually written with the assumption that you're a Linux guru, and many drivers lying around manufacturers' sites are outdated and impossible to compile on modern Linux without modifying source code.

Also, if your card has native support, 95% of the time the driver is already built into Ubuntu, unless your card is really new.  If you provide a link to the driver you were looking at, someone can tell you whether it's included in Ubuntu already or not, and if not, how you can compile it yourself.

It's better to use native drivers instead of ndiswrapper whenever possible, but in reality a lot of the newer native drivers (like b43 and the iwl* drivers) are not very stable in certain cases, so sometimes it makes more sense to use ndiswrapper if you don't want to fight with driver bugs.

---

### Post by fylup17 on 2009-01-04
> **RensD said:**
> Hi,

I just installed ubuntu hardy heron on my computer (64-bit edition). Now before I found your tutorial I already tried to install the driver myself with ndiswrapper from the package but it didn't work out.
I'm giving your tutorial a shot now and I'm getting stuck again. When I tried to install ndiswrapper from downloading it and then installing it with the terminal myself (I'm not proficient in the linux jargon yet ;)) I got an error.

```
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.

```

I tried doing that for a while but it didn't give me any results. So I installed ndiswrapper as the tutorial suggested from the packetmanager.

When I got to the step of typing
```
sudo ndiswrapper -l
```
Terminal replied that hardware was present and driver installed.

```
sudo ndiswrapper -m
```
Terminal replied:
```
module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

```

I figured that's a bad thing but gave the next step a try as well just to see what would happen.

```
sudo modprobe ndiswrapper
```
Terminal replied:
```
FATAL: Could not open '/lib/modules/2.6.24-19-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko': No such file or directory

```

So... could you please try to help me out. It'd be appreciated a lot.

I'm having the same problem. I'm using the ndiswrapper from the repo because when I try to compile ndiswrapper from the source, when i enter...
```

make

```

I get multiple error messages (can't copy/paste right now-I'm using a different computer). I made sure my gcc compiler was up to date and i still have the same problem. Help!

---

### Post by pytheas22 on 2009-01-04
> I'm having the same problem. I'm using the ndiswrapper from the repo because when I try to compile ndiswrapper from the source, when i enter...
Code:

make

I get multiple error messages (can't copy/paste right now-I'm using a different computer). I made sure my gcc compiler was up to date and i still have the same problem. Help!

On Ubuntu 8.10, the ndiswrapper source won't compile because the ndiswrapper project is functionally dead and no one is apparently maintaining the code anymore.  If you're using Ubuntu 8.10, this is probably what's wrong.

Luckily, there's a third-party patch that you can use on 8.10 to compile ndiswrapper.  If you just run these commands, it will grab the ndiswrapper source and patch and compile and install everything for you (provided you have an wired existing Internet connection with which to download the code; if that's impossible, let me know):
```

sudo apt-get install build-essential patch
wget http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.53.tar.gz?modtime=1211931005&big_mirror=0
tar -xzvf ndiswrapper*
cd ndiswrapper*
wget http://www.slackware.com/~alien/slackbuilds/ndiswrapper/build/ndiswrapper_kernel_2.6.27.patch
patch -p0 < ndiswrapper_kernel_2.6.27.patch
make
sudo make install
```

If this doesn't work, please post the exact output that you get from 'make'.

---

### Post by edgar84 on 2009-01-23
This guide looks great. I've been trying to get my wireless internet running for quite some time now. Unfortunately I ran into some problems.

When I typed cd pathtofolder (In my case "cd /home/christian/Skrivbord/namnlos mapp" I got the message that the directory didn't exist.

Any ideas why I get this message?

(I unpacked the "ndiswrapper-1.54.tar.gz" through the archive manager, does that make any difference, instead of using the terminal?)

(I'm quite a noob so don't get to angry :) and I have tried to google it and searched the forum)

/edgar

---

### Post by HokeyFry on 2009-02-09
When you have a path, you cant have a space in the pathname unless you escape the space with a '\' or you put the entire path in quotes (not the cd but everything after it).

---

### Post by pytheas22 on 2009-02-09
> When you have a path, you cant have a space in the pathname unless you escape the space with a '\' or you put the entire path in quotes (not the cd but everything after it).

In other words, type:
```

cd /home/christian/Skrivbord/namnlos\ mapp
```

Also remember that you can press 'tab' while you're typing and the shell will auto-complete the entry for you.

---

### Post by iceman_ch on 2009-02-09
Can someone help me out or point me in the right direction.  I have a dell m1530 with ubuntu 8.10.  My wireless card works fine out of the box until I try to connect to an encrypted network using eep or wpa.  I've installed configured Ndiswrapper and it didn't help at all. Whenever I try to connect to an encrypted network I get a kernel panic.

thanks

---

### Post by 1needhelp1 on 2009-04-29
when i do the command [I]
sudo ifconfig wlan0 up 
[/I]I got this output
*SIOCSIFFLAGS: No such file or directory*

I did the same exact steps as the last time I did this a few weeks ago and now it wont work

---

### Post by pytheas22 on 2009-05-02
**1needhelp1**: what are the outputs of these commands:
```

lspci -nn
lsusb
ndiswrapper -l
lshw -C Network
dmesg | grep -e ndis -e wlan
```

---

### Post by ricprice on 2009-06-05
Spent lots of time working this issue - to no avail.  Found this instruction page, reinstalled Xubuntu to get back to fresh copy, and followed these instructions.  Worked like a charm.    Easy to follow.  Thanks, HotKeyFry

---

### Post by phoenix_verma on 2009-09-12
> **ayed said:**
> I don't know why none of this is working, when I put this in the follwoing turns out:

ayed@Ayeds-Laptop:~$ sudo apt-get install build-essentials
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essentials
As far as I know its "build-essential" and not "build-essentials". Thats why u r not getting the package.

---

### Post by speedygonzalas on 2009-12-22
Hi I managed to get the build essential and install my wireless program, I believe any ways, but I seem to be having problems connecting to the network, when I put the command
```
iwconfig
```
it gives me this
```

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"speedstream"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I notice that it shows no signal level, link quality, or noise level but it does give me the name speedstream which I believe is correct. Whenever I enter the password it gives me the message 'invalid argument'. 
Does this mean that I simply have no connection or that my password is wrong?

---

### Post by pytheas22 on 2009-12-22
**speedygonzalas**: how are you trying to connect to the network?  Are you doing it from the command line with iwconfig commands?  If so, please tell us the commands you're using.  Also try putting the interface down first with "ifconfig wlan0 down"; that may help.

Otherwise, please try using the GUI.  If you left-click on the NetworkManager applet that should be in the upper-right corner of your screen, you will see a list of available wireless networks and can choose to connect to yours.  This should hopefully work.

---

### Post by speedygonzalas on 2009-12-23
> speedygonzalas: how are you trying to connect to the network? Are you doing it from the command line with iwconfig commands? If so, please tell us the commands you're using. Also try putting the interface down first with "ifconfig wlan0 down"; that may help.

Otherwise, please try using the GUI. If you left-click on the NetworkManager applet that should be in the upper-right corner of your screen, you will see a list of available wireless networks and can choose to connect to yours. This should hopefully work.

I start off by scaning with 
```
sudo iwlist wlan0 scan
```

and then it gives me four different cells, with usually the first one (essid bell_wireless) having the highest signal so I choose that name.

then i use:
```
sudo iwconfig wlan0 essid ID key k
```
With ID as bell_wireless and the k as the key code

then it responds with
```
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "mycode".
```

I just tried using the sudo ifconfig wlan0 down command and got no visible reaction, so i tried the same connection code after and no luck, I also looked at my network manager and noticed a connection for Wired, but found nothing under wireless. 

The only thing I think I might have screwed up was turning the computer off right after Step 4 part 4) where you need to type these
```
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```

and then I added 
```
ndiswrapper
```
to the bottom of /etc/module

---

### Post by speedygonzalas on 2009-12-23
ok never mind, I ended up getting the wireless connection working, somewhat, I just re-entered the 
```
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```

rebooted and tried again and it was there. Now when I click on the network manager it will show a connection and all I need to do is click on the right one put the code in and it 'connects' except I can't browse anywhere and it just keeps asking me for the password and going back off-line. So I'm stumped again...
I noticed that in /etc/modules theres a 'lp' at the end, is that a loop command? cuz if it is should I add the 'ndiswrapper' right before it. I have it right after it at the very end right now I don't know if that could be the problem.

Also, I installed ndiswrapper through add/remove program instead of manually. I seemed to have absolutely no problems installing, but I hope it's not the reason for my bad connection...
Edit: ok, I just looked at my NDISwrapper info file and it shows a copywrite date from 2000-2003 and I'm using Ubuntu 9.04. Although in the terminal it said that the installation was a success without any problems what so ever I think this might be my problem... visibly everything looks perfect, but nothing works, if this is my problem then what's the best way to un-install the wireless driver and all that jazz so I can start the installation again from scratch?

---

### Post by pytheas22 on 2009-12-23
> ok, I just looked at my NDISwrapper info file and it shows a copywrite date from 2000-2003 and I'm using Ubuntu 9.04. Although in the terminal it said that the installation was a success without any problems what so ever I think this might be my problem... visibly everything looks perfect, but nothing works, if this is my problem then what's the best way to un-install the wireless driver and all that jazz so I can start the installation again from scratch?

Don't worry about that.  The copyright might be old, or it might be referring to the Windows driver file.  In any case, if you're using Ubuntu 9.10, ndiswrapper is the most recent version, which came out a few months ago.
> 
I noticed that in /etc/modules theres a 'lp' at the end, is that a loop command? cuz if it is should I add the 'ndiswrapper' right before it. I have it right after it at the very end right now I don't know if that could be the problem.

Don't worry about that either.  'lp' is the name of a module, not a loop control statement.  Having 'ndiswrapper' at the end of the file is fine.

I'm not sure what else could be causing ndiswrapper not to work, but if you could please post the output of the following commands, it will provide a fuller picture of your situation and hopefully help figure out a solution:
```

lshw -C Network
uname -rm
lsusb
lspci -nn
dmesg | grep -e ndis -e wlan
sudo iwlist scan
```

---

### Post by speedygonzalas on 2009-12-23
ok I just got my wireless working, it turned out it was that I was given the wrong Key code, I just had to reset the key and then bam, I'm using my wireless connection as I type, thanks alot.

BTW, to everyone who had problems with ndiswrapper, I simply installed it through add/remove program and I had absolutely no problems with it. My connection is now PERFECT!!! Man I'm so happy now, to think that I spent a day and a half killing myself over something that had nothing to do my programing, watever, awsome post.

---

### Post by MelRia on 2009-12-23
Real good. Thanks for the Step by Step walking through. as you see below , I could get the WLAN card installed, but cannot pull it up cuz of the warning. could you help please?

(code)
mel@Mel-laptop:~$ sudo ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
bcmwl5 : driver installed
    device (14E4:4315) present (alternate driver: ssb)

---

### Post by pytheas22 on 2009-12-25
MelRia: don't worry about that warning.  It's not the problem.  What's probably preventing ndiswrapper from working is that the wireless card is being claimed by the b43 driver.  To remove b43 so ndiswrapper can work, type:
```

sudo rmmod b43
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

Then see if you can connect.  If this works, let me know and I'll tell you how to make the solution permanent (for the time being, you would need to run those commands after each reboot in order for ndiswrapper to claim the wireless card).

For what it's worth, your card would also probably work (and be capable of more features) using the b43 driver, which is a native Linux driver for this device (no Windows drivers involved).  But b43 probably needs firmware installed before it can work; to get that, run:
```

sudo apt-get update
sudo apt-get install b43-fwcutter
```

and you will be asked if you want to download the firmware automatically say yes.

Either route (ndiswrapper or b43) should get your card working, so choose whichever one you like.

---

### Post by MelRia on 2009-12-25
Thanks a bunch for following. 
installed b43. still cannot see the device. 
 
mel@mel-laptop:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
 
That's what I get When trying to pull it up. 
What do say? :(
By the way, I removed ndiswrapper and drivers I had copied from Windows. from What you said I thought I ain't gonna need them no more. 
was anything needed in addition to b43 files? 
Thanks even more.

---

### Post by pytheas22 on 2009-12-26
Sorry it didn't work with b43 when you tried.  If you could please post the output of these commands (in this order), it should provide a better idea of what's wrong:
```

sudo rmmod b43
sudo modprobe b43
lshw -C Network
sudo rmmod b43
sudo rmmod wl
sudo modprobe wl
lshw -C Network
dmesg | grep -e wlan -e b43 -e wl
ls /lib/firmware | grep b43
```

(Note that some commands may have no output.)

If b43 turns out not to want to work, we can go back down the ndiswrapper route.  But b43 would be preferable because it provides many more features (support for monitor mode, master mode, etc.) than ndiswrapper, and would probably also be snappier.

---

### Post by MelRia on 2009-12-26
You can say that again. I googles b43 after what you said before. good stuff. Lotsa good thing about it. Here is what you asked for however, 

mel@mel-laptop:~$ sudo rmmod b43
[sudo] password for mel: 
ERROR: Module b43 does not exist in /proc/modules
mel@mel-laptop:~$ 
mel@mel-laptop:~$ sudo modprobe b43
mel@mel-laptop:~$ 
mel@mel-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:25:64:45:e7:02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.70 latency=0 multicast=yes
       resources: irq:29 ioport:de00(size=256) memory:f0010000-f0010fff(prefetchable) memory:f0000000-f000ffff(prefetchable) memory:f0020000-f003ffff(prefetchable)
mel@mel-laptop:~$ sudo rmmod b43
mel@mel-laptop:~$ 
mel@mel-laptop:~$ sudo rmmod wl
ERROR: Module wl does not exist in /proc/modules
mel@mel-laptop:~$ 
mel@mel-laptop:~$ sudo modprobe wl
FATAL: Module wl not found.
mel@mel-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:25:64:45:e7:02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.70 latency=0 multicast=yes
       resources: irq:29 ioport:de00(size=256) memory:f0010000-f0010fff(prefetchable) memory:f0000000-f000ffff(prefetchable) memory:f0020000-f003ffff(prefetchable)
mel@mel-laptop:~$ dmesg | grep -e wlan -e b43 -e wl
[    1.802994] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.803011] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[    9.358718] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[    9.460259] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 6, Type 5, Revision 1)
[    9.460306] b43: probe of ssb0:0 failed with error -95
[ 3349.689331] b43-pci-bridge 0000:0c:00.0: PCI INT A disabled
[ 4635.087094] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 4635.087119] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[ 4635.207248] b43-phy1: Broadcom 4312 WLAN found (core revision 15)
[ 4635.300260] b43-phy1 ERROR: FOUND UNSUPPORTED PHY (Analog 6, Type 5, Revision 1)
[ 4635.300322] b43: probe of ssb0:0 failed with error -95
mel@mel-laptop:~$ 
mel@mel-laptop:~$ dmesg | grep -e wlan -e b43 -e wl
[    1.802994] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.803011] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[    9.358718] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[    9.460259] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 6, Type 5, Revision 1)
[    9.460306] b43: probe of ssb0:0 failed with error -95
[ 3349.689331] b43-pci-bridge 0000:0c:00.0: PCI INT A disabled
[ 4635.087094] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 4635.087119] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[ 4635.207248] b43-phy1: Broadcom 4312 WLAN found (core revision 15)
[ 4635.300260] b43-phy1 ERROR: FOUND UNSUPPORTED PHY (Analog 6, Type 5, Revision 1)
[ 4635.300322] b43: probe of ssb0:0 failed with error -95
mel@mel-laptop:~$ 
mel@mel-laptop:~$ ls /lib/firmware | grep b43
b43
b43legacy
mel@mel-laptop:~$ 
mel@mel-laptop:~$ 
mel@mel-laptop:~$ 


Thank a bunch.

---

### Post by pytheas22 on 2009-12-26
hmmm, it looks like b43 may not actually like your card for some reason.  But before we go back to ndiswrapper, please give these commands a try and see if they bring up the device.  First run:
```

sudo apt-get update
sudo apt-get install --reinstall bcmwl-kernel-source
```

Then reboot.  After the reboot, type:
```

sudo rmmod b43
sudo rmmod ssb
sudo rmmod wl
sudo modprobe wl
```

Now see if the wireless works.  If so, we make this solution permanent (for the time being, you'd have to run those last four commands after each reboot to get online).  Otherwise, we may have to go back to ndiswrapper.

---

### Post by MelRia on 2009-12-26
Downloaded the file and that DID bring up the interface. Thanks. Now the problem is that (or so I think) it cannot talk to my router. neither does it scan for available WLANs. 
I tried to set it up manually, gave it the SSID and Key and all that settings, it searches for like 2 min then it asks for the Key again saying that it was requested by the router.  By the way I'm learning a lot from you. as you can tell I'm fairly new to Linux and kinda like it.
P.s. running  **sudo modprob wl  **Ubuntu crashed. I stopped running it.

---

### Post by pytheas22 on 2009-12-26
Do you know at which point the interface was brought up, or which command you typed before it appeared?  I would think that "sudo modprobe wl" would have been the one, but it sounds like not if that makes your system crash.

One possible reason that the card can't see wireless networks is that it's turned off.  On most laptops there's a physical switch or software switch (like Fn+F2) that can toggle the wireless on and off.  Please make sure that's on, then see if networks appear.

If that doesn't help, please let me know the output of these commands when the interface is up:
```

ifconfig
lshw -C Network
sudo iwlist scan
dmesg | grep -e wlan -e wl -e b43 -ie radio
```

---

### Post by MelRia on 2009-12-26
Oh I didn't tell you. I managed to get it scan. what I did was I reinstalled the network manager. Now it scans, and I reinstalled the last file you told me to install hopping that will solve the authentication problem. That did not happen. still having authentication problem. 
when I click on my wireless (which has WEP encryption)  off the available wireless points' list, it communicating. A min goes by and it asks for Key again saying it is required by the router. another min alter does it again, and does it again and does it again. 
I switched my router to unencrypted, attempted to connect but never happened. I reviewed my routers log and it showed attempt to connect via this interface. that means it goes as far as to my router now (all with your help I must say)  
p.s. The interface came up right after I downloaded**  bcmwl** files, and rebooted.  
please see the out puts below


mel@mel-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:25:64:45:e7:02  
          inet addr:192.168.1.70  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:64ff:fe45:e702/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:137867 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71878 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:168404207 (168.4 MB)  TX bytes:6383568 (6.3 MB)
          Interrupt:28 Base address:0xe000 

eth2      Link encap:Ethernet  HWaddr 00:22:5f:cf:dd:79  
          inet6 addr: fe80::222:5fff:fecf:dd79/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

mel@mel-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth2
       version: 01
       serial: 00:22:5f:cf:dd:79
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:25:64:45:e7:02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.70 latency=0 multicast=yes
       resources: irq:28 ioport:de00(size=256) memory:f0010000-f0010fff(prefetchable) memory:f0000000-f000ffff(prefetchable) memory:f0020000-f003ffff(prefetchable)
mel@mel-laptop:~$ sudo iwlist scan
[sudo] password for mel: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth2      Failed to read scan data : Invalid argument


mel@mel-laptop:~$ dmesg | grep -e wlan -e wl -e b43 -ie radio
[   13.148767] wl: module license 'MIXED/Proprietary' taints kernel.
[   13.214107] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.214121] wl 0000:0c:00.0: setting latency timer to 64
mel@mel-laptop:~$ 
mel@mel-laptop:~$ 

Thanks a lot.

---

### Post by pytheas22 on 2009-12-27
So it looks like the 'wl' driver is working for you (not sure why modprobing it caused your system to freeze), but there's still some weird stuff going on, for example the failure of "sudo iwlist scan" to work.

It might help if you recompile the driver using the latest source code from the hardware vendor's website, rather than the version included in Ubuntu.  To do that, run these commands:
```

sudo apt-get update
sudo apt-get install build-essential
wget http://www.broadcom.com/docs/linux_sta/hybrid-portsrc-x86_32-v5.10.91.9.3.tar.gz
tar -xzvf hybrid-portsrc-x86_32-v5.10.91.9.3.tar.gz
make
sudo make install
```

Then reboot, and please see if the wireless works any better.

---

### Post by MelRia on 2009-12-27
Quip question, is that what I should see after running the command **make** 


mel@mel-laptop:~$ make
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-16-generic'
  LD [M]  /home/mel/wl.o
ld: Relocatable linking with relocations from format elf32-i386 (/home/mel/lib/wlc_hybrid.o_shipped) to format elf64-x86-64 (/home/mel/wl.o) is not supported
make[2]: *** [/home/mel/wl.o] Error 1
make[1]: *** [_module_/home/mel] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
make: *** [all] Error 2
mel@mel-laptop:~$ sudo make install
install -D -m 755 wl.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/wl.ko
install: cannot stat `wl.ko': No such file or directory
make: *** [install] Error 1
mel@mel-laptop:~$ 
mel@mel-laptop:~$ 


note the Errors. Thanks.

---

### Post by pytheas22 on 2009-12-28
Ah, it looks like it didn't compile because you have a 64-bit kernel but that source code was for 32-bit.  Please give these instructions a try; they use the 64-bit code:

```
rm -r hybrid-portsrc*
sudo apt-get install build-essential
wget http://www.broadcom.com/docs/linux_sta/hybrid-portsrc-x86_64-v5.10.91.9.3.tar.gz
tar -xzvf hybrid-portsrc-x86_32-v5.10.91.9.3.tar.gz
make
sudo make install
```

Sorry about this.  I was assuming you were on 32-bit because that's most popular, but you know what happens when you assume things...

---

### Post by MelRia on 2009-12-31
Up and running. Thank you so so very very much. you are such a life saver. All you showed me, all I learned , I'm now much more interested in learning Linux. Thanks a lot.

---

### Post by pytheas22 on 2009-12-31
Glad to hear it's working.  One last thing you should note: when you upgrade your kernel via Ubuntu Updates, you will probably need to recompile the wireless driver again by running the commands in my last post.

Hopefully in Ubuntu 10.10 it will no longer be necessary to compile the driver yourself and the wireless will work out-of-the-box.

---

### Post by atjesse on 2010-01-03
Am sorry to reply late.. Just came across this post..

Those packages ndiswrapper and build-essential are in Ubuntu shipment CD and there's no need of internet to install them.

Just go Uncheck all internet sources, ie, unceck all sources except CD and reload sources. These packages will be there in uninstalled section of synaptic.
I tried it with 910 Free Shipment CD.

---

### Post by bart1452 on 2010-08-30
I didn't see it mentioned here, but after installing the wireless driver, while still in the Administrator account go to Administration>Users and Groups and make sure that the users all have the box checked for wireless privileges under the Advanced Settings. It could save a little bit of time and frustration because that is not the default setting in V.10.04.

---

