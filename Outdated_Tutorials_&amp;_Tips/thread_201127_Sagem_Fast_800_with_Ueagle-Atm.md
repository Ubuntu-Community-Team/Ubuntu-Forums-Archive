---
title: "Sagem Fast 800 with Ueagle-Atm"
date: 2006-06-21
forum: Outdated Tutorials &amp; Tips
---

### Post by aces21 on 2006-06-21
This howto works with both Dapper and Edgy (at least for me). It hasn't been tested with any older releases so your mileage may vary. I know a lot of people use this modem so I hope this howto helps you all.

You need to compile and install modules, so I assume you already have build-essential and kernel-headers installed. If not:

```
$ sudo apt-get install build-essential linux-headers-'uname -r'
```

where 'uname -r' is your kernel version.

If you can't use apt because your modem isn't working (which is probably why you're here), then you can get the required modules either off your installation CD, or if you upgraded online then go to [http://packages.ubuntu.com/]("http://packages.ubuntu.com/") and search for the required packages using the search function on the front page. If you download the .deb files and then copy them onto you Ubuntu system, you can install them using the command:

```
$ sudo dpkg -i 'filename'
```

where filename is the full name of the .deb file.


Both the Dapper and Edgy kernels come with eagle-usb and usbatm modules that need removing. If you already had your modem plugged in, you may even have the eagle-usb module loaded. You can check with:

```
$ sudo lsmod | grep eagle
```

If it returns anything, then unload the eagle-usb module with:

```
$ sudo modprobe -r eagle-usb
```

Now remove the modules from your machine:

```
$ sudo rm /lib/modules/'uname -r'/kernel/drivers/usb/atm/usbatm.ko
$ sudo rm /lib/modules/'uname -r'/kernel/drivers/usb/net/eagle/eagle-usb.ko
```

Now unplug your modem if it isn't already, to make sure its memory is cleared.


Plug it back in again :)


The latest ueagle-atm v1.3 work with both Edgy and Dapper. You can get it [here]("http://download.gna.org/ueagleatm/ueagle-atm-1.3.tar.gz")

Save the file in your home directory, then:

```
$ cd ~
$ tar -xvzf ueagle-atm-1.3.tar.gz
$ cd ueagle-atm-1.3
$ sudo make
$ sudo make install
```

This should now have installed modules called usbatm and uealge-atm in '/lib/modules/'uname -r'/extras/'


Now you need to install the modem firmware. This was easy for me, but it depends on your ISP (I am with Tiscali in the UK).

I had to do the following (it is cut & pasted directly from the Ueagle-Atm wiki, I hope this is o.k.):

Download ueagle-data-1.1.tar.gz from [here]("http://eagle-usb.org/ueagle-atm/non-free/")

Now untar it and change to the created directory:

```
$ tar xzf ueagle-data-1.1.tar.gz
$ cd ueagle-data-1.1
```

Create a subdirectory "ueagle-atm" in the firmware dir. For both Edgy and Dapper this is:

```
$ sudo mkdir /lib/firmware/ueagle-atm
```

Then copy all the files to it:

```
$ sudo cp -a * /lib/firmware/ueagle-atm
```

For me that was all. However you should check the official Ueagle wiki to see if your ISP is known to have problems. The wiki is [here]("http://atm.eagle-usb.org/wakka.php?wiki=UeagleAtmDoc")


If you're happy your firmware is setup properly, run:

```
$ sudo modprobe ueagle-atm
```

Fingers crossed this doesn't return an error. If all went well, your modem lights should flash for a bit, then both stay on. Now run:

```
$ dmesg|grep ueagle
```

You should see something like:

usb 1-2: [ueagle-atm] modem operational
usb 1-2: [ueagle-atm] ATU-R firmware version : 43e2ead7

If you have problems, take another look at the UEagle wiki for a possible soluton.


Now you just need to setup your internet conection. My ISP uses PPPoA, which is lucky for me because it looks the easiest to setup.

Create a file called ueagle-atm in /etc/ppp/peers, containing the following :

```
user "myusername"
plugin pppoatm.so VP.VC
noipdefault
usepeerdns
defaultroute
persist
noauth
```

You should replace "myusername" with the username you have with your ISP. Also you need to replace VP.VC on the plugin line with the VP.VC pair used by your ISP. These are the same as were required by eagle-usb, EXCEPT that Ueagle-Atm needs DECIMAL values, not hex. For example, the line in my ueagle-atm file is:

```
plugin pppoatm.so 0.38
```


The easiest way to make this file is to run:

```
$ sudo gedit /etc/ppp/peers/ueagle-atm
```

cut and paste the above into gedit, then save.

Now modify /etc/ppp/chap-secrets:

```
$ sudo gedit /etc/ppp/chap-secrets
```

You should have a single line which looks like this:

```
"myusername"  "*"  "mypassword"  "*"
```

again, you should replace "myusername" and "mypassword" with your ISP login.

Once the configuration is ok, you need to run

```
$ sudo modprobe pppoatm
$ pon ueagle-atm
```

To check connection try:

```
$ ifconfig
```

You should see something like:

ppp0    Link encap:Point-to-Point Protocol  
          inet addr:83.30.157.107  P-t-P:213.25.2.202  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:2019 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2025 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:724078 (707.1 KiB)  TX bytes:184065 (179.7 KiB)

Also, the command 'plog' should return something similar to:

Jun 27 21:25:27 hostname pppd[5179]: Connect: ppp0 <--> 0.38
Jun 27 21:25:32 hostname pppd[5179]: CHAP authentication succeeded
Jun 27 21:25:32 hostname pppd[5179]: CHAP authentication succeeded
Jun 27 21:25:32 hostname pppd[5179]: Cannot determine ethernet address for proxy ARP
Jun 27 21:25:32 hostname pppd[5179]: local  IP address 83.30.157.107
Jun 27 21:25:32 hostname pppd[5179]: remote IP address 212.74.111.187
Jun 27 21:25:32 hostname pppd[5179]: primary   DNS address 80.225.252.58
Jun 27 21:25:32 hostname pppd[5179]: secondary DNS address 80.225.252.50



Smile :D  You're done. Go browse your favourite sites!

Next time you reboot, if your modem is plugged in the ueagle-atm and pppoatm should load automatically. You just need to run 'pon ueagle-atm'. You could put this in a script or your session startup if you want.

**KERNEL UPGRADE**

If you upgrade your kernel, be sure to also get the same version kernel headers. The auto updater doesn't do this for you. Either get them with synaptic or else:

```
$ sudo apt-get install linux-headers-'uname -r'
```

Once you are booted into the new kernel, follow the steps above to remove the old eagle-usb modules and make ueagle-atm for your new kernel:

```
$ sudo modprobe -r eagle-usb
$ sudo rm /lib/modules/'uname -r'/kernel/drivers/usb/atm/usbatm.ko
$ sudo rm /lib/modules/'uname-r'/kernel/drivers/usb/net/eagle/eagle-usb.ko
```

Unplug then reconnect the modem, then:

```
$ cd ueagle-atm-1.3
$ sudo make
$ sudo make install
$ sudo modprobe ueagle-atm
```

When the lights stop flashing:

```
$ pon ueagle-atm
```

That should be it.


I hope this helps at least one person. I know its a long post, but it was fairly easy, honest. If you have any problems, feel free to ask, I may be able to help. Or you could try the Ueagle wiki, and they also have a forum [here]("http://forum.eagle-usb.org/") which is particularly good if you speak French (of course I don't, I'm english!). Finally, there is a mailing list [here]("https://mail.gna.org/listinfo/ueagleatm-dev/") with a link to archived posts which I found particularly useful.

---

### Post by deepershade on 2006-06-21
I'm having problems =/

I've followed your instructions to the letter, but it's not allowing me to connect.

This is what ifconfig gives out:

```
Link encap: Local Loopback
inet addr:127.0.0.1 Mask: 255.0.0.0
inet6 addr: ::1/128 Scope: Host
UP LOOPBACK RUNNING MTU:16436 Metric: 1
RX Packets: 51 errors: 0 dropped: 0 overruns: 0 frame: 0
TX Packets: 51 errors: 0 dropped: 0 overrruns: 0
collisions: 0 txqueuelen: 0
RX bytes: 4028 (3.9kib) TX bytes:4028 (3.9kib)
```

The modem is shown to be operational, but it just won't connect to anything.
I have a sneaking suspision that the 'local loopback' might have something to do with it. I have a feeling that it's basically connecting to itself (I thought only windows borked like that? :))

Any help you can give would be awesome. I can't use ubuntu until the modem works (can't get it to load X on any graphics settings so I need flgrx).

---

### Post by aces21 on 2006-06-22
deepershade,

if your model is operational, i.e. dmesg|grep ueagle gives you something like:

usb 1-2: [ueagle-atm] modem operational
usb 1-2: [ueagle-atm] ATU-R firmware version : 43e2ead7

then it is likely a login issue. Which ISP are you with - are you sure it uses PPPOATM? If it does, then the most common problem I have seen is that pap-secrets and/or chap-secrets are wrong. You should check you have only the single line in both:

"myusername"  "*"  "mypassword"  "*"


I also read that the correct way to startup pppd is to use the 'pon' command.  So in this example, it would be:

```
$ pon ueagle-atm
```

And to stop the connection, you would use:

```
$ sudo poff ueagle-atm
```

I haven't tried this yet though. If it works, I'll update my howto. More importantly, you should be able to use the command:

```
$ plog
```

to get diagnostic information from either /var/log/ppp.log or /var/log/syslog. Can you try this - what output do you get from plog? If you don't get anything, what is in /var/log/ppp.log and what do you get from the command:

```
$tail /var/log/syslog
```

Let us know how you get on.

---

### Post by underthing on 2006-06-23
Thanks a lot for posting this **aces**. I just upgraded to Dapper and never would have figured all this out on my own - or I would have, but with great difficulty ;) 

I did notice one minor typo in the post, although maybe it doesn't really matter:

Where you say to do

```

$ sudo rm /lib/modules/'uname r'/kernel/drivers/usb/net/eagle/eagleusb.ko

```

On my machine, it was actually located here:
```

$ sudo rm /lib/modules/'uname r'/kernel/drivers/usb/net/eagle/eagle-usb.ko

```

(note hyphen in the file name)

Another thing that kind of threw me was that I need to use decimal values for the VP.VC setting...however, there is a page on the eagle-usb wiki that breaks down lots of ISPs and their settings:

[http://faq.eagle-usb.org/wakka.php?wiki=ListConfigADSL]("http://faq.eagle-usb.org/wakka.php?wiki=ListConfigADSL")

I'm on Wanadoo in France, so I used:

```
plugin pppoatm.so 0.38
```

**deepershade**, this could be the issue with your connection problems. At first I had the hex values instead of decimal, and the modem would do everything but connect. So perhaps the ISP table on the wiki at the link above will help you.

Cheers again **aces**! 8)

---

### Post by christhemonkey on 2006-07-04
Im having major problems getting this to work,
every time i try and run sudo make, it says:
> 
make[1]: Entering directory '/lib/modules/2.6.15-23-386/build'
make[1]: *** No targets specified and no makefile found.     Stop.
make[1]: Leaving directory '/lib/modules/2.6.15-23-386/build'
make[1]: *** [all] Error 2


I have linux-headers and linux-headers-386 for my kernel version installed, and make installed. (i am on a computer with no internet access, and build-essential has loooooads of dependencies, so im guessing this is the root of the problem, but so far, just having make has been fine for most things)



EDIT: Have installed build-essential, and exactly same thing happens.
I redownloaded the .tar.gz from the other mirror, and exactly the same thing happens.

---

### Post by aces21 on 2006-07-04
[QUOTE=christhemonkey]Im having major problems getting this to work,
every time i try and run sudo make, it says:


I have linux-headers and linux-headers-386 for my kernel version installed, and make installed. (i am on a computer with no internet access, and build-essential has loooooads of dependencies, so im guessing this is the root of the problem, but so far, just having make has been fine for most things)



EDIT: Have installed build-essential, and exactly same thing happens.
I redownloaded the .tar.gz from the other mirror, and exactly the same thing happens.[/QUOTE]

Are you running make from the directory where you unpacked the tar.gz? It says it can't find the makefile, which should be in there. To recap, did you:

```
$ tar -xvzf ueagle-atm-1.3.tar.gz
$ cd ueagle-atm-1.3
$ sudo make
$ sudo make install
```

---

### Post by christhemonkey on 2006-07-04
Yes i did, and it fails at the sudo make stage.
I have taken a brief look at the makefile, and there isnt much in it.
It tries to compile things in /lib/modules/'uname -r'/build

The folder exists on my system, but there is nothing in there...


EDIT:
Funnily enough on packages.ubuntu.com , when using the search contents of package option, it does not seem to be able to find my kernel version at all.... only the 2.6.15-22-various_architecture versions.

---

### Post by christhemonkey on 2006-07-04
Well, installing the latest kernel (2.6.15-25-686) seems to have solved that problem.
Sorted!

EDIT: No it isnt sorted.
It compiles and installs fine, but when i try and modprobe the ueagle-atm module, it reports that there were errors and then does not load it.
Being the idiot i am, i decided to force load it, which led to a kernel that would no longer accept any sort of calls.
Just rebooting now, will let know if problem still occurs.


EDIT NO2: When loading the ueagle-atm kernel module, it says this:
> FATAL: Module ueagle_atm (/lib/modules/2.6.15-25-686/extra/ueagle-atm.ko):
Unknown symbol in module, or unknown parameter (see dmesg)

So here is the relevant dmesg output:
> 
usbcore: deregistering driver eagle-usb
[eagle-usb] ADSL Device removed
[eagle-usb] driver unloaded
ueagle_atm: disagrees about version of symbol usbatm_usb_probe
ueagle_atm: Unkown symbol usbatm_usb_probe


This is using the 1.3 version of the ueagle-atm thing.

---

### Post by christhemonkey on 2006-07-05
Should i recompile using the cvs/svn version, you reckon?

Any opinions, thoughts, advice?

---

### Post by babis85 on 2006-07-08
> **deepershade said:**
> I'm having problems =/

I've followed your instructions to the letter, but it's not allowing me to connect.

This is what ifconfig gives out:

```
Link encap: Local Loopback
inet addr:127.0.0.1 Mask: 255.0.0.0
inet6 addr: ::1/128 Scope: Host
UP LOOPBACK RUNNING MTU:16436 Metric: 1
RX Packets: 51 errors: 0 dropped: 0 overruns: 0 frame: 0
TX Packets: 51 errors: 0 dropped: 0 overrruns: 0
collisions: 0 txqueuelen: 0
RX bytes: 4028 (3.9kib) TX bytes:4028 (3.9kib)
```

The modem is shown to be operational, but it just won't connect to anything.
I have a sneaking suspision that the 'local loopback' might have something to do with it. I have a feeling that it's basically connecting to itself (I thought only windows borked like that? :))

Any help you can give would be awesome. I can't use ubuntu until the modem works (can't get it to load X on any graphics settings so I need flgrx).


Hello, might [this](http://www.ubuntuforums.org/showthread.php?t=197753&highlight=sagem)  thread help you. I had exactly the same problem. Notice, specially the #9 post.

---

### Post by ColdDeath on 2006-08-03
Sorry to bump up this guide, but I'd just like to thank Aces21 for it.

The Sagem Fast modem has always been a problem for me in the Linux world, but as soon as I learnt to compile its drivers it was easy. But with the kernel change the drivers wouldn't compile. I searched for a bit and found htis thread and it works perfectly. Thanks for the help.

Just one question though: I would I set it to connect at startup and disconnect when shutdown or rebooted?

:-k

---

### Post by lots_of_entropy on 2006-08-05
Btw. If you see this masage in dmesg

[ueagle-atm] (re)booting started

and it stops ... plug in your phone line ;-).

Cheers

Dom

---

### Post by christhemonkey on 2006-08-05
I still have no internet :(

This is with a Sagem F@ST 800-840 that comes with Tiscali Broadband in the UK.
Running ubuntu dapper drake 2.6.15-25-686 kernel.

---

### Post by ColdDeath on 2006-08-08
Try what he says, it works and it works well.

---

### Post by christhemonkey on 2006-08-08
From the page before:
> EDIT NO2: When loading the ueagle-atm kernel module, it says this:

Quote:
FATAL: Module ueagle_atm (/lib/modules/2.6.15-25-686/extra/ueagle-atm.ko):
Unknown symbol in module, or unknown parameter (see dmesg)
 

So here is the relevant dmesg output:

Quote:
usbcore: deregistering driver eagle-usb
[eagle-usb] ADSL Device removed
[eagle-usb] driver unloaded
ueagle_atm: disagrees about version of symbol usbatm_usb_probe
ueagle_atm: Unkown symbol usbatm_usb_probe
 


This is using the 1.3 version of the ueagle-atm thing.

---

### Post by aces21 on 2006-08-09
> **christhemonkey said:**
> From the page before:

EDIT NO2: When loading the ueagle-atm kernel module, it says this:
Quote:
FATAL: Module ueagle_atm (/lib/modules/2.6.15-25-686/extra/ueagle-atm.ko):
Unknown symbol in module, or unknown parameter (see dmesg)
So here is the relevant dmesg output:
Quote:
usbcore: deregistering driver eagle-usb
[eagle-usb] ADSL Device removed
[eagle-usb] driver unloaded
ueagle_atm: disagrees about version of symbol usbatm_usb_probe
ueagle_atm: Unkown symbol usbatm_usb_probe

This is using the 1.3 version of the ueagle-atm thing.


I just saw the Unknown symbol usbatm_usb_probe message too. This was after the update manager decided I should upgarde to kernel version 2.6.15-26, even though that was the version I was already using! After (re?)installing the new kernel and rebooting, I recompiled ueagle-atm and then modprobe didn't work, as you said. I'm suspicious of this kernel version and reading the forums it looks like other people have seen problems with it.

Anyway, I figured I'd try the latest SVN so I rebooted into kernel 2.6.15-25 where ueagle-atm did work, downloaded the source, then went back into 2.6.15-26. My modem lights start flashing! When I check, the ueagle modules have loaded o.k. Wierd.

I really have no idea what is going on. Its like being in XP! Seriously though, if you get the modprobe error, try rebooting and see what happens. It makes no sense that this should work and I'll search around to see if its been reported when I have time. Worth a shot though. And if it still doesn't work you could try the latest SVN.

By the way, I'm usng the stock 386 kernel, not the 686 one. You could try that too.

---

### Post by christhemonkey on 2006-08-09
Ok, i shall try a reboot.
and if that does not succeed, then downgrading to the 686 kernel.


The latest SVN will be next after all that though :p

---

### Post by monkeydust on 2006-08-13
Hello - I'm very sorry for troubling you folks, but I'm also having problems installing my Sagem F@st 800.

I hope someone can help me, because I'm getting bored of having to reboot between Windows and Linux!

Here's all the info I can think of:

I'm running Ubuntu 6.0.6lts (I think?), on a DELL 1.6ghz Intel x86

My kernel is 2.6.15-26-386

Running SUDO Modprobe ueagle-atm returns nothing.

Running DMESG returns:

Driver ueagle-gna 1.3 loaded
ADSL founded 0x1110 pid 0x9031 - Eagle III
Using ISO mode
(re)booted
Created Proc ueagle-atm 002-002
USBCORE - registered new driver ueagle-atm
(re)booted
(re)booted
ADSL Device Removed

...I'm really stumped!

Someone said (re)booted means the phone line is not plugged in, but it definitely is. Also: the two lights on the front appear to remain on the whole time.

Is this enough info? I'm using diver UEAGLE-ATM ver 1.3, with Firmware from the non-free dir of the ueagle website (as per all the tutorials on this).

Thanks for any advice -- David

---

### Post by Kiongku on 2006-08-13
OMG u saved me.
After several days of mindwracking and pc restarts i was on the verge of giving up on kubuntu.
The guide is very good.
I followed it by the letter and got my kubuntu with kernel 2.6.15-26 to work with an internet connection at last ^^.

---

### Post by aces21 on 2006-08-14
> **monkeydust said:**
> Hello - I'm very sorry for troubling you folks, but I'm also having problems installing my Sagem F@st 800.

I hope someone can help me, because I'm getting bored of having to reboot between Windows and Linux!

Here's all the info I can think of:

I'm running Ubuntu 6.0.6lts (I think?), on a DELL 1.6ghz Intel x86

My kernel is 2.6.15-26-386

Running SUDO Modprobe ueagle-atm returns nothing.

Running DMESG returns:

Driver ueagle-gna 1.3 loaded
ADSL founded 0x1110 pid 0x9031 - Eagle III
Using ISO mode
(re)booted
Created Proc ueagle-atm 002-002
USBCORE - registered new driver ueagle-atm
(re)booted
(re)booted
ADSL Device Removed

...I'm really stumped!

Someone said (re)booted means the phone line is not plugged in, but it definitely is. Also: the two lights on the front appear to remain on the whole time.

Is this enough info? I'm using diver UEAGLE-ATM ver 1.3, with Firmware from the non-free dir of the ueagle website (as per all the tutorials on this).

Thanks for any advice -- David

David,

if you unplug the USB cable from your modem, then plug it back in again, what happens to the lights? Also, what does dmesg now say?

---

### Post by monkeydust on 2006-08-14
Hi there Aces21

Firstly -- thank you very much for this thread - you've been very generous with your time + tutorial, it's just a shame it's not worked first time for me.

When I unplug+replug the modem the lights both come on instantly and remain on, and DMESG|grep Eagle returns exactly the same.

I know that the ADSL light should start off flashing and then come on constant, but under Ubuntu it just stays stubbornly lit!

---

### Post by christhemonkey on 2006-08-14
Aces21, i must say an amazingly large thankyou!!

I know have my internet working, and really working well! (over120 kbps downloads?!)

All i did was switch on the laptop, insert the modem, modprobe pppoatm, and then, magic happened :D

Cheers from a very happy christhemonkey.

---

### Post by aces21 on 2006-08-15
> **monkeydust said:**
> Hi there Aces21

Firstly -- thank you very much for this thread - you've been very generous with your time + tutorial, it's just a shame it's not worked first time for me.

When I unplug+replug the modem the lights both come on instantly and remain on, and DMESG|grep Eagle returns exactly the same.

I know that the ADSL light should start off flashing and then come on constant, but under Ubuntu it just stays stubbornly lit!

David,

you could try running ueagle-diag to get more diagnostics info. If you don;t already have it, you can get it as part of ueagle-utils [here]("http://download.gna.org/ueagleatm/ueagle-utils-1.3.tar.gz").

I haven't had time to play with it yet but it might throw up something useful.

---

### Post by monkeydust on 2006-08-17
Sorry guys - I'm giving up...

Anyone know of any friendly Linux distributions that will identify and correctly install my Sagem Fast 800 without any effort?

I can't seem to win with this! I've tried every tutorial online, mixing bits from different ones and have completely reinstalled four times...

Any distro suggestions welcome!

---

### Post by christhemonkey on 2006-08-17
You wernt typing:
```
dmesg | grep Eagle 
```
Where you?
I believe bash is case sensitive, so that would return nothing.
```
dmesg | grep eagle 
```
However may return something useful :)

Just my £0.02

And no, i cant think of any linux distros that come with ueagle-atm as default, mayhaps Suse?

---

### Post by aces21 on 2006-08-18
> **monkeydust said:**
> Sorry guys - I'm giving up...

Anyone know of any friendly Linux distributions that will identify and correctly install my Sagem Fast 800 without any effort?

I can't seem to win with this! I've tried every tutorial online, mixing bits from different ones and have completely reinstalled four times...

Any distro suggestions welcome!


If your main priority is getting the Sagem modem working then you could try Breezy Badger, the last release of Ubuntu. It used eagle-usb rather than ueagle-atm, but as far as I remember it was included as part of the install and worked first time for me.

Other than that, any distro that has the 2.6.16 kernel or newer should have ueagle-atm built-in. Of course that's no guarantee it will work!

It is a real pain that Linux doesn't play so nice with USB modems, especially as thats what most cheap ISPs provide. If you've got an ethernet card then another option is to pick up a cheap ethernet based modem. Apparent that should work pretty much straight off. Never tried it though.

Sorry we couldn't get you going.

---

### Post by christhemonkey on 2006-08-18
Breezy was very temperemental with my modem for me, hoary worked beautifully though!
All i did was set up my chap-secrets file and then connect and it was fine.

EDIT: but i dont think i would go back to hoary now :s

---

### Post by monkeydust on 2006-08-19
Thanks guys for all your advice. Will just have to carry on doing things the 'Windows Way' for now...

---

### Post by Magnes on 2006-08-19
> **monkeydust said:**
> Thanks guys for all your advice. Will just have to carry on doing things the 'Windows Way' for now...

Maybe you should [try this](http://download.gna.org/eagleusb/eagle-usb-2.3.0/eagle-usb-2.3.3.tar.bz2).
It's eagle-usb hacked to work with new kernels. I don't use it since uagle-atm works fine for me, but it's popular method in Poland to get Sagem800 working on linux.
Installation is identical like the old eagle-usb in breezy.

---

### Post by aces21 on 2006-08-22
> **Magnes said:**
> Maybe you should [try this](http://download.gna.org/eagleusb/eagle-usb-2.3.0/eagle-usb-2.3.3.tar.bz2).
It's eagle-usb hacked to work with new kernels. I don't use it since uagle-atm works fine for me, but it's popular method in Poland to get Sagem800 working on linux.
Installation is identical like the old eagle-usb in breezy.

Now I recall, I used a hacked eagle-usb with breezy also. It was hoary that worked without problem.

---

### Post by silent_scream on 2006-08-23
Something goes wrong with me but i don't know what...
Could you help me?

Everything is good untill...

```
silent@MetallicA:~$ sudo pon ueagle-atm
Plugin pppoatm.so loaded.
silent@MetallicA:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:287 errors:0 dropped:0 overruns:0 frame:0
          TX packets:287 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:20996 (20.5 KiB)  TX bytes:20996 (20.5 KiB)

silent@MetallicA:~$ plog
Aug 24 05:55:01 MetallicA pppd[5765]: pppd 2.4.4b1 started by root, uid 0
Aug 24 05:55:01 MetallicA pppd[5765]: Using interface ppp1
Aug 24 05:55:01 MetallicA pppd[5765]: Connect: ppp1 <--> 8.35
Aug 24 05:55:08 MetallicA pppd[5571]: connect(8.35): Address already in use
Aug 24 05:55:08 MetallicA pppd[5571]: Exit.
Aug 24 05:55:24 MetallicA pppd[5510]: LCP: timeout sending Config-Requests
Aug 24 05:55:24 MetallicA pppd[5510]: Connection terminated.
Aug 24 05:55:24 MetallicA pppd[5510]: Modem hangup
Aug 24 05:55:34 MetallicA pppd[5765]: No response to PAP authenticate-requests
Aug 24 05:55:34 MetallicA pppd[5765]: Connection terminated.

```

so have i done something wrong?
I am from Greece so the VP.VC should be 8.35 according with the link you gave, right?

---

### Post by aces21 on 2006-08-24
> **silent_scream said:**
> Something goes wrong with me but i don't know what...
Could you help me?

Everything is good untill...

```
silent@MetallicA:~$ sudo pon ueagle-atm
Plugin pppoatm.so loaded.
silent@MetallicA:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:287 errors:0 dropped:0 overruns:0 frame:0
          TX packets:287 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:20996 (20.5 KiB)  TX bytes:20996 (20.5 KiB)

silent@MetallicA:~$ plog
Aug 24 05:55:01 MetallicA pppd[5765]: pppd 2.4.4b1 started by root, uid 0
Aug 24 05:55:01 MetallicA pppd[5765]: Using interface ppp1
Aug 24 05:55:01 MetallicA pppd[5765]: Connect: ppp1 <--> 8.35
Aug 24 05:55:08 MetallicA pppd[5571]: connect(8.35): Address already in use
Aug 24 05:55:08 MetallicA pppd[5571]: Exit.
Aug 24 05:55:24 MetallicA pppd[5510]: LCP: timeout sending Config-Requests
Aug 24 05:55:24 MetallicA pppd[5510]: Connection terminated.
Aug 24 05:55:24 MetallicA pppd[5510]: Modem hangup
Aug 24 05:55:34 MetallicA pppd[5765]: No response to PAP authenticate-requests
Aug 24 05:55:34 MetallicA pppd[5765]: Connection terminated.

```

so have i done something wrong?
I am from Greece so the VP.VC should be 8.35 according with the link you gave, right?

It looks like it could be a password problem. I'm not sure but it looks like your ISP uses PAP instead of CHAP, so I'd check your pap-secrets file. It should look exactly the same as chap-secrets. Hope this helps.

---

### Post by silent_scream on 2006-08-24
you mean EXACTLY the same? beacuse there aren't the same right now.
could you paste your pap-secrets and chap-secrets file here for me?

so there isn't something wrong with the VP.VC ?

---

### Post by aces21 on 2006-08-25
> **silent_scream said:**
> you mean EXACTLY the same? beacuse there aren't the same right now.
could you paste your pap-secrets and chap-secrets file here for me?

so there isn't something wrong with the VP.VC ?

Yes, exactly the same. I can't paste my own files as they contain my ISP login and password! But, they should both look like:

```
"myusername" "*" "mypassword" "*"
```

(you should replace "myusername" and "mypassword" with your ISP login.)

---

### Post by silent_scream on 2006-08-25
yeah i'm sorry.
but you could paste the files and replace your ISP login and pass with "***" !!!

p.m. me if you want!

thnx for your time!

edit: man you were right!!!
i'm using ubuntu now!
you re great! that was a great how-to!

last thing: the VP.VC is right?
i am from greece so it should be

```
pppoatm.so 8.35
```

right?

could you check it out?
thnx for all...!

---

### Post by Magnes on 2006-08-25
dmesg:
> ueagle_atm: disagrees about version of symbol usbatm_usb_probe
ueagle_atm: Unkown symbol usbatm_usb_probe

I have this problem now after installing some updates (two days ago) to Ubuntu, before that ueagle worked like a charm. Don't have older kernel to test method described above (on 2nd page). What should I do? :confused:

SOLVED: deleting usbatm.ko and ueagle-atm.ko from kernel/drivers/usb/atm (or sth similiar) and recompiling ueagle-atm helped. :D

---

### Post by HAL98 SE on 2006-08-27
Thank you for this HOWTO. Its excellent and works really well.

---

### Post by HAL98 SE on 2006-08-27
Doh!

I'm having a similar issue with regards modprobe - dmesg returning '
FATAL: Error inserting ueagle_atm (/lib/modules/2.6.15-26-server/extra/ueagle-atm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
', you say you resloved this? how?  is it just a case of rebooting and then plugging in the modem?


Yup. Just a case of restarting it, sorted the problem!!

Thanks for the HOWTO! long live OSS.

---

### Post by HAL98 SE on 2006-08-27
I'm back, and this time there's some kind of conflict occuring between my LAN and the modem.

```
plog
Aug 27 19:17:37 steveserver pppd[4042]: CHAP authentication succeeded
Aug 27 19:17:37 steveserver pppd[4042]: CHAP authentication succeeded
Aug 27 19:17:37 steveserver pppd[4042]: not replacing existing default route via 192.168.0.1
Aug 27 19:17:37 steveserver pppd[4042]: Cannot determine ethernet address for proxy ARP
Aug 27 19:17:37 steveserver pppd[4042]: local  IP address **.**.**.**
Aug 27 19:17:37 steveserver pppd[4042]: remote IP address 212.74.111.216
Aug 27 19:17:37 steveserver pppd[4042]: primary   DNS address 80.225.252.50
Aug 27 19:17:37 steveserver pppd[4042]: secondary DNS address 80.225.252.58
```



When i unplug the LAN cable and reboot ubuntu, the modem works fine, but if i boot with the LAN connected/connect the LAN after connecting using eagle, I get the above output (and the internet connection doesnt work/fails). It's something to do with ppp trying to use the default ICS route or something. (I have an XP machine that was originally the default gateway and ICS)

any suggestions more than welcome!!

 ](*,) :-D

---

### Post by shaughan on 2006-09-16
Hi All

I thought everything was going well until I tried loading the Point to Point Tunneling protocol thingy after having gone through this guide (Thinking that might have been a problem). Now When I try pon ueagle, I get this "/usr/sbin/pppd: /usr/lib/pppd/2.4.4b1/pppoam.so: cannot open shared object file: No such file or directory
/usr/sbin/pppd: Couldn't load plugin pppoam.so
"
I think I am going to go nuts. I am in the UK on Tiscali. My modem also comes on immediately without flashing it's lights.

Any ideas?:frown:

---

### Post by shaughan on 2006-09-16
> **shaughan said:**
> Hi All

I thought everything was going well until I tried loading the Point to Point Tunneling protocol thingy after having gone through this guide (Thinking that might have been a problem). Now When I try pon ueagle, I get this "/usr/sbin/pppd: /usr/lib/pppd/2.4.4b1/pppoam.so: cannot open shared object file: No such file or directory
/usr/sbin/pppd: Couldn't load plugin pppoam.so
"
I think I am going to go nuts. I am in the UK on Tiscali. My modem also comes on immediately without flashing it's lights.

Any ideas?:frown:

Edit: I went away in frustration and came back to it.Silly me, it was staring me right in the face. I left out the t in ppoatm.so, didn't I? What an arse. Excellent tutorial. Thanks:p

---

### Post by monkeydust on 2006-09-19
Hello all!

I finally got it working! 

THEN: the new Kernel release came in and it's stopped working...

Please could someone tell me what I'm supposed to do?

In honesty, I'm totally baffled why an update should go out that destroys peoples nvidia graphics/DSL modems etc. (from other posts here). Will this happen every time a new Kernel comes out?

Thanks a LOT.

---

### Post by monkeydust on 2006-09-20
Was just being a newbie :rolleyes: - don't worry, think I've got it sorted now.

---

### Post by Aenigma on 2006-10-05
Aces i would like to thankyou, like everyone else does.
This is my first post from linux :) and although your how to didnt seem to work first time, it would have if i had entered my isp login name right in the ueagle-atm file in /etc/ppp/peers.

I would like everyone having the same problem as dave, an operational modem, but no connection to check their Chap-secrets, Pap-secrets and etc/ppp/peers/Ueagle-atm file as this is what caused my problems. Silly i know but its fixed now. :)  Im just wondering, now im online, if the kernel updates, do i have problems again?


Thanks again.

---

### Post by aces21 on 2006-10-05
> **Aenigma said:**
> Im just wondering, now im online, if the kernel updates, do i have problems again?

If you update your kernel, make sure you also get the new kernel-hearders, boot into the new kernel, then install the modules for the new kernel. There ae full instructions at the bottom of the howto.

---

### Post by digitalantichrist on 2006-10-23
Hi, I downloaded Ubuntu yesterday, I'm very new to Linux so I know practically nothing about it, and I'm having a few (ha!) problems.

I've been trying to get my sagem modem up and running, so far with no success.  This is where I get to before my brow furrows and I need to imbibe liquid, heh.

user@user-desktop:~$ tar -xvzf ueagle-atm-1.3.tar.tar
ueagle-atm-1.3/
ueagle-atm-1.3/COPYING
ueagle-atm-1.3/Makefile
ueagle-atm-1.3/ueagle-atm.c
ueagle-atm-1.3/usbatm.c
ueagle-atm-1.3/usbatm.h
ueagle-atm-1.3/README
user@user-desktop:~$ cd ueagle-atm1.3
bash: cd: ueagle-atm1.3: No such file or directory
user@user-desktop:~$ cd ueagle-atm-1.3
user@user-desktop:~/ueagle-atm-1.3$ sudo make
Password:
make -C /lib/modules/2.6.15-26-amd64-generic/build M=/home/darren/ueagle-atm-1.3
make: *** /lib/modules/2.6.15-26-amd64-generic/build: No such file or directory.   Stop.
make: *** [all] Error 2
user@user-desktop:~/ueagle-atm-1.3$

Its at about this point that I wonder.... hmmm, easier than windows? ;)
 
Can you offer advice?  In simple terms, please.

---

### Post by christhemonkey on 2006-10-23
You need your kernel-headers
```
sudo apt-get install linux-headers-2.6.15-26-amd64-generic
```

(and if you have no internet, then you can go to here:
[http://packages.ubuntu.com/dapper/devel/linux-headers-2.6.15-26-amd64-generic](http://packages.ubuntu.com/dapper/devel/linux-headers-2.6.15-26-amd64-generic)
and get the .deb and all of its dependencies)

---

### Post by ehird on 2006-10-24
Stuck on the first command. If I don't have an internet connection, how on earth can I use apt-get?

---

### Post by ehird on 2006-10-24
Bump :(

---

### Post by ehird on 2006-10-24
Any help? :S

---

### Post by ehird on 2006-10-24
Guess my problem is obscure? :(

---

### Post by christhemonkey on 2006-10-25
No,

If your ubuntu box is offline (for the moment), then you have to visit this site:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

And search for the packages that you want to install.

Be sure though to get all the dependencies of the packages (they are listed when you go to download the package)

This can be a time consuming process.
But its worth it :p

---

### Post by ehird on 2006-10-25
Yeah... I tried that before and spent years getting dependencies and nuked my Kubuntu install. But I'll try.

---

### Post by ehird on 2006-10-25
I'm getting this error:
```
ehird@ehird-desktop:~/ueagle-atm-1.3$ sudo make
make -C /lib/modules/2.6.15-26-386/build M=/home/ehird/ueagle-atm-1.3
make: *** /lib/modules/2.6.15-26-386/build: No such file or directory.  Stop.
make: *** [all] Error 2
ehird@ehird-desktop:~/ueagle-atm-1.3$
```
I tried just making the directory but it complains about a missing makefile iirc.

---

### Post by christhemonkey on 2006-10-25
Ok the files i think you need to get (including all dependencies) are:

NOTE: im assuming you are running kernel 2.6.15-27-386, if not replace 2.6.15-27-386 with the output of this terminal command:
```
uname -r
```


linux-headers-2.6.15-27-386
linux-headers-2.6.15-27
build-essential
dpkg-dev
binutils
cpio
make
patch
perl-modules
perl
perl5
g++
g++-4.0
cpp
cpp-4.0
gcc-4.0-base
gcc-4.0
gcc
libstdc++6-4.0-dev
ibstdc++6
libgcc1
libc6-dev


I think that is it!

---

### Post by christhemonkey on 2006-10-25
And you need your kernel headers, that is what it is failing over.

So get this file from packages.ubuntu.com:
linux-headers-2.6.15-27-386
(replacinf 2.6.15-27-386 with whatever kernel your running)

---

### Post by ehird on 2006-10-25
I've got all of those packages except:

perl*
cpio
dpkg*
patch
linux-headers*

I'll get them now.

---

### Post by ehird on 2006-10-25
I give up.

First I had to change $(BUILD) or whatever was equaling gcc in the makefile to gcc-4.1.

Then it complains about there being no directory called M=/home/ehird/.

I remove the M= and one of the things it seems to run complains about a missing file.

Linux will never work with my modem.

---

### Post by christhemonkey on 2006-10-25
It will if you persist.

I have to go now but im sure someone can help you with your problem.

---

### Post by christhemonkey on 2006-10-25
Ok, im back,

Could you be a touch more patient and possibly list the exact errors it gives you?

---

### Post by ehird on 2006-10-25
Makefile:
```

ifndef KERNELDIR
KERNELDIR  := /lib/modules/$(shell uname -r)/build
endif

obj-m := ueagle-atm.o
obj-m += usbatm.o

all:
	gcc-4.1 -C $(KERNELDIR) M=$(PWD)

debug:
	gcc-4.1 -C $(KERNELDIR) M=$(PWD) EXTRA_CFLAGS="-DDEBUG"
	
clean:
	gcc-4.1 -C $(KERNELDIR) M=$(PWD) clean

install:
	gcc-4.1 -C $(KERNELDIR) M=$(PWD) modules_install
	/sbin/depmod -ae


```
Output:
```

ehird@ehird-desktop:~/ueagle-atm-1.3$ sudo make
gcc-4.1 -C /lib/modules/2.6.15-26-386/build M=/home/ehird/ueagle-atm-1.3
gcc-4.1: M=/home/ehird/ueagle-atm-1.3: No such file or directory
make: *** [all] Error 1
ehird@ehird-desktop:~/ueagle-atm-1.3$

```
Makefile:
```

ifndef KERNELDIR
KERNELDIR  := /lib/modules/$(shell uname -r)/build
endif

obj-m := ueagle-atm.o
obj-m += usbatm.o

all:
	gcc-4.1 -C $(KERNELDIR) $(PWD)

debug:
	gcc-4.1 -C $(KERNELDIR) $(PWD) EXTRA_CFLAGS="-DDEBUG"
	
clean:
	gcc-4.1 -C $(KERNELDIR) $(PWD) clean

install:
	gcc-4.1 -C $(KERNELDIR) $(PWD) modules_install
	/sbin/depmod -ae

```
Output:
```

ehird@ehird-desktop:~/ueagle-atm-1.3$ sudo make
gcc-4.1 -C /lib/modules/2.6.15-26-386/build /home/ehird/ueagle-atm-1.3
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
make: *** [all] Error 1
ehird@ehird-desktop:~/ueagle-atm-1.3$  

```

---

### Post by christhemonkey on 2006-10-25
Ok, the second makefile where it complains about not finding crt1.o, this .o file is provided by the package libc6-dev, please make sure you have that installed correctly.

I do not know why the first makefile does not work.

---

### Post by ehird on 2006-10-25
Looking in [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.1/](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.1/) (where I got libc6), I can't find a libc6-dev. Any assistance?

(By the way, THANK YOU a million times for your help. I know i've been a bit stubborn, I just want to get the 'net working before I start experimenting too much :))

Edit: Found it :) now to test

Edit 2: darn, can't find glibc 2.4

---

### Post by christhemonkey on 2006-10-26
Gcc4.1 is an edgy .deb im afraid.

gcc-4.0 is the latest gcc version for dapper.

So i wouldnt use it.

Also i would really recommend [http://packages.ubuntu.com](http://packages.ubuntu.com) for package searching as that is what it is for (a frontend for archive.ubuntu.com and the other mirrors)

So with a quick search you can find that libc6-dev was here:
[http://packages.ubuntu.com/dapper/libdevel/libc6-dev](http://packages.ubuntu.com/dapper/libdevel/libc6-dev)

---

### Post by christhemonkey on 2006-10-26
Oops just noticed that edgy is indeed out today so you may be running on it.

In which case gcc-4.1 is fine for you to install.

---

### Post by ehird on 2006-10-26
After wiping my kubuntu install today and adding a new edgy install, WITH build-essentials thank god, i get really close now: but when i unplug and replug my modem, both the lights go on! o_O, after the modprobe which should make them flash - that doesn't do anything, but it seems to work after, but everything doesn't work because it can't get to the 0.39 thing. Now I use Tiscali UK too so I don't know why it shouldn't work? :confused:

---

### Post by christhemonkey on 2006-10-26
Edgy again uses the eagle-usb package which does not work with our modems.

Are you sure you actually installed the drivers?
And removed the eagle-usb ones?


What is the output of `dmesg | tail` when you have plugged the modem in?

---

### Post by ehird on 2006-10-26
I obviously did the two things as it's part of the tutorial. will post the output now.

---

### Post by christhemonkey on 2006-10-26
Ok, was just checking whether you tried the steps of the tutorial first thats all!

---

### Post by ehird on 2006-10-26
OMG!!! I'm posting this on Ubuntu!!!! It obviously just needed a restart!!! :) :) :) :D :D :D

Thanks for your help, everyone!

---

### Post by christhemonkey on 2006-10-26
Haha ok no problem!

Glad we sorted your problem ("we" or maybe it was just you... anyways :D)

---

### Post by NX5 on 2006-10-27
Hi,

I'd just like to say a huge thanks to aces21 for writing this guide. I'd be completely stuck without it. :) You should send this to the ISP's who give out these modems by default *cough* Tiscali *cough*.

Thanks again.

---

### Post by aces21 on 2006-10-31
I've updated the howto, firstly to note that it works with Edgy as well as Dapper, and secondly to point people to [http://packages.ubuntu.com/]("http://packages.ubuntu.com/") if they need to get build-essential of the headers and can't use apt because they don't have a working internet connection.

Thanks to christhemonkey for the second point, I didn't realise the place existed!

---

### Post by aces21 on 2006-11-08
So it looks like the edgy kernel already includes ueagle-atm (as well as eagle-usb). This means you don't need to build ueagle yourself. You can stop eagle-usb loading by adding it to the modprobe blacklist and then your modem should work automatically and not break when you upgrade your kernel. I'll update the howto shortly.

---

### Post by klittzzer on 2006-11-30
Aces, I have followed your tutorial to the letter on many occassions now yet have never managed to make my modem operational. Upon entering  sudo modprobe ueagle-atm, the lights remain on permanently, do not flash, and,
I get the message, driver loaded, amongst other things. (I will try it again the next time I boot Ubuntu and copy the message modprobe gives so I can display it here in full. 
I reckon it is because I am running the latest(or am I?) 2.6.17-10, 2.6.17-10-generic kernel in Edgy. This link will show you why I feel this is what is stopping my modem becoming operational despite my following your instructions. It is something to do with the fact that there are 2 kernels (2.6.17-10 & 2.6.17-10-generic) or something like that-

[http://forum.eagle-usb.org/viewtopic.php?t=4499](http://forum.eagle-usb.org/viewtopic.php?t=4499)

Will I have to do the following (from link above)?

-remove the linux headers generic package and the directory in /lib/modules
-remove the 2.6.17-10 directory in /lib/modules
-install the linux-headers-2.6.17-10 & linux-headers-2.6.17-10-386 packages

- make sure the build link in the /lib/modules/2.6.17-10-386 points to /usr/src/linux-headers-2.6.17-10-386

recompile and install ueagel-atm and reboot

I don't know if that is the issue, or, if it is, how to remove the headers etc (can I remove them with Synaptic Package Manager?). I would be double grateful if you, or anyone who understands this stuff, can have a look at the page the above link leads to and let me know if I will have to remove headers etc. A link to a tutorial regarding romoving headers etc would be useful if anyone knows of one.

Thanks for your time Aces. You do a good job of explaining this stuff to this newby.

Klittzzer:confused:

---

### Post by klittzzer on 2006-12-01
Can you help? I am stumped.

I have a problem with connecting to the net though Ubuntu Edgy kernel 2.6.17-10, 2.6.17-10-generic. I am using a Sagem fast 800 USB modem and have been through dozens of walkthroughs to get my modem operationl and thus log on to my ISP (Tiscali UK).

These are some of the methods I have tried,#

[http://ubuntuforums.org/showthread.php?t=201127&highlight=sagem](http://ubuntuforums.org/showthread.php?t=201127&highlight=sagem)

[http://forum.eagle-usb.org/viewtopic.php?t=4499](http://forum.eagle-usb.org/viewtopic.php?t=4499)

[http://www.mail-archive.com/ueagleatm-dev@gna.org/msg00480.html](http://www.mail-archive.com/ueagleatm-dev@gna.org/msg00480.html)

[http://translate.google.com/translate?hl=en&sl=fr&u=http://forum.eagle-usb.org/viewtopic.php%3Fp%3D24367%26sid%3Dfe8eb84a335de94df26140e0e94798d0&sa=X&oi=translate&resnum=2&ct=result&prev=/search%3Fq%3DInstall%2Bueagle-atm-1.3%26hl%3Den%26lr%3D%26sa%3DG](http://translate.google.com/translate?hl=en&sl=fr&u=http://forum.eagle-usb.org/viewtopic.php%3Fp%3D24367%26sid%3Dfe8eb84a335de94df26140e0e94798d0&sa=X&oi=translate&resnum=2&ct=result&prev=/search%3Fq%3DInstall%2Bueagle-atm-1.3%26hl%3Den%26lr%3D%26sa%3DG)

Just some, and I have been through them all several times.

I have installed the headers and build essential requirements, 
everything goes well until I enter

sudo modprobe ueagle-atm

No lights blink, they just stay on.

and when I enter

dmesg|grep ueagle

I always get

[1717959.39600] [ueagle-atm]driver ueagle-gna 1.3 loaded
[1717959.39600] usb2-1 : [ueagle-atm] ADSL device founded vid (ox1110) pid (ox9032) 

: eagle III
[1717959.468000] [usb2-1 : [ueagle-atm] pre firmware device, uploading firmware
[1717959.468000] usb2-1 :[ueagle.atm] loading firmware ueagle-atm/eagle III.fw
[1717959.468000] usbcore : registred new driver ueagle-atm

Not 'modem is operational.
What am I doing wrong? I have tried installing the Eagle data and utils in synaptic through my live cd but non of it makes any difference. I simply cannot connect to the net.

I have posted my problem elsewhere yet no one has repilied. Even if it is to say, you cannot log on through the kernel I have, at least I will know.

I would really appreciate it if someone could have a look at this and get back to me. I am getting well wound up about it.

Please help

Cheers

Klittz:confused: :confused: :confused:

---

### Post by blueprint on 2006-12-06
a big thankyou to aces21, but i got caught out because i had prev used my ethernet card at some point to access the internet through a lan, i had to remove the gateway address in the ethernet settings.

---

### Post by aces21 on 2006-12-06
Hi Klittzzer,

sorry I haven't looked at this thread for a while, I've been busy with non-computer stuff :(

After you removed the eagle-usb and usbatm modules, then unplugged and replugged your modem, what lights are on? Then after 'sudo modprobe ueagle-atm', do both lights come straight on?

There should be no problem with having multiple kernels - I have this and my ueagle works o.k. As long as you have compiled ueagle for the kernel you are currently trying to use then it should work.

After you do 'sudo modprobe ueagle-atm', can you then do 'tail -50 dmesg' to print out the last 50 lines of dmesg and post the results here?

---

### Post by fugative on 2006-12-08
I've been ubuntuing for about a month now and nearly ready to make the full leap. Got to tip my hat to you ACES you've earned your tag in my book, your HOWTO saved my marriage after two weeks of banging my head against a wall you included two small points that no-one else had and everything worked! (deleting the eagle files).

so just one thing more on this subject, how do i get the $pon ueagle-atm into the start up session so it boots up on-line so my wife doesn't need to go near the terminal.

Ta in advance

---

### Post by aces21 on 2006-12-08
> **fugative said:**
> I've been ubuntuing for about a month now and nearly ready to make the full leap. Got to tip my hat to you ACES you've earned your tag in my book, your HOWTO saved my marriage after two weeks of banging my head against a wall you included two small points that no-one else had and everything worked! (deleting the eagle files).

so just one thing more on this subject, how do i get the $pon ueagle-atm into the start up session so it boots up on-line so my wife doesn't need to go near the terminal.

Ta in advance

Hi Fugative,

to add pon ueagle-atm to your startup, go to 

System->Preferences->Sessions->Startup Programs

then select 'Add' and in the box that appears just type 'pon ueagle-atm'(the default order should be fine). Next time you startup or login, the command should run and voila - instant internet!

Have fun :)

---

### Post by fugative on 2006-12-08
:KS cheers aces, once again simplicity wins the day. I might have found that but lets face it life is too short. 
don't know anything about ad-hoc wireless lans do you?

take it easy

---

### Post by veganrailpunk on 2006-12-18
Hello

I have just done a big automatic security update for Edgy. A couple of the files were linux kernel header updates, quite big (20MB or so). It then prompted me to reboot and when i did I had lost the option for booting windows in GRUB (now sorted) and also my internet connexion wouldn't work. I don't think the kernel was updated. I think I'm still using v 2.6.17-10-generic but i don't know how to check.

I went through the "how to" again and it returned a FATAL ERROR at 

sudo modprobe ueagle-atm

please help! - it was working perfectly

pete
xx

---

### Post by veganrailpunk on 2006-12-19
Ok scratch that.. it started working again all on it's own... strange

---

### Post by Chilli Burger on 2007-01-04
I upgraded my pc to  AMD 3200+ 64 bit and have been trying out various 32 and 64 bit versions of Linux. One desirable function was to be able to use my Sagem modem, supplied by Tiscali U.K. Despite following instructions neither of the first 2 worked, so next on my list was Kubuntu. This seemed no better until I discovered your Howto.

There were, however, one or two discrepancies and also a suggestion.

First the suggestion. The commands to use are well laid out, and being lazy I use cut and paste wherever possible. Unfortunately any command including 'uname -r' needs to be edited. If the execution apostrophe was used i.e. `uname -r` this would remove that necessity. As I said, i am lazy.

The first problem was that following the commands to install ueagle-atm-1.3.tar.gz there was no directory '/lib/modules/'uname -r'/extras/'. There was however one ending in extra. I presume that this was a typo? The required files were in the 'extra' directory.

As I got further on (I think it was the 'sudo modprobe ueagle-atm' ) up came with a file not found error. On looking at '/lib/modules/'uname -r'/kernel/drivers/usb/atm/' there was no ueagle-atm.ko or usbatm.ko file. Once these were copied from the 'extra' file the error went away.

From then on everything went swimmingly, and I was soon connected to Tiscali. When I had finished it appeared that there were updates available, So I started them off, saw it would be a lengthy job and went off to get my dinner. On my return all was finished so the pc was shut down and I went off to sit watching tv with my wife (who commented that my grumpiness had gone).

Next morning I booted the pc.](*,)  There is a problem with Kubuntu, my disks and grub when a new kernel is installed. Corrected that and, rather as expected, the Sagem was sulking. So out came the instructions (always keep a local copy) which were quite simple and duly followed. Sagem modem continued to sulk. It turned out that once again the files made up in the 'extra' directory needed also to be in the '/lib/modules/'uname -r'/kernel/drivers/usb/atm/' directory. This time they were soft linked into it in the hope that if the kernel is updated again that bit won't need doing.

Sorry if this sounds a bit negative, compared with the problems I had everywhere else it was a breeze. Remind me to tell you about the Suse 64 bit instructions that finished up with most of the kernel files removed o that i had to re-install to get it back working (still with no Sagem)....

---

### Post by CaptainHowdy on 2007-01-27
Hello people!

I have Kubuntu 6.06 with kernel 2.5.15-27-686 (as far as i remember) and 
i followed all the steps but i get the messages below:

when i do after the installation:
cat /var/log/messages

Jan 27 11:31:35 Kaldera pppd[6527]: Plugin pppoatm.so loaded.
Jan 27 11:31:35 Kaldera pppd[6528]: pppd 2.4.4b1 started by root, uid 0
Jan 27 11:31:35 Kaldera pppd[6528]: Exit.

and:

dmesg | grep eagle

[17179940.572000] [ueagle-atm] driver ueagle-gna 1.3 loaded
[17179940.572000] usbcore: registered new driver ueagle-atm


Any ideas?

---

### Post by gh0st-01 on 2007-02-04
I have a similar problem. First of all the led doesn't flash when i'm giving **modprobe**  and the modem isn't working.

The command** sudo dmesg|grep ueagle ** returns

[B][17179881.956000] [ueagle-atm] driver ueagle-gna 1.3 loaded
[17179881.956000] usbcore: registered new driver ueagle-atm[/B]

not **modem operational** and **firmware version** as you say.

Look also these commands :
[B]
$ sudo lsmod | grep eagle
ueagle_atm             31276  0 
usbatm                 21504  1 ueagle_atm
usbcore               134912  5 ueagle_atm,usbatm,ehci_hcd,uhci_hcd[/B]

[B]$ sudo plog
Feb  4 12:36:15 acer-laptop pppd[5114]: Plugin pppoatm.so loaded.
Feb  4 12:36:15 acer-laptop pppd[5116]: pppd 2.4.4 started by ubuser, uid 1000
Feb  4 12:36:15 acer-laptop pppd[5116]: connect(8.35): No such device
Feb  4 12:36:15 acer-laptop pppd[5116]: Exit.[/B]

Any idea ?

---

### Post by o_neos on 2007-03-09
After searching a lot in the Web, I guess that the usb adsl modem Sagem Fast 800 E4 is not supported yet.

Therefore if you type the following commands and you get:

dmesg | grep ueagle

[17222367.036000]: [ueagle-atm] driver ueagle-gna 1.3 loaded
[17222367.036000]: usbcore: registered new driver ueagle-atm

plog

Feb 25 19:30:16 user-desktop pppd[4703]: Plugin pppoatm. so loaded
Feb 25 19:30:16 user-desktop pppd[4705]: pppd 2.4.4 by user,uid 1000
Feb 25 19:30:16 user-desktop pppd[4705]: connect (8.35): No such device
Feb 25 19:30:16 user-desktop pppd[4705]: Exit

Check the following link

[http://forum.eagle-usb.org/viewforum.php?f=11](http://forum.eagle-usb.org/viewforum.php?f=11)

and participate in the development of the new ueagle driver.
:KS

---

### Post by aces21 on 2007-03-13
**UPDATE**

It appears that ueagle-atm is now in the Ubuntu kernel, so you don't have to compile it yourself. Unfortunately so is the old eagle-usb module and the two conflict. However, you can stop eagle-usb from ever loading again by blacklisting it. Just add eagle-usb to the file "/etc/modprobe.d/blacklist":

```
sudo gedit /etc/modprobe.d/blacklist
```

and add the line:

```
blacklist eagle-usb
```


And voila, no more eagle-usb getting in the way.

If you're setting up your modem from scratch, just follow the rest of the instructions in my first post from the line "Now you need to install the modem firmware." onwards.

If you've just upgraded your kernel, then you don't need to do anything, which is nice.

I'll add this to the main post shortly.

Happy internetting.

---

### Post by o_neos on 2007-03-14
check the following links:

[http://eagleedgy.site.voila.fr/index.html](http://eagleedgy.site.voila.fr/index.html)
[http://cathubuntu.free.fr/index.html](http://cathubuntu.free.fr/index.html)

although they are in french you can find the drivers you need in order to make your sagem usb modem working [even E4 & kernel 2.6.17-10-generic], I did it...

you can reach their posts at:

[http://forum.ubuntu-fr.org/viewtopic.php?id=82353&p=1](http://forum.ubuntu-fr.org/viewtopic.php?id=82353&p=1)

;)

---

### Post by ElemonGW on 2007-04-17
Hello! Well, unfortunately, I am also a user of this modem so I also have problems.  I followed this guide but I am still not able to connect to the Internet. Here are the problems/odd things that i get during the installation of my modem, using of course this guide. I hope that somebody can help me. Anyway let's start. Everything was going right until the step that I should type

[PHP]$ dmesg|grep ueagle[/PHP]
when it didn't give me
[PHP]usb 1-2: [ueagle-atm] modem operational
usb 1-2: [ueagle-atm] ATU-R firmware version : 43e2ead7[/PHP]

but

[PHP][17179587.284000] [ueagle-atm] driver ueagle 1.3 loaded
[17179587.284000] usbcore:registered new driver ueagle-atm
[17180275.516000] usb 1-2: [ueagle-atm] ADSL device founded vid (0X1110) pid (0X9032): Eagle III
[17180275.776000] usb 1-2: [ueagle-atm] loading firmware ueagle-atm/eagle III.fw[/PHP]

The next odd thing happened when I should type

[PHP]$ sudo gedit /etc/ppp/chap-secrets
[/PHP]
This file didn't contain
[PHP]
"myusername"  "*"  "mypassword"  "*"[/PHP]

but

[PHP]#Secrets for authentication using CHAP
#client               server secret               IP addresses


[/PHP]

The next odd was at this step

[PHP]ifconfig[/PHP]

that it didn't' give me anything like that

[PHP]ppp0 Link encap:Point-to-Point Protocol
inet addr:83.30.157.107 P-t-P:213.25.2.202 Mask:255.255.255.255
UP POINTOPOINT RUNNING NOARP MULTICAST MTU:1500 Metric:1
RX packets:2019 errors:0 dropped:0 overruns:0 frame:0
TX packets:2025 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:3
RX bytes:724078 (707.1 KiB) TX bytes:184065 (179.7 KiB)[/PHP]

but

[PHP]lo:                 Link encap:Local Loopback
    inet addr:127.0.0.1 Mask: 255.0.0.0
    inet6 addr:      ::1/128   Scope: Host
    UP LOOPBACK RUNNING MTU: 16436 Metric: 1
    RX packets: 530 errors: 0   dropped: 0   overruns:0  frame:0
    TX packets: 530 errors: 0   dropped: 0    overruns:0  carrier:0
    collisions: 0 txqueuuelen: 0
    RX bytes: 39140 (38.2KiB)  TX bytes: 39140 (38.1 KiB)[/PHP]

The problem here is the fact that the ip adress that it gave me was 127.0.0.1 , which means that i am not connected whith the internet. Finally when i typed plog it didn't gave me anything like that

[PHP]hostname pppd[5179]: Connect: ppp0 <--> 8.35
hostname pppd[5179]: CHAP authentication succeeded
hostname pppd[5179]: CHAP authentication succeeded
hostname pppd[5179]: Cannot determine ethernet address for proxy ARP
hostname pppd[5179]: local IP address 83.30.157.107
hostname pppd[5179]: remote IP address 212.74.111.187
hostname pppd[5179]: primary DNS address 80.225.252.58
hostname pppd[5179]: secondary DNS address 80.225.252.50[/PHP]

but

[PHP]Apr 8 15:56:13 elemon-desktop pppd [12679]: Plugin pppoatm.so loaded
Apr 8 15:56:13 elemon-desktop pppd [12601]: pppd 2.4.4 started by elemon, uid 10
00
Apr 8 15:56:13 elemon-desktop pppd [12679]: connect(8.35): No such device
Apr 8 15:56:13 elemon-desktop pppd [12679]: Exit[/PHP]

I hope that somebody can help me.
PS: I have to say the truth: I didn't read the whole thread because i was bored :) . However from what i read i get confused from the answers. So, if this was answered before you have my apologies.

---

### Post by ElemonGW on 2007-04-17
Oh, and forgot to mention that I used version 6.10 of ubuntu.

---

### Post by ElemonGW on 2007-04-20
C'me on guys. Anybody?!?!?!?! PLZ!!!!!

---

### Post by SledgeHammer_999 on 2007-04-21
@ElemonGW please follow this [wiki](https://help.ubuntu.com/community/UsbAdslModem/ueagle-atm). It is based on this thread but it is updated and clean. (for feisty you don't need to do step 4)

---

### Post by YamiTenshi on 2007-04-30
I followed the guide (except for setting up the connection, my ISP uses PPPoE)
Everything seems to work fine, except I still have no internet connection.

I read something about chap-secrets having to be identical to pap-secrets. Do they really have to be identical (except for the comments, of course)? 'Cause pap-secrets contains a lot of text and chap-secrets contains two lines of comment which don't help me at all... Or the other way around, I don't remember.

If that's not the problem, can anybody help me set up the connection?

---

### Post by xlq on 2007-05-16
When I plug the modem in, it seems to get stuck on synchronisation.

Here are the relevant parts of my dmesg:

```

[ 8473.249601] usb 2-2: new full speed USB device using ohci_hcd and address 20
[ 8473.344370] usb 2-2: configuration #1 chosen from 1 choice
[ 8473.371307] usb 2-2: [ueagle-atm] ADSL device founded vid (0X1110) pid (0X9021) : Eagle II pots
[ 8473.450338] usb 2-2: reset full speed USB device using ohci_hcd and address 20
[ 8473.575479] usb 2-2: [ueagle-atm] using iso mode
[ 8473.575590] usb 2-2: [ueagle-atm] (re)booting started
[ 8474.470861] usb 2-2: [ueagle-atm] ATU-R firmware version : 44e2ea17
[ 8474.501320] usb 2-2: [ueagle-atm] Modem started, waiting synchronization

```

At this point, the 'ADSL' LED on the modem is not lit.

Help!

---

### Post by ElemonGW on 2007-07-01
Well, even if late, it is better late than never :) . So, I would like to thanks you, SledgeHammer_999. By following the guide you gave me and another one I managed to make it work.
PS: I was so late because I didn't have enough time to install ubuntu ( because I have uninstalled them). So I tried it the previous week and yeah it worked :) .

---

### Post by Grizli on 2008-05-27
I have Sagem Fast 800/840 A4 and he works on Ubuntu 8.04 with UbuDSL (You can find here [http://www.ubudsl.com/](http://www.ubudsl.com/) )without any problem and it is very easy to install. (exp. ONLY after FIRST restart I had to unpluged modem becouse Ubuntu 8.04 did not wonth to boot. After that issue I did not have any other problem.)Sorry for my bad English.:lolflag:

---

