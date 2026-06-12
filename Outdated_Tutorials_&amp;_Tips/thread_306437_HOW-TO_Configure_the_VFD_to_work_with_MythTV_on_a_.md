---
title: "HOW-TO Configure the VFD to work with MythTV on a Antec Fusion case"
date: 2006-11-25
forum: Outdated Tutorials &amp; Tips
---

### Post by piec2 on 2006-11-25
I have a Antec Fusion case and I have been working for a little while to get the VFD to work correctly without impacting the functionality of my remote.

If you have a Antec Fusion case, this one is for you!

First, let's start by saying that eventhough the VFD on the Fusion is the OEM version of the Soundgraph iMon, it does not have the infrared module. In fact, even the firmware on that VFD doesn't have the necessary code to read IR, which means there's no way to extend it to become a full iMon IR/VFD.

Eventhough Antec says on their web site that the case allows for a "space for a user-mounted IR Receiver", that's not true. There would have been enough space in the case, but the designer simply forgot about it.  Like several others, I dismantled the front bezel and VFD to figure that out.

Of course you will need a IR receiver to work with you Fusion case.  For me a Mircosoft MCE receiver does the job.

So here are the steps to get the VFD to work. I did this on MythTV 0.20 and Ubuntu Edgy.

Let's first thanks the appropriate people and sites from which this info was collated: Venky Raju ([http://venky.ws]("http://venky.ws")) and Garth Dahlstrom ([http://stacktrace.org/)](http://stacktrace.org/)).
These guys made it all possible !

**STEP 1: INSTALL LCDPROC**
Use Synaptics to get lcdproc (or from command line apt-get install lcdproc).  
Now if that install was doing everything right we could jump to the next step, but there's a few problems with it which we must fix manually.

Do the following:
```
sudo vi /etc/LCDd.conf
```

Search for the section [server] and comment out the Driver=CFontzPacket.
Uncomment the line Driver=imon

Search for DriverPath and change it to read 
```
DriverPath=/usr/lib/lcdproc/
```

Save the file.

Now edit the following file:
```
sudo vi /etc/init.d/LCDd
```

Change the line DAEMON_OPTS to read:
```
DAEMON_OPTS="-s true -f true -c /etc/LCDd.conf
```

Yes, eventhough the MAN pages for LCDd don't mention this, it really needs the "true" arguments.

**STEP 2: INSTALL IMON_VFD**
Now download the file from Venky for the standalone Imon VFD Driver:
[http://venky.ws/projects/imon/#standalone]("http://venky.ws/projects/imon/#standalone")

Untar it:
```
tar xvzf imon_vfd.tgz
cd imon
```

Donwload the following patch from Garth Dahlstrom's web site and put it in the imon directory:
[http://stacktrace.org/index_html/20060904-imon_vfd_standalone/imon-2.6.patch]("http://stacktrace.org/index_html/20060904-imon_vfd_standalone/imon-2.6.patch")

Then apply the patch and compile
```
cat imon-2.6.patch | patch
make -C /usr/src/linux SUBDIRS=$PWD modules
sudo make install
```

This will have created the /dev/lcd0 device that you need to talk to the LCD.

**STEP 3: LOAD EVERYTHING**
Now let's do the final steps: loading the drivers and testing if everything works.
```
modprobe imon_vfd
# Run /usr/sbin/LCDd manually to check all is good.
sudo /usr/sbin/LCDd
```

If it worked without error you should see something on your VFD. We can now kill LCDd:
```
sudo killall LCDd
```

And start it like it should be started, in the background:
```
sudo /etc/init.d/LCDd start
```

Now we need to make sure all this gets loaded properly when rebooting:
Edit /etc/modules and add the following line at the end:
```
imon_vfd
```

That's it!  All you have to do is reboot.

**STEP 4: ACTIVATE LCD IN MYTHTV**
Now start MythTV front-end and go to the Setup/Appearance section.

In there you will find the "Enable LCD device" option. By setting it ON, the mythlcdserver be started and it will communicate with LCDd and display info on the LCD during various MythTV operations.

Enjoy !

**Troubleshooting:**
If you cannot find the module LCDd when you do a "ps ax | grep LCDd" then you may have to:
```
sudo update-rc.d LCDd defaults
```

If you want to figure out what is happening, you will find the LCDd error messages in /var/log/syslog

---

### Post by K.Mandla on 2006-11-25
Nicely done. I'll move this into the Howto section, so it has a prominent place in history. ;)

---

### Post by vesok on 2006-12-02
Thanks for the HOWTO, works nicely. 2 minor notes:

> DAEMON_OPTS="-s true -f true -c /etc/LCDd.conf
missing closing quote, should be
DAEMON_OPTS="-s true -f true -c /etc/LCDd.conf"

I had to change the make command too:
> make -C /usr/src/linux SUBDIRS=$PWD modules

The command that worked for me was:

make -C /usr/src/linux-headers-2.6.17-10-generic/ SUBDIRS=$PWD modules

Any idea how to get the big volume knob working?

---

### Post by piec2 on 2006-12-04
Thanks for the notes vesok !

I still haven't figured out the volume knob. The solution probably lies around the use of LIRC imon module, however if we activate it we must be careful not to lose our standard USB IR receiver functionality.

I believe the LIRC iMon module was made to work with the standard iMon package which includes the VFD and the IR receiver all-in-one. With the Antec case since the IR Receiver is separate, we would need to somehow indicate to lirc_imon that we only want it to take control of the volume knob and leave alone the other IR functionality.

Maybe it would work if we setup the lirc_imon as a second IR module?  I haven't given this a try yet. If you do, let me know. If I get it working I'll post the how-to here.

Please note this How-To was also copied to the How-to section, so I would post the reply to the How-to section as well.

---

### Post by akendall1966 on 2006-12-13
Hi,

First many thanks for the how to worked for my to get my fusion case display up and running.

I have one issue I hope someone can shed light on, I am using mythTV on the system the antec houses all the menu items and media itms display OK but when I turn the clock on I am not getting complete charcaters formed. Is there some set up in LCDPorc or MythTV that could effect this behaviour?

Thanks AK

---

### Post by piec2 on 2006-12-13
Two things I would check:

If your problem is only when the time is displayed (while all the rest works fine), then you problem is likely the setting for "Display Large Clock".
In MythTV, in the Setup/Apperance menu, go to the "LCD device display" screen and make sure the "Display Large Clock" checkbox is NOT checked.
There appears to be a bug with this and I'm not sure if it's in MythTV itself of LCDProc. Only the "one line" clock will work.

If your problem is with any thing that is displayed on your VFD, then check out /etc/LCDd.conf and make sure that in your section " [imon]" the "Size=16x2".

---

### Post by pejcao on 2007-03-21
Is it possible on the stand alone imon VDF to use simultaneously the VDF + Lirc + the Knob?
Does the VDF works in lcd4linux?

---

### Post by piec2 on 2007-03-21
As far as I know you will be able to use the VFD and the remote.
I don't think the knob will work (at least not with Venky's patch).

---

### Post by broxtor on 2007-04-15
I've got the knob to work. At least, I can get it to work once I've booted my computer. But I wasn't able to do it automatically during boot, but perhaps there's somebody here who can help me with that.
Here's how I did it.

I assume that you've got the VFD already working. I used the lirc_imon module for that. You can compile it from the lirc sources. During configuration choose the IMON Multimedian IR/VFD driver. (There's also a IMON Knob driver, but that did strange things to my sound).

Next, add the following to your lird.conf file: [(source)]("http://www.mythtv.org/wiki/index.php/SilverstoneTek_LC16M#Click_Wheel")
```
begin remote

  name  ClickWheel
  bits           24
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  post_data_bits  8
  post_data      0xFF
  gap          131993
  toggle_bit      0

      begin codes
          WheelCC                  0x010000
          WheelCW                  0x000100
          WheelClick               0x000008
      end codes
end remote
```

The line "WheelClick 0x000008" isn't necessary for the Antec Fusion, since that knob isn't a clickwheel, but it doesn't hurt to leave in there.

Now since we have two lirc devices (your remote and the Antec volume knob) we have to have two instances of lircd running. In my case, my PVR-350 remote is on /dev/lirc0 and my volume knob is on /dev/lirc1. You can determine which lirc device you have by doing:
```

cd /dev
ls | grep lirc

```
You're output will look something like:
```

lirc
lirc0
lirc1
lircd

```
To determine which lirc is which device type:
```

ps ax | grep lirc

```
You will now get (amongst others) a line like:
```

4820 ?        Ss     0:00 /usr/sbin/lircd --device=/dev/lirc0

```
This will be the device you've already got working, probably your remote.

Now, stop lircd by doing:
```

sudo killall lircd

```
Or on not Debian-like distro's:
```

su
killall lircd

```

Now start the two lircd instances in the following way: 
```

# First use the lirc device for the volume knob, in my case /dev/lirc1
lircd --driver=default --device=/dev/lirc1 --output=/dev/lircd1 --pidfile=/var/run/lircd1.pid --listen

# Now use the lirc device for your remote
lircd --driver=default --device=/dev/lirc0 --output=/dev/lircd --pidfile=/var/run/lircd.pid --connect=localhost:8765

```

If everything went well, you're volume knob is now working. You can test this by doing:
```

irw

```
Now turn the knob and press some buttons on your remote. You will see an output similar to the one below.
```

#Output for the volume knob
00000000000100ff 00 WheelCW ClickWheel
00000000000100ff 01 WheelCW ClickWheel
00000000000100ff 02 WheelCW ClickWheel
00000000010000ff 00 WheelCC ClickWheel
00000000010000ff 01 WheelCC ClickWheel

#Output for the remote
0000000000001790 00 Vol+ Hauppauge_350
0000000000001790 00 Vol+ Hauppauge_350
00000000000017a0 00 Ch+ Hauppauge_350
00000000000017a0 01 Ch+ Hauppauge_350
00000000000017a1 00 Ch- Hauppauge_350

```

To make the knob actually do something you have to add entries to your .lircrc file.

This is how far I got it to work. If anyone here knows how start lircd in this way during boot, I would really appriciate it if you could let me know.

---

### Post by peterthewolf on 2007-05-01
Followed howto with cuurent feisty linux kernel 2.6.20-15 and I get these errors
Any help appreciated


mythtv@peter-desktop:~/imon$ make -C /usr/src/linux-headers-2.6.20-15-generic/ SUBDIRS=$PWD modules
make: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/mythtv/imon/imon_vfd.o
/home/mythtv/imon/imon_vfd.c:34:26: error: linux/config.h: No such file or directory
/home/mythtv/imon/imon_vfd.c:43:35: error: linux/devfs_fs_kernel.h: No such file or directory
/home/mythtv/imon/imon_vfd.c: In function ‘send_packet’:
/home/mythtv/imon/imon_vfd.c:328: warning: passing argument 6 of ‘usb_fill_int_urb’ from incompatible pointer type
make[1]: *** [/home/mythtv/imon/imon_vfd.o] Error 1
make: *** [_module_/home/mythtv/imon] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
mythtv@peter-desktop:~/imon$

---

### Post by andymg on 2007-05-01
I have the same error on Feisty -no header files (even though I have the kernel source & headers installed).

I have a possible **(partial) solution**, but this will need further investigation by someone more experienced than me:

From googling it appears that there could be issues compiling some code using devfs references.
.
I managed to get the VFD working in Feisty <from the command line> by commenting out a single line in the imon_vfd.c driver file from: [http://venky.ws/projects/imon/#standalone]("http://venky.ws/projects/imon/#standalone")

The line to comment-out is:#include <linux/devfs_fs_kernel.h>

It's line 43 (after the patch is applied.

You should then be able to build the driver if you follow the above guide & modprobe successfully - the /dev/lcd0 point is also created successfully.

sudo /usr/sbin/LCDd will then enable the imon VFD.

The stage I am at is trying to get it to work in MythTV -the VFD just wont activate, all I can do (so far) is turn it on from the command line.

My suspicion is that another devfs reference needs to be removed/modified in the imon_vfd.c driver file.
Unfortunately, my experience level probably isn't as good as it could be to resolve this issue/do so elegantly -maybe someone else could help-out in this regard? From this point I'm just going by trial & error.

---

### Post by broxtor on 2007-05-02
First you commented out a line in the source and now the driver doesn't work. Sounds like a possible cause to me.
But for the problem with missing source: Besides de the kernel headers you also need the ncurses-dev package I believe.

Tip: Have a look at: [http://www.mythtv.org/wiki/index.php/Imon](http://www.mythtv.org/wiki/index.php/Imon)

---

### Post by peterthewolf on 2007-05-04
Broxtor
That link is just no good you end up modprobe lirc_imon which does not exist after going through all the install steps.

In fact that link goes against everything in this posting in that you cannot just use lcdproc for imon.

---

### Post by peterthewolf on 2007-05-13
Andymg

You said
I managed to get the VFD working in Feisty <from the command line> by commenting out a single line in the imon_vfd.c driver file from: [http://venky.ws/projects/imon/#standalone](http://venky.ws/projects/imon/#standalone)

The line to comment-out is:#include <linux/devfs_fs_kernel.h>

Do as above but also change #include <linux/config.h> to #include <linux/configfs.h> and reinstall.
I did this and now the vfd works with mythtv.

---

### Post by Isntitknoying on 2007-05-16
I have commented out and modified the aforementioned lines of code, and re-installed the imon driver, and when I run LCDd from the command line, my VFD will work. However, when I attempt to start LCDd with /etc/init.d/LCDd start, it fails. 

My syslog shows the following:

knoy-htpc LCDd: Non-option arguments on the command line !
knoy-htpc LCDd: Critical error while processing settings, abort.

Does anyone have any idea as to what could be causing this? I feel like I am really close to having my VFD working again, but I'm stuck. 

Thanks for any help!

---

### Post by ktrnka on 2007-05-18
This should help some.

[http://stacktrace.org/index_html/20070208lirc-fix-for-linux-2.6.19/?searchterm=imon](http://stacktrace.org/index_html/20070208lirc-fix-for-linux-2.6.19/?searchterm=imon) 

sorry nevermind

---

### Post by ktrnka on 2007-05-18
> **Isntitknoying said:**
> I have commented out and modified the aforementioned lines of code, and re-installed the imon driver, and when I run LCDd from the command line, my VFD will work. However, when I attempt to start LCDd with /etc/init.d/LCDd start, it fails. 

My syslog shows the following:

knoy-htpc LCDd: Non-option arguments on the command line !
knoy-htpc LCDd: Critical error while processing settings, abort.

Does anyone have any idea as to what could be causing this? I feel like I am really close to having my VFD working again, but I'm stuck. 

Thanks for any help!

I had the same problem. I fixed it by going through synaptic and completely removing lcdproc and then reisntalling it. I then went back through the LCDd.conf and changed the driver and driver path like before. I then tried to start it 
/etc/init.d/LCDd start and it worked. I'm not quite sure what the problem was but it worked for me.

Oh wait, I did one more thing. I was reading somewhere that the old config.h was actually replaced with autoconf.h. i reinstalled the imon driver  but instead of changing the #include <linux/config.h> to <linux/configfs.h>    it should be #include <linux/autoconf.h>
then did the previous steps.  

Just redo the imon driver steps but change #include <linux/config.h> to #include <linux/autoconf.h>

If it helps let me know.

---

### Post by striscio on 2007-05-18
Hi, I would like to know your hardware configuration: motherboard, video-card, dbv(-t) card etc. because I'm planning to build an HTPC with linux and the antec fusion case. Please if you can send me a message, thanks

---

### Post by ktrnka on 2007-05-18
> **striscio said:**
> Hi, I would like to know your hardware configuration: motherboard, video-card, dbv(-t) card etc. because I'm planning to build an HTPC with linux and the antec fusion case. Please if you can send me a message, thanks

ECS RS-482
Amd x2 3800+ 65w
Happague PVR-150
Geforce FX-5500 PCI (with fan removed) cause the i was havin problems with the onboard ati graphics.

---

### Post by peterthewolf on 2007-05-19
PC is as follows

Antec Fusion
ASRock ALiveNF4G-DVIhttp://wiki.ubuntu-it.org/RalinkRT73ASRock ALiveNF4G-DVI
AMD AM2 3200+
2 x 512 MB

SATA SAMSUNG HD160JJ
PIONEER DVD-RW DVR-105, ATAPI CD/DVD-ROM drive

Hauppage WinTV-NOVA-T model 909
KeySonic Wireless-Mini keyboard/mouse
DLINK USB Wireless DWL-G122 internet connection

Silverstone NT05 heat sink with one of antec 12cm fans mounted on top and one still mounted on the side of the case. This gives a near silent unit with temperatures between 25C and 40C. As I write this Core is at 26C, Sys Temp 35C, CPU 32C and AUX 32C

Ubuntu Feisty

For Mythtv I used the advice on this site - very easy
[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

For Wireless internet I used the advice here again very easy
[http://wiki.ubuntu-it.org/RalinkRT73](http://wiki.ubuntu-it.org/RalinkRT73)

The only problem I have is that CD/DVD writing is unreliable and I have to use an external USB CD/DVD writer most of the time. I have swapped CD units between the case and external but no success in case. All I can think is that Linux does not like the mixture of SATA hard disk and IDE CD.

---

### Post by Isntitknoying on 2007-05-19
Ok, after a reinstall of lcdproc, and rebuilding the imon driver with the changes you suggested, I still get the same error. The only thing that I have that can shed any light on this is when I build the imon driver, I get the following message:

/home/isntitknoying/VFD/imon/imon_vfd.c:331: warning: passing argument 6 of ‘usb_fill_int_urb’ from incompatible pointer type

Anyone have any ideas? I can still start the VFD from the /usr/sbin/LCDd command, and it will show the "0 Screens" stuff, but starting with the /etc/init.d/LCDd command will provide me with these erros in the syslog:

knoy-htpc LCDd: Non-option arguments on the command line !
knoy-htpc LCDd: Critical error while processing settings, abort.

Thanks for all of your help!

---

### Post by Isntitknoying on 2007-05-19
Updates all around. I have my VFD working in MythTV with feisty. The changes I made are as follows:

1. Rebuild and install imon driver with 
#include <linux/devfs_fs_kernel.h> commented out ( surround it with /* and */) 
and with 
#include <linux/config.h> changed to #include <linux/autoconf.h>

2. Modify /etc/init.d/LCDd and change the line that reads 
DAEMON_OPTS="-s true -f true -c /etc/LCDd.conf"
to read 
DAEMON_OPTS="-s 1 -f -c /etc/LCDd.conf"

This got everything working for me after a restart of mythtv.
Thanks to everyone for your help!!!

---

### Post by ijustam on 2007-05-22
Hi all, this post has been a godsend but for some reason it won't install /dev/lcd0 on my Feisty machine.  The make and make install execute without error but they don't seem to actually do anything.

This is my "make install" output:
/usr/bin/install imon_vfd.ko /lib/modules/`uname -r`/kernel/drivers/usb/misc
depmod

Is it supposed to just echo the contents of the makefile?

---

### Post by ktrnka on 2007-05-23
anyone have an easy way of getting the knob to work in feisty?

---

### Post by broxtor on 2007-05-23
Yes, I do. See my comments on page 1 of this thread.

---

### Post by ktrnka on 2007-05-25
> **broxtor said:**
> Yes, I do. See my comments on page 1 of this thread.

when i ls | grep lirc i get these devices
lirc
lircd
lircd1
lircm

I tried to start it similar to yours but and changed --device=/dev/lirc1 to each one of the devices to figure out which one is the knob but every time i run irw it says connection refused even though I can see it running. Any ideas?

---

### Post by elzapp on 2007-06-14
Does anyone have the imon-2.6.patch lying around, if so, could you put it online somewhere? The stacktrace.org site is down

---

### Post by elzapp on 2007-06-15
It seems that was a temporar error

---

### Post by Funkyboogaloo on 2007-07-11
Hi all, thanks for the info on this so far.  I followed some info on the mythtv wiki regarding this and managed to get the display working ok but struggled with the volume nob.   Anyways, after some messing about I managed to get it to work using the instructions on this page with the additional to get it working at boot (Distro: Fedora 2) :

in /etc/sysconfig/lircd

add the following lines:

killall lircd
LIRCD_OPTIONS="--driver=default --device=/dev/lirc1 --output=/dev/lircd1 --pidfile=/var/run/lircd1.pid"
LIRCD_OPTIONS="--driver=default --device=/dev/lirc0 --output=/dev/lircd --pidfile=/var/run/lircd.pid"

save and reboot, you're vol control should now work at boot.

SJ

---

### Post by Funkyboogaloo on 2007-07-16
Additional regarding last posting:

OK, this was working fine for a day or so but a reboot of the box seems to have deleted all the config I made to get the thing working in the first place! I don't know why this is but all lirc config files have been deleted.

MS MCE is now looking an attractive alternative even though multi room is much more hassle!

Does anyone else have any thoughts on how to get this working in a stable configuration?

SJ

---

### Post by chairman on 2007-07-22
> **Isntitknoying said:**
> Updates all around. I have my VFD working in MythTV with feisty. The changes I made are as follows:

1. Rebuild and install imon driver with 
#include <linux/devfs_fs_kernel.h> commented out ( surround it with /* and */) 
and with 
#include <linux/config.h> changed to #include <linux/autoconf.h>

2. Modify /etc/init.d/LCDd and change the line that reads 
DAEMON_OPTS="-s true -f true -c /etc/LCDd.conf"
to read 
DAEMON_OPTS="-s 1 -f -c /etc/LCDd.conf"

This got everything working for me after a restart of mythtv.
Thanks to everyone for your help!!!

I have done the changes, but still get

sudo make -C /usr/src/linux SUBDIRS=$PWD modules
make: Entering directory `/usr/src/linux-source-2.6.20'
  CC [M]  /home/chairman/imon/imon_vfd.o
/home/chairman/imon/imon_vfd.c:147: error: unknown field ‘owner’ specified in initializer
/home/chairman/imon/imon_vfd.c:147: warning: initialization from incompatible pointer type
/home/chairman/imon/imon_vfd.c:162: error: unknown field ‘mode’ specified in initializer
/home/chairman/imon/imon_vfd.c: In function ‘send_packet’:
/home/chairman/imon/imon_vfd.c:328: warning: passing argument 6 of ‘usb_fill_int_urb’ from incompatible pointer type
make[1]: *** [/home/chairman/imon/imon_vfd.o] Error 1
make: *** [_module_/home/chairman/imon] Error 2
make: Leaving directory `/usr/src/linux-source-2.6.20'

any ideas what could be wrong?

I forgot to patch after I unpacked it again

---

### Post by axelsvag on 2007-08-14
Tonight I succeded to make my VFD work after 5 weeks constant testing. For me the problem was that I did not understood where I went wrong. The command in my feisty installation that went wrong was this 

make -C /usr/src/linux SUBDIRS=$PWD modules 


I had to change it as you all said but I did not understood to 

make -C /usr/src/linux-headers-2.6.20-16-generic/ SUBDIRS=$PWD modules

Maybe it has something to do with an upgrade in the summer but the 2.6.20-15 did not work for me.

---

### Post by period3 on 2007-08-19
I was also getting errors about modpost:

/bin/sh: scripts/mod/modpost: not found
make[1]: *** [__modpost] Error 127
make: *** [modules] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.20-16'


I fixed this by changing to the linux header directory (/usr/src/linux-headers-2..20-16) and typing:  'make scripts'

---

### Post by hovenko on 2007-08-25
Installing lirc and the lirc modules should do it for Ubuntu Feisty.
```
aptitude install lirc lirc-modules-2.6.20-15-generic
```

The installed module is named lirc_imon.
```
modprobe lirc_imon
```

I'm not 100% sure it works, since I'm not in front of my system (remote login), but a /dev/lcd0 device was created after loading the module. I can echo text to the device without getting errors in my logs :)
```
echo -n "Hello" > /dev/lcd0
```

Output from dmesg when loading the module (the last two lines occured when echoing to the device, believe it's only debugging):
```
[110344.952000] lirc_dev: IR Remote Control driver registered, at major 61
[110344.952000] lirc_imon: no version for "struct_module" found: kernel tainted.
[110344.956000] /usr/src/modules/lirc/drivers/lirc_imon/lirc_imon.c: Driver for Soundgraph iMON MultiMedian IR/VFD, v0.3
[110344.956000] /usr/src/modules/lirc/drivers/lirc_imon/lirc_imon.c: Venky Raju <dev@venky.ws>
[110344.956000] /usr/src/modules/lirc/drivers/lirc_imon/lirc_imon.c: imon_probe: found IMON device
[110344.956000] lirc_dev: lirc_register_plugin: sample_rate: 0
[110344.956000] /usr/src/modules/lirc/drivers/lirc_imon/lirc_imon.c: imon_probe: Registered iMON plugin (minor:0)
[110344.956000] /usr/src/modules/lirc/drivers/lirc_imon/lirc_imon.c: imon_probe: iMON device on usb<2:4> initialized
[110344.956000] usbcore: registered new interface driver lirc_imon
[110551.952000] /usr/src/modules/lirc/drivers/lirc_imon/lirc_imon.c: VFD port opened
[110552.000000] /usr/src/modules/lirc/drivers/lirc_imon/lirc_imon.c: VFD port closed
```

---

### Post by axelsvag on 2007-08-26
I am maybe stupid, but what do want with your last text. Do you have a problem or are you trying to help someone.

---

### Post by disciple3d on 2007-08-31
Hi all, the instructions here a useful, but I've not been able to get my VFD to do anything.  I have compiled the imon_vfd module in Ubuntu Feisty, and managed to install it fine.  However, no /dev/lcd0 device is created, and so I can't start the LCDd process.  

I have an Antec Fusion Case with an MSI K9MM-V motherboard.

Dmesg output shows:

 [  917.108000] /home/chris/imon/imon_vfd.c: Driver for Soundgraph iMON VFD, v0.1a1
[  917.108000] /home/chris/imon/imon_vfd.c: Venky Raju <dev@venky.ws>
[  917.108000] usbcore: registered new interface driver imon

It looks like it loads OK, so I decided to check for the USB device, but it doesn't appear in the lsusb list anywhere - I only have the wireless keyboard in there.  I assume it should be showing?  

I have tried both usb headers on the motherboard, and also plugging it into a USB socket directly too, but it doesn't seem to make any difference!  I hope my VFD isn't broken, I don't want to have to send another case back to Ebuyer :( 

Does anyone have any ideas?

Thanks,

Chris

---

### Post by disciple3d on 2007-08-31
Doh... please ignore my question.  I'd neglected to plug in the floppy power connector for the VFD which was hidden under the CD drive... 

When all else fails RTFM :)

---

### Post by Fopper on 2007-09-09
> **Funkyboogaloo said:**
> Hi all, thanks for the info on this so far.  I followed some info on the mythtv wiki regarding this and managed to get the display working ok but struggled with the volume nob.   Anyways, after some messing about I managed to get it to work using the instructions on this page with the additional to get it working at boot (Distro: Fedora 2) :

in /etc/sysconfig/lircd

add the following lines:

killall lircd
LIRCD_OPTIONS="--driver=default --device=/dev/lirc1 --output=/dev/lircd1 --pidfile=/var/run/lircd1.pid"
LIRCD_OPTIONS="--driver=default --device=/dev/lirc0 --output=/dev/lircd --pidfile=/var/run/lircd.pid"

save and reboot, you're vol control should now work at boot.


Does anyone know how to configure this for Ubuntu, because this seems to be a typical Fedora configuration. The map sysconfig does not exists. As far as I can find it should be done in hardware.conf, but I don't know how.

---

### Post by modulok on 2007-10-07
I have an Antec Fusion (first version) and an ATI Remote Wonder (Bob). I haven't played with getting either to work yet, but does anyone have this combo with all three features working? (knob, vfd, remote)

---

### Post by ktrnka on 2007-10-08
I have a pvr-150 but I do have remote, knob, and vfd working.

---

### Post by modulok on 2007-10-08
I have pvr-500 (basically two pvr-150's)...but do you have the same ati remote?

---

### Post by ktrnka on 2007-10-08
No I don't have the same remote though. Are you having problems? I'd figure it'd be a similar configuration. Does your system see it if you plug it in? Plug it in and run:

lsusb

If it doesn't then you might have to look at lirc. I've also read about some people just using xmodmap to map the buttons. 
Some resources:

[http://remotew.free.fr/index.htm](http://remotew.free.fr/index.htm)

[http://www.mythtv.org/wiki/index.php/ATI_Remote_Wonder](http://www.mythtv.org/wiki/index.php/ATI_Remote_Wonder)

[http://www.mythtv.org/wiki/index.php/ATI_Remote_Wonder_II](http://www.mythtv.org/wiki/index.php/ATI_Remote_Wonder_II)

[http://knoppmythwiki.org/index.php?page=ATIRemote](http://knoppmythwiki.org/index.php?page=ATIRemote)

Let me know if any of this helps

---

### Post by tobycatlin on 2007-10-09
Does anyone know if the procedure for getting the vfd running on the version 2 of this case is any different to the v1 case?

I have got the v2 case and have followed all instructions posted above. Wiped them down and tried a totally different method from stacktrace. although everything seems to install with no errors the vfd hasn't changed.

LCDd starts fine and /dev/lcd0 exists

When i echo anything out to the display i don't get an error message but i don't get any display either. The display is always on, even when the pc is off. If the motherboard has power then all lights blaze. 

Anyone done this already? any help would be very welcome

thanks

toby

---

### Post by ktrnka on 2007-10-09
The only difference I can find between the versions is that version 2 has a built in IR receiver. As for the problems you are having you're running Feisty right?

---

### Post by ktrnka on 2007-10-09
If you are running feisty, did you do the little fix on page 2-3?

"Updates all around. I have my VFD working in MythTV with feisty. The changes I made are as follows:

1. Rebuild and install imon driver with
#include <linux/devfs_fs_kernel.h> commented out ( surround it with /* and */)
and with
#include <linux/config.h> changed to #include <linux/autoconf.h>

2. Modify /etc/init.d/LCDd and change the line that reads
DAEMON_OPTS="-s true -f true -c /etc/LCDd.conf"
to read
DAEMON_OPTS="-s 1 -f -c /etc/LCDd.conf"

This got everything working for me after a restart of mythtv.
Thanks to everyone for your help!!!"

---

### Post by tobycatlin on 2007-10-10
Yes i did include those two tweaks re-complied and re-booted.

All lights on the vfd are lit up on a permanent basis.

Does anyone have any suggestions on anything else i could do to test it?

---

### Post by tobycatlin on 2007-10-10
As i am getting desperate i thought i'd flick through the manual and it says quote:
"Fusion 2 comes with a Vacuum Florescent Display (VFD) and the Fusion Black comes with a Liquid Crystal Display"

I have the Fusion black and had assumed that the display would be the same for both cases. It appears not.  I have attached a picture for clarity. 

anyone got one of these working?

---

### Post by tobycatlin on 2007-10-10
just found this page [http://codeka.com/blogs/index.php/dean/2007/09/03/imon_lcd_patch_v0_1]("http://codeka.com/blogs/index.php/dean/2007/09/03/imon_lcd_patch_v0_1")

Seems like there is hope yet. I'll try this now and see what happens. I'll keep you all posted of any tremendously exciting developments as they develop.

t

---

### Post by Cuppa-Chino on 2007-10-10
> **tobycatlin said:**
> As i am getting desperate i thought i'd flick through the manual and it says quote:
"Fusion 2 comes with a Vacuum Florescent Display (VFD) and the Fusion Black comes with a Liquid Crystal Display"

I have the Fusion black and had assumed that the display would be the same for both cases. It appears not.  I have attached a picture for clarity. 

anyone got one of these working?

that is the LCD but it work with mythtv / linux as well

---

### Post by Dirt Diver on 2007-10-19
I've just recieved my Antec, and I've put down some time to get the display working. I've followed the steps mentioned in this thread.

(I'm at work right now so I can't provide the exact  error message.)

BUT when I'm trying to start the lcd deamon with
```
sudo /usr/sbin/LCDd
```

I get an error saying that havn't loaded the imon module into the kernel.

The problem is that I _have_ insmoded the module.

Is there anyone out there with the same problem that can point me into the right direction?

---

### Post by tobycatlin on 2007-10-19
the tutorial suggests running:
sudo LCDd -f -r 4 in the LCDProc folder. Did this work? It's a good starting point to check everything is in place.

I think it might be a good idea to split this thread off on to a new one specifically for the Antec LCD rather than VFD

---

### Post by axelsvag on 2007-10-21
I have been using this tutorial succesfully for the feisty era. But now when I changed to Gutsy I made a fresh install. unfirtunately I get lots of problem to install the VFD/LCD functions. I get stuck at the patch part. After I say the the patch command I get this answer "
>  Can't rename file /tmp/poZWnrmB to imon_vfd.c : Permission denied

Does anyone have any suggestions?

---

### Post by tobycatlin on 2007-10-22
Looks like you don't have permission to rename /tmp/poZWnrmB to imon_vfd.c

Are you running the command as root?

---

### Post by ardnut on 2007-10-23
> **axelsvag said:**
> I have been using this tutorial succesfully for the feisty era. But now when I changed to Gutsy I made a fresh install. unfirtunately I get lots of problem to install the VFD/LCD functions. I get stuck at the patch part. After I say the the patch command I get this answer "


Does anyone have any suggestions?

Which version of the Antec Fusion case do you have?
I just brought a Silver Antec Fusion v2 case and got the VFD, Volume knob and IR receiver all working quite easily without the need to patch anything and using default gutsy packages via apt-get.

Ash


Sorry, ignore me, I missed reading a page thus didn't see your post explaining what version you have - and can't find the delete post button.

---

### Post by orasetaina on 2007-10-23
Will this work with a thermaltake Mozart sx running plain fiesty without mythtv?

---

### Post by axelsvag on 2007-10-24
I was not logged as root but used the sudo command which I thought made the same thing. 

ardnut
About using V2 or not I am not quite sure. I said V 2 on the box and manual but... What did you use to make vfd work in gutsy? is there any easier way than with patches??

---

### Post by volkswagner on 2007-12-10
help stuck in the middle of lcd install

patching file Makefile
eric@FamilyRoom:~/imon$ make -C /usr/src/linux SUBDIRS=$PWD modules
make: *** /usr/src/linux: No such file or directory.  Stop.

when I navigate to /usr/src the file is empty, I am running mythbuntu 7.10

---

### Post by KjetilK on 2007-12-14
> **ardnut said:**
> 
I just brought a Silver Antec Fusion v2 case and got the VFD, Volume knob and IR receiver all working quite easily without the need to patch anything and using default gutsy packages via apt-get.


Yup!

For future reference, I guess it is useful to know exactly what you did. I needed only install lcdproc and set the Driver in the [server] section of LCDd.conf to imon. Then restart, and it looks like it works.:)

---

### Post by RawMustard on 2008-01-04
Do you need to use mythtv to get this thing to work in gutsy?
I installed lcdproc and set the driver to imon but nothing happens???

I tried sudo echo -n "Hello" >lcd0 but get permission denide and as root I get /dev/lcd0 Device or resource busy

The Sound knob does nothing.

Am I missing something?  I've got a Fusion Black with the lcd screen.

---

### Post by Bokonon on 2008-01-09
> **broxtor said:**
> 
Now start the two lircd instances in the following way: 
```

# First use the lirc device for the volume knob, in my case /dev/lirc1
lircd --driver=default --device=/dev/lirc1 --output=/dev/lircd1 --pidfile=/var/run/lircd1.pid --listen

# Now use the lirc device for your remote
lircd --driver=default --device=/dev/lirc0 --output=/dev/lircd --pidfile=/var/run/lircd.pid --connect=localhost:8765

```

This is how far I got it to work. If anyone here knows how start lircd in this way during boot, I would really appreciate it if you could let me know.

I got it to work with a bit of a hack.  It certainly is not the most elegant way, but it works.

Basically, I could not get both of those to run via the start-daemon line in /etc/init.d/lirc  Whichever one started first would run and the other would not.  I was able to start them both from the command line similar to you.

My hack was making two files in /etc/init.d/ one to start up each device.

One is lirc (and setup to use the config for my remote similar to above)
One is lirc_imon (and setup to use the config for the imon similar to above)

That still didn't fix it.  For some reason, /usr/sbin/lircd would not start a new daemon and if I did a restart, the existing one died.  So I copied /usr/sbin/lircd to /usr/sbin/lircd1 and setup the imon config to run that instead of /usr/sbin/lircd

Create symlinks in both /etc/rc2.d/ and /etc/rc0.d/ to start them on boot and stop them on shutdown.

Now when I boot, both start up, but the imon is controlled by the copied /usr/sbein/lircd1

Extra Steps (in addition to the guide above and at mythtv.org)
0. Make backup files of everything you adjust so that you can go back to it if needed.
1. Get one of them working using /etc/init.d/lirc.  Don't mess with it anymore.
2. Copy /usr/sbin/lircd to /usr/sbin/lircd1 so you have two files to run
```

sudo cp /usr/sbin/lircd /usr/sbin/lircd1 

```
3. Create a new 'lirc' file such as /etc/init.d/lirc_imon with the settings for the imon and also using the lircd1 instead of lircd (both start and stop)
```

sudo cp /etc/init.d/lirc /etc/init.d/lirc_imon

```
4. Create symlinks in /etc/rc2.d/ and /etc/rc0.d/ to the new lirc_imon setup in order to start/stop it on boot/shutdown.  Just make them similar to the already existing lirc links.  For me, an example is /etc/rc2.d/S52lirc_imon -> ../init.d/lirc_imon
```

sudo ln -s /etc/init.d/lirc_imon /etc/rc2.d/S52lirc_imon
sudo ln -s /etc/init.d/lirc_imon /etc/rc0.d/K52lirc_imon

```
The line in lirc (and lirc_imon) that needs to be changed is this:

If you already have one working, just edit the other one with your favorite text editor.

**original lirc**
```

start-stop-daemon --start --quiet --exec /usr/sbin/lircd -- $LIRCD_ARGS \ < /dev/null

```

I changed mine to something similar to:
**lirc**
```

start-stop-daemon --start --quiet --exec /usr/sbin/lircd -- $LIRCD_OPTIONS

```

**lirc_imon**
```

start-stop-daemon --start --quiet --exec /usr/sbin/lircd1 -- $LIRCD1_OPTIONS

```

$LIRCD_OPTIONS and $LIRC1_OPTIONS were defined as per the guide at mythtv.org, so I just used those.

If you have trouble, you might try reinserting the < /dev/null part, but I didn't need it.

In both, there is also a shutdown section.  You should change your lirc_imon file to use the /usr/sbin/lircd1 as well.

**lirc_imon**
```

start-stop-daemon --stop --quiet --signal 1 --exec /usr/sbin/lircd1

```


I hope that helps.  Sorry it isn't the best guide around.  Perhaps someone with better writing skills can clean it up some.

---

### Post by Electricboots on 2008-01-18
Hello everybody,

I wasn't sure if I should make a new thread or post in this one, but here we go.

I'm trying to setup a Mythbuntu 7.10 computer with the following hardware:
[LIST]
[*][Antec Fusion 430]("http://www.antec.com/us/productDetails.php?ProdID=15740")
[*][Biostar TF7050-M2 motherboard]("http://www.biostar.com.tw/app/en-us/t-series/introduction.php?S_ID=182")
[*][Hauppauge-WinTV-PVR-150 card]("http://www.hauppauge.com/pages/products/data_pvr150.html") (comes with a remote control)
[*]Wireless LAN card, 2GB ram, 500GB harddrive
[/LIST]

My two main problems right now are:
[LIST=1]
[*]Getting the remote that came with my PVR-150 to work with the IR receiver built in the VFD screen.
[*]Getting the VFD screen to show things
[/LIST]

(Eventually I want to get the volume knob to work but that's low priority).

**First, about the remote.**

With irrecord, I can make little . dots appear when I press on buttons on the remote.  With mode2 I can get it to show things like "code: 0x800f041e" when I press on buttons on the remote.  I cannot make irw react though, it's like I'm not doing anything. 

In Mythbuntu Control Centre -> Remote Control,  I have 'Hauppauge TV card' selected.

 When I load MythTV, it doesn't react at all to keypresses on the remote control. :(

**Now, about the VFD screen.**

First problem, I think there's a permission issue with /dev/lcd0.  If I try to do "echo Hello > /dev/lcd0", I get Permission Denied.  If I 'chmod 666' it, then when I echo "Hello", it shows "Hello" on the VFD.  If I reboot, I'll have to 'chmod 666' it again.

Whatever I echo to the VFD stays there forever until I turn off the power supply switch at the back of the computer.

In MythTV, I have enabled the LCD, but nothing ever appears on it. :(

Any ideas  what I could do next? :|

Thanks in advance for any help!

---

### Post by Electricboots on 2008-01-18
Quick update:  I was able to get my VFD screen working finally.


I just checked the remote, it says RC6 at the back.   Not sure if that's of any help...

I just realized that all this time I've been using lirc_imon module.
I just tried the lirc_mceusb2 module, but it doesn't change anything.

Back to the drawing board...

---

### Post by RawMustard on 2008-01-25
> **broxtor said:**
> This is how far I got it to work. If anyone here knows how start lircd in this way during boot, I would really appriciate it if you could let me know.

Add those lines to /etc/lirc/hardware.conf like so```
# Arguments which will be used when launching lircd
LIRCD_ARGS="--driver=default --device=/dev/lirc1 --output=/dev/lircd1 --pidfile=/var/run/lircd1.pid --listen"
LIRCD2_ARGS="--driver=default --device=/dev/lirc0 --output=/dev/lircd --pidfile=/var/run/lircd.pid --connect=localhost:8765"
```

After grappling with getting my streamzap remote and the Fusion Black volume knob working together on gutsy, I came across your commands and tried putting them like I've shown you - and guess what?  They worked :)

Thankyou for your input.

I'm still trying to get the LCD screen working, but from what I've read, it's only useful and works with mythtv which I dislike with a passion.  So I might just hide it altogether until the drivers for it allow you to write to the screen via a python script or something.

---

### Post by oct on 2008-02-06
I have an Antec Fusion v2 silver and a Hauppauge NovaT 500 tuner card. I'd like to use the tuner remote control (the snowboard shaped one) with the integrated IR module. I succeeded in making the VFD to work, but  I still have problems with the IR and the volume knob.

I don't need to have both receivers running, I only need the Imon one, if it is compatible with the remote control. All the guides I found talk about having more than one device in /dev/lirc*, but I only have one. The Hauppauge output goes to /dev/input/event4, so I don't know what to do. I tried to load only the device /dev/lirc0, but irw gives no result. If I try to load both IR receivers, as described earlier in this post, none work.

How can I troubleshoot this? How can I be sure that /dev/lirc0 is the Imon PAD? And, is the Hauppauge remote compatible with the Imon IR receiver?

Thank you

Oct

---

### Post by Skerit on 2008-02-06
Everyone's so fixed on that VFD & wheelknob thing that nobody's actually talking about that DAMNED IR RECEIVER!

However, I think a new thread is in order! This one was actually for the Antec Fusion V1 case, with a VFD screen *without* ir receiver, a couple of ubuntu versions ago ...

All this help here is completely useless, files shifting around, drivers upgrading, bla bla bla

---

### Post by RawMustard on 2008-02-06
from my understanding, the ir reciever works with the lirc_mceusb2 module and the volume nob works with the lirc_imon module.  This is because antec butchered the soungraph controller to work with M$ Mediacenter remotes.

If you want to get the vfd or lcd working as well, you need to [patch lirc with this ]("http://codeka.com/blogs/index.php/dean/2007/09/26/imon_lcd_patch_v0_3")and build a new lirc_imon module.  But you'll still need to use the lirc_mceusb2 module to use the ir reciever.

---

### Post by oct on 2008-02-08
So, if the volume knob uses a module, and the IR receiver another one, should I have two devices under /dev, lets say lirc0 and lirc1, or not? I have tried to change the driver using Mythbuntu control centre but, as I've seen, it only modifies Lircd.conf and .lircrc files, but does not modify hardware.conf, who only refers to /dev/input/event4 (my hauppauge remote control). I think that if i don't load the correct module, I should see at least trash on irw, isn't it?

I'm sorry if I'm a bit confused, but I'm relatively new to Ubuntu, and I think i'v read too much howto's about the Antec, lirc, Imon, etc...

Thanks

---

### Post by TheBurner on 2008-08-21
Wow never thought fixing a VFD / IR would be so tough. Does anyone have a working Antec Fusion v2 silver vfd and the ir working? IF you do drop me a msg i need help. Thanks

---

### Post by chrisbain88 on 2008-08-23
Hi All,

Brought a Antec Fusion v2 and have been unable to get the display working.  How have people got the display working on Mythbuntu 8.04?
If so are you able to write a quick documentation on the process you have followed as curretly all I have found is pieces instructions everywhere.
Help is greatly appreciated.

Cheers,
Chris

---

### Post by mlord on 2008-09-06
I have the black Antec V1 case, and I wrote my own Myth interface for it.  Totally standalone (well, needs libusb installed), single file executable.   With source code, and no configuration required.  Just build/run that one executable.

Get it from [http://rtr.ca/vfd_updater/](http://rtr.ca/vfd_updater/)

It works for me; and the source is there if you want to customize how it works for you.

The display is simple, useful, and uncluttered.  It automatically scrolls, but not annoyingly, and the wheel (by default) is simply used to slow/control the scrolling if wanted.

I really cannot think of any good use for that wheel -- sure it looks nice there, but nearly everyone uses a remote control for Myth, so the wheel isn't really very useful.  But you can make it do anything you want it to, rather easily.

Cheers

---

### Post by niceangelbaby on 2008-09-07
just been browsing and came across  [www.watchesshopping.net](http://www.watchesshopping.net) there prices seem to be way lower that standard. All of the watches seem to be priced around $200 to $300. Are they fakes? The site seems to look quite legit.

---

### Post by peterthewolf on 2008-11-26
mlord

more info please

I am running Ubuntu 8.10 386

1. How to run at start up - putting in start up session did not work. The only way I can start it is with sudo from terminal.

2. When I run  then I get these errors, something to do with temperature, I have lm-sensors and sensor-applet installed which displays core0 and core1 temp at screen top. What should I do.

[sudo] password for tv: 
detaching inum 0 from kernel driver "lirc_imon"
/proc/acpi/thermal_zone/THRM/temperature: No such file or directory
ERROR 1054 (42S22) at line 1: Unknown column 'parentid' in 'where clause'
got short reply: 0 bytes
/proc/acpi/thermal_zone/THRM/temperature: No such file or directory
ERROR 1054 (42S22) at line 1: Unknown column 'parentid' in 'where clause'
got short reply: 0 bytes

3. vfd_updater causes the following display on the vfd

Mythtv not running.
15:52 Nov-26 ??


The not running message never changes no matter what mythtv is doing.

---

### Post by rocketlynx on 2009-04-28
I hope I'm in the correct area.  I'm new to this so be gentle.  The folks at "forum.linuxmce.org" told me to check here because of what I need.  I'm running LinuxMCE of which sits on top on Kubuntu 710.  It's the last stable version of LinuxMCE, so I'm kinda stuck if I want stability on my Home Automation System for now.

I have an Antec Fusion V2 (silver) Case with A Soundgraph VFD (imon w/ ir).  I've read the forum info and understand what to to but the first thing I need is LCDPROC and I can't seem to get it. I've tried apt-get install lcdproc or Adept package Installer but they both fail.

Being on 710, the Repos have changed and I seemed to be forced to use, if I understand it all correctly, Adept Package Manager because, as commented on the LinuxMCE forums, synaptic or any other sub package manager can have an adverse effect on the system installation.  Adept, with older Kubuntu 710, will not show me lcdproc because, I've been told, it's in an older repository that is not supported.

I'm also on kernel 2.6.22-14-generic.  Is there a way to ad an older source to adept or do a command line entry on the Konsole, more than just "apt-get install lcdproc"?  That fails because my system doesn't have a proper source to obtain is as stated above.

Any help would be greatly appreciated.

---

