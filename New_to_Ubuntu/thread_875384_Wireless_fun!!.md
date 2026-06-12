---
title: "Wireless fun!!"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by djzalzer on 2008-07-30
I hate to ask so many questions in quick succession, but after my install is working properly I promise I'll help others. ^_^

ANYWAY  I installed a WG111v3 wireless adapter on linux using ndiswrapper.  Everything seemed to work fine, and it can sense when the device is plugged in or not, but other than that offers no functionality...  I can't access my network, in other words.

So I went to the network management thing to check all the right boxes, fill in ip addresses, etc.  But there was only wired connection, and some sort of modem one-on-one type of thing.  No wireless option. :[

Any advice?

---

### Post by phidia on 2008-07-30
In a terminal enter these commands: > iwconfig&> lshw -C network You can search and/or post the output of those.

---

### Post by djzalzer on 2008-07-30
Outputs:



iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.


lshw -C network 

It tells me to be a "power user" (I lost the !@#$ copy-paste of it, I'll have to go back and get it, but I have to leave in 5 minutes)

when I run it as root, however, it returns nothing. :[

Thanks for your help.

---

### Post by phidia on 2008-07-30
bash-the terminal always gives that line about being root but outputs the info anyway. 

Is "WG111v3 wireless adapter" a usb or pcmcia device? Whatever it is it doesn't seem to be configured. If it was "iwconfig" would have shown us a wlan0 device.

---

### Post by djzalzer on 2008-07-30
It's a wireless usb dongle.  And it shows up in the 'wirerless device manager' fine...

---

### Post by phidia on 2008-07-31
That might be but this: > iwconfig

lo no wireless extensions.

eth0 no wireless extensions.

is telling us it's not enabled/configured. There is a HOWTO on that device [here]("http://ubuntuforums.org/showthread.php?t=802122&highlight=WG111v3").

---

### Post by djzalzer on 2008-07-31
That's the guide that I followed...

But ndiswrapper didn't sppear to install any .sys or .cat files.  Are these necessary?  If so, where would I put them?

---

### Post by AKsuited09 on 2008-07-31
have a very similar problem. totally noob. where do i find the "terminal"?

---

### Post by halitech on 2008-07-31
> **djzalzer said:**
> That's the guide that I followed...

But ndiswrapper didn't sppear to install any .sys or .cat files.  Are these necessary?  If so, where would I put them?

very needed and you would have to either download them from the manufactorer or provide them from your driver disk.

> **AKsuited09 said:**
> have a very similar problem. totally noob. where do i find the "terminal"?

Applications - Accesories - Terminal

---

### Post by ChocolateChip_Wookie on 2008-07-31
The terminal can be found under either of the following :

type : Alt+F2 (to get the run box)
type : 'terminal' and click the program

Or, hit the Applications (or Go button in Mint)
Find accessories, find 'Terminal'

Alternatively, <right> click one of the panel bars
Click Add to Panel
Click Applications Launcher (Copy a launcher from the applications menu)
Click Forward/Next
Expand Accessories
Find Terminal
Click OK/Add

---

### Post by djzalzer on 2008-07-31
Hi,

I have those files.  When I installed the drivers with the ndiswrapper, it didn't ask for a location of these files; I assumed they were unneeded.  But they're still on my hard disk.  Is there a certain directory that I need to place these in?

If not, what do I do with them?

Thanks.

---

### Post by bobnutfield on 2008-07-31
When you installed the .inf file for ndiswrapper, the .sys file should have been in the same directory as the .inf file.  Ndiswrapper does not ask for it, but it uses that file when it installs the .inf file.  Try to remove the driver:

> sudo ndiswrapper -r <nameOfDriver>

Then do:

> sudo ndiswrapper -l

To make sure there is no driver loaded.

Then reinstall the driver.  Make sure both the .inf file and the .sys file is in the same directory you are in.  It's best and easiest to do this from your home directory

> sudo ndiswrapper -i <nameOfDriver>

Then, of course, as you probably already know,
do

> ndiswrapper -l

again, and you should see driver installed, device present

The make sure the usb address is associated:

> sudo ndiswrapper -ma

Then,

> sudo modprobe ndiswrapper

The lights on you USB dongle should now be blinking and you should be able to set up your networking information with iwconfig.

---

### Post by djzalzer on 2008-07-31
Hi,

I did your instructions (thanks) and it all went fine until

root@isaac-desktop:/home/isaac# ndiswrapper -ma
module configuration information is stored in /etc/modprobe.d/ndiswrapper

this was the contents of said file:
alias usb:v0846p4260d*dc*dsc*dp*ic*isc*ip* ndiswrapper

then, when I did this:

root@isaac-desktop:/home/isaac# modprobe ndiswrapper
FATAL: Module ndiswrapper not found.

I know the dongle works because i'm using it to send this message on windows.

---

### Post by bobnutfield on 2008-07-31
> root@isaac-desktop:/home/isaac# ndiswrapper -ma
module configuration information is stored in /etc/modprobe.d/ndiswrapper

This is the normal output.  It is OK

Try again with:

> sudo modprobe ndiswrapper

---

### Post by djzalzer on 2008-07-31
Uh, the exact same thing happened.

Like, 4 times.

---

### Post by bobnutfield on 2008-07-31
OK, I find that odd because the module clearly exists.  Try:

> depmod -a

Then run modprobe ndiswrapper again.

---

### Post by phidia on 2008-07-31
> **djzalzer said:**
> Uh, the exact same thing happened.

Like, 4 times.

You mean you get this > 
root@isaac-desktop:/home/isaac# modprobe ndiswrapper
FATAL: Module ndiswrapper not found.

??

ndiswrapper is not installed correctly

I can't remember now but I think you installed from tar.gz 
Something did not go right and/or you got error messages  that you were not aware of. 

I think you need to start at the beginning and try and install ndiswrapper making sure that the install completes successfully.

****Added: OR the path for your root account doesn't contain the directory where ndiswrapper is installed did you install ndiswrapper in a different directory or something??

---

### Post by bobnutfield on 2008-07-31
Thank you, phidia.  I missied that, I had assumed he had installed via Synaptic

---

### Post by phidia on 2008-07-31
> **bobnutfield said:**
> Thank you, phidia.  I missied that, I had assumed he had installed via Synaptic

Thanks for the thanks but I'm confused on this one-obviously he should not be getting the no module found message. 

I'm thinking since it appears a root account has been enabled (maybe that's not significant though?) but anyway the path may not be correct if ndiswrapper got installed to a non-standard directory?

djzalzer, if you type (in terminal) > whereis ndiswrapper what is the output?

---

### Post by djzalzer on 2008-07-31
This very well could be the problem; I'm completely oblivious to how to work the terminal.  It's just been copy-paste so far.

I'll edit this posts with the info; I need to switch back to ubuntu.

Geez, its already seeming better than winxp..

EDIT: here's whereis ndiswrapper
ndiswrapper: /usr/sbin/ndiswrapper /etc/ndiswrapper /usr/share/man/man8/ndiswrapper.8.gz
do I do cd /usr/sbin/ndiswrapper or something?

ALSO: I didn't install via Synaptic, but through the default package installer through which I've installed everything else... I had a short amount of time where I could have a cabled hookup.

Again, thanks for all your help guys. I'll figure a way to give you guys a good turn... somehow.

---

### Post by bobnutfield on 2008-07-31
If installed correctly, nediswrapper should be in /usr/sbin, with the config files in /etc/ndiswrapper.  If that is the case, being root I don't believe would matter.  More than likely it is a corrupt or incomplete install.  However, this is confusing since apparently ndiswrapper installed his drivers.

---

### Post by djzalzer on 2008-07-31
Should I attempt an uninstall/reinstall?

---

### Post by phidia on 2008-07-31
> **djzalzer said:**
> Should I attempt an uninstall/reinstall?

I presume by "the default package manager" you meant apt-get?
It can't hurt to try a uninstall and reinstall-hopefully you will be able to load the driver and use the network.

---

### Post by djzalzer on 2008-07-31
You know, sometimes I hate myself.

A good reason that it doesn't work just may be that I was using drivers for a wg311v3 card, not a wg111v3.

ARGH

Well, let's see if it works with the right drivers, eh? :]

---

### Post by djzalzer on 2008-07-31
By 'default' I mean the one where you go Applications > Add/Remove...

So I reinstalled, and got new drivers, and it still doesn't work... it still balks at modprobe.

I'm getting sick of this.  Should I reformat and reinstall Ubuntu? (Although I doubt that would help, the disk has no errors and this is a fresh install besides Envy and a few applications...)

Oops, sorry about the double post.... :[

---

### Post by phidia on 2008-07-31
Stick with it djzalzer you can get it working.

What happened with > A good reason that it doesn't work just may be that I was using drivers for a wg311v3 card, not a wg111v3.?

Did you unload the incorrect driver "sudo ndiswrapper -r (drivername)
And load the correct one?

Added: What version are you using and is it 32 bit or 64?

---

### Post by liquidfunk on 2008-07-31
I have that exact card!!! 

This is what I did,

Make yourself a folder in your Home directory.

Call it WG111v3 or something. 

Extract this and copy and paste them into that folder

[http://www.avengergear.com/upload/WG111v3.tar.bz2](http://www.avengergear.com/upload/WG111v3.tar.bz2) 

If you haven't already got the GUI NDISwrapper, where you can just click on Windows Wireless Drivers, get it. Its called ndisgtk I think from Synaptic.

 Else, open up Windows Wireless Drivers from System - Administration, press install, locate the .inf driver from the folder you made. 

 Reboot.

 Bob is your offical uncle!

---

### Post by djzalzer on 2008-07-31
Thanks for your replies, guys.  I think I'm onto something.

I uninstalled all drivers and reinstalled what I thought were new ones.  Still didn't work.

Using 32-bit.  

LiquidFunk,
That's what I did at first, but it didn't work.  This is why we're doing all this backwards crap ^_^

Okay, so I'm going to try installing this with a fresh new install of everything, and I promise not to make any mistakes!  

I'll edit this post with my Terminal postings!

Thanks, guys!

EDIT:

When I try to install the driver via the terminal, this happens:

root@isaac-desktop:/home/isaac# ndiswrapper -i WG111
installing wg111 ...
couldn't get manufacturer section - installation may be incomplete

What's this mean?!

---

### Post by djzalzer on 2008-08-01
I hope this is a 'respectable' period to bump, so bump... and I'm still stumped, btw.

I figured out what the problem is, sorta.  Ndiswrapper is simply not installing the drivers.  The area in /etc/ndiswrapper/wg111 (wg111 being the name of the installed driver) there is simply nothing. So I uninstalled the non-graphical version and installed the graphical version via the ubuntu DVD. I tried again, against all hope.

I'm using 8.04 Hardy Heron, and an AMD CPU... are these things that effect wireless?  Everyone else with this card seems to install it with relative ease, and I'm trying to narrow down the variables to why I'm not even able to make the wireless option appear in the Network menu...

---

### Post by unutbu on 2008-08-01
Open a terminal. Type:

```
cd path/to/WG111   
ls -l
```

You should see something like 

```

  -rwxr--r-- 1 man man  12705 2007-05-10 22:22 WG111v3.inf
  -rwxr--r-- 1 man man  13312 2007-10-24 06:22 WG111v3.PNF
  -rwxr--r-- 1 man man 236334 2007-05-15 07:19 wg111v3.sys
```

If you don't see these files, you are in the wrong directory.

Now type:
```

sudo ndiswrapper -i WG111v3.inf
```

Now check that the driver has been installed:
```

ndiswrapper -l
``` You should see something like
```
WG111: driver installed
        device (....:....) present
```
If it doesn't work, please copy and paste the terminal output (and your commands) into your next post.

---

### Post by djzalzer on 2008-08-01
Hi, Unutbu.

Everything went exactly as planned; as I suspected, it never was the installation that was the problem.

The problem is:  How to I configure wireless networks and make the drivers do their job?

No matter how many times I install it, the problem doesn't go away: The thing's LED never turns on, I never get the option to configure a wireless network in my network admin panel.  When I click on Edit Wireless Networks (right click on the network icon in the system tray) nothing shows up.

I checked the /etc/ndiswrapper/wg111/ folder.  There were drivers inside of it.  The installation has gone by fine.

But how do I get the stupid thing to work from here?

---

### Post by unutbu on 2008-08-01
Type

```
lsmod | grep ndiswrapper
```

You should see something like

```
ndiswrapper           185240  0 
```

If you aren't seeing this, then it means that the ndiswrapper module has not been loaded into your kernel. If that's the case,

```
gksu gedit /etc/modules
```

Add a line at the bottom which says:
```

ndiswrapper
```

Save and quit gedit.

Now power down / power up the machine. I'm a bit superstitious about this -- for some people doing a soft reboot works, but on my machine, I must do a hard power down / power up to reset my wireless adapter. For the time being, please humor me in my superstition and do hard power down / power ups. Once we get things running, you can experiment with cutting out the superstition.

When you reboot look for blinking lights on your wireless adapter.
If you don't see them, go to a terminal and type
```

lsmod | grep ndiswrapper
ifconfig
```

and post the output here.

---

### Post by djzalzer on 2008-08-02
Thanks for all your help, unutbu.  I really appreciate it.

Sadly, I don't think we're any closer to solving this problem-whenever I type in lsmod | grep ndiswrapper, it simply returns... nothing.  It just goes down to the next line.

The output from ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:1b:b9:cf:3f:4d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1210 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1210 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:60500 (59.0 KB)  TX bytes:60500 (59.0 KB)

---

### Post by unutbu on 2008-08-02
I'm wondering if we're missing something basic. Please run the following commands
```
dmesg | bzip2 -c > dmesg.out.bz2
lspci -nn > lspci.out
lsusb > lsusb.out
sudo lshw > lshw.out
```
and post dmesg.out.bz2, lspci.out, lsusb.out, lshw.out as attachments.

---

### Post by djzalzer on 2008-08-02
OK, here they are...

OK, only the .bz2 worked... so I uploaded the others to a more private server.

Feel free to virus scan, they don't have anything.

[http://www.cereus-games.com/phpBB2/uploads/lshw.out](http://www.cereus-games.com/phpBB2/uploads/lshw.out)
[http://www.cereus-games.com/phpBB2/uploads/lspci.out](http://www.cereus-games.com/phpBB2/uploads/lspci.out)
[http://www.cereus-games.com/phpBB2/uploads/lsusb.out](http://www.cereus-games.com/phpBB2/uploads/lsusb.out)

Thanks!

EDIT: 0846:4260 NetGear, Inc. on lsusb.out is the wireless controller!

---

### Post by unutbu on 2008-08-02
Hm. Nothing in the output is jumping out at me as the problem. Would you please post one more thing?

```
grep -i ndis /var/log/messages
```

---

### Post by Garyhans on 2008-08-02
Hi. I've never tried this nor sure if it will work. Worth a read for Wireless.

[https://launchpad.net/auto-ndiswrapper](https://launchpad.net/auto-ndiswrapper)

---

### Post by unutbu on 2008-08-02
djzalzer, are you running 64-bit Ubuntu, or 32-bit Ubuntu?
Please post 
```

uname -m
```
Oh, what the heck. Please post
```
uname -a
```

---

### Post by Diggs808 on 2008-08-03
Okay...I have one idea....

Right click on the wireless manager in the tool bar.  It should look like a couple of little computer monitors sitting close to one another.  Do you see where it says wireless enabled?

One of the problems I have run into with the wireless network manager in Gnome is that it doesnt pick up on new wireless networks at times.  What I do is simple.  

1. Open system monitor (System>administration>system monitor)
2. go to the second tab that says Processes
3. scroll down until you see nm-applet
4. Right click on the word nm-applet and choose "end Process"
5. if it pops up a warning go ahead and click on ok.
6. open a terminal and type in nm-applet

that restarts the Gnome network manager

I know that I have never had much luck getting the gnome network manager to work with Ndiswrapper.  You might try to install Wicd.  go to this link [here]("http://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460&release_id=617339") and download the .deb file.  Double click the file (wherever you downloaded it to) and it should take care of all the dependencies.  Just a bit of warning...It will have you uninstall the default gnome network manager.  It prompted me to do that the last time i tried it.

---

### Post by djzalzer on 2008-08-03
That didn't help.

:[

Thanks for your reply, though.

---

### Post by djzalzer on 2008-08-04
Bump?

---

### Post by unutbu on 2008-08-04
djzalzer, I'm not positive I'll figure out how to solve this problem. As I see it, the problem is that ndiswrapper is not getting loaded by the kernel. 

I'm hoping that there might be an error message in your /var/log/messages that will shed light on the problem. To that end, please try

[http://ubuntuforums.org/showpost.php?p=5511167&postcount=36](http://ubuntuforums.org/showpost.php?p=5511167&postcount=36)

Also, I see in a previous post you mentioned you are using 32-bit drivers.
So I wonder if you are using the 64-bit version of Ubuntu. I don't know much about 64-bit stuff, but it seems ([http://www.linuxquestions.org/questions/linux-wireless-networking-41/has-anyone-ever-had-ndiswrapper-work-in-a-64-bit-environment-384970/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/has-anyone-ever-had-ndiswrapper-work-in-a-64-bit-environment-384970/)) there are some issues involved in getting ndiswrapper to work with 64-bit. Maybe some other forum reader can clarify. 

Anyway, to check if you are running 64-bit, please try

[http://ubuntuforums.org/showpost.php?p=5511337&postcount=38](http://ubuntuforums.org/showpost.php?p=5511337&postcount=38)

If you see
i686 it means you are running 32-bit
x86_64 means you are running 64-bit

---

### Post by djzalzer on 2008-08-04
isaac@isaac-desktop:~$ uname -m
i686
isaac@isaac-desktop:~$ uname -a
Linux isaac-desktop 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux
isaac@isaac-desktop:~$ 

There you go.  Looks 32-bit to me

---

### Post by phidia on 2008-08-04
Wow, I think everyone deserves some praise, including djzalzer, for working so hard on this.
I re-read most of the thread and I never saw if ndiswrapper actually loaded-I could have missed that (this is 5 pages now) 
What does > sudo modprobe ndiswrapper output? 

Btw I can try this a little while tonight everyone get a snack and come back-this is a mystery we can solve! :) (I'm being sincere)

---

### Post by unutbu on 2008-08-04
djzalzer, I posted the first link wrong, would you please post the output to 

```
grep -i ndis /var/log/messages
```

([http://ubuntuforums.org/showpost.php?p=5511167&postcount=36](http://ubuntuforums.org/showpost.php?p=5511167&postcount=36))

---

### Post by djzalzer on 2008-08-04
phidia, it outputs saying that the module is not installed.

Are we getting warm? ;]

I'll post that unutbu, and thanks for your fantastic help!

---

### Post by phidia on 2008-08-04
> **djzalzer said:**
> phidia, it outputs saying that the module is not installed.

Are we getting warm? ;]

I'll post that unutbu, and thanks for your fantastic help!

I'd say "hot" the ndiswrapper module should be loaded. _Why_ it's not loading is _the_ question???

Added: There is a guide [here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") that Ubuntu wiki on ndiswrapper could be helpful. 

Feel free to bring up anything that comes to you or you notice though.

---

### Post by djzalzer on 2008-08-04
So grep -i ndis /var/log/messages didn't return anything in the terminal.  Here are the contents of the file:

[http://www.cereus-games.com/phpBB2/uploads/messages](http://www.cereus-games.com/phpBB2/uploads/messages)

I hope this isn't too big a post.  If so, I will upload the file...

---

### Post by unutbu on 2008-08-04
No problem. Got it. You might want to edit the post and put code wrappers around the output however:

[http://ubuntuforums.org/showpost.php?p=5490091&postcount=43](http://ubuntuforums.org/showpost.php?p=5490091&postcount=43)

---

### Post by phidia on 2008-08-04
Shouldn't we or djzazer be concerned/focused on this?
> it outputs saying that the module is not installed.

---

### Post by unutbu on 2008-08-04
phidia, I agree -- the ndiswrapper module not getting installed is the problem.
I am surprised there are no error messages about ndiswrapper in /var/log/messages.

However, if djzalzer runs
```

grep -i dis /var/log/messages
```

he'll see:
```

Aug  4 12:19:40 isaac-desktop kernel: [   16.484987] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug  4 12:19:40 isaac-desktop kernel: [   16.485328] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug  4 12:19:40 isaac-desktop kernel: [   16.485496] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug  4 12:19:40 isaac-desktop kernel: [   16.485663] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug  4 12:19:40 isaac-desktop kernel: [   16.485831] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug  4 12:19:40 isaac-desktop kernel: [   16.485999] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug  4 12:19:40 isaac-desktop kernel: [   16.486169] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug  4 12:19:40 isaac-desktop kernel: [   16.486504] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug  4 12:19:40 isaac-desktop kernel: [   16.487007] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug  4 12:19:40 isaac-desktop kernel: [   16.487677] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug  4 12:19:40 isaac-desktop kernel: [   16.488018] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Aug  4 12:19:40 isaac-desktop kernel: [   16.488219] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
Aug  4 12:19:40 isaac-desktop kernel: [   16.488603] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
Aug  4 12:19:40 isaac-desktop kernel: [   16.488796] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
Aug  4 12:19:40 isaac-desktop kernel: [   16.488988] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
Aug  4 12:19:40 isaac-desktop kernel: [   16.489180] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
Aug  4 12:19:40 isaac-desktop kernel: [   16.489371] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
Aug  4 12:19:40 isaac-desktop kernel: [   16.489563] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
Aug  4 12:19:40 isaac-desktop kernel: [   16.490527] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0, disabled.
Aug  4 12:19:40 isaac-desktop kernel: [   16.491106] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
Aug  4 12:19:40 isaac-desktop kernel: [   16.491299] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
Aug  4 12:19:40 isaac-desktop kernel: [   16.491685] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
```

ACPI is involved in hardware detection. I don't really understand what these messages mean, but it looks like something is getting disabled, and so I wonder if this might somehow be related. (Could this be related to the fact that your network adapter does not show up in the lshw output? But then why does "0846:4260 NetGear, Inc." it show up in the lsusb output?)

Well, I'm groping here, but would you (djzalzer) please show us the output of 

```
cat /proc/interrupts 
```

This will show what IRQs have been assigned  to various pieces of hardware. I don't know what I'm looking for, but it may be interesting or useful.

Also, please post

```
find /etc/modprobe.d -print0 | xargs -0 grep -Hi ndis 

```
This is just to check that ndiswrapper is not getting blacklisted.

---

### Post by Diggs808 on 2008-08-05
Just throwing out a theory here (I am not the most technical user so I usually throw out ideas better than solutions..).  In my Bios there is an option to turn off USB/PC Cards/external stuff...could that be disabled in his bios?  Or conversely, could there be some quirk in his system that is not activating USB ports??

---

### Post by phidia on 2008-08-05
> Everything seemed to work fine, and it can sense when the device is plugged in or not, but other than that offers no functionality... I can't access my network, in other words.

I don't think that would be happening if usb was disabled.

---

### Post by djzalzer on 2008-08-06
I'm using this device to post this message on the same PC, different hard disk.  That's not the issue here.

Sorry I didn't catch up yesterday, I was too busy.

I'll edit this post with the output, unutbu.

---

### Post by djzalzer on 2008-08-16
Sorry I haven't posted for awhile, guys; school started last week and I've had a rather demanding work schedule.

Here's the outputs. *I hope you guys haven't forgotten about this! :\*
isaac@isaac-desktop:~$ sudo ndiswrapper -mi
sudo: unable to resolve host isaac-desktop
[sudo] password for isaac: 
module configuration information is stored in /etc/modprobe.d/ndiswrapper
isaac@isaac-desktop:~$ cat /proc/interrupts
           CPU0       CPU1       
  0:        166          1   IO-APIC-edge      timer
  1:          0          2   IO-APIC-edge      i8042
  4:          0          1   IO-APIC-edge    
  6:          0          5   IO-APIC-edge      floppy
  7:          1          0   IO-APIC-edge      parport0
  8:          0          3   IO-APIC-edge      rtc
  9:          0          0   IO-APIC-fasteoi   acpi
 12:          0          4   IO-APIC-edge      i8042
 14:         61      24594   IO-APIC-edge      libata
 15:          0          0   IO-APIC-edge      libata
 16:         24      37744   IO-APIC-fasteoi   ohci_hcd:usb1, nvidia
 17:          6       2609   IO-APIC-fasteoi   ehci_hcd:usb2
 19:          0          0   IO-APIC-fasteoi   sata_nv
 20:          1        454   IO-APIC-fasteoi   CMI8738-MC8
220:        122      49076   PCI-MSI-edge      eth0
NMI:          0          0   Non-maskable interrupts
LOC:      39843      40594   Local timer interrupts
RES:      16152       8985   Rescheduling interrupts
CAL:        258        140   function call interrupts
TLB:        681        578   TLB shootdowns
TRM:          0          0   Thermal event interrupts
SPU:          0          0   Spurious interrupts
ERR:          1
MIS:          0
isaac@isaac-desktop:~$ find /etc/modprobe.d -print0 | xargs -0 grep -Hi ndis
/etc/modprobe.d/ndiswrapper:install usb:v0846p4260d*dc*dsc*dp*ic*isc*ip* /sbin/modprobe ndiswrapper
i

---

### Post by GrandpaLeaman on 2008-08-16
> **djzalzer said:**
> sudo: unable to resolve host isaac-desktop

This may be a long shot, but I notice you get an error when using sudo. This may not be your problem, but there is a solution to this particular error. This has also caused problems with wireless access. It is an easy fix, so couldn't hurt. See this thread for the fix:

[http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361)

Hope this helps!

---

### Post by djzalzer on 2008-10-07
Sorry for the belatedness of this reply (several months!).

I been busy; that's my only excuse.  I'm still working on it.

So i checked out my wicd settings... here they are.

[IMG]http://i406.photobucket.com/albums/pp143/gyrocopter/Screenshot-Preferences.png[/IMG]

wireless interface: none looks kind of menacing

---

### Post by djzalzer on 2008-10-08
bump...

---

