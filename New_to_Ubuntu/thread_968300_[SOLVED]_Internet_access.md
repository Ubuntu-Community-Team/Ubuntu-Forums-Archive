---
title: "[SOLVED] Internet access?"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by petelew48 on 2008-11-02
Hi,
I am new to linex and I have just installed ubuntu on my hard drive as a dual boot system with windows xp home.
At present I am accessing the internet via AOL broadband. I would like to access the internet using ubuntu but AOL inform me that they do not support linex.
Information (as much as possible please) would be appreciated as to what I require, with regards to an ISP and software, to access the internet via ubuntu. :confused:

---

### Post by ezramorris on 2008-11-02
> **petelew48 said:**
> Hi,
I am new to linex and I have just installed ubuntu on my hard drive as a dual boot system with windows xp home.
At present I am accessing the internet via AOL broadband. I would like to access the internet using ubuntu but AOL inform me that they do not support linex.
Information (as much as possible please) would be appreciated as to what I require, with regards to an ISP and software, to access the internet via ubuntu. :confused:

Hi,
Firstly, welcome to Ubuntu Forums!

Just because AOL doesn't 'support' Lin**u**x, it doesn't necessarily mean it won't work. ;-)

What's your setup? Are you connected directly to the internet with a modem, or using a router? If it's a modem, then are you connecting via a cable or wirelessly?

---

### Post by echolink on 2008-11-02
> **petelew48 said:**
> Hi,
I am new to linex and I have just installed ubuntu on my hard drive as a dual boot system with windows xp home.
At present I am accessing the internet via AOL broadband. I would like to access the internet using ubuntu but AOL inform me that they do not support linex.
Information (as much as possible please) would be appreciated as to what I require, with regards to an ISP and software, to access the internet via ubuntu. :confused:

You should be able to use ur AOL connection with Ubuntu, when they say they don't support "Linex" lol, they mean they can't give you support, because they basically don't no jack sh$* about Linux and they don't want to be held responsible if they help you screw something up with ur Ubuntu installation, that and they cant install all of there useless crap on ur computer and that usually pisses them off. Besides in a sense your support for Interweb, and Ubuntu is here with the Ubuntu Community which is way better than anything AOL could give you. ;) I have the same issue with Comcast whenever they come out to my house to work on my connection for whatever stupid reason, the tech that comes out dosn't even have a clue to what OS im running. When they first came out the tech was like I can install internet here, because they dont support firefox, or Linux, and he couldn't figure out how to get everything set up to install the software, that Comcast wants to install. I told him to just get the connection hot, and I would go from there and do the rest myself. But hey it saves me money when I do it myself, and its amusing to see the reaction when they come to my house lol.

---

### Post by Crafty Kisses on 2008-11-02
You should be able just to use Firefox if you have a net connection, you don't really need AOL.

---

### Post by ezramorris on 2008-11-03
Just try it. If it works, great. If not, let us know about your hardware etc.

---

### Post by Obeide on 2008-11-03
I'm posting this on ubuntu through AOL right now! ):P

---

### Post by petelew48 on 2008-11-03
Hi again,
Firstly, thankyou for the welcome.
Secondly, apologies for the wrong spelling of Linux.
Thirdly, I have tried connecting to internet via Firefox but no joy, telling me to check 'DNS settings'?????
My hardware is AMD Sempron 2600+ with 1gig ram and nvidia geforce 6200 graphics. My modem is a wired ADSL BT Voyager 105 (DSL light does not come on when trying to use firefox with ubuntu).
Running dual boot system windows xp sp3/ubuntu 8.04 LTS desktop edition.
Thanks for your help and advise so far.

---

### Post by alphacrucis2 on 2008-11-03
> **petelew48 said:**
> Hi again,
Firstly, thankyou for the welcome.
Secondly, apologies for the wrong spelling of Linux.
Thirdly, I have tried connecting to internet via Firefox but no joy, telling me to check 'DNS settings'?????
My hardware is AMD Sempron 2600+ with 1gig ram and nvidia geforce 6200 graphics. My modem is a wired ADSL BT Voyager 105 (DSL light does not come on when trying to use firefox with ubuntu).
Running dual boot system windows xp sp3/ubuntu 8.04 LTS desktop edition.
Thanks for your help and advise so far.

From the menu - Applications/terminal

type ifconfig

What is it showing for the inet address of eth0?

---

### Post by ezramorris on 2008-11-03
See if [_this thread_]("http://ubuntuforums.org/showthread.php?t=140010") helps.

---

### Post by petelew48 on 2008-11-07
ezramorris I tried the link.
Get as far as 'gedit' but wont save file after entering 'dabusb'.
After reboot on entering 'eciadsl-config-tk' I get the message 'bash: /usr/bin/eciadsl-config-tk: /usr/bin/wish: bad interpreter: No such file or directory.

---

### Post by petelew48 on 2008-11-07
> **alphacrucis2 said:**
> From the menu - Applications/terminal

type ifconfig

What is it showing for the inet address of eth0?

eth0    Link encap: ethernet HWaddr 00:1.1:2f:f1:cd:60
        UP BROADCAST MULTICAST MTU:1500 Metric:1
        RX packets:0 errors:0 dropped:0 overruns:0 frame:0
        TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000
        RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
        Interupt:19

lo      Link encap: Local Loopback
        inety addr:127.0.0.1 Mask:255.0.0.0
        inet6 addr: ::1/128 Scope: Host
        UP LOOPBACK RUNNING MTU:16436 Metric:1
        RX packets:1796 errors:0 dropped:0 overruns:0 frame:0
        TX packets:1796 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0
        RX bytes: 89800 (87.6KB) TX bytes: 89800 (87.6KB)

---

### Post by ezramorris on 2008-11-07
> **petelew48 said:**
> Tried the link.
Get as far as 'gedit' but wont save file after entering 'debusb'.
After reboot on entering 'eciadsl-config-tk' I get the message 'bash: /usr/bin/eciadsl-config-tk: /usr/bin/wish: bad interpreter: No such file or directory.

try
```
sudo gedit /etc/modprobe.d/blacklist
```
and adding the following line at the end of the file:
```
blacklist dabusb
```
Note the 'da' not 'de'

Also for the /usr/bin/wish problem, try installing the package tk8.4 before running that command.

Later on when you run /usr/bin/eciadsl-start you might have problems, in this case run
```
sudo /usr/bin/eciadsl-start
```

If you have any further problems, have a quick look at the last few posts of that thread, as people seem to be having similar problems.

P.S. just a thought - before you go any further, did you check in System>Administration>Hardware drivers to see if there was a driver in there?

---

### Post by petelew48 on 2008-11-08
> **ezramorris said:**
> try
```
sudo gedit /etc/modprobe.d/blacklist
```
and adding the following line at the end of the file:
```
blacklist dabusb
```
Note the 'da' not 'de'

Also for the /usr/bin/wish problem, try installing the package tk8.4 before running that command.

Later on when you run /usr/bin/eciadsl-start you might have problems, in this case run
```
sudo /usr/bin/eciadsl-start
```

If you have any further problems, have a quick look at the last few posts of that thread, as people seem to be having similar problems.

P.S. just a thought - before you go any further, did you check in System>Administration>Hardware drivers to see if there was a driver in there?

Checked in System>Administration>Hardware drivers and it says
'No propriety drivers are in use on this system'
 Device Driver
 nvidia_new        Enabled      Not in use

---

### Post by ezramorris on 2008-11-08
> **petelew48 said:**
> Checked in System>Administration>Hardware drivers and it says
'No propriety drivers are in use on this system'
 Device Driver
 nvidia_new        Enabled      Not in use

Yep, there isn't one for your modem.

---

### Post by petelew48 on 2008-11-09
> **ezramorris said:**
> Yep, there isn't one for your modem.

Does this mean that I am on a loser then?
I thought I had downloaded the drivers required when I was following the instructions in the other thread you directed me to.

I do have a new Siemens Gigaset SE587 WLAN dsl modem with a Tiscali sticker on. Would that do the job? Do you think I would stand a better chance with that?

---

### Post by ezramorris on 2008-11-09
> **petelew48 said:**
> Does this mean that I am on a loser then?
I thought I had downloaded the drivers required when I was following the instructions in the other thread you directed me to.

I do have a new Siemens Gigaset SE587 WLAN dsl modem with a Tiscali sticker on. Would that do the job? Do you think I would stand a better chance with that?

Sorry, I didn't make myself very clear.

I was just getting you to check that there wasn't a modem driver already set up for instant use before you continued, but there isn't, so you can carry on :-)

---

### Post by petelew48 on 2008-11-09
> **petelew48 said:**
> Checked in System>Administration>Hardware drivers and it says
'No propriety drivers are in use on this system'
 Device Driver
 nvidia_new        Enabled      Not in use

Hope I'm not getting to be a pain with this.
Have got 'blacklist dabusb' in ok but when I try and install the package 'tk84' I get the following:-
'sudo dpkg -i tk8.4
 [sudo] password for pete:
 dpkg: error processing tk8.4 (--install)
 cannot access archive: No such file or directory
 Errors were encountered while processing:
 tk8.4

---

### Post by ezramorris on 2008-11-09
> **petelew48 said:**
> Hope I'm not getting to be a pain with this.
Have got 'blacklist dabusb' in ok but when I try and install the package 'tk84' I get the following:-
'sudo dpkg -i tk8.4
 [sudo] password for pete:
 dpkg: error processing tk8.4 (--install)
 cannot access archive: No such file or directory
 Errors were encountered while processing:
 tk8.4

The command line tool for installing and removing packages from repositories is apt-get:
```
sudo apt-get install tk8.4
```
You could alternatively use Synaptic.

---

### Post by petelew48 on 2008-11-09
> **ezramorris said:**
> The command line tool for installing and removing packages from repositories is apt-get:
```
sudo apt-get install tk8.4
```
You could alternatively use Synaptic.

Oops! sorry, I plead ignorance here.
Is there a thread containing all the commands that I can refer to?

---

### Post by petelew48 on 2008-11-09
> **ezramorris said:**
> The command line tool for installing and removing packages from repositories is apt-get:
```
sudo apt-get install tk8.4
```
You could alternatively use Synaptic.

Here we go again!
Tried installing tk8.4 as follows:-
sudo apt-get install tk8.4
[sudo] password for pete:
Reading package lists...Done
Building dependency tree
Reading state information...Done
Package tk8.4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source.
E: Package tk8.4 has no insallation candidate

I found a reference to tk8.4 in libpurple0 and tried to install.

sudo apt-get install libpurple0
[sudo] password for pete:
Reading package lists...Done
Building dependency tree
Reading state information...Done
libpurple0 is already the newest version
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded

---

### Post by ezramorris on 2008-11-10
> **petelew48 said:**
> Oops! sorry, I plead ignorance here.
Is there a thread containing all the commands that I can refer to?

Regarding what?

> **petelew48 said:**
> Here we go again!
Tried installing tk8.4 as follows:-
sudo apt-get install tk8.4
[sudo] password for pete:
Reading package lists...Done
Building dependency tree
Reading state information...Done
Package tk8.4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source.
E: Package tk8.4 has no insallation candidate

I found a reference to tk8.4 in libpurple0 and tried to install.

sudo apt-get install libpurple0
[sudo] password for pete:
Reading package lists...Done
Building dependency tree
Reading state information...Done
libpurple0 is already the newest version
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded

You will need to enable the universe repository in Sytem>Administration>Software sources. Tick the line which ends in 'universe', then close and let it reload.

Try just tk instead of tk8.4

```
sudo apt-get update
sudo apt-get install tk
```

---

### Post by petelew48 on 2008-11-10
> **ezramorris said:**
> Regarding what?



You will need to enable the universe repository in Sytem>Administration>Software sources. Tick the line which ends in 'universe', then close and let it reload.

Try just tk instead of tk8.4

```
sudo apt-get update
sudo apt-get install tk
```

Regarding a list of commands for use in Terminal.

Thanks for this. I am working away for a week now so cannot try anything at the moment. But no doubt I will be back in touch when I get home.

---

### Post by petelew48 on 2008-11-14
> **ezramorris said:**
> Regarding what?



You will need to enable the universe repository in Sytem>Administration>Software sources. Tick the line which ends in 'universe', then close and let it reload.

Try just tk instead of tk8.4

```
sudo apt-get update
sudo apt-get install tk
```

Tried to enable the universe repository and it said software out of date and I needed an active internet connection to download, which I do not have. Tried also from Hardy cd and same result. Tried 'close' and 'reload' but no good.
Tried the update and install in Terminal anyway and got no where.

---

### Post by ezramorris on 2008-11-15
> **petelew48 said:**
> Tried to enable the universe repository and it said software out of date and I needed an active internet connection to download, which I do not have. Tried also from Hardy cd and same result. Tried 'close' and 'reload' but no good.
Tried the update and install in Terminal anyway and got no where.

Yep. You need a working internet connection to update apt, or install packages, terminal or otherwise.

---

### Post by Sealbhach on 2008-11-15
```
sudo apt-get install -s tk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  tcl tcl8.4 tk8.4
Suggested packages:
  tclreadline
The following NEW packages will be installed
  tcl tcl8.4 tk tk8.4

```

If you get onto the internet some other way, you can get the packages as .deb files and save them onto a USB stick or something like that.

If you're using Intrepid you can get them here:

[http://packages.ubuntu.com/intrepid/tk](http://packages.ubuntu.com/intrepid/tk)

Note you will also need to get the dependencies

tcl tcl8.4 tk8.4



.

---

### Post by petelew48 on 2008-12-14
I apologise for the long delay in replying but I have been moving home and no longer subscribe to AOL. I am now with Virgin media on cable and connected with the internet immediately through Ubuntu.
My sincere thanks to all who tried to guide and advise me.
I can now look forward to learning a great deal more about Linux without having to rely on a connection through Windows.

Once again thanks to all. ):P

---

