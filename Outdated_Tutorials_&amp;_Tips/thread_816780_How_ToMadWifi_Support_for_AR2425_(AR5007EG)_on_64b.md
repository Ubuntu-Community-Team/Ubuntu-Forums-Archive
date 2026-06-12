---
title: "How To:MadWifi Support for AR2425 (AR5007EG) on 64bit Ubuntu !!!"
date: 2008-06-03
forum: Outdated Tutorials &amp; Tips
---

### Post by Anduu on 2008-06-03
[B][COLOR="Red"]Updated April 18,2009 10:43:08 A.M. MST

* Please read this how-to in it's entirety before proceeding[/COLOR][/B]

Oh man this made me sooo happy when I found this!I just have to share ;)

I can't take any credit for this how to but I have tried it out and it works great...no more ndiswrapper for this puppy :)
You can see all the details regarding the lack of support for Atheros on 64bit linux here [http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679) and here [http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192)

You will need an internet connection so get wired up if need be.

Lets give it a go.

**1:** First off be sure the build-essential package is installed
```
sudo apt-get install build-essential
```

**2:** You will need the linux-restricted-modules package installed to be able to compile the driver
```
sudo apt-get install linux-restricted-modules-$(uname -r)
```
**3:** Also install subversion
```
sudo apt-get install subversion

```

NOTE:If you have been using ndiswrapper like I was you need to disable/remove it

[COLOR="Red"]I recommend doing what I did and run the first command in section 4 *_before_* removing ndiswrapper that way you can avoid hooking up to a wired network if your wireless is functional using ndiswrapper[/COLOR]
```
sudo ndiswrapper -e net5211
sudo modprobe -r ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils ndisgtk

```
Also run
```
gksudo gedit /etc/modprobe.d/blacklist
```

Remove any references to ath_pci and ath_hal

***** Before the next steps go to System ->Administration ->Hardware Drivers and make sure both Atheros drivers are ***disabled*** and reboot the system if they were not.

**4:** Get the files and install the driver
```
svn co http://svn.madwifi-project.org/madwifi/branches/madwifi-hal-0.10.5.6
cd ~/madwifi-hal-0.10.5.6
make
sudo make install
sudo depmod -ae
sudo modprobe ath_pci
echo ath_hal | sudo tee -a /etc/modules
echo ath_pci | sudo tee -a /etc/modules
```

**5:** Finally go to System ->Administration ->Hardware Drivers and reenable the Atheros drivers and reboot the system.

:KS One thing I should add is you will need to repeat this procedure whenever you get a kernel update.I have just kept the downloaded packages on my system and after booting into a new kernel I do:

```
cd ~/madwifi-hal-0.10.5.6
make clean
sudo make install

```

Reboot and I am up and running again.
Hopefully this makes your day like it did mine![SIZE="4"][/SIZE]

[COLOR="Red"][SIZE="4"]Note:[/SIZE][/COLOR]
If everything installs and loads properly but you cannot connect to any networks you probably need to configure your network properly.Try browsing through here [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo) for assistance.

**[SIZE="4"]Addendum: [/SIZE]**

Wifi light not working?Try [ZeroXtreme's]("http://ubuntuforums.org/member.php?u=243792") fix.

In a terminal type:

```
1. sudo sysctl -w dev.wifi0.ledpin=3
2. sudo sysctl -w dev.wifi0.softled=1
```

If this works, add the following to your /etc/sysctl.conf file to make the changes persistent:

```
sudo geditit /etc/sysctl.conf and add
```
```
# Enable WiFi LED
dev.wifi0.ledpin=3
dev.wifi0.softled=1
```

I won't guarantee this will work for everyone but it works on ZeroExtreme's and my Acer Aspire.

---

### Post by be4truth on 2008-06-07
Is that a solution for 32 bit as well? So far nothing worked for me fixing this issue.

---

### Post by Anduu on 2008-06-07
> **be4truth said:**
> Is that a solution for 32 bit as well? So far nothing worked for me fixing this issue.

This is strictly 64bit...try this if you haven't yet [http://ubuntuforums.org/showthread.php?p=4999962](http://ubuntuforums.org/showthread.php?p=4999962)

---

### Post by braveerudite on 2008-06-08
IT WORKS PERFECT!!!

Oh my God!!! Dude I feel like crying of so much joy.  You have no idea how much I needed this so bad.  I can't believe how simple it was to get it all working by just copy pasting the codes.  I been fighting for the last week with Atheros.  I manage to get the drivers install before with ndiswrapper and was able to see my wireless networks but couldn't connect no matter what I try.  I installed Wicd and Wi-Fi Radar and still didn't work.  But with this new method is beautiful and flawless , I did a clean Ubuntu install again for my laptop and kept the default network manager .  Thank you so much for sharing with us. Did you forget to mention in your guide to unchecked the drivers before starting this method?  I had both unchecked before starting to do this and it work on the first try.  I love you man, I love you.!!! w00t!!

:guitar:

---

### Post by freakwillie on 2008-06-08
Anduu,

You cant imagine how grateful I am to you. In fact I registered to the forum just to thank you.

Ive been trying to make my wifi work for two weeks so far, no even ndiswrapper would work for me. Followed dozens of howtos, got nothing. Indeed, yours was the only one that worked. Added to favorites, saved the page to my hard drive. 

You are my hero!

---

### Post by Anduu on 2008-06-08
Glad I could help :)

Like I said I'm just passing the info along...It's the guys at [Madwifi]("http://madwifi.org/") who deserve all the credit :KS

One thing I should add is you will need to repeat this procedure whenever you get a kernel update.I have just kept the downloaded packages on my system and after booting into a new kernel I do:

```
cd madwifi
make clean
sudo make install BINDIR=/usr/bin MANDIR=/usr/share/man
```

Reboot and I am up and running again.

---

### Post by 11hjpphty76lkjj on 2008-06-08
Thank you so much for this.  I'd been struggling with getting it working for the past week!

:)

---

### Post by uwe.koch.k on 2008-06-09
Hi Anduu,

following your instructions, I am getting the following error, which seems to be related with the uname path:

enrique@acer:~/madwifi$ sudo make install BINDIR=/usr/bin MANDIR=/usr/share/man
cd: 1: can't cd to /lib/modules/2.6.24-19-rt/build
Makefile.inc:66: *** /lib/modules/2.6.24-19-rt/build is missing, please set KERNELPATH.  Alto.

May you give me a hint?

Thanks in advance,

---

### Post by Anduu on 2008-06-09
> **uwe.koch.k said:**
> Hi Anduu,

following your instructions, I am getting the following error, which seems to be related with the uname path:

enrique@acer:~/madwifi$ sudo make install BINDIR=/usr/bin MANDIR=/usr/share/man
cd: 1: can't cd to /lib/modules/2.6.24-19-rt/build
Makefile.inc:66: *** /lib/modules/2.6.24-19-rt/build is missing, please set KERNELPATH.  Alto.

May you give me a hint?

Thanks in advance,

You need to have the linux-restricted-modules package installed,in your case the real time ones.

```
sudo apt-get install linux-restricted-modules-rt
```

I guess I should append that to the how-to ;)

---

### Post by dan1701a on 2008-06-09
> **Anduu said:**
> Glad I could help :)

Like I said I'm just passing the info along...It's the guys at [Madwifi]("http://madwifi.org/") who deserve all the credit :KS

One thing I should add is you will need to repeat this procedure whenever you get a kernel update.I have just kept the downloaded packages on my system and after booting into a new kernel I do:

```
cd madwifi
make clean
sudo make install BINDIR=/usr/bin MANDIR=/usr/share/man
```

Reboot and I am up and running again.

Hi, Anduu,

I recently installed Ubuntu using the Wubi installer under Windows Vista, and I must say I am impressed with the speed on my 64-bit AMD Athlon X2 processor. However, I too am having problems with my Atheros AR5007EG wireless card. I performed all the steps listed in the previous posts, and it connected for a brief time; yet now, I cannot connect using wifi at all, and my wifi connection is listed as "ath0:avahi". I do not understand what that means, except that I cannot connect with that interface. And when I attempt to configure it, I am told the "interface name does not exist." (The same holds true for my Gig-E Ethernet connection, though, which makes me think there's something wrong with the networking module instead.)

Also, I cannot turn on my wireless card using my "enable wireless" button - it simply does not seem to function. This may be related to the problem.

Do you have any other insight into why this is happening? My computer is an Acer 4520-5458, AMD Athlon 64 X2 (TK-57), Atheros AR5000EG 802.11b/g wireless, nVidia GeForce 7000M graphics, 120gb HDD, 1gb RAM.

Thanks in advance for your help.

---

### Post by uwe.koch.k on 2008-06-10
> **Anduu said:**
> You need to have the linux-restricted-modules package installed,in your case the real time ones.

```
sudo apt-get install linux-restricted-modules-rt
```

I guess I should append that to the how-to ;)
Hi Anduu,

I did that and the system tells me that the *rt version already is the latest. I am stucked. By coincidence, the laptop I am configuring is the same as Dan1701a's.

---

### Post by uwe.koch.k on 2008-06-10
> **Anduu said:**
> You need to have the linux-restricted-modules package installed,in your case the real time ones.

```
sudo apt-get install linux-restricted-modules-rt
```

I guess I should append that to the how-to ;)

> **uwe.koch.k said:**
> Hi Anduu,

I did that and the system tells me that the *rt version already is the latest. I am stucked. By coincidence, the laptop I am configuring is the same as Dan1701a's.

uname -r tells me 2.6.24-19-rt, but last build tells me /lib/modules/2.6.24-19-generic/build . How may I build 2.6.24-19-rt?

---

### Post by L337_K3y5 on 2008-06-10
I did the exact same thing you did to work it, and I have the same Wireless Stuff (trying to get through this fast).  I get everything started up, and it shows my network just fine, but I can't get online with anything?  What gives?  Here is my pic:
[IMG]http://i302.photobucket.com/albums/nn102/Keyblade_frog/Stupid_Photobucket.png[/IMG]
Oh no need to read this, because I got it working...Thank you!!!  I've spent forever looking for a fix!  Although, you need to put in the post that you have to uncheck the drivers before installation or after, then restart, reactivate them, restart again to function.

---

### Post by DapperMe17 on 2008-06-10
Hello Anduu,

Thank you for your work!

Would you be able to tell me how to get a copy of "build-essential", "linux-restricted-module" and "subversion"? 

I do not have a wired connection to my Kubuntu 8.04 machine. However, I do have the LiveCD. 

Also, how would I accomplish your step #4, without a internet connection to the Kubuntu machine?

Thanks for any help you could offer.

---

### Post by freakwillie on 2008-06-10
> **DapperMe17 said:**
> 

Would you be able to tell me how to get a copy of "build-essential", "linux-restricted-module" and "subversion"? 



Go to [http://packages.ubuntu.com/hardy/build-essential](http://packages.ubuntu.com/hardy/build-essential) and download the right package for your cpu type. Transfer the file (its a .deb file) to the computer in question and double click the file. 

Hope I've helped.

---

### Post by logrusmage on 2008-06-10
Ok... this didn't work at all ;_;

Now I can't even scan for networks... wtf...

I had it working with ndiswrapper too.... damn

How the hell do I fix or undue this all????

---

### Post by Anduu on 2008-06-10
For those who can't get it to work try as L337_K3y5 suggested...go to System->Administration->Hardware Drivers and uncheck both Atheros restricted drivers,reboot and try again.

If you haven't deleted the source code yet,clean up what you did previously by swtching to the madwifi dir and run
```
sudo make uninstall
make clean
```

I am not sure why some are having problems getting the appropriate linux-restricted-modules packages.Run in terminal
```
uname -r
```
Then open synaptic and manually install the appropriate linux-restricted-modules package.

---

### Post by Anduu on 2008-06-10
> **logrusmage said:**
> Ok... this didn't work at all ;_;

Now I can't even scan for networks... wtf...

I had it working with ndiswrapper too.... damn

How the hell do I fix or undue this all????

Without some specifics on what went wrong we can't help you.If need be all you need to do to get ndiswrapper back up is repeat whatever steps you took to make it work in the first place.

> **DapperMe17 said:**
> Hello Anduu,

Thank you for your work!

Would you be able to tell me how to get a copy of "build-essential", "linux-restricted-module" and "subversion"? 

I do not have a wired connection to my Kubuntu 8.04 machine. However, I do have the LiveCD. 

Also, how would I accomplish your step #4, without a internet connection to the Kubuntu machine?

Thanks for any help you could offer.

Getting and installing packages from [http://packages.ubuntu.com/hardy](http://packages.ubuntu.com/hardy) can be a tricky business...you need to find the packages plus any dependencies they require.This can quickly add up to a lot of files and installing them all through debs can be a pain.I highly recommend you beg/borrow/steal a wired connection somehow.

---

### Post by logrusmage on 2008-06-10
> **Anduu said:**
> Without some specifics on what went wrong we can't help you.If need be all you need to do to get ndiswrapper back up is repeat whatever steps you took to make it work in the first place.


Sigh... just tried that, ndiswrapper doesn't work anymore.

Question:

HAL is not checked off, but it still says IN USE. =/ The other driver has a red circle and says disabled. Is this the problem that is not allowing my ndiswrapper to work?

---

### Post by Anduu on 2008-06-10
> **logrusmage said:**
> Sigh... just tried that, ndiswrapper doesn't work anymore.

Question:

HAL is not checked off, but it still says IN USE. =/ The other driver has a red circle and says disabled. Is this the problem that is not allowing my ndiswrapper to work?

From what I recall from when I used ndiswrapper the atheros drivers needed to be disabled before ndiswrapper could be installed/enabled.

---

### Post by logrusmage on 2008-06-10
> **Anduu said:**
> From what I recall from when I used ndiswrapper the atheros drivers needed to be disabled before ndiswrapper could be installed/enabled.

But how can I disable it? It is unchecked, but it still says in use...

---

### Post by Anduu on 2008-06-10
> **logrusmage said:**
> But how can I disable it? It is unchecked, but it still says in use...

Did you reboot?

---

### Post by logrusmage on 2008-06-11
> **Anduu said:**
> Did you reboot?

Multiple times. Still unchecked, still in use.

---

### Post by Anduu on 2008-06-11
> **logrusmage said:**
> Multiple times. Still unchecked, still in use.

```
gksudo gedit /etc/modules
```

Remove any reference to ath_hal and ath_pci.Save and reboot.

---

### Post by logrusmage on 2008-06-11
Well, that worked for that small problem, but didn't help my internet at all.

Think I should try your way again? When I did it the first time HAL was still active but unchecked.

(Thanks so much for all of the help BTW)

---

### Post by Anduu on 2008-06-11
> **logrusmage said:**
> Well, that worked for that small problem, but didn't help my internet at all.

Think I should try your way again? When I did it the first time HAL was still active but unchecked.

(Thanks so much for all of the help BTW)

It can't hurt to try again...leave them unchecked.
Just remember to watch carefully and take note of any errors.

---

### Post by logrusmage on 2008-06-11
> **Anduu said:**
> It can't hurt to try again...leave them unchecked.
Just remember to watch carefully and take note of any errors.

Leave them unchecked even at the end?

If I do recheck them, do I recheck both?

I got no errors, this time at least.

---

### Post by Anduu on 2008-06-11
> **logrusmage said:**
> Leave them unchecked even at the end?

If I do recheck them, do I recheck both?

I got no errors, this time at least.

I rechecked both.Try it then reboot.

---

### Post by logrusmage on 2008-06-11
> **Anduu said:**
> I rechecked both.Try it then reboot.

They're both suddenly in use... w/e... rebooting now.

EDIT: Yeah... still can't see any networks. iwlist turns up nothing as well =/

;_; This is ridiculous. It worked at RANDOM times with ndiswrapper, I would start it up and it would have internet, then the next twelve times I started it up, I couldn't get an IP.

It has been a month since I've gotten this computer. This is so frustrating.

> beowolf@beowolf-laptop:~$ sudo iwconfig
[sudo] password for beowolf: 
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11b  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:0 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



This look normal to you?

> beowolf@beowolf-laptop:~$ sudo dhclient atho
There is already a pid file /var/run/dhclient.pid with pid 6225
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
SIOCSIFADDR: No such device
atho: ERROR while getting interface flags: No such device
atho: ERROR while getting interface flags: No such device
wifi0: unknown hardware address type 801
Bind socket to interface: No such device


Ok... so why is there no such device...?

---

### Post by Anduu on 2008-06-11
Man I am just as baffled as you are.

Does your laptop have a wireless on/off button?Try it and see what it does.

You could also try leaving the restricted drivers unchecked...my nvidia drivers are unchecked but shows in use and they still works
.
Also right click the network manager icon and see if the enable wireless option is there.

---

### Post by burakerenn on 2008-06-11
Hello there, tried to get rid of ndiswrapper but seems madwifi doesn't like me. :(

My kernel was 2.6.24-16-generic.
Installing subversion, build-essential and restricted modules returned already have the newest result.
I uninstalled ndiswrapper.

Then here's the error message :(

fea@fea-laptop:~/madwifi$ sudo make install BINDIR=/usr/bin MANDIR=/usr/share/man
Makefile.inc:161: *** TARGET x86_64-elf is invalid, valid targets are: .  Stop.

Then I booted 2.6.24-18-generic kernel.

fea@fea-laptop:~/madwifi$ sudo apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
fea@fea-laptop:~/madwifi$ sudo apt-get install linux-restricted-modules-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-restricted-modules-2.6.24-18-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
fea@fea-laptop:~/madwifi$ sudo apt-get install subversion
Reading package lists... Done
Building dependency tree       
Reading state information... Done
subversion is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
fea@fea-laptop:~/madwifi$ mv hal hal.old
mv: cannot stat `hal': No such file or directory
fea@fea-laptop:~/madwifi$ sudo make install BINDIR=/usr/bin MANDIR=usr/share/man
Makefile.inc:161: *** TARGET x86_64-elf is invalid, valid targets are: .  Stop.

Any help? :(

---

### Post by freakwillie on 2008-06-11
Just to register: it worked for HP Pavillion DV6768Se (Special Edition) with Atheros AR5006X and Ubuntu 8.04 Hardy Heron 64 Bits.

So now all the fellows from search engines will be taken here. :)

---

### Post by knut100 on 2008-06-11
Okay, here it goes.

I've tried this som many times now. And I think there now is several reasons why it doesn't work. 
Anyway, you Anduu sound like the person to set things straight.:)

FACTS;
Acer Aspire 7520 w/ wifi-button that will glow red when on, hasn't happend

Atheros A5007EG (I'm quite certain)

Ubuntu Hardy Heron 8.04 AMD64bits

have tried madwifi/ndiswrapper/unchecking/unistalling/installing/blacklisting and so on and NEVER GOTTEN THE WIFI UP AT ALL. Don't get the option in manual internet-config.

ERRORS: 

when reaching code; ```
sudo modprobe ath_pci
```
I get the error;
```
WARNING: /etc/modprobe.d/blacklist line 41: ignoring bad line starting with '&#8220;blacklist'
WARNING: /etc/modprobe.d/blacklist line 42: ignoring bad line starting with '&#8220;blacklist'
```

let's start there, and if you have any other brilliant ideas, PLEASE inform me.

Thanks in advance
Knut (****** up first-timer from Norway):confused:

---

### Post by Anduu on 2008-06-11
**[COLOR="Red"]This information has been appended to the main how-to[/COLOR]**

It appears things are changing quickly in regards to official support from Madwifi.
There is now a working snapshot which includes a new hal from Madwifi as opposed to the 3rd party patched  hal we have been using.

```
svn co https://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6
cd ~/madwifi-hal-0.10.5.6
make
sudo make install
sudo depmod -ae
sudo modprobe ath_pci
echo ath_hal | sudo tee -a /etc/modules
echo ath_pci | sudo tee -a /etc/modules
```

I have implemented the changes on my laptop and all is functioning.

Hopefully this will resolve the issues some have been experiencing.Please indicate whether or not this makes a difference so I can append the how-to accordingly.

---

### Post by knut100 on 2008-06-11
Can you please check out my problem?

---

### Post by Anduu on 2008-06-11
> **knut100 said:**
> Okay, here it goes.

I've tried this som many times now. And I think there now is several reasons why it doesn't work. 
Anyway, you Anduu sound like the person to set things straight.:)

FACTS;
Acer Aspire 7520 w/ wifi-button that will glow red when on, hasn't happend

Atheros A5007EG (I'm quite certain)

Ubuntu Hardy Heron 8.04 AMD64bits

have tried madwifi/ndiswrapper/unchecking/unistalling/installing/blacklisting and so on and NEVER GOTTEN THE WIFI UP AT ALL. Don't get the option in manual internet-config.

ERRORS: 

when reaching code; ```
sudo modprobe ath_pci
```
I get the error;
```
WARNING: /etc/modprobe.d/blacklist line 41: ignoring bad line starting with '&#8220;blacklist'
WARNING: /etc/modprobe.d/blacklist line 42: ignoring bad line starting with '&#8220;blacklist'
```

let's start there, and if you have any other brilliant ideas, PLEASE inform me.

Thanks in advance
Knut (****** up first-timer from Norway):confused:

Check /etc/modprobe.d/blacklist
```
gksudo gedit /etc/modprobe.d/blacklist
```
...make sure ath_pci and ath_hal are not listed.If they are remove the entries.

Try the new snapshot I posted above and see if it makes a difference.

My laptop is the same model as yours.The wireless indicator led on my laptop does not light up either however wireless works fine.

---

### Post by knut100 on 2008-06-11
*******, there it was. Thank you, man!

Now I only need to fix one more thing, and my ubuntu adventure will be on its way!

Thanks!

---

### Post by rowlf63 on 2008-06-11
Awesome!!!
You just made my day!
After struggling for days, It just worked!

Acer Aspire 7520 Hardy 8.04 64 bit

Thanks! \\:D/

---

### Post by Anduu on 2008-06-11
Glad to see this is working out for so many :)

I have added a note to the OP updating the instructions and will modify the how-to accordingly.

---

### Post by braveerudite on 2008-06-11
> **Anduu said:**
> **[COLOR="Red"]This information has been appended to the main how-to[/COLOR]**

It appears things are changing quickly in regards to official support from Madwifi.
There is now a working snapshot which includes a new hal from Madwifi as opposed to the 3rd party patched  hal we have been using.

```
svn co https://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6
cd ~/madwifi-hal-0.10.5.6
make
sudo make install
sudo depmod -ae
sudo modprobe ath_pci
echo ath_hal | sudo tee -a /etc/modules
echo ath_pci | sudo tee -a /etc/modules
```

I have implemented the changes on my laptop and all is functioning.

Hopefully this will resolve the issues some have been experiencing.Please indicate whether or not this makes a difference so I can append the how-to accordingly.

Wow dude this is even better news since now we are fetching the files directly from the official MAd Wi-Fi site.  No need to worry now that the files needed to get this thing working could be taken down in the future.  I'm glad we are getting now official support.

By the way you need to put in your guide that both restricted Atheros drivers need to be uncheck and then reboot before starting this whole thing.  I mean that's the way I have been doing it and has work in 3 separate times for me.

---

### Post by Anduu on 2008-06-11
> **braveerudite said:**
> Wow dude this is even better news since now we are fetching the files directly from the official MAd Wi-Fi site.  No need to worry now that the files needed to get this thing working could be taken down in the future.  I'm glad we are getting now official support.

By the way you need to put in your guide that both restricted Atheros drivers need to be uncheck and then reboot before starting this whole thing.  I mean that's the way I have been doing it and has work in 3 separate times for me.

Yes this is definitely a good thing.They say barring any major problems it won't be long before it hits trunk.So hopefully this will mean native support for Ubuntu soon.

When I initially found this info and tried it my Atheros restricted drivers were already disabled so I never considered it a factor.You are probably correct however that they should be disabled before installing this new snapshot.I'll add it.

Another thing I have come to realize is that for those who are using ndiswrapper presently they were most likely instructed to blacklist ath_pci and ath_hal so we will have to fix that as well.

OK updating I go ;)

---

### Post by Anduu on 2008-06-11
I added a poll...please vote.

Even if you didn't feel the need to post a comment I would like to know how many people tried it and what the results were.

---

### Post by freakwillie on 2008-06-12
I'm glad there's support from the official mad-wifi developers. I've tried and it works fine for me. 

I hope Ibex features it natively, having it to work out of the box would be great. 

The last thing I need to setup to have my desktop fully functional is the internal mic, already upgraded the Alsa drivers but nothing. Hopefully I'll fix that soon.

---

### Post by uwe.koch.k on 2008-06-13
The site of [http://madwifi.org](http://madwifi.org) is down:( since yesterday.

enrique@acer:~$ svn co [https://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6](https://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6)
svn: requerimiento PROPFIND falló en '/madwifi/branches/madwifi-hal-0.10.5.6'
svn: PROPFIND de '/madwifi/branches/madwifi-hal-0.10.5.6': Could not resolve hostname `svn.madwifi.org': No hay direcci  n asociada con el nombre de host ([https://svn.madwifi.org](https://svn.madwifi.org))
enrique@acer:~$ 

Well, I got to be patient in order to see all things working strait on!:)

---

### Post by freakwillie on 2008-06-13
> **uwe.koch.k said:**
> The site of [http://madwifi.org](http://madwifi.org) is down:( since yesterday.

enrique@acer:~$ svn co [https://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6](https://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6)
svn: requerimiento PROPFIND falló en '/madwifi/branches/madwifi-hal-0.10.5.6'
svn: PROPFIND de '/madwifi/branches/madwifi-hal-0.10.5.6': Could not resolve hostname `svn.madwifi.org': No hay direcci  n asociada con el nombre de host ([https://svn.madwifi.org](https://svn.madwifi.org))
enrique@acer:~$ 

Well, I got to be patient in order to see all things working strait on!:)

I uploaded it for you: [http://www.mediafire.com/?mjokzl02dxu]("http://www.mediafire.com/?mjokzl02dxu")

---

### Post by uwe.koch.k on 2008-06-13
> **freakwillie said:**
> I uploaded it for you: [http://www.mediafire.com/?mjokzl02dxu]("http://www.mediafire.com/?mjokzl02dxu")

Thank you so much. I appreciate the help and will give a try tomorrow, since I am not in front of the laptop now.

---

### Post by smaliz on 2008-06-13
Thankyou freakwillie for uploading the file. I have gone crazy since last night trying to find out what happened to the madwifi servers. 
And ofcourse thankyou Anduu. This saved me from dumping Ubuntu and going to Vista.

---

### Post by Anduu on 2008-06-13
Wow the Madwifi site is still down...wonder what's up with that :(

Thanks willie for uploading the files.:KS

---

### Post by itchy8me on 2008-06-14
still down :-|

---

### Post by TamirEr on 2008-06-14
Hi Anduu,

Thank you very much for sharing this information.
I tried it on my laptop, which has a [gigabye gn-ws50g-rh]("http://www.gigabyte.com.tw/Products/Communication/Products_Spec.aspx?ProductID=2684") wireless card and it worked!

All the best,
Tamir

---

### Post by itchy8me on 2008-06-14
indeed thanks. for the upload as well.
works on opensuse factory(11.0) 64bit, Acer Aspire 7520

---

### Post by logrusmage on 2008-06-14
Hey! I'm back! Wirelessly! The stuff you posted a few pages ago (the madwifi update os something) did it!

However, WICD still doesn't recognize my card like it did with ndiswrapper. I had to do it manually through the terminal. Is there any way I can get it to set up on start up on start up? It'd be inconvenient but I'll deal. Anyone have, like, a script tutorial or something?

EDIT: Nevermind. I had to change my wireless device from wlan0 to ath0. I really hope this holds after a reboot (all other fixes failed after reboot). Thanks for everything OP!!!!!

---

### Post by L337_K3y5 on 2008-06-14
Hey Anduu, you should add the chipset now into this list of supported Chipsets, you'll just have to set it correctly.:)
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

---

### Post by Anduu on 2008-06-14
> **logrusmage said:**
> Hey! I'm back! Wirelessly! The stuff you posted a few pages ago (the madwifi update os something) did it!

However, WICD still doesn't recognize my card like it did with ndiswrapper. I had to do it manually through the terminal. Is there any way I can get it to set up on start up on start up? It'd be inconvenient but I'll deal. Anyone have, like, a script tutorial or something?

EDIT: Nevermind. I had to change my wireless device from wlan0 to ath0. I really hope this holds after a reboot (all other fixes failed after reboot). Thanks for everything OP!!!!!

Hey that's great to hear you sorted it out :)

If you are still having troubles with WICD suggest going back to Network Manager.It seems to work well with Madwifi.

> **L337_K3y5 said:**
> Hey Anduu, you should add the chipset now into this list of supported Chipsets, you'll just have to set it correctly.:)
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

I think it would be prudent to wait until it is being supplied by the restricted drivers manager before claiming 100% support

---

### Post by L337_K3y5 on 2008-06-15
> **Anduu said:**
> 
I think it would be prudent to wait until it is being supplied by the restricted drivers manager before claiming 100% support
True, but its nearly there, isn't Atheros already trying to support the 64 bit version now anyway?:)
Ok, I just wish it would be 100% supported already!
Oh, just thought about it, shouldn't this also be in the networking/wireless section?  Not saying its supposed to be there, but shouldn't there be a guide copy there too?

---

### Post by lostsoul79 on 2008-06-15
hello all ubers in the land of linux wifi hell :)

6 (SIX) hours now i have been trying to get this to work... six

system config ---

amd 64
nforce 560 chipset
atheros 5006 -- NOT 5007!!!!!
2gb ram
vista / ubuntu x64 - 8.04 dual boot

i actually at one point got it working and... please smack me... had to repartition my harddrive.... so i sat down and with the thought that it couldnt be quite so hard to get it going again since i just did it... i started over

the first time i made a mess --- btw im a linux noob... probably THE KING of linux noobs.... -- but i did notice that i had the same problems everyone else was having but only in peices....

problem steps... 
first (basic) card is "recognized" by linux, and "installed" -- at this point i cannot even see the card listed in network manager.

second... follow the various steps SCATTERED throughout the web on how to install your atheros xxxx wifi card... -- went to 5 different places and followed 3 different how-to's.. -- ended up with the ability to see my router and have my laptop laugh at me while pretending to connect...

third... oops... i made a few mistakes *read : superior changes based on the knowledge of zero* .. but then i realized .. umm.. its working...

things to note, and im only going from my reinstall steps...

i followed the how-to at :
[http://ubuntuforums.org/showthread.php?t=800686](http://ubuntuforums.org/showthread.php?t=800686)
including the pre-x script

i used the drivers available at :
[http://www.mediafire.com/?mjokzl02dxu](http://www.mediafire.com/?mjokzl02dxu)

--the link way up top there

then i read this post and followed the majority of the directions here... accept.....2 minor things....


i never re-enabled my wireless card drivers in system > admin > drivers

i did this how-to first and failed finding / connectiong to a wifi network but when i did it in this order it worked

so somwhere along the lines.... doing somthign else got this how-to to not be a smashing experience for my laptop

thank you to ALL the various solution havers... and to the solution writer for this thread


gl to the next poor noob like me who is #1 when it comes to the manufacturer, stores, and salespersons that insist that the customer is the most important thing..... after thier done taking a **** that is

oh... this wifi card.... a pain in the *** to get working in vista or xp as well so i nominate atheros for the lick azz award given out by maximum pc

---

### Post by ltsat on 2008-06-15
:lolflag:
worked perfectly on acer aspire 7520g (amd turion 64 x2 + atheros ar5007eg) w/ ubuntu 8.04 amd64.
congratulations to the madwifi guys and thank you mr anduu for bring it up!
:lolflag:

---

### Post by freakwillie on 2008-06-15
The madwifi website is working again :)

---

### Post by Vishal Agarwal on 2008-06-17
Dear Anduu,

First of all,

Thanks for all this support.

But I Had still one problem. when ever I am booting my machine, the wireless card remain off. I have to start it switiching on using the physical switch.

My Machine is ASUS F5RL. Pls can u tell me how the hw can be started automatically while machine is going up.

I hope I made you clear about my problem.

Thanks again in advance.

Vishal Agrwal

---

### Post by phidia on 2008-06-18
I was using ndiswrapper on this install of 7.10 x86_64 on a HP dv6707us laptop with the dreaded 2425 chipset AR5007EG card. Ndiswrapper worked however I believe it caused issues with suspend.
This howto set up my card perfectly! I don't believe there was madwifi support for this card in 64 bit before this. I'm on the road testing it now-so far so good and while there are still some snags with resume when it does resume the wireless comes back too!
Thanks very much for this!!!

---

### Post by oblivious on 2008-06-18
And I'm saying this from the bottom of my heart... I love you man.

---

### Post by pico977 on 2008-06-19
Hi

I have ubuntu 8.04 64bit, and I installed madwifi for my atheros 5007, like you suggest in this post.
Now my wifi card work, it is releaved correctly by os, but it releave only the signal of wpa and wpa2's AP, while my AP is configured to work with WEP protocol.
I cannot change my AP to work to wpa or wpa2, so, I don't connect to my AP.
Have you any idea?

Thank's

PS: sorry for my english

---

### Post by MarcG on 2008-06-19
I've got a new Compaq Presario F761US, with the AR242x, and am just now trying to get 8.04-64 running. The wireless didn't work "out of the box", so I tried various things. The latest is this Howto. It got me closer, but no connect yet. Before this I had no wireless devices showing up in Network Tools, Network Settings, iwconfig, or ifconfig.

Here is the iwconfig output:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:16484  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

The Network Settings just shows Wireless Network in "Roaming mode enable".
Network Tools shows wifi0 has some small traffic and ath0 has nothing going on.

And ifconfig is:
```

ath0      Link encap:Ethernet  HWaddr 00:1f:3a:46:a0:c7  
          inet6 addr: fe80::21f:3aff:fe46:a0c7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:1e:68:27:6e:e4  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe27:6ee4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:307 errors:0 dropped:0 overruns:0 frame:0
          TX packets:359 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:238376 (232.7 KB)  TX bytes:72977 (71.2 KB)
          Interrupt:252 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:98 errors:0 dropped:0 overruns:0 frame:0
          TX packets:98 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4900 (4.7 KB)  TX bytes:4900 (4.7 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-1F-3A-46-A0-C7-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20285 errors:0 dropped:0 overruns:0 frame:804
          TX packets:487 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:2384339 (2.2 MB)  TX bytes:22402 (21.8 KB)
          Interrupt:19 


```

It looks like this worked more most people, so I'm sure I goofed somewhere. Any ideas?

Thanks.
--Marc

---

### Post by Anduu on 2008-06-19
First off double/triple check to make sure you followed every step correctly.

Left click on the network manager icon...it should show any wireless networks in range if the card is working.
Also right click and see if wireless is enabled.

It is possible the other things you have tried have left your system in a state where it can't work.Could you elaborate on what you have tried so far?

My best suggestion if all else fails is try a fresh install and see what happens.

---

### Post by Anduu on 2008-06-19
> **pico977 said:**
> Hi

I have ubuntu 8.04 64bit, and I installed madwifi for my atheros 5007, like you suggest in this post.
Now my wifi card work, it is releaved correctly by os, but it releave only the signal of wpa and wpa2's AP, while my AP is configured to work with WEP protocol.
I cannot change my AP to work to wpa or wpa2, so, I don't connect to my AP.
Have you any idea?

Thank's

PS: sorry for my english

Not sure why however I highly recommend you switch to wpa/wpa2 as wep is not very secure these days

---

### Post by pico977 on 2008-06-20
> Not sure why however I highly recommend you switch to wpa/wpa2 as wep is not very secure these days 

many thanks

---

### Post by MarcG on 2008-06-20
> **Anduu said:**
> First off double/triple check to make sure you followed every step correctly.

My best suggestion if all else fails is try a fresh install and see what happens.

I did a few things before trying this Howto, I disabled and re-enabled the Atheros drivers, one at a time. I also tried removing the Atheros drivers, but that caused my nVidia video driver to stop working. So I just did a clean install, but now the madwifi.org is not responding. Oh well,... I guess I get to try again later.

---

### Post by Anduu on 2008-06-20
> **MarcG said:**
> I did a few things before trying this Howto, I disabled and re-enabled the Atheros drivers, one at a time. I also tried removing the Atheros drivers, but that caused my nVidia video driver to stop working. So I just did a clean install, but now the madwifi.org is not responding. Oh well,... I guess I get to try again later.

Here is a link to the drivers [http://www.mediafire.com/?mjokzl02dxu](http://www.mediafire.com/?mjokzl02dxu)

All you need to do is extract the archive to your home folder and skip ```
svn co https://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6
```

---

### Post by MarcG on 2008-06-21
THANKS, and a very big WOO HOO!! to you. I am wirelessly typing right now.

Take care and have a great life.

--Marc

---

### Post by uwe.koch.k on 2008-06-21
Hi Anduu,

I am still stuck on a build problem, as posted before, any idea how to overcome the problem?

enrique@acer:~/madwifi-hal-0.10.5.6$ make
cd: 1: can't cd to /lib/modules/2.6.24-19-rt/build
Makefile.inc:66: *** /lib/modules/2.6.24-19-rt/build is missing, please set KERNELPATH.  Alto.
enrique@acer:~/madwifi-hal-0.10.5.6$ 

I updated as of today with the hope the build would appear, but nothing happened. You don't know how much I would like to integrate the happy 24 guys from the poll!

---

### Post by Anduu on 2008-06-21
> **uwe.koch.k said:**
> Hi Anduu,

I am still stuck on a build problem, as posted before, any idea how to overcome the problem?

enrique@acer:~/madwifi-hal-0.10.5.6$ make
cd: 1: can't cd to /lib/modules/2.6.24-19-rt/build
Makefile.inc:66: *** /lib/modules/2.6.24-19-rt/build is missing, please set KERNELPATH.  Alto.
enrique@acer:~/madwifi-hal-0.10.5.6$ 

I updated as of today with the hope the build would appear, but nothing happened. You don't know how much I would like to integrate the happy 24 guys from the poll!

Strange...that error indicates the linux-restricted-modules for your kernel is not installed.

Try going into synaptic and check to see if the restricted modules package for your kernel is installed.If it is try removing and reinstalling it.

Double/triple check the how to and make sure you did everything correctly.

---

### Post by phidia on 2008-06-22
There's no good way to say this and I noticed after installing madwifi that my connection (opening/resolving webpages) was quite slow. I did some small tests like checking using [this site]("http://reviews.cnet.com/7004-7254_7-0.html"), I need to do more, but it seems that the madwifi driver is very slow-for me-compared to the windows driver with ndiswrapper. It's about a third the speed of using the windows driver.
I wish I knew more about how to tweak or fix that.

---

### Post by Anduu on 2008-06-22
> **phidia said:**
> There's no good way to say this and I noticed after installing madwifi that my connection (opening/resolving webpages) was quite slow. I did some small tests like checking using [this site]("http://reviews.cnet.com/7004-7254_7-0.html"), I need to do more, but it seems that the madwifi driver is very slow-for me-compared to the windows driver with ndiswrapper. It's about a third the speed of using the windows driver.
I wish I knew more about how to tweak or fix that.

That is a shame....:(

I do notice a slight performance hit but nothing on the scale you are talking about.I am far from being an expert on the matter but maybe someone else may have a tip or two.

Just remember however,the driver is still being developed so I'm sure performance will be improved.

---

### Post by phidia on 2008-06-22
> **Anduu said:**
> That is a shame....:(

I do notice a slight performance hit but nothing on the scale you are talking about.I am far from being an expert on the matter but maybe someone else may have a tip or two.

Just remember however,the driver is still being developed so I'm sure performance will be improved.

I am glad we have a open source driver for 64 bit so don't get me wrong.
I think it's probably a combo of less range and something else? I do need to be closer to the wifi signal now. I will keep looking for the latest drivers I think and thanks for the reply.

---

### Post by phidia on 2008-06-22
Just following up with the hard data (which I am a little glum about :( )

Often subjective phrases or perceptions are used to describe performance but I like tests.
The bandwidth meter test that I linked in my previous post confirms what I've been experiancing.

With a wired connection-my desktop done last night I got below the stated dsl rate but still an ok 650Kbps.

This morning I performed the bandwidth test using a usb install of gutsy that has ndiswrapper, 
and then my internal hard drive install of gutsy with madwifi the tests were performed within mintues of each other.

Using ndiswrapper the test showed 668.5 Kbps

Using madwifi the test showed  	199.8 Kbps

Added 6-23-08 @ approx 8PM: I checked and rechecked the connection speed over the last day and a half.
The madwifi driver connection continually came out to 1/3 the speed of ndiswrapper so for now I switched back to ndiswrapper.

---

### Post by cmcfarland21 on 2008-06-23
:KS One thing I should add is you will need to repeat this procedure whenever you get a kernel update.I have just kept the downloaded packages on my system and after booting into a new kernel I do:

```
cd ~/madwifi-hal-0.10.5.6
make clean
sudo make install

```

Reboot and I am up and running again.
Hopefully this makes your day like it did mine![SIZE="4"][/SIZE][/QUOTE]


I have a HP Pavilion DV6700 and this worked perfectly..  My only question is how you kept the downloaded package on your system.  So I don't have to find a wired connection next time there is a kernel update like today.

---

### Post by phidia on 2008-06-23
> I have a HP Pavilion DV6700 and this worked perfectly..  My only question is how you kept the downloaded package on your system.  So I don't have to find a wired connection next time there is a kernel update like today.


You can just save the directory from unpacking to your /home/yourusername.

---

### Post by Anduu on 2008-06-23
> I have a HP Pavilion DV6700 and this worked perfectly..  My only question is how you kept the downloaded package on your system.  So I don't have to find a wired connection next time there is a kernel update like today.

Once the *svn co ....* command is completed look in your home folder...there will be a folder called madwifi-hal-0.10.5.6 .It contains the sources for the driver.It will be there until you delete it.

---

### Post by hellarough on 2008-06-24
okay i have an hp dv6812nr with the atheros 5007 card for sure. on a fresh install of linux with the most recent kernel. I tried this tutorial and now i can see wireless networks but I am unable to connect to them. here is some out put to give you an idea of what is going on...

```
ryan@therabbithole:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:74916  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ryan@therabbithole:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:1f:e1:19:99:15  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:132 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6600 (6.4 KB)  TX bytes:4503 (4.3 KB)

eth0      Link encap:Ethernet  HWaddr 00:1e:68:6c:5e:a5  
          inet addr:192.168.1.70  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe6c:5ea5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10575 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2054 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2359818 (2.2 MB)  TX bytes:227826 (222.4 KB)
          Interrupt:252 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:216 errors:0 dropped:0 overruns:0 frame:0
          TX packets:216 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10800 (10.5 KB)  TX bytes:10800 (10.5 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-1F-E1-19-99-15-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:83883 errors:0 dropped:0 overruns:0 frame:11552
          TX packets:2829 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:8354532 (7.9 MB)  TX bytes:134261 (131.1 KB)
          Interrupt:19 


```

---

### Post by Anduu on 2008-06-24
> **hellarough said:**
> okay i have an hp dv6812nr with the atheros 5007 card for sure. on a fresh install of linux with the most recent kernel. I tried this tutorial and now i can see wireless networks but I am unable to connect to them. here is some out put to give you an idea of what is going on...

```
ryan@therabbithole:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:74916  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ryan@therabbithole:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:1f:e1:19:99:15  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:132 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6600 (6.4 KB)  TX bytes:4503 (4.3 KB)

eth0      Link encap:Ethernet  HWaddr 00:1e:68:6c:5e:a5  
          inet addr:192.168.1.70  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe6c:5ea5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10575 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2054 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2359818 (2.2 MB)  TX bytes:227826 (222.4 KB)
          Interrupt:252 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:216 errors:0 dropped:0 overruns:0 frame:0
          TX packets:216 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10800 (10.5 KB)  TX bytes:10800 (10.5 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-1F-E1-19-99-15-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:83883 errors:0 dropped:0 overruns:0 frame:11552
          TX packets:2829 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:8354532 (7.9 MB)  TX bytes:134261 (131.1 KB)
          Interrupt:19 


```

I suspect it is a problem with your router/network setup.Can you see your network?

If your network is encrypted make sure you are connecting using the right method.

You can right click the network manager icon and select "edit wireless networks" and change your settings there.

---

### Post by ddg on 2008-06-24
Hi Anduu,

I wanted to say thankyou. After two weeks and now I got everyt thing running.
I could see the wireless device and I need to bring to the place with the facility, that is the only thing left.
Thanks,
ddg

---

### Post by uwe.koch.k on 2008-06-24
Hi Anduu,

I followed your suggestion, tried to remove the linux-restricted-nodules for my *rt kernel. I did not do that, since it also would have removed the *rt kernel, so I reinstalled it. After making, the error still is the same, the build is missing. I also installed the linux-restricted-modules generic, but nothing happened. May be someone else could help me on the matter? I know there is another user that has the same laptop I am using, but don't know if he could succeed installing the driver.

I'm running an acer aspire 4520.

---

### Post by uwe.koch.k on 2008-06-24
> **uwe.koch.k said:**
> Hi Anduu,

I followed your suggestion, tried to remove the linux-restricted-nodules for my *rt kernel. I did not do that, since it also would have removed the *rt kernel, so I reinstalled it. After making, the error is still the same, the build is missing. I also installed the linux-restricted-modules generic, but nothing happened. May be someone else could help me on the matter? I know there is another user that has the same laptop I am using, but don't know if he could succeed installing the driver.

I'm running an acer aspire 4520.

After I wrote this, I checked on another PC (Desktop), where I'm running the same configuration, except for the wireless connection: there is a build in the /lib/modules/2.6.24-19-rt directory, so the remaining question is how to build it in the laptop? I don't have any idea.

---

### Post by Popoi on 2008-06-25
This Howto works perfect on Compaq Presario F752LA. Before this, it was a hell...

From the deep of my hearth, THANK YOU!! :D

---

### Post by skb on 2008-06-25
This worked perfectly for me on an HP Pavilion dv6809wm with an Atheros 5007EG. Thanks a ton for the help. You really have no idea how great this is for me, since the last time I tried Ubuntu (a couple of years ago), the wireless support was the thing that made me give it up!

---

### Post by hellarough on 2008-06-25
> **Anduu said:**
> I suspect it is a problem with your router/network setup.Can you see your network?

If your network is encrypted make sure you are connecting using the right method.

You can right click the network manager icon and select "edit wireless networks" and change your settings there.

Yeah I can see tons of wireless networks (and mine has the strongest signal) but I cant connect to any of them (even the unencrypted ones, although those do have a weak signal).

---

### Post by BKonkle on 2008-06-25
Oh my gosh, Anduu you are amazing.  I've been NDISWrapper since Hardy Beta on my HP DV6000 laptop.  The instructions in your very first post worked flawlessy!  You saved me from having to remove and then re-add the NDISWrapper driver every time I rebooted.  Thank you so much for sharing your discovery!

---

### Post by kungfupanda on 2008-06-26
Great work!:guitar:
My card is Atheros 5006x :lolflag:running on ubuntu 8.04-amd64,after intalling ndiswrapper,I could 

see my wireless networks but wasn't able to connect to them no matter how I configured 

arguments automatically or manully.

:KSThank you and MadWiFi developers.

---

### Post by gpc on 2008-06-26
> **Anduu said:**
> 
Hopefully this makes your day like it did mine![SIZE="4"][/SIZE]

omg you just did:):):)

This guide worked flawlessly on a Acer Aspire 4720Z

---

### Post by uwe.koch.k on 2008-06-26
Hi Anduu,

finally, I am number 33, a christian coincidence. After comparing the distros, I found that on my laptop wasn't a linux-headers* file downloaded.

Thanks to all of you for being so patient and thanks Anduu for posting this forum.

---

### Post by Anduu on 2008-06-26
> **uwe.koch.k said:**
> Hi Anduu,

finally, I am number 33, a christian coincidence. After comparing the distros, I found that on my laptop wasn't a linux-headers* file downloaded.

Thanks to all of you for being so patient and thanks Anduu for posting this forum.

Hey that's great!

I am really glad too hear you sorted it out :KS

---

### Post by ddg on 2008-06-27
[QUOTE=Anduu;5103560][B][COLOR="Red"]Updated June 17,2008 9:23:18 P.M. MST

* Please read this how-to in it's entirety before proceeding[/COLOR][/B]

Oh man this made me sooo happy when I found this!I just have to share ;)

I can't take any credit for this how to but I have tried it out and it works great...no more ndiswrapper for this puppy :)
You can see all the details regarding the lack of support for Atheros on 64bit linux here [http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679) and here [http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192)

Hallo Anduu,

I need your help. I installed ubuntu 8.04 Hardy Heron on Acer Aspire 4520. I have been trying to solve the issue of wireless and vga card.
I found your way and I tried step by step and every thing went on without error.

I could see the wireless device, the wired device and ppp device. Today I brought the notebook to an area with wireless facility. I tried by changing setting the wireless network from enable roaming to static IP. (the place does not use dhcp) but it still does not work.
Any more tips??
rgds,
ddg:confused:

---

### Post by pdl on 2008-06-27
You guys rock!

In order to get the madwifi build working on my new 64 bit ubuntu install, all I had to do is:

apt-get build-dep command

It wouldn't see one of my wifi routers, a dlink 655.  I remembered that I had decreased beacon period to 20ms and increased dtim to 5.  This was so that my stupid t-mobile nokia voip phone would stay connected and actually work reasonably well  ( known problem with the Nokia 6086 rm-260 ).  I scaled these numbers back to 40ms and 1 respectively, voip still works, and now router shows up and works perfectly.  Don't know why, but post here for someone much smarter than me.

Anyway thanks again.

Ubuntu 8.04 hardy (alternate 64bit install)
kernel 2.6.24-19-generic
gnome 2.22.2
Compaq T750US
2.5GB RAM
Dual Core Athlon 64 X2 TK-57

---

### Post by dmbeer on 2008-06-27
Hi Anduu

Thanks for the guide unfortunately I can't seem to get everything working. I am running an Acer Aspire 5520 with a AR5007EG wireless chip.

I have followed your guide step by step even copy and paste this a new install of 8.04 64bit.

The hardware is recognised but just wont connect to any wireless networks. 

here is the output of lspci -v:
```
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: AMBIT Microsystem Corp. Unknown device 0428
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at d0400000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

```

iwconfig shows

```
IEEE 802.11g  ESSID:"Untitled"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=12/70  Signal level=-84 dBm  Noise level=-96 dBm
          Rx invalid nwid:2876  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Any advice suggestions would be great.

Thanks

David

---

### Post by dmbeer on 2008-06-27
Hi

It seems that I had to continue setting my wireless device as described on [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo]("http://madwifi.org/wiki/UserDocs/FirstTimeHowTo"). This also describes how to setup your device with WPA.

I just have some minor issues to clean up.

Thanks

David

---

### Post by squalho on 2008-06-29
You saved me!! I've been able to use the wireless connection only under ubuntu 32 bit, and only with ndiswrapper using the windows driver. This how to is just wonderful!
Thank you so much!

---

### Post by Anduu on 2008-06-29
> **dmbeer said:**
> Hi

It seems that I had to continue setting my wireless device as described on [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo]("http://madwifi.org/wiki/UserDocs/FirstTimeHowTo"). This also describes how to setup your device with WPA.

I just have some minor issues to clean up.

Thanks

David

Cool beans :)

I'll add that link to the how-to in case anyone else has trouble getting connected.

---

### Post by Clemens1947 on 2008-06-30
Fantastic Anduu, you are a whizz.

Acer Aspire 5100
AMD Turion64 x2
Kubuntu 8.04 AMD 64bit
KDE 4.1
AR242x 802.11abg Wireless PCI Express Adapter

Thank you.

---

### Post by Vishal Agarwal on 2008-06-30
Dear **Anduu**,

I am posting again. as I am a no voice user and new to UBUNTU, I did installed my wireless lan card successfully using your instructions given in earlier pages of this post. my madwifi is working well and i can connect to the WIFI networks. **_But now the problem is that during the booting of my laptop the wireless pci card goes off. I need to switch on it using the wireless on/off switch._** can u pls help me how can i get it in switch on state during the booting. And i need not to switch on it with wireless on/off switch.

Pls Help.

I am using ASUS F5RL machine with HARDY 8.04.

I hope I made you clear about my problem.

Thanks again in advance.

Vishal Agarwal

---

### Post by feno102 on 2008-07-02
:KS Hi guys especially Anduu, thanks for your great post here. I was using Acer Aspire 4520 with specification:
AMD Turion 64 x2, NVIDIA GeForece 7000M, 1 GB DDR2 RAM, 80 GB HDD, Atheros 2425 (ARG5007EG) 802.11b/g WLAN.

Ok, for other user of Aspire 4520 who want to activate their wireless using madwifi, here the step by step procedures:
1. Install [COLOR="Blue"]build-essential, linux-restricted-modules[/COLOR], and [COLOR="Blue"]subversion[/COLOR] can 
   be  done by using sudo apt-get install .... or Synaptic Package Manager.
2. Download the file needed (madwifi driver) from 
   _[http://www.mediafire.com](http://www.mediafire.com)  /?mjokzl02dxu_ put in your home 
   directory
3. Go to System > Administration > Hardware Drivers. And then disable both 
   [COLOR="Blue"]Atheros HAL[/COLOR] and [COLOR="Blue"]Support for Atheros 802.11 wireless LAN card[/COLOR], and then 
   reboot. If you succeed, the status of them are "NOT IN USE"
4. Now, open your terminal > Change to root > Home directory > extract 
   madwifi driver using "tar -xvf madwifi....."
5. Type in the command prompt:
   ifconfig ath down
   ifconfig wifi0 down
6. Now go to inside madwifi directory and write
   cd script
   ./madwifi-unload
   ./find-madwifi-modules.sh $(uname -r) 
   (then choose 'r' to remove older madwifi modules)
   cd ..
5. write make, make install, and mod ath_pci respectively. Once you are   
   done go to System > Administration > Hardware Drivers and reenable the 
   atheros driver and reboot.
6. When you enter Ubuntu you already able to configure your wireless but  
   it still deactivated. To activate your wireless, reboot your computer 
   once again and now you can surf again in the virtual world :)

---

### Post by abonon on 2008-07-03
thanks for the guide initial poster! It worked perfectly for after following many other guides not working i was about to give up.  Much appreciated!  :)

---

### Post by djwisdom on 2008-07-04
I would like to thank God first and foremost, and thank you for posting the instructions.
It worked on my Aspire 4520G. No hassles, no tweaking. It just worked after I rebooted.


Here's the specs:

Aspire 4520G
AMD Turion 64x2 Mobile Technology TL-58 (1.9GHz, 2 x 512 KB L2 cache)
Up to 384MB Nvidia GeForce 8400M G TurboCache
2GB DDR2
160 GB HDD
DVD Super Multi DL
802.11b/g WLAN
Bluetooth 2.0+EDR

And finally to everyone at [www.madwifi.org](www.madwifi.org)... keep up the good work!

Sincerely,

Dennis

---

### Post by ASchweitzer on 2008-07-05
YES!!! works great from a fresh install! I skipped the package-installation bits and did those through synaptic as I was updating the rest of my packages.
Thanks you!!!

EDIT: should mention:
Acer Aspire 5100
lspci recognized my card as the AR2425

---

### Post by dmac71 on 2008-07-07
thanks for the how to.  It worked great at home on my WEP Hex secured network.  However, I brought the laptop to work and it will not connect to my office's unsecured wireless network.  I do not understand this.  I have a dual install and when I am in windows, it connects fine.  However, in Ubuntu, it will not connect.  There are like 6 unsecured wireless networks within range and it only connects to one of them.  It will not connect to any of the other networks.  Baffles me.  Does anyone have any ideas on this one?

---

### Post by Tigin on 2008-07-07
i ve set wireless on same laptop more then 3 times every time successfully , here is my simple how-to :

"" sudo apt-get install build-essential ""

get this file :[http://primepage.de/downloads/stuff/misc/madwifi_patch.tar.bz2](http://primepage.de/downloads/stuff/misc/madwifi_patch.tar.bz2)

run ""install sh""

then uncheck "atheros Hardware Access Layer (HAL)" and "support for atheros 802.11 wireless lan cards" in "SYSTEM>ADMINISTRATION>HARDWARE DRIVERS" menu , then restart.

cheers



(My system : AMD64 AthlonX2 Acer Aspire 5520 ubuntu 8.04 64 bit )

---

### Post by Anduu on 2008-07-07
> **Tigin said:**
> i ve set wireless on same laptop more then 3 times every time successfully , here is my simple how-to :

"" sudo apt-get install build-essential ""

get this file :[http://primepage.de/downloads/stuff/misc/madwifi_patch.tar.bz2](http://primepage.de/downloads/stuff/misc/madwifi_patch.tar.bz2)

run ""install sh""

then uncheck "atheros Hardware Access Layer (HAL)" and "support for atheros 802.11 wireless lan cards" in "SYSTEM>ADMINISTRATION>HARDWARE DRIVERS" menu , then restart.

cheers



(My system : AMD64 AthlonX2 Acer Aspire 5520 ubuntu 8.04 64 bit )

Thanks for the tip....It may work fine however I prefer to get the source directly from Madwifi and install it myself rather than through a third party.

---

### Post by Anduu on 2008-07-07
> **dmac71 said:**
> thanks for the how to.  It worked great at home on my WEP Hex secured network.  However, I brought the laptop to work and it will not connect to my office's unsecured wireless network.  I do not understand this.  I have a dual install and when I am in windows, it connects fine.  However, in Ubuntu, it will not connect.  There are like 6 unsecured wireless networks within range and it only connects to one of them.  It will not connect to any of the other networks.  Baffles me.  Does anyone have any ideas on this one?

I haven't had the chance to try connecting to networks other than my own so I can't say whether it would work.

I have no reason to believe it is the driver causing problems connecting to other networks seeing as you can connect to your own.I suspect possibly a network manager issue or some such thing.

Far from being an expert on these things I suggest maybe checking in the networking/wireless forums for similar issues.

---

### Post by hudarsono on 2008-07-08
Hello all,

Very great to see you guys very enthusiastic with it.

By the way, I have followed the guide in front, but my macbook white 2,4Ghz, still did't see the atheros card. I just bought this macbook 2 months ago. I haven't know yet what the type of my atheros chipset.

Do you guys know how to make it works? I am very deserve it.

When I have followed the guide, and open Hardware driver in ubuntu hardy, there is no driver listed. when I type ifconfig :

[INDENT]eth0      Link encap:Ethernet  HWaddr 00:1e:c2:18:49:ba  
          inet6 addr: fe80::21e:c2ff:fe18:49ba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11038 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8683 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14247156 (13.5 MB)  TX bytes:964353 (941.7 KB)
          Interrupt:17 

eth0:avahi Link encap:Ethernet  HWaddr 00:1e:c2:18:49:ba  
          inet addr:169.254.6.177  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:106881 (104.3 KB)  TX bytes:106881 (104.3 KB)
[/INDENT]

My macbook didn't see the atheros.

---

### Post by Rewarp on 2008-07-08
After more than 3 months of frustration, I am glad to find my wireless connection functioning relatively perfectly through the instructions given by Anduu.

Thank you.

Model: Compaq Presario F762AU

---

### Post by ruggrat on 2008-07-09
Thanks for your instructions, sadly, this is one more attempt that didn't work for me.  
I'll dump some stuff here, but it looks like I'll have to go back to fight with (non-functional) ndiswrapper, which at least sees the networks which it refuses to connect to.

Any advice is deeply appreciated.  Next step is to admit defeat and start over with 32 bit instead...

```

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:d4:68:d0  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fed4:68d0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:327 errors:0 dropped:0 overruns:0 frame:0
          TX packets:259 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:349757 (341.5 KB)  TX bytes:52852 (51.6 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1598 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1598 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:79900 (78.0 KB)  TX bytes:79900 (78.0 KB)

lshw -C network
*-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:24:d4:68:d0
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5787m-v3.23 ip=192.168.1.3 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s

```

Edit: with ndis, when I managed to get it to "claim" the atheros card, it lists it as wlan0, but when I removed ndis this time, and installed this madwifi, it stopped working.

---

### Post by db163404 on 2008-07-09
Thanks Anduu, you saved the day. This was great!

---

### Post by uwe.koch.k on 2008-07-11
Hi Anduu,

sadly I am back. On my Acer Aspire 4520 happened something strange: due to a hang-up, I had to pull out the battery. As a consequence, the "radar" lets me see a lot of wireless connection, but I can not establish a communication. On the usual connection I use I have enabled a wpa2 password, which I know, but the radar tells me that it is waiting for the password, when I pass the cursor over it. Passwordless connections do not work either. I removed and reinstalled from scratch, but the problem remains.

Any idea what's going wrong?

---

### Post by Anduu on 2008-07-11
For those having troubles with seeing networks but not being able to connect I highly recommend giving Network Manager 0.7.0 a try.It solves a lot of issues the Hardy version has.

See this thread here [http://ubuntuforums.org/showthread.php?t=848135&highlight=network](http://ubuntuforums.org/showthread.php?t=848135&highlight=network) for more info.

---

### Post by nunnst on 2008-07-11
Worked perfectly for fresh install on Compaq Presario C700.  The wireless indicator light remains in the red state even though wireless works. This is a minor annoyance.  
Thank you for posting this Anduu.

---

### Post by rexon on 2008-07-12
> **Anduu said:**
> Glad I could help :)

Like I said I'm just passing the info along...It's the guys at [Madwifi]("http://madwifi.org/") who deserve all the credit :KS

One thing I should add is you will need to repeat this procedure whenever you get a kernel update.I have just kept the downloaded packages on my system and after booting into a new kernel I do:

```
cd madwifi
make clean
sudo make install BINDIR=/usr/bin MANDIR=/usr/share/man
```

Reboot and I am up and running again.


Thanks!!! Anduu. My wifi now works.

But I have 2 questions:
1. What procedure are you trying to tell us that would be repeated?
2. What download packages?

I do not understand the whole syntax to make my wifi work. I just trusted your instructions. With your final note regarding repeating procedure/s and package, I am lost in the whole jargon of syntax.

I hope you could help and explain to us who are not knowledgable with these. Thanks again, Anduu!!! :)

---

### Post by dmac71 on 2008-07-12
This method did not work for me until I actually reinstalled Ubuntu and started with a clean install--don't know if that helps you or not

---

### Post by uwe.koch.k on 2008-07-12
> **Anduu said:**
> For those having troubles with seeing networks but not being able to connect I highly recommend giving Network Manager 0.7.0 a try.It solves a lot of issues the Hardy version has.

See this thread here [http://ubuntuforums.org/showthread.php?t=848135&highlight=network](http://ubuntuforums.org/showthread.php?t=848135&highlight=network) for more info.

This made a sound connection. Additionally, I had to remove my "default" connection, while "open" connections did it, do not know why. Then I rebooted and, voila, all went o.k., default connection included.

Thanks again for the hint.:cool:

---

### Post by uwe.koch.k on 2008-07-13
Hi Anduu,

something strange happened after my last post and your answer. While working on my laptop, I run out of charge on my battery. As a consequence, after launching, I could not restablish the wireless connection. I do not see the alternative on the network manager hilighted. If I try a new connection, the radar keeps searching, but is not able to connect. Any idea how to enable the wireless connection or what starts the problem?

---

### Post by archer2000 on 2008-07-13
Works fine on **P200-Pro T8100 Bordoso** with a clean install!
Thank you!

---

### Post by lanenoland on 2008-07-14
Thank you very much, Anduu.  I finally got wireless working after two weeks of trying all the other solutions.  This is the way to go. I'm new to Linux and was considering defecting back to Windows if i couldn't get the wireless up.  But I think now I'm a permanent convert.  


I'm running an Atheros AR2425 on an HP dv6000

---

### Post by jeffegg2 on 2008-07-15
Finally got it to work!!!

Computer: Compaq presario C700 with pentium dual core
Provider: ATT with 2WIRE wireless router

I had to use the 64 bit version of ubuntu 8.04! I followed the instructions here, and it showed the 2WIRE networks, I set up the WEP hex and passwork, but it still would not let me in. Then for some reason I configured the Point to point connection with my username and password. That did it!! I am now in.

Still showing red on the wireless button, and it is not functioning, but I don't really care..  Horraaaaayyyyy!!

---

### Post by beny-4.56 on 2008-07-17
I use madwifi-ng-r3366+ar5007, but i forgot the url where i downloaded it. I use it in my Mandriva 2008.1 and it works. :lolflag: to me

---

### Post by uwe.koch.k on 2008-07-17
Hmmm, strange. Another issue appeared as of Thuesday: subversion network-manager file was updated from 0.7.0 pre0 to 0.7.0 pre4. As a consequence, while still suffering the before posted problem, I lost the wired connection. Trying to solve the problem, I reinstalled the pre0 version, could not establish a wired connection (may be I have to configure it again), can see a lot of wireless connections, but can not connect. The card or its related driver is really exasperating. I am seriously thinking about the possibility to change the card to a more standarized one.:confused:

---

### Post by Anduu on 2008-07-17
> **uwe.koch.k said:**
> Hmmm, strange. Another issue appeared as of Thuesday: subversion network-manager file was updated from 0.7.0 pre0 to 0.7.0 pre4. As a consequence, while still suffering the before posted problem, I lost the wired connection. Trying to solve the problem, I reinstalled the pre0 version, could not establish a wired connection (may be I have to configure it again), can see a lot of wireless connections, but can not connect. The card or its related driver is really exasperating. I am seriously thinking about the possibility to change the card to a more standarized one.:confused:

The SVN Network Manager 0.7.0 update from a couple of days ago broke my wired connection on my desktop so I didn't bother updating my wireless.

As of yesterdays update which I did apply to my laptop everythibg seems to be functioning correctly again.

Perhaps try reconfiguring your connection...ie go to edit connections in network manager and removing your present connections and recreate them from scratch.

---

### Post by Texbuntu on 2008-07-18
Wasted an ENTIRE DAY trying to use ndiswrapper on a new compaq F700 series.  It did recognize the wifi twice but could never connect.  almost gave up before i came to ubuntuforums and found this post.  did a fresh install of HH64 and followed these instruction.  success the first time!  like a few others i created a login here just to say THANKS and this worked.

new ubuntuforums loyalist

---

### Post by phidia on 2008-07-18
I don't know if I'm the only one that experiances really horrible performance with madwifi. I would really like this to work and it does but I'm lucky if I get 25% of the bandwidth I get with ndiswrapper and the windows driver. Sometimes it's a little more but then it can also drop to almost dial up speed. I wanted this to work so much I reinstalled madwif today but the bandwidth seems to eventually get slower and slower. That does not happen with ndiswrapper.

---

### Post by Anduu on 2008-07-18
> **phidia said:**
> I don't know if I'm the only one that experiances really horrible performance with madwifi. I would really like this to work and it does but I'm lucky if I get 25% of the bandwidth I get with ndiswrapper and the windows driver. Sometimes it's a little more but then it can also drop to almost dial up speed. I wanted this to work so much I reinstalled madwif today but the bandwidth seems to eventually get slower and slower. That does not happen with ndiswrapper.

Yeah that sucks :(

How long has it been since you installed?There have been a few revisions to the driver since I originally posted and it is still being worked on.

Hopefully you are not the only one with performance issues and they will get things sorted out.

Perhaps post your concerns here [http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192) Maybe they can help you out.

---

### Post by phidia on 2008-07-18
Thanks Anduu I'm sort of getting to be an expert at installing and uninstalling madwifi/ndiswrapper. I had some time to day and played around with it. I'm back to ndiswrapper right now and the performance difference is really noticable. I also believe I downloaded the most recent release from madwifi, I will checkout the link.
Thanks again.

---

### Post by raziel on 2008-07-20
Thank you very much, this worked like a charm!

Acer Aspire 5315 Laptop - 64bit support, was using 32bit and recently decided to switch to 64bit.


Thanks again!

---

### Post by freakwillie on 2008-07-23
Has anyone tried madwifi 0.9.5 yet? I`m going to try it out and tell what happened.

---

### Post by cleobrag on 2008-07-23
I purchased an ACER 4520 with AMD64 AthlonX2 processor.
It came with Linpus Linux which doesn't have a GUI.
So I installed UBUNTU 8.04.1 for AMD64 on it.

The sound, crystal eye webcam installed out of the box.
I was able to install the NVidia driver easily by enabling it through Synaptic Package Manager.
All went well...
EXCEPT for the Atheros WiFi.

I spent quite some time googling for ways to enable it.
Unfortunately I didn't realize that most of the available solutions
are all for 32bit Ubuntu Linux.
When I read the tutorial on how to enable MadWifi support for AR5007EG on 64bit U,
I had just about reached my wits' end,
and I had decided that if this didn't work,
I wouldn't bother about the WiFi anymore.

Needless to say, 
it worked beautifully.
There were a few anxious moments 
after rebooting,
because it didn't pick up the signal immediately,
but once it did, it functioned beautifully.

Thanks for sharing this solution.

---

### Post by Sockerdrickan on 2008-07-25
> **Anduu said:**
> This is strictly 64bit...[]("http://ubuntuforums.org/showthread.php?p=4999962")
It is not if anyone wonders. It works with various architectures. :)

---

### Post by Anduu on 2008-07-25
> **Tux0r said:**
> It is not if anyone wonders. It works with various architectures. :)

I remember when I first started testing it it was for 64bit so it's good to know it's works for 32bit as well now.

---

### Post by gar2feed on 2008-07-26
only one question. i have no internet connection. that was the whole point of me reading your post. i need help with my Atheros wifi card. if i cant get a connection, how can i download the neccesary fix's? catch 22. vista, no problems finding wifi, ubunto sees my card but no action. can i download the info on vista somehow? coz once i reboot to ubunto, no internet, no fixy. very frustrated. i have read a thousand posts with problems similar to mine...clicked on a thousand help buttons on linux, all for nothing. any suggestions would be greatly appreciated. sorry if i sound P.O., just frustrated.

---

### Post by Anduu on 2008-07-26
> **gar2feed said:**
> only one question. i have no internet connection. that was the whole point of me reading your post. i need help with my Atheros wifi card. if i cant get a connection, how can i download the neccesary fix's? catch 22. vista, no problems finding wifi, ubunto sees my card but no action. can i download the info on vista somehow? coz once i reboot to ubunto, no internet, no fixy. very frustrated. i have read a thousand posts with problems similar to mine...clicked on a thousand help buttons on linux, all for nothing. any suggestions would be greatly appreciated. sorry if i sound P.O., just frustrated.

It is as simple as booting into Windows and downloading the tarball you want from here [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/)

Copy it to a thumb drive or burn it to a cd...then you can boot into Ubuntu and extract it and compile/install.

Note you may also need to download and install some dependencies.During the compiling process you will be notified of any problems.Take note of missing files...they can be found here [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
There is a handy search feature which should help you find what you need.

---

### Post by freakwillie on 2008-07-26
Hi, all.

Based on [this post]("http://ubuntuforums.org/showpost.php?p=5271094&postcount=7") I've made a script for keeping the driver after kernel upgrades and think it's noteworthy. So I'll explain how to do it below.

First, create the a text file under your home directory:
```
gedit ~/update-atheros
```

Then paste the code inside it and save it:
```
#!/bin/bash

echo "Building Atheros driver for $1" >&2
cd /usr/src/atheros-driver
make clean 2>&1 > /dev/null
make install KERNELPATH=/lib/modules/$1/build 2>&1 > /dev/null

depmod -a $1
```

Create the directory where it will stay and install it
```
sudo mkdir -p /etc/kernel/postinst.d
sudo install ~/update-atheros /etc/kernel/postinst.d
```

And that's it, next time you upgrade your kernel via apt-get or make-kpkg it will automatically keep (actually install) the drivers.

---

### Post by psst on 2008-08-01
I have a Toshiba Satellite A210-12U AMD Turion x2 64 lappy with the Atheros AR5007EG card on board. I am a total Linux/Ubuntu newbie. I just installed it as a dual boot the other day.

Anyway like many others,the wireless didnt work

I followed these simple instructions and it worked first time ! Thanks a lot to the Linux Gurus who have been working on this seemingly very difficult problem !

Having let it "sleep" it also wakes up successfully and the wireless reconnects quickly.

---

### Post by vbose on 2008-08-02
Hi Anduu,

It works like a charm. I thank you so much for the post. When I got my new Compaq F756NR AMD 64 back in May 2008, I was so excited to install Ubuntu 8.0.4 Hardy. However, I tried so hard to get the wireless working for weeks using the previous posts. But nothing worked. I just looked at the forum again and found your post and I followed your instructions.

Thanks so much again.

---

### Post by RichardLaurenson on 2008-08-05
Yay :guitar:
thanks a ton... Brilliant clear helpful....

Have 1 year old Acer :twisted:
lots of closed stuff... and its too tiny for VISTA but GREAT on HERON.... except for the closed hardware etc.... I think this is the last of the BIG potholes on my road to a new OS...

(Penguin flirt rather than lover)

---

### Post by afewtips.com on 2008-08-06
Thank YOU!!

It worked for me - Acer Extensa 5620-4025.

I actually thought I had 32 bit, so I did this and thought what do I have to loose? It worked perfectly. In fact I believe it checks to make sure you have the appropriate setup (but I am no expert). 

After it was setup it couldn't connect, but then I read somewhere that you need to try multiple times to connect by changing the setup a couple of times. So that's what I did and sure enough, I little graph showed up in the top right and I connected at 54. The computer is roaming mode.

In all my attempts at changing the router setup, I'm not sure if I turned off WEP, so that may have contributed

---

### Post by Ripfox on 2008-08-07
> **be4truth said:**
> Is that a solution for 32 bit as well? So far nothing worked for me fixing this issue.

I followed this to the letter on a fresh install 32 bit for my Sony Vaio VGN-NR360E and it worked perfectly. Thanks!!!

---

### Post by jeffegg2 on 2008-08-07
Trying this with "Studio Ubuntu 8.04.1 amd64.

I get the error:
cd: 1: cant' cd to /lib/modules/2.6.24-19-rt/build is missing, please set KERNELPATH. Stop.

Help!

---

### Post by kungfupanda on 2008-08-09
It's a pity that the driver doesn't support the injection of aircrack-ng.

kungfupanda@kungfupanda-laptop:~$ sudo modinfo ath_pci
[sudo] password for kungfupanda: 
filename:       /lib/modules/2.6.24-20-generic/net/ath_pci.ko
license:        Dual BSD/GPL
version:        svn r3722
description:    Support for Atheros 802.11 wireless LAN cards.
kungfupanda@kungfupanda-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"linksys"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: I don't know   
          Bit Rate:18 Mb/s   Tx-Power:17 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=30/70  Signal level=-66 dBm  Noise level=-96 dBm
          Rx invalid nwid:85977  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

kungfupanda@kungfupanda-laptop:~$ sudo airmon-ng stop ath0


Interface	Chipset		Driver

ath0		Atheros		madwifi-ng VAP (parent: wifi0) (VAP destroyed)

kungfupanda@kungfupanda-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.


kungfupanda@kungfupanda-laptop:~$ sudo airmon-ng start wifi0


Interface	Chipset		Driver

(can't start monitor mode,???)
kungfupanda@kungfupanda-laptop:~$ sudo wlanconfig ath create wlandev wifi0 wlanmode sta
ath0
(restart managed mode)
kungfupanda@kungfupanda-laptop:~$waiting for injection patch

---

### Post by Anduu on 2008-08-09
> **jeffegg2 said:**
> Trying this with "Studio Ubuntu 8.04.1 amd64.

I get the error:
cd: 1: cant' cd to /lib/modules/2.6.24-19-rt/build is missing, please set KERNELPATH. Stop.

Help!

Try

```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by tom1979 on 2008-08-10
Excellent!!! Ubuntu has defo advanced since i last tried to fix my wifi!

Worked perfectly, fresh install with wifi working thanks to this guide in under an hour, screw you windows!!!

---

### Post by lowell216 on 2008-08-11
Went through the whole thing and now I can connect to unsecured wireless networks, but it isn't letting me into my WEP-Open network. I keep trying to put in the WEP key, but it just doesn't work. Any ideas?

---

### Post by anh_that_tinh on 2008-08-11
I install madwifi. It scan and see wifi but can not connect :-(. Plz, help me. I was testing with ndiswrapper but it was not better(do not scan wifi :-( )

---

### Post by 12345 on 2008-08-11
I would like to say thanks for this post. The procedures worked great.
I am currently running ubuntu hardy heron 64 bit on a toshiba satellite p205d 8804. Followed the steps and my wifi is up and running. This is the wifi card built in to my system: AR5418 802.11abgn Wireless PCI Express Adapter according to hardware manager. Thanks for this info it was driving me crazy for weeks.

---

### Post by stabbymctwist on 2008-08-11
Thanks a lot, seriously.  I'd use the built-in thing for saying thank you, but I don't know how.

---

### Post by FizzBuntu on 2008-08-11
It works, it works, yeeeehhhaaaaaaaaaaaaa

Yeah, I know that's sounds a little too much, but believe me, it's 3 A.M., and now that I've convince my father of the efficency of linux, he was getting ready to blast my head off because of the "no wifi ?!' issue.

So, thx a lot for the howto, and you have a cold beer waiting for you in my fridge anytime...

---

### Post by JacenMandarin on 2008-08-13
Thanks a lot man (or lady. ^^)! I was using ndiswrapper with 32bit, just upgraded to 64 and decided to use your guide, worked perfectly the first time. Now, when you say I'll need to redo this after a kernel update, is that everytime I update period or a certain type of update? Sorry, newb. ^^;

---

### Post by Anduu on 2008-08-13
> **JacenMandarin said:**
> Thanks a lot man (or lady. ^^)! I was using ndiswrapper with 32bit, just upgraded to 64 and decided to use your guide, worked perfectly the first time. Now, when you say I'll need to redo this after a kernel update, is that everytime I update period or a certain type of update? Sorry, newb. ^^;

You will see an update will be available for say "linux-image-2.6.xx-xx-generic" and a restart will be required.

Typically minor revision updates won't break the driver.For example updating the kernel you are currently running won't have any ill effects.

However if it wants to update to a newer kernel for example from 2.6.24-20 to 2.6.24-21 it will break.

Anyways you will know soon enough if it breaks as will not work any more.All you need to do is repeat the procedure sans the downloading from SVN.Simply recompile/install the driver and restart and all should be good to go.

Hope this helped :)

---

### Post by JacenMandarin on 2008-08-14
Yes indeedy it did, thankee sai. ^_^ Thanks a lot. :)

---

### Post by endjo on 2008-08-14
Wohooo finaly, after lots of troubles I did start my wireless properly. BIG THX Anduu, You are great !!!!

---

### Post by jeffegg2 on 2008-08-16
cd: 1: can't cd to /lib/modules/2.6.24-19-rt/build
Makefile.inc:66: *** /lib/modules/2.6.24-19-rt/build is missing, please set KERNELPATH.  Stop.


Getting the above error.... I only get this when loading the files for Studio Ubuntu using the synaptic.... why is this here before and not now?

---

### Post by makkan77 on 2008-08-18
Thanks!

Worked without a hitch ony my Acer Aspire 5715Z.

---

### Post by noothe on 2008-08-18
it worked out of the box with a clean install of 64bit xubuntu on an samsung r60 t7250 divial. you really saved my day anduu :) thx alot!

---

### Post by pharma on 2008-08-21
[FONT="Comic Sans MS"]Thank you so much - my laptop is HP Pavilion DV6820 and I have spent days trying to set up wireless on Ubuntu.  Followed the process here - used AR5007EG-Madwifi3745-AircrackPatched-HAL10.5.6.tar.gz drivers and everything is working.[/FONT]

---

### Post by dan1701a on 2008-08-24
Thanks! I had to reinstall Ubuntu Hardy 8.04 and rediscovered this post, and thanks to the new instructions and driver it works just fine. Network monitor showed that the interface (ath0:avahi) didn't exist, but I removed it from the panel and re-added it, and now it detects the interface with no problems.

Speedtest.net shows that my download speed is a little slower than under Vista (1.1 mbps as opposed to 1.4 mbps), but upload speed is actually a little faster. So it seems to work like a champ! Hopefully when I reboot it'll still work, but in the meantime it's great to have a "real" laptop running Ubuntu at my disposal!

Thanks again.

And, to the mods: How do I send "thanks" to the OP for his post?

---

### Post by kaffeboy on 2008-08-26
After two weeks with Ubuntu, two fresh installs I did manage to install it in one try. However, on the Network Manager, no Wireless Networks seem to appear?! Did I miss something or did I screw something up!?

I do have the option of Connecting to Other Wirelesss Networks and various other options. 

This is what appears after typing iwconfig. In the past, I only had lo and eth0.

```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


Please help me.

---

### Post by dan1701a on 2008-08-26
I have discovered that, when I reboot, my WPA Personal passkey field is blank. I have to re-enter my passkey in order to connect. If you are using a secured network, this may alleviate the problem. However, I don't know if it's actually an issue or if it's the normal behavior of the network manager.

Seems like a bit of a pain to re-enter your passkey each time you want to connect, but I guess it would keep folks from hacking into your PC if you weren't home (kids, wife, dogs, cats, etc.).

---

### Post by Fixion on 2008-08-29
I really appreciate the howto, but I'm having a bit of trouble.  I was able to download and make the driver, however 'sudo make install' fails.

EDIT: I've narrowed it down a bit, 'make install' calls 'install-modules' and 'install-tools' (inside the Makefile).  While 'sudo make install-modules' completes successfully, 'sudo make install-tools' fails, but I don't know where or why it's failing.  Here's the output.

```
fixion@goninja:/usr/src/madwifi-hal-0.10.5.6$ sudo make install-tools
make -C ./tools all || exit 1
make[1]: Entering directory `/usr/src/madwifi-hal-0.10.5.6/tools'
for d in ath_info; do \
		make -C $d || exit 1; \
	done
make[2]: Entering directory `/usr/src/madwifi-hal-0.10.5.6/tools/ath_info'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/usr/src/madwifi-hal-0.10.5.6/tools/ath_info'
make[1]: Leaving directory `/usr/src/madwifi-hal-0.10.5.6/tools'
make -C ./tools install || exit 1
make[1]: Entering directory `/usr/src/madwifi-hal-0.10.5.6/tools'
for d in ath_info; do \
		make -C $d || exit 1; \
	done
make[2]: Entering directory `/usr/src/madwifi-hal-0.10.5.6/tools/ath_info'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/usr/src/madwifi-hal-0.10.5.6/tools/ath_info'
install -d /usr/local/bin
for i in athstats 80211stats athkey athchans athctrl athdebug 80211debug wlanconfig wpakey; do \
		install $i /usr/local/bin/$i; \
		strip /usr/local/bin/$i; \
	done
strip: /usr/local/bin/athstats: File format not recognized
strip: /usr/local/bin/80211stats: File format not recognized
strip: /usr/local/bin/athkey: File format not recognized
strip: /usr/local/bin/athchans: File format not recognized
strip: /usr/local/bin/athctrl: File format not recognized
strip: /usr/local/bin/athdebug: File format not recognized
strip: /usr/local/bin/80211debug: File format not recognized
strip: /usr/local/bin/wlanconfig: File format not recognized
strip: /usr/local/bin/wpakey: File format not recognized
make[1]: *** [install] Error 1
make[1]: Leaving directory `/usr/src/madwifi-hal-0.10.5.6/tools'
make: *** [install-tools] Error 1
fixion@goninja:/usr/src/madwifi-hal-0.10.5.6$ 

```

I have no idea what's going on and would really appreciate any help!

---

### Post by frklin on 2008-08-30
Hey, I did so as how to and everything works. But I have a problem with finding the speed of the transfer. Downloading something of a speed 140 kb/s and the system says that 280 kb/s. Can be somehow fix it? :confused:

---

### Post by TRBD16Z6 on 2008-08-30
Thank-you so much. No I don't have to use the crappy Vista that came with my Compaq laptop. I mean I still have a couple other problems with Ubuntu but I have a feeling it has more to do with running the Ubuntu 8.10 Alpha 4 version. But just so everyone know it work on my setup.

Compaq CQ50-100CA (CQ50-100 CA)
AMD X2 64 TL-60
2GB Memory
160GB Sata HDD
Atheros AR5007 wifi /now working perfectly. Thanks =)/
Originally had Vista Home Premium installed
Nvidia 8300m Graphics

---

### Post by van_zwier on 2008-09-05
thanks, it really works

---

### Post by ihc100 on 2008-09-07
Works great, desktop amd64 hardy abit airpace wifi.
If i knew how to officially thank you i would have done so.

---

### Post by bhgerhar on 2008-09-08
It works on my aspire 4715-4053 running hardy 64bit with an atheros AR242x card.
Thanks for the how-to!

---

### Post by sunny_nwho on 2008-09-09
Thanks a lot mate! working perfectly as of now.. will check again from home

---

### Post by lvdude on 2008-09-15
Don't want to be preachy, but if you're like me and have been trying to get this particular card (AR242x/AR5007EG) to work for months, consider donating to the Madwifi project--without their efforts your card, and mine, would still be bricks.

---

### Post by Anduu on 2008-09-15
> **lvdude said:**
> Don't want to be preachy, but if you're like me and have been trying to get this particular card (AR242x/AR5007EG) to work for months, consider donating to the Madwifi project--without their efforts your card, and mine, would still be bricks.

I'll second that emotion ;)

---

### Post by ColmCille on 2008-09-19
I waded through most of these messages, and didn't see my problem, so I hope I'm not repeating. My prob is with the very first line of the tutorial, i.e. getting the build essentials. It tells me they aren't available. 

Am I supposed to have an internet connection for that? I'm on a dual boot Vista machine, so if someone can tell me where to download it, and anything else I might need to download, such as the Linux restricted modules and subversion, I may be able to do this the hard way (already have the HAL on my usb stick, and I saw the link to download any dependencies). 

If I get tired of trying to do it the hard way, I'll try and borrow an ethernet line from another computer somewhere. Hopefully a wired connection will work better than the wireless. 

If it does, I think the first thing I'll do is try and get my nVidia graphics card working. That brown birdie wallpaper, along with the 800X480 resolution, is driving me bonkers. :)

Thank you.

---

### Post by dan1701a on 2008-09-19
> **ColmCille said:**
> I waded through most of these messages, and didn't see my problem, so I hope I'm not repeating. My prob is with the very first line of the tutorial, i.e. getting the build essentials. It tells me they aren't available. 

Am I supposed to have an internet connection for that?

Yes. Pretty hard to download without one.

>  I'm on a dual boot Vista machine, so if someone can tell me where to download it, and anything else I might need to download, such as the Linux restricted modules and subversion, I may be able to do this the hard way (already have the HAL on my usb stick, and I saw the link to download any dependencies).

Are you planning on downloading these modules from within Windows? If you are, then (while in Ubuntu), go to Synaptic Package Manager and go to "Settings>Repositories" and write down the web addresses you find under the "Third Party Software" tab. However, this method is not really recommended, because you can't directly download the packages from there. I don't understand the process involved, but trust me on this one - you won't find what you're looking for that way.

The obvious best way is as you suggest below...

> If I get tired of trying to do it the hard way, I'll try and borrow an ethernet line from another computer somewhere. Hopefully a wired connection will work better than the wireless. 

If it does, I think the first thing I'll do is try and get my nVidia graphics card working. That brown birdie wallpaper, along with the 800X480 resolution, is driving me bonkers. :)

Thank you.

That's what you should try. Also, make sure your "restricted drivers" are properly updated and operating. The only way to do this is with an internet connection.

You can find your restricted drivers in "System>Administration>Hardware Drivers". You should have three - two of them deal with your Atheros wireless card, and the third is your nVidia graphics. Since Canonical doesn't directly offer drivers for these devices, they use drivers that are proprietary and cannot be modified. They're free, but you have to enable them directly. Once you do that and restart (possibly several times), your nVidia graphics will operate properly. As an example, I have a widescreen (14.2") Acer Aspire laptop with 1280x960 graphics, and the nVidia driver works perfectly.

Good luck.

---

### Post by jgrantham on 2008-09-19
Thanks so much for this. I have been trying for a year to get my 5007 working non my laptop. This worked like a champ. I have two Acer Aspire 5100's and it worked perfectly on both. BTW, I converted my wife to Ubuntu last night. Now we only have one computer running M$. As soon as I can find a video capture card that isn't too expensive, I will move that one to Ubuntu also.

---

### Post by ColmCille on 2008-09-19
> **dan1701a said:**
> 

Yes. Pretty hard to download without one.

Zing!

Pretty funny, guy.=D>


> 

Are you planning on downloading these modules from within Windows? If you are, then (while in Ubuntu), go to Synaptic Package Manager and go to "Settings>Repositories" and write down the web addresses you find under the "Third Party Software" tab. However, this method is not really recommended, because you can't directly download the packages from there. I don't understand the process involved, but trust me on this one - you won't find what you're looking for that way.

The obvious best way is as you suggest below...Yes, obviously, but it is might be difficult for me to borrow a connection. It looks like I'll have to, though. 

It seems to me Ubuntu should include at least enough in the box to get the internet connection, whether wired or wireless, going. At least, make it easier to directly download what is needed. 

Internet is essential, after all. Without it, you're pretty much screwed as far as doing anything else. Besides, connecting to the internet without worrying about all the nasties aimed at Windows is the biggest reason I installed Linux in the first place.

It looks like installing was the easy part. Good thing I have a laptop--easier to drag to a connection somewhere. I pity someone with a big desktop box trying to do this.


> 
That's what you should try. Also, make sure your "restricted drivers" are properly updated and operating. The only way to do this is with an internet connection.

You can find your restricted drivers in "System>Administration>Hardware Drivers". You should have three - two of them deal with your Atheros wireless card, and the third is your nVidia graphics. Since Canonical doesn't directly offer drivers for these devices, they use drivers that are proprietary and cannot be modified. They're free, but you have to enable them directly. Once you do that and restart (possibly several times), your nVidia graphics will operate properly. As an example, I have a widescreen (14.2") Acer Aspire laptop with 1280x960 graphics, and the nVidia driver works perfectly.

Good luck.

I had the Atheros drivers enabled fine, actually (though they may have been old). Not that they were any help. In any case, it looks like I will have to leave them disabled in order to use the process explained in this thread.

The nVidia driver, the one I want to activate, wouldn't activate at all, of course. Would be nice if the nVidia driver were included in the box, though it may be a proprietary issue.

Anyway, thanks for responding. Hopefully I won't be back with more problems.

---

### Post by ColmCille on 2008-09-19
I'm back, and typing at you on a 1280 X 800 screen, and WiFi! My system is a Compaq Presario F767NR, Turion 64 X2, with Atheros AR5007 built in. 

I've taken a slight hit in speed, and some bottlenecking, probably because my reception isn't as good as in Windows. Hopefully Madwifi can improve that in future releases.

Thank you very much, Anduu. :KS Thanks to you, I didn't have to go to the kind  of trouble so many others before you came along.

---

### Post by an3se on 2008-09-23
I just begun with UBUNTU, and WiFi was my last problem.
Now I'm so ferry happy that it works, so I will let you no it.

Thanks again, Roelof Andriese the Netherlands.

(sorry for my English)   
\\:D/

---

### Post by alizais on 2008-09-23
Thank you so much for this post! I have spent three days on my wireless problems, trying all the tutorials I could find online. 

I even found a tutorial that was very similar to yours. It instructed the user to install the exact version of madwifi that is in this tutorial. 

But the difference? What made yours work and not others was your suggestion to remove ndiswrapper. See, I had followed other (failed) tutorials to install and use ndiswrapper but they never told me to uninstall it. 

Thank you again for a thorough, easy-to-follow, excellent tutorial!

---

### Post by Zefal on 2008-09-25
This worked for me!! Thank you so much, took me so long to get this working and was on verge on giving up on linux, still don't Linux is quite there yet for home users and its a bitch to configure and not everything "just works". Also i've never been successful getting any Linux working on my desktop with X-Fi sound card, but I'm stubborn. Got working ok with beta drivers in stereo mode, but flash in firefox refused to give out sounnd. THis is off topic though - thanks so much for this thread!!!n:)

---

### Post by qkarma on 2008-09-25
Thanx a ton !!!!  it worked like a charm for me :)

---

### Post by XMaverickX on 2008-09-29
I just voted NO, but boy was I wrong, I did not accept the website for the download so it didnt work, but now I put a t when it asked and it just worked perfect!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
I am not gay but if I saw the guy who just made this thread he would be getting a hug and a kiss :D
Eternally grateful, Rocky

---

### Post by osoviajero on 2008-10-04
Thank you thank you thank you !!!!!!!!!

---

### Post by slarrabe on 2008-10-14
I... what the?  It actually worked?!  DUDE!  IT WORKS!

:guitar: :popcorn: =D> \\:D/

---

### Post by Anduu on 2008-10-14
I am glad to see this is working out so well for everyone :)

Something I have been meaning to mention for a while now but keep forgetting is that Atheros has open sourced their HAL for our chipset.You can read the news here [http://madwifi.org/wiki/news/20080929/hal-source-code-released](http://madwifi.org/wiki/news/20080929/hal-source-code-released)

This is definitely good news as it should mean out-of-the-box support for our cards under Ubuntu in the not so distant future :popcorn:

---

### Post by osoviajero on 2008-10-15
Anduu,
Man you are good! I tried for days to get the wifi card going, and couldn't until I followed your directions. Then the updates I installed today screwed up the driver. Luckily I could find your post again to get the thing working again. Now I've bookmarked the page. THANKS!!!!:KS

---

### Post by hughc1 on 2008-10-17
This patch was loaded months ago and works fine.  But starting two weeks ago my Compaq Presario F700 running 64 bit Ubuntu loses the ip address.  If I reboot or come back from hibernation the adapter works fine.  
What I see happening is the ip was 192.168.15.8 and changes to 69.254.1.219

Here is the log:

Oct 15 13:20:41 Lion64 NetworkManager: <info>  Deactivating device eth1. 
Oct 15 13:20:41 Lion64 NetworkManager: <info>  eth1: Device is fully-supported using driver 'forcedeth'.  
Oct 15 13:20:41 Lion64 NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 15 13:20:41 Lion64 NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 15 13:20:41 Lion64 NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth1'. 
Oct 15 13:20:41 Lion64 NetworkManager: <info>  Deactivating device eth1. 
Oct 15 13:20:42 Lion64 ntpdate[10168]: adjust time server 91.189.94.4 offset -0.021887 sec
Oct 15 13:20:43 Lion64 ntpdate[10190]: adjust time server 91.189.94.4 offset -0.021367 sec
Oct 15 13:23:27 Lion64 avahi-daemon[5153]: Withdrawing address record for 192.168.15.8 on wlan0.
Oct 15 13:23:27 Lion64 avahi-daemon[5153]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.15.8.
Oct 15 13:23:27 Lion64 avahi-daemon[5153]: Interface wlan0.IPv4 no longer relevant for mDNS.
Oct 15 13:23:27 Lion64 avahi-autoipd(wlan0)[10404]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Oct 15 13:23:27 Lion64 avahi-autoipd(wlan0)[10404]: Successfully called chroot().
Oct 15 13:23:27 Lion64 avahi-autoipd(wlan0)[10404]: Successfully dropped root privileges.
Oct 15 13:23:27 Lion64 avahi-autoipd(wlan0)[10404]: Starting with address 169.254.1.219
Oct 15 13:23:33 Lion64 avahi-autoipd(wlan0)[10404]: Callout BIND, address 169.254.1.219 on 

Maybe its my hardware?  I recompiled and reinstalled, same problem.  Maybe it has to do with an Ubuntu update from two weeks ago

recovery from the bad connection is - dhclient wlan0

Has anyone else had a problem with the driver?

---

### Post by ma7hatter on 2008-10-30
Thanks so much, I've been waiting  a long time for this...

---

### Post by atreide on 2008-10-30
I'm really quite new to linux, i got everything up and running over the past week and ubuntu is at a stage where i'm really happy with it and everything functions, especially the wireless thanks to this guide!!!

My question is, has anyone updated to 8.10 yet?  Did the wireless continue to work or did you have to repeat the steps in this howto?

cheers. atr.

---

### Post by Anduu on 2008-11-01
I recently upgraded to Ibex and there is now support "out of the box" for this card now...sort of...

If you install the linux-backport-modules package and do some tinkering it does work however performance is poor.

I recommend sticking with our version for now...it should simply be a matter of repeating the steps of the how-to and you should be up and running again.

Make sure you have a wired connection handy(in case the upgrade messes up wireless...) or a copy of the svn version still on your system.

---

### Post by inuk2600 on 2008-11-01
I followed these instructions after a fresh install of Ubuntu 8.10 (no, it still does not work out-of-the-box quite right) on a new Compaq Presario A900 and it worked. The only thing I would add is that I had to unplug the ethernet cable before the wireless connection can be established. I should also add that the system was unstable at gnome startup as well as build-essentials was not available UNTIL the updates were installed.

So make sure you go to System->Administration->Update Manager and apply the updates on Ubuntu 8.10 before following Anduu's instructions.

Thanks a million for the solution Anduu!

ps. Has anyone figured out how to get the wifi button to toggle (red-off, blue-on)?

---

### Post by Anduu on 2008-11-01
> **inuk2600 said:**
> 
Thanks a million for the solution Anduu!

ps. Has anyone figured out how to get the wifi button to toggle (red-off, blue-on)?

AFAIK there is no way to get the LED working but beggars can't be choosers I suppose :p

---

### Post by yuretsz on 2008-11-02
[http://madwifi.org](http://madwifi.org) is down. Who can send me driver for 64bit?
[email]yuretsz@gmail.com[/email] Please help me. I really need it!

---

### Post by a-musing amazon on 2008-11-03
I upgraded at the weekend and this note is just to confirm that your fix still runs OK on Intrepid 64-bit (I have a Abit AR5007EG), while the other options I tried (such as ath5k) still seem to suck.

What initially threw me is that I use WPA encrytion and Ubuntu have also provided a new version of wpa_supplicant in Intrepid which no longer supports the 'madwifi' WPA driver option, so until you change to the standard 'wext' driver option you may find that your network manager (I use wicd) or console 'sudo iwist scan' can see access points but you will fail to connect.

---

### Post by a-musing amazon on 2008-11-03
Yuretsz wrote:
> http://madwifi.org[/url] is down.
> Who can send me driver for 64bit?
> Please help me. I really need it!
>
madwifi seem to be back again now.

---

### Post by upsidedown010 on 2008-11-03
ok this was great, it worked for me before but i had to reboot my computer and now i'm doing it again. running a toshiba satellite l305d-s5874 and i got this when i got to the 4th step and i typed and entered enter "make"
cd: 1: can't cd to /lib/modules/2.6.24-21-server/build
Makefile.inc:66: *** /lib/modules/2.6.24-21-server/build is missing, please set KERNELPATH.  Stop.
you gave advice on this to another user and i tried using that advice but to no avail and i was wondering if you had any other tricks up your sleeve.
once again thanks.

---

### Post by mathieu.ward on 2008-11-05
grassy *** :):)

have had to find this again! this wokes on 32bit systems also

---

### Post by uwe.koch.k on 2008-11-10
Please refer to quote 91. Probably you need to download the linux-headers. I had a similar problem before.

Good luck!

---

### Post by hp59dk on 2008-11-13
This great tutorial helped me once, but now i have updated and off course lost connection. But following the steps does not work now. I am sure that here is guidance to find, but there is so many posts. Would You give me a shortcut to which post to read?

Problem is that this does not work:> 

4: Get the files and install the driver
Code:

svn co [https://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6](https://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6)
cd ~/madwifi-hal-0.10.5.6
make
sudo make install
sudo depmod -ae
sudo modprobe ath_pci
echo ath_hal | sudo tee -a /etc/modules
echo ath_pci | sudo tee -a /etc/modules

5: Finally go to System ->Administration ->Hardware Drivers and reenable the Atheros drivers and reboot the system.

One thing I should add is you will need to repeat this procedure whenever you get a kernel update.I have just kept the downloaded packages on my system and after booting into a new kernel I do:

Code:

cd ~/madwifi-hal-0.10.5.6
make clean
sudo make install

Reboot and I am up and running again.
Hopefully this makes your day like it did mine!


Maybe it is only that madwifi-hal-0.10.5.6 is updated, but i have no knowledge of what i am doing, i just follow steps, and i don't know what to seek for.

Help is appreciated
Thank You


I wonder, 
Ohh it is here: [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/)
I wonder how i can delete my post, when i realize that it is irrelevant

---

### Post by bruno386 on 2008-11-16
worked for me :D

i was using hardy heron

---

### Post by tjlane on 2008-11-16
Worked like a charm! Thank you for posting!

---

### Post by senadsin on 2008-12-21
Thanks! Finally After 5 days! You ROCK>>>>>>>>>>>>>>>>>>>>>.

---

### Post by hughc1 on 2008-12-23
[QUOTE=hughc1;5982075]This patch was loaded months ago and works fine.

---

### Post by hughc1 on 2008-12-23
This patch has worked for months. Thank you.

---

### Post by RezoApio on 2008-12-26
Thanks for the nice posting. 
It works on my Asus F5RL but I need to switch off/on the wireless card on each reboot.

I have seen one other user of the forum complain of the same. Any idea what would cause such a strange issue ?

Light is green both for wifi and bluetooth at reboot and then before the login screen appears the wifi led stops. 

In this configuration, you can see the network (my correct essid) and even enter the WEP passphrase but it never connects.

off/on the wireless and it works...

nothing in dmesg ...

Any hints welcome.

---

### Post by Anduu on 2008-12-26
> **RezoApio said:**
> Thanks for the nice posting. 
It works on my Asus F5RL but I need to switch off/on the wireless card on each reboot.

I have seen one other user of the forum complain of the same. Any idea what would cause such a strange issue ?

Light is green both for wifi and bluetooth at reboot and then before the login screen appears the wifi led stops. 

In this configuration, you can see the network (my correct essid) and even enter the WEP passphrase but it never connects.

off/on the wireless and it works...

nothing in dmesg ...

Any hints welcome.

What version of Ubuntu are you running?...I know the version of Network Manager that comes with Hardy has issues that the 0.7 version in Intrepid fixes.

---

### Post by ZeroXtreme on 2009-01-08
I got the LED working on my Acer Aspire 4520G by doing the following:

1. sudo sysctl -w dev.wifi0.ledpin=3
2. sudo sysctl -w dev.wifi0.softled=1

If this works, add the following to your /etc/sysctl.conf file to make the changes persistent:

# Enable WiFi LED
dev.wifi0.ledpin=3
dev.wifi0.softled=1

By the way, my system's config is as follows:

Acer Aspire 4520G
Ubuntu Linux 8.10 (Intrepid) x64
madwifi-hal-0.10.5.6-r3879-20081204

On a side note, I've tried all three drivers with my current config, the backport method is the easiest to do, but the network speed is slow and unreliable, the ndiswrapper method is ok, but the madwifi method gives the fastest most stable network speed.

Hope this helps.

---

### Post by Anduu on 2009-01-09
> **ZeroXtreme said:**
> I got the LED working on my Acer Aspire 4520G by doing the following:

1. sudo sysctl -w dev.wifi0.ledpin=3
2. sudo sysctl -w dev.wifi0.softled=1

If this works, add the following to your /etc/sysctl.conf file to make the changes persistent:

# Enable WiFi LED
dev.wifi0.ledpin=3
dev.wifi0.softled=1

By the way, my system's config is as follows:

Acer Aspire 4520G
Ubuntu Linux 8.10 (Intrepid) x64
madwifi-hal-0.10.5.6-r3879-20081204

On a side note, I've tried all three drivers with my current config, the backport method is the easiest to do, but the network speed is slow and unreliable, the ndiswrapper method is ok, but the madwifi method gives the fastest most stable network speed.

Hope this helps.

Hey great find!!!

I have been looking for that info for ages.It works like a charm on my Aspire 7520

Thanks heaps :KS

EDIT:
I concur with your finding that Madwifi is the best of the three performance-wise

---

### Post by cd-r80 on 2009-01-11
Not working. Why?

Hardware enabled. Was off when compiling

lspci
Atheros Communications Inc. AR242x 802.11abg

Using Wicd. No wireless  networks.

Dmesg it is loaded:
AR5210,....RF2425 etc.
MadWifi: ath_attach: Switching rfkill capability off.
wifi0: Atheros AR2425 Chip Found..
ath_pci_ wifi0: Atheros 5424/2424...

 /etc/modules Ok.
No blacklisted

ifconfig: No wireless devices.

Ndiswrapper uninstalled.

? 64bit Hardy Heron / Acer 5520 
Under laptop:AR5BxB63

Does it work with Wicd?
No difference with network manager.

---

### Post by cd-r80 on 2009-01-11
No hope! I found this from [http://madwifi-project.org/wiki/Compatibility/Atheros:](http://madwifi-project.org/wiki/Compatibility/Atheros:)

Atheros AR5BXB63

Chip:	 wi-fi.org says that is AR5006EG
Supports:	IEEE 802.11b, 802.11g
Notes:	Dosen't work at all.
Notes:	DevID 0428
Notes:	In windows it's appears like AR5007EG 

Going back to randomly working ndiswrapper or Goodbye to 64 bit Ubuntu.

I found that kernel 2.6.24-19-generic <--has an ath_pci module built. Built in kernel?
I will try: "a new kernel 2.6.24-20 gets installed, it will not have an ath_pci module built for it." & then  reinstall ndiswrapper.

---

### Post by gmendoza20 on 2009-01-18
Thanks very much, Anduu, for share it, my card is working correctly. I spend around 2 days traying to get it works, using ndiswrapper and diferent ways for install madwifi with nothing results.

Thanks again.

---

### Post by fukr on 2009-01-27
Wonderful -- I cannot thank you enough for providing this easy tutorial.

One suggested revision, If I may: madwifi.org is no longer hosting this stuff; after quickly Googling the file name, I found it at:

[http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/)

The svn commands you provided will not work here, but it can be easily downloaded by web and extracted manually to a temporary folder (yeah, I'm new). Once you enter the new madwifi-hal folder in the terminal, everything else works according to your brilliant instructions.

FYI: I'm single-booting Ubuntu 8.04.2 LTS (Hardy Heron) 64-bit on my 15" Macbook Pro 3,1 "Santa Rosa" with 4GB RAM. I found the 64-bit 8.10 (Intrepid Ibex) completely unusable on this machine, whereas Hardy has been flawless, apart from the initial frustrations I encountered with the Atheros wifi adapter.

Thank you again, Anduu. You truly made my day.

---

### Post by war_eagle14 on 2009-03-01
Thanks Anduu, you rock!
:guitar:

---

### Post by rellis on 2009-03-09
Hello ubuntu community,
I install ubuntu 8.10 in my new Acer 4520 and I can not reach wifi, PLEASE HELP....
Ellis

---

### Post by Zefal on 2009-03-09
Just incase anyone is as silly I was regarding atheros/madwifi/ubuntu 64bit I'll post this.

I got wireless working using this method just fine (thanks to whoever found out solution and posted here) and in fact I've used this method a few times when I've re-installed ubuntu. It works perfectly everytime!! However - for some reason my wireless suddenly stopped working... the adpaters were showing in ifconfig but no APs were showing in network manager and it wasn't connecting to my configured AP either..

Anyway I couldn't work it out for days and finally found out that my hard switch to turn wireless on/off on laptop was off (I must have knocked it) - I switched it back on and it worked fine - doh! 

So I've added the other fix to make LED work so I can see if its turned on or not. This is really helpful!

So if anyone is as silly as I am and find that they can't scan for any APs or connect to existing ones , try turning on the damn wireless card! ](*,)

---

### Post by Worp8d on 2009-03-14
Don't know if anyone's posted this yet but the URL for the svn check-out needs to be changed.  Use:

```
svn co http://svn.madwifi-project.org/madwifi/branches/madwifi-hal-0.10.5.6
```


Great post though, helped me out enormously, thanks!

---

### Post by Anduu on 2009-03-14
> **Worp8d said:**
> Don't know if anyone's posted this yet but the URL for the svn check-out needs to be changed.  Use:

```
svn co http://svn.madwifi-project.org/madwifi/branches/madwifi-hal-0.10.5.6
```


Great post though, helped me out enormously, thanks!

Okeedokee....updated the How-To....been meaning to do that but kept forgetting :p

Thanx for the reminder :KS

---

### Post by lems on 2009-03-19
I love you op :) :KS

---

### Post by shane2peru on 2009-03-19
> **Worp8d said:**
> Don't know if anyone's posted this yet but the URL for the svn check-out needs to be changed.  Use:

```
svn co http://svn.madwifi-project.org/madwifi/branches/madwifi-hal-0.10.5.6
```


Great post though, helped me out enormously, thanks!

Is this newer or better than the old one?  I have been using the previous one (madwifi-hal-0.10.5.6-r3861-20080903), and it has been working great.  But you know how it goes, keep tinkering till it is broken!  :D  Let me know if this one is better!  Thanks.

Shane

---

### Post by bobmon on 2009-03-21
YAYYYY!!!

This process worked for me!  Some details:
    Kubuntu 8.10, amd64 version
    Lenovo Thinkpad w700, w/ "03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)" (lspci output)
    Managed WLAN w/ WEP encryption

Color me HAPPY.

---

### Post by xenosaga456 on 2009-04-18
OMFG dude i ******* love u i have been trying to fix tis 4evaer:KS:D

---

### Post by cunliffe on 2009-04-25
Thanks so much!

I had no connection at all; I have no wired connection. I was still able to do it like this:

1) restart with the previous kernel (which still works) by selecting it in the grub loader

2) find this thread

3) do all the downloading ahead of time (subversion, madwifi)

4) restart in the new, broken kernel

5) follow instructions

---

### Post by venusfenix on 2009-04-25
Hi people,

I have read your post, I am having the same problem
I have an ACER 7520 laptop 64bitsx2 with ubuntu 64 bits.

I am having the same issue with madwifi, and I have followed your indications, but, in my case, without successs, hardware driver still saying that driver is disable.

I am using Wicd and only recognized wired conections.

what happens??

what I am doing wrong??

thanks for your help!!

---

### Post by a-musing amazon on 2009-04-26
Just to note that I found that this method of enabling the AR5007EG still works with Ubuntu 9.04 after upgrading, though obviously you still need to compile, install and reboot to re-enable wifi after the upgrade.

---

### Post by michael.conner on 2009-05-14
Thanks!

Just downgraded to Hardy because of Intel video issues in Jaunty. Glad to get my wifi working on this laptop!

---

### Post by ludvique on 2009-05-15
You are a computer-God. I love Ubuntu and use it on both of my PCs. My gf has a HP Pavilion dv6700 and the wireless was refusing to yield whatever I tried. On my own laptop (Acer) the wireless setup was seamless and smooth as butter, but on her's it was a nightmare. I must confess I had all but given up and was heading for the relatively good Windows 7 (Ubuntu beats it though) as my ultimate defeat when I stumbled across your thread. This did it for me:

```
sudo apt-get install build-essential
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install subversion
sudo ndiswrapper -e net5211
sudo modprobe -r ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils ndisgtk
gksudo gedit /etc/modprobe.d/blacklist
svn co http://svn.madwifi-project.org/madwifi/branches/madwifi-hal-0.10.5.6
cd ~/madwifi-hal-0.10.5.6
make
sudo make install
sudo depmod -ae
sudo modprobe ath_pci
echo ath_hal | sudo tee -a /etc/modules
echo ath_pci | sudo tee -a /etc/modules
```Finally go to System ->Administration ->Hardware Drivers and reenable the Atheros drivers and reboot the system.

---

### Post by Zefal on 2009-05-18
Hi All,

Just another thanks to all that fixed this...and although it's been a long time that I've been happily working with my wireless on Ubuntu and laptop - all is not great - turns out when that you can't connect to any WPA2 encryption wireless devices (never tried this as my old AP is only WPA)

If anyone knows a fix for this please post one... I know this probably isn't the place to post this, but as it's still wireless issue and means this isn't completely fixed I'm just guna add it in case anyone else sees this issue...along with the fact that I simply cannot be bothered anymore.

It's annoying because as much as I like Linux (use every day at work too).. it backs up my thinking that Linux is simply not there yet on the desktop, is better suited to the data centre and why there's always going to be a place for a small partition of WinXP on my machines for when you need to get 'that something' working...

Paul

---

### Post by juankaos on 2009-05-28
> **ludvique said:**
> You are a computer-God. I love Ubuntu and use it on both of my PCs. My gf has a HP Pavilion dv6700 and the wireless was refusing to yield whatever I tried. On my own laptop (Acer) the wireless setup was seamless and smooth as butter, but on her's it was a nightmare. I must confess I had all but given up and was heading for the relatively good Windows 7 (Ubuntu beats it though) as my ultimate defeat when I stumbled across your thread. This did it for me:

```
sudo apt-get install build-essential
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install subversion
sudo ndiswrapper -e net5211
sudo modprobe -r ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils ndisgtk
gksudo gedit /etc/modprobe.d/blacklist
svn co http://svn.madwifi-project.org/madwifi/branches/madwifi-hal-0.10.5.6
cd ~/madwifi-hal-0.10.5.6
make
sudo make install
sudo depmod -ae
sudo modprobe ath_pci
echo ath_hal | sudo tee -a /etc/modules
echo ath_pci | sudo tee -a /etc/modules
```Finally go to System ->Administration ->Hardware Drivers and reenable the Atheros drivers and reboot the system.





Thank you, ludvique!! worked great!

Thanks again!!:D:D:D

---

### Post by fr@nk on 2009-06-23
it works for me too.
Acer Aspire 4520 (Ubuntu 9.04, after update from 8.10)
Thanx :)

---

### Post by JESbrc on 2009-07-05
It worked perfectly for my machine, thanks a lot!

Ubuntu 8.04 in an HP Pavilion dv9700, model #: dv9910us

---

### Post by bigbrovar on 2009-07-22
Just wanted to say a word of thanks to the kind soul who wrote this. it worked like a charm on my friends Toshiba L305D-S5881 ..

---

### Post by Kenmoo on 2009-08-03
This worked as well on my Samsung N110 for my Linux Mint installation. Thanks for the guide!

---

### Post by acutshall1 on 2009-08-19
question; when I run the command "gksudo gedit /etc/modprobe.d/blacklist" is the container supposed to have contentto remove? I just plugged in my pci card and to my knowledge, since I did not install drivers,  no drivers are installed to blacklist
thx

---

### Post by makkan77 on 2009-09-28
I got it working on my Acer Aspire 5715Z but still have one deal breaking problem. When I'm in my kitchen (on floor down from my AP) I get a weak signal (two bars) and transfers vary from speedy to full stop. However if I touch the screen as if I were to close the laptop lid, the connection might get faster. Also after a while connection to my AP will be lost and I won't be able to connect again. It finds the AP but just keeps asking for the password. 

I might add that I have similar issues for both drivers (the one supplied in 9.04 and madwifi). I've also tried the 32-bit version of 9.04 but the problems persist. 
I should say that in vista I have none of these problems so I'm not to far away from the AP. Allthough the problems seems to be linked to signal strenght.

Anyone got a tip on how this might be fixed?

---

