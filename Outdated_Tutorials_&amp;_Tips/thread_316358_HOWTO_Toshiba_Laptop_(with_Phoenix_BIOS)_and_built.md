---
title: "HOWTO: Toshiba Laptop (with Phoenix BIOS) and built-in Bluetooth support"
date: 2006-12-10
forum: Outdated Tutorials &amp; Tips
---

### Post by Azriphale on 2006-12-10
[COLOR="Red"]***Note: The project website at [http://omnibook.sourceforge.net](http://omnibook.sourceforge.net) seems to no longer be available. While it appears to no longer be maintained, the source code is still available from [http://sourceforge.net/projects/omnibook](http://sourceforge.net/projects/omnibook). As it may no longer be maintained, it is probably a good idea to find an alternative to this module. Unfortunately, I have not had the time (or need as yet) to search for a usable alternative.***[/COLOR]

**HOWTO: Toshiba Laptop (with Phoenix BIOS) and built-in Bluetooth**

I hope somebody will find this useful. I have seen a few people with problems using bluetooth on the Phoenix BIOS models of Toshiba laptops, in this forum and elsewhere on the internet (while searching for answers to this problem).

This is a subject that is sorely lacking all over the place. There are wonderful utilities (or seemingly so, as I cannot use them) for Toshiba models that do not have a Phoenix BIOS, but rather a Toshiba BIOS, such as the “toshset” utility. 

Toshiba models that use a Phoenix BIOS cannot use the toshset utility. This is a problem when you wish to use bluetooth. I came across a utility originally for the HP Omnibook, with support for various Toshiba (notably those with a Phoenix BIOS) and Acer models.

The omnibook module is written by Mathieu Bérard, and all credit goes to him.

I have a Toshiba Satellite Pro M70-235 (available in Europe, Africa, and I guess the Middle East – as those regions tend to be grouped as EMEA – but I am unsure about the US), with the following specs:
Pentium M 1.86GHz
512 MB RAM (Upgraded to 1GB)
60GB HDD
DVD Writer
ATI X700
WiFi
Bluetooth

In short, its a powerful machine, but has everything required for mobility and ease of use etc (such as I will require bluetooth for using my phone as a GPRS modem when I am away from home this Christmas).

I was very worried today that I might have to reinstall Windows after wiping it off (again) so that I would be able to use Bluetooth.

The problem is this: The Toshiba bluetooth radio is disabled at boot, and it can only be enabled with a particular ACPI call. In Windows, you hit the Enable Bluetooth Radio button, and on you go. In GNU/Linux, you ... spend hours on the Internet and give up. Or maybe you find the omnibook sourceforge project (who would look there for a Toshiba problem?), which allows (through the /proc filesystem) control of things like the WiFi and Bluetooth radios. At least, that is all I have used it for. presumably, you can also use it to set up the multimedia buttons and whatnot, which I may have a bash at soon, but bluetooth was the big thing for me.

The omnibook project can be found at [http://omnibook.sourceforge.net]("http://omnibook.sourceforge.net")
Only source code is available, and you HAVE TO (!!!!!) use the svn trunk. At the time of writing this, the latest source package available on sourceforge did not work for me!

Before you download the required packages, and build, install and attempt to use the omnibook kernel module, head over to the [supported laptops list]("http://omnibook.sourceforge.net/doku.php?id=laptops&DokuWiki=0464a1502966a79e4adf2e1b0b19abe0") and see if your machine (or a similar machine, if you feel daring) is listed. Note the number next to the name of the machine (in my case, the Toshiba Satellite M70 has a value of 12 for the ectype field). You may need this value if your machine is not directly supported (as mine was not – i.e. the module did not detect what options it should load as I have a Satellite Pro, different from the Satellite listed there).

Packages that you will need in order to download and build the omnibook kernel module:

```

subversion
build-essential
linux-source

```
note that linux source is fairly large (in the region of 40 MB). I am not certain if this is required, but it is listed clearly as a dependency in the original install instructions.

You should probably also install the linux-headers package relating to your kernel, for instance linux-headers-generic

So, simply issue this command to install them:

```

$ sudo apt-get install subversion build-essential linux-source linux-headers-generic

```

make a folder in your home directory called “omnibook”, and use svn (subversion) to download the latest omnibook module sources:

```

$ cd ~
$ mkdir omnibook
$ cd omnibook
$ svn co https://omnibook.svn.sourceforge.net/svnroot/omnibook/omnibook/trunk

```

you will get notification of each file downloaded, and when it is done, you need to cd into the trunk folder:

```

$ cd trunk

```

now, you need to build and install the module:
```

$ make
$ sudo make install

```

load the module by performing the following command (which will run depmod and modprobe for you):

```

$ sudo make load

```

now, cd to /proc/omnibook/ (which should now exist)

```

$ cd /proc/omnibook
$ ls

```

There should be, at the very least, two files listed there:
dmi
version

If these are the only two files listed, then your machine is not supported directly. I will get to working around that in a second. If you have other files listed there, like wifi, bluetooth, lcd, temparature, touchpad, or others, then your machine is supported and you can enable bluetooth by using the following command:

```

$ sudo su
# echo 1 > bluetooth

```

(I do the “sudo su” to get a root console because a normal “sudo echo 1 > bluetooth” does not work. More on this later, and how to fix it)

To disable: 
```

$ sudo su
# echo 0 > bluetooth

```

The same can be done for wifi.
You can also get information about each item by doing this:

```

$ sudo cat bluetooth

```

To stop having to use a root console to set the paramaters, load the module with this option: “userset=1”

so, instead of running “make load” as we did earlier, do this:

```

$ sudo depmod -a
$ sudo modprobe omnibook userset=1

```

now a normal user will be able to enable/disable bluetooth, or edit any other omnibook paramater:

```

$ echo 1 > bluetooth

```

Once bluetooth is enabled using this method, you will be able to use it as normal. Issue a "hcitool dev" command in the console and you should get this:

```

$ hcitool dev
Devices:
        hci0    xx:xx:xx:xx:xx:xx
$

```

```
xx:xx:xx:xx:xx:xx
```
is your bluetooth HW address

where before you had this:

```

$ hcitool dev
Device:
$

```

If you do not have the settings files (such as bluetooth and wifi), but only have the dmi and version files, all is not lost if you feel like taking a risk. If your computer is similar to one of the models listed as supported, I think this is a small risk, but if it is completely different.. well, here is the warning from the website:

> 
WARNING: Forced load on an unsupported machine may cause unpredictable result. You have been warned...


I take no responsibility for damaged caused by loading the module on an unsupported machine.

Here is where you need the “ectype” from the supported laptop list described above (the number in the column next to the laptop model – 12 in my case)

when you load the module, you will need to specify the ectype as a module option:

```

$ sudo depmod -a
$ sudo modprobe omnibook ectype=12

```

You should now have a list of files something like this in /proc/omnibook
blank
bluetooth
display
dmi
hotkeys
lcd
temperature
touchpad
version
wifi

You can make the module start on boot:

make a file called omnibook.modprobe in /etc/modprobe.d/ and place the module options in it:

```

options omnibook ectype=12 userset=1

```

append “omnibook” to /etc/modules to load it at boot:

```

$ sudo su
# echo “omnibook” > /etc/modules

```

You can also run this command to get a list of module options:

```

$ modinfo omnibook

```

then you can disable support for various elements completely. For instance, using bluetooth=0 as a module option will prevent the bluetooth file from showing up in /proc/omnibook and thus prevent you from modifying it.

see [http://omnibook.sourceforge.net]("http://omnibook.sourceforge.net") for full documentation to discover what else you can do with this utility.

EDIT: See post #3 below for my issues with omnibook.
EDIT (13-12-2007): Update the URL to the SVN repository (It changed, and the one on the website is also incorrect....).

---

### Post by zasf on 2006-12-12
It is very useful and I quote every single word with a few exceptions:

[LIST]
[*] I did not use svn trunk source, but I have a different laptop (M40-281, still with phonenix BIOS) and not tested the bluetooth functionality
[*] in my opinion, the flickering/garbled X session is some kind of compatibility problem but not with omnibook module, I always had that (every fourth/fifth boot) more frequently without the fglrx driver
[/LIST]

I think we should try to get more attention on the omnibook module wich is very precious for owners of laptops with phoenix BIOS, by the way, do you know how to bind commands to FN keys?

EDIT: flickering was due to ati open source driver, this is now fixed with gutsy. It was a long standing bug with ati open source driver which has been only recently fixed.

---

### Post by Azriphale on 2006-12-12
I guess this could be a followup post after testing some of the features. I will contact the author of the omnibook module (probably only next month, I am going away tomorrow, out of range of cheap internet, only with GPRS. Hence the need for bluetooth) to see if we can get some of these fixed.  Some may only be a problem on my yet unsupported machine.

The Fn keys (/proc/omnibook/hotkeys) do not do anything for me, I have everything enabled, which for my machine seems to only be Fn keys and multimedia keys, but I get no scancodes when testing the keys, so I think it is not working. Looking at the homepage, the author does list the scancodes the keys generate, so I thought you would use them just as creating any other shortcut (for instance, through "System->Preferences->Keyboard Shortcuts" in Gnome, or in kcontrol somewhere-i forget-with KDE). Maybe I am mistaken and its more manual than that, but xev does not pick up the scancodes at all. Probably my machine being unsupported.

/proc/omnibook/temperature seems to me to be ridiculously hot, but it is consistent, so I guess it could be right, because its not like cooling is running constantly.

I have not tested /proc/omnibook/display . I may at some point, but I really don't feel like disconnecting one of my monitors from my desktop now. Maybe I'll test it with a TV sometime.

/proc/omnibook/lcd (to control LCD brightness) works perfectly. But so do Fn+F6 and Fn+F7 out of the box, so I don't use that.

/proc/omnibook/touchpad works to enable and disable the touchpad, but again, so does Fn+F9 out of the box.

That just leaves bluetooth and wifi on my system. Wifi will enable and disable properly, but it seem that once i have loaded the omnibook module, I cannot disable the bluetooth radio again, so I have removed it from the modules that load on start.

about the garbled X at startup, I thought it was probably fglrx and Edgy, but My first restart after installing fglrx was also after omnibook. It also prevents me from reaching the Ctrl+Alt+F1 through Ctrl+Alt+F6 cirtual consoles, which is what really bothers me. I was actually just about to roll back to dapper because of this. By roll back I mean reinstall completely. I suppose I should stick it out for the holiday, while I can't download any more packages. Do you have problems with

---

### Post by zasf on 2006-12-12
here is what I get

```
root@burnt:~# dmesg | grep omnibook
[ 1851.498000] omnibook: Driver version 2.20060921.
[ 1851.498000] omnibook: Toshiba Satellite M40 detected.
[ 1851.501000] omnibook: Enabling all hotkeys.
[ 1851.507000] omnibook: Enabled features: bluetooth display hotkeys version dmi lcd wifi.
```

[SIZE="3"]**bluetooth**[/SIZE]

if enabled in windows, then works pretty well

```
matteo@burnt:~$ sudo hcitool dev
Password:
Devices:
        hci0    aa:bb:cc:dd:ee:ff
matteo@burnt:~$ sudo hcitool scan
Scanning ...
        11:22:33:44:55:66       Shiny dog

```

omnibook lets me shotdown it but then it doesn't wake up anymore

```
root@burnt:~# echo 0 > /proc/omnibook/bluetooth 
root@burnt:~# echo 1 > /proc/omnibook/bluetooth 
root@burnt:~# cat /proc/omnibook/bluetooth 
Bluetooth adapter is present and disabled.

```

[SIZE="3"]**display**[/SIZE]

```
root@burnt:~# cat /proc/omnibook/display 
Internal LCD: port enabled
External VGA: port disabled
External TV-OUT: port disabled

```

I don't have the hardware to test it with right now

**[SIZE="3"]hotkeys[/SIZE]**

```
root@burnt:~# cat /proc/omnibook/hotkeys 
Fn hotkeys are enabled.
Stick key is disabled.
Press Fn twice to lock is disabled.
Dock events are enabled.
Fn + F5 hotkey is enabled.

```

it seems like working, but xev doesn't catch any..

[SIZE="3"]**dmi**[/SIZE]

root@burnt:~# cat /proc/omnibook/dmi 
BIOS Vendor:   TOSHIBA
BIOS Version:  Version 1.10
BIOS Release:  09/26/2005
System Vendor: TOSHIBA
Product Name:  Satellite M40
Version:       PSM42E-01E00MIT
Serial Number: X5130222Q
Board Vendor:  TOSHIBA
Board Name:    Version A0

[SIZE="3"]**lcd**[/SIZE]

works very well

```
root@burnt:~# echo 1 > /proc/omnibook/lcd 
root@burnt:~# echo 7 > /proc/omnibook/lcd 

```

but I would love to bind it to Fn keys, since they do not work

[SIZE="3"]**wifi**[/SIZE]

works

```
root@burnt:~# cat /proc/omnibook/wifi 
Wifi adapter is present and disabled.
Wifi Kill switch is on.
root@burnt:~# echo 1 > /proc/omnibook/wifi 
root@burnt:~# echo 1 > /proc/omnibook/wifi 
root@burnt:~# cat /proc/omnibook/wifi 
Wifi adapter is present and enabled.
Wifi Kill switch is on.
root@burnt:~# ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=255 time=20.4 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=255 time=272 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=255 time=3.22 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 3.223/98.567/272.054/122.874 ms
root@burnt:~# echo 1 > /proc/omnibook/bluetooth 
root@burnt:~# cat /proc/omnibook/bluetooth 
Bluetooth adapter is present and disabled.
```

I think I should definitely try the svn version.

About the garbled thing, I would start another thread because in my opinion it is a different topic. I can tell you that I always had it, since breezy when I didn't know about omnibook. If it happens at after boot, you can ctrl+alt+f1 - ctrl+alt+f7 as many times as you need to see X properly.

---

### Post by Azriphale on 2006-12-12
I did mention that the latest source package did not work for me. I suppose I should have given the specifics. It would allow me to enable bluetooth, but that would disable wifi, and I would not be able to reverse it (i.e. disable bluetooth and enable wifi). Perhaps your issue with bluetooth is related and the svn trunk version fixes it was well.

As for hotkeys, we need to contact the author regarding this as I am also having no luck. I get no scancodes in xev. I will not be able to do this for about a month, as I am about to go away, and don't have time to do so now. If anybody else does before I return, plese post your results here!

I really do think the svn version should fix your problems. I hope it does.

---

### Post by vitorsouza on 2006-12-15
I have a Toshiba Satellite M45 and omnibook works for me sort of like it's working for you guys, partially.

```
vitor@seattle:~$ cat /proc/omnibook/dmi
BIOS Vendor:   TOSHIBA
BIOS Version:  Version 1.00
BIOS Release:  08/21/2005
System Vendor: TOSHIBA
Product Name:  Satellite M45
Version:       PSM42U-016006
Serial Number: 95065131Q
Board Vendor:  TOSHIBA
Board Name:    Version A0
```

```
vitor@seattle:~$ ls /proc/omnibook/
bluetooth  display  dmi  hotkeys  lcd  version  wifi
```

```
vitor@seattle:~$ cat /proc/omnibook/bluetooth
Bluetooth adapter is absent.
```

```
vitor@seattle:~$ cat /proc/omnibook/display
Internal LCD: port enabled
External VGA: port disabled
External TV-OUT: port disabled
```

```
vitor@seattle:~$ cat /proc/omnibook/hotkeys
Fn hotkeys are enabled.
Stick key is disabled.
Press Fn twice to lock is disabled.
Dock events are enabled.
Fn + F5 hotkey is enabled.
```

```
vitor@seattle:~$ cat /proc/omnibook/lcd
LCD brightness:  6 (max value: 7)
```

```
vitor@seattle:~$ cat /proc/omnibook/wifi
Wifi adapter is present and disabled.
Wifi Kill switch is on.

```

I wish the hotkeys would work...

Vitor Souza

---

### Post by zasf on 2007-01-02
Hi all,

I suggest to try gnome-power-manager 2.17.4 wich can be found in feisty repository. You simply need to enable feisty repository, update apt-get and then 'apt-get install gnome-power-manager'. It will upgrade Hal so that in combination with omnibook module, you will have the possibility to set different brightness settings depending on AC/battery or to increase/decrease brightness with brightness applet!!

I also checked the cvs source and compiled it, in order to have 2.17.9 version wich is even better (see pics)!!

[IMG]http://kate.homeunix.net/~matteo/gpm_2.18/OnAcPower.png[/IMG]

[IMG]http://kate.homeunix.net/~matteo/gpm_2.18/OnBattery.png[/IMG]

[IMG]http://kate.homeunix.net/~matteo/gpm_2.18/General.png[/IMG]

---

### Post by Neo4 on 2007-02-13
can we change the fan speed too? i Think i'm getting low fps under UT 2004 because of the eat!

---

### Post by Azriphale on 2007-02-14
> **Neo4 said:**
> can we change the fan speed too? i Think i'm getting low fps under UT 2004 because of the eat!

See the "Fan Status and Control" section at this URL:

[http://omnibook.sourceforge.net/doku.php?id=readme#features_list]("http://omnibook.sourceforge.net/doku.php?id=readme#features_list")

If the omnibook module supports the fan control on your laptop, then you should be able to follow those instructions. I can't help you any further as the module does not support that on my machine, as far as I can remember (Tosh Satellite Pro M70)...

---

### Post by Neo4 on 2007-02-14
so i guess my wont work too, its an toshiba M70-164!


so games in linux forget it! or just can't be run good with wine or problems with the eating!

---

### Post by Reducer on 2007-03-04
Great thread!  Got my Bluetooth working on a Toshiba Satellite A130.  Only problem is my mouse won't connect on start up I always have to manually type

```
sudo hidd --connect xx:xx:xx:xx:xx:xx
```

Here's my /etc/default/bluetooth.  Any ideas on how to have this auto connect?  Works fine in Vista. :(

```
# Defaults for bluez-utils

# This file supersedes /etc/default/bluez-pan.  If
# that exists on your system, you should use this
# file instead and remove the old one.  Until you
# do so, the contents of this file will be ignored.

# start bluetooth on boot?
# compatibility note: If this variable is not found bluetooth will
# start
BLUETOOTH_ENABLED=1

############ HIDD
#
# To have Bluetooth mouse and keyboard support, get the
# Linux 2.6.6 patch or better from bluez.org, and set 
# HIDD_ENABLED to 1.
HIDD_ENABLED=0
HIDD_OPTIONS="--connect xx:xx:xx:xx:xx:xx --server"
# to make hidd always use a particular interface, use something
# like this, substituting the bdaddr of the interface:
# HIDD_OPTIONS="-i AA:BB:CC:DD:EE:FF --server"
#
# remove '--master' if you're having trouble working with Ericsson
# T630 phones with hidd operational at the same time.

############ COMPATIBILITY WITH OLD BLUEZ-PAN
# Compatibility: if old PAN config exists, use it
# rather than this file.
if test -f /etc/default/bluez-pan; then
    . /etc/default/bluez-pan
    return
fi
############

############ DUND
#
# Run dund -- this allows ppp logins. 1 for enabled, 0 for disabled.
DUND_ENABLED=0

# Arguments to dund: defaults to acting as a server
DUND_OPTIONS="--listen --persist"

# Run dund --help to see the full array of options.
# Here are some examples:
#
# Connect to any nearby host offering access
# DUND_OPTIONS="--search"
#
# Connect to host 00:11:22:33:44:55
# DUND_OPTIONS="--connect 00:11:22:33:44:55"
#
# Listen on channel 3
# DUND_OPTIONS="--listen --channel 3"

# Special consideration is needed for certain devices. Microsoft
# users see the --msdun option.  Ericsson P800 users will need to
# listen on channel 3 and also run 'sdptool add --channel=3 SP'

############ PAND
#
# Run pand -- ethernet: creates new network interfaces bnep<N>
# that can be configured in /etc/network/interfaces
# set to 1 for enabled, 0 for disabled
PAND_ENABLED=0

# Arguments to pand
# Read the PAN howto for ways to set this up
# http://bluez.sourceforge.net/contrib/HOWTO-PAN
PAND_OPTIONS=""

# example pand lines
#
# Act as the controller of an ad-hoc network
# PAND_OPTIONS="--listen --role GN"
#
# Act as a network access point: routes to other networks
# PAND_OPTIONS="--listen --role NAP"
#
# Act as a client of an ad-hoc controller with number 00:11:22:33:44:55
# PAND_OPTIONS="--role PANU --connect 00:11:22:33:44:55"
#
# Connect to any nearby network controller (access point or ad-hoc)
# PAND_OPTIONS="--role PANU --search"

############ SDPTOOL
# this variable controls the options passed to sdptool on boot, useful if you
# need to setup sdpd on boot.
# options are ;-separated, i.e. for every ; an sdptool instance will be
# launched
#
# examples:
# SDPTOOL_OPTIONS="add --channel=3 SP" # ericsson P800 serial profile
# SDPTOOL_OPTIONS="add --channel=8 OPUSH ; add --channel=9 FTRN" # motorola
#                                             # object push and file transfer
SDPTOOL_OPTIONS=""
```

Thanks

---

### Post by zasf on 2007-03-05
> **Reducer said:**
> Only problem is my mouse won't connect on start up I always have to manually type

```
sudo hidd --connect xx:xx:xx:xx:xx:xx
```

why don't you add it to your /etc/rc.local? It is just as simple as that :)

---

### Post by Reducer on 2007-03-05
That doesn't seem to work either. ;(

Based on the documentation that has got me this far, I should just be able to add it to the /etc/default/bluetooth file, which is what I was hoping to do.

Thanks!

---

### Post by SonicTheHedgehog on 2007-03-12
I get an error when I type 'make'.

```
nticompass@nticompass-laptop:~/omnibook/trunk$ make
make -C /lib/modules/2.6.17-11-386/build SUBDIRS=/home/nticompass/omnibook/trunk modules
make[1]: Entering directory `/lib/modules/2.6.17-11-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.17-11-386/build'
make: *** [omnibook.ko] Error 2

```

What's wrong?

---

### Post by Azriphale on 2007-05-21
Do you have the Linux kernel source installed?

If not, you need to:
```

$ sudo apt-get install linux-source

```

---

### Post by soro2005 on 2007-05-31
Just thought I should say thank you! Had my fan clogged recently which led to the system overheating which led, it seems, in the last instance to the harddrive dying... So I really want to have a watchful eye on my temps, and thanks to your instructions, I now will. :-)

My specs: Toshiba Satellite M35x-S349, and I got
```
xxx:~$ ls /proc/omnibook/
blank  bluetooth  display  dmi  lcd  temperature  throttling  version  wifi
```
Excellent, thanks!

---

### Post by pingpongboss on 2007-06-17
WOW! thank you so much! I've been looking for ways to change thte brightness on my Toshiba laptop's monitor for months! All i needed to do was follow your directions and everything is working fine now. thank you!

now if only Fn hotkeys would work.. :P

---

### Post by Azriphale on 2007-06-17
Unfortunately it seems that not all functionality of the module works on all machines. The function keys, and media softkeys do not work for me either.

I'm glad it was able to help you, and people are still finding it useful.

---

### Post by Pronco on 2007-07-06
After executing:

```
sudo modprobe omnibook ectype=12
```

It has no effects as I'm still have the both files dmi and version and there's no new files created.

Besides the output of the following command:

```
dmesg | grep ominbook

[17185883.804000] omnibook: Driver version 2.20070211-trunk.
[17185883.804000] omnibook: Unknown model.
[17185883.808000] omnibook: Enabled features: version dmi.
```

Please attend to this issue 

Thank you

---

### Post by Azriphale on 2007-07-06
As I mentioned in the first post, check the [supported laptops list](http://omnibook.sourceforge.net/doku.php?id=laptops&DokuWiki=0464a1502966a79e4adf2e1b0b19abe0). If you do not get anything from using the module without specifying an Ectype, choose the Ectype corresponding to your model from that list. If you still have problems (and are certain that you have a model with a Phoenix BIOS), please contact the author with your problems.

The homepage of the module is [http://omnibook.sourceforge.net/](http://omnibook.sourceforge.net/)
You can find the author's contact details there.

You can also see what model the omnibook module reads your computer as by using this command:
```

$ cat dmi

```

---

### Post by Pronco on 2007-07-07
It detects:

```
BIOS Vendor:   Phoenix Technologies LTD
BIOS Version:  1.70   
BIOS Release:  05/08/2006
System Vendor: TOSHIBA
Product Name:  SATELLITE PRO A100
Version:       PSAACE-001009AR
Serial Number: 66849489G
Board Vendor:  Intel Corporation
Board Name:    Not Applicable

```

Thank you.

---

### Post by Azriphale on 2007-07-07
> SATELLITE PRO A100

There is no Satellite A100 listed in the supported laptop list, and I do not know what the closest model on that list is to yours. I would guess that the Ectype 14 is closest (Satellite A105), from what I know about the Toshiba laptop feature lists, but for all I know the hardware could be completely different. For this model it only fully supports Bluetooth.

From my understanding of the Toshiba models, the xx0 variant (such as your A100) are customisable, and the xx5 (such as the A105) have a few submodels, each corresponding to a particular common customisation. Meaning that the A100 and A105 are the same underlying hardware (BIOS and motherboard). But I could be completely wrong!

A warning on the omnibook website: It can be dangerous to use this with an unsupported machine by forcing a particular ectype.

If you want to try, you may want to find out what you can about which model is closest to yours on that list first. Or you may not.

---

### Post by Mavrik on 2007-07-08
Note: Toshiba Satellite A105 and A100 are identical models (A100 is European name).

Also, I've noticed... the newest "Vista" BIOS upgrade fixes the multimedia and Fn keys, so now they work perfectly in Ubuntu too (at least the multimeda and screen brightness keys) without additional software (I've got a Satellite A100).

---

### Post by Azriphale on 2007-07-08
Your news about the Vista BIOS upgrade is most welcome, thank you. I'll see if there is one for my Satellite Pro M70. I have been irritated by the lack of MM keys since i got the machine.

And the Ectype 14 should work for you, then.

---

### Post by Mavrik on 2007-07-09
Omnibook module with ectpe 14 works to some extent (it only recognises LCD brigtness). If I try to echo some brightness level to /proc/omnibook/lcd, nothing changes until I press the Fn brightness key. After I press the key, the brightness suddenly jumps to the set level. 

I can't test the module for bluetooth though, since my model doesn't have BT built in. At least the MM keys and brightness control are working, so I can achieve approximately the same battery life than on Windows.

---

### Post by Pronco on 2007-07-09
WoW, it works for me

The omnibook module with ectype 14 parameter is working with TOSHIBA A100 model 

```

bluetooth  dmi  lcd  version < It detects the appropriate bluetooth control 

```

Bluetooth is present and enabled
LCD brightness:  7 (max value: 7)

Thank you

---

### Post by psycho_NIX on 2007-07-23
> **Pronco said:**
> WoW, it works for me

The omnibook module with ectype 14 parameter is working with TOSHIBA A100 model 

```

bluetooth  dmi  lcd  version < It detects the appropriate bluetooth control 

```

Bluetooth is present and enabled
LCD brightness:  7 (max value: 7)

Thank you

Hi i got Toshiba A100-405 PSAA9E, after fresh install of Ubuntu 7.04 my WiFi worked out of box, i could adjust screen brightness by using Fn key. But bluetooth doesn't want to work.
I have tryed omnibook, but it didn't worked for me either. could you plz give me step by step of your howto, since you have also A100.
thnx

---

### Post by Sollos on 2007-08-09
Hi! I've just got a Satellite M205 and it is not working perfectly. After search on the Net, i found many suggestion to use omnibook but it seems to me, after do a "make install" with the source cod, nothing happen. I can't found the folder named "omnibook" in my /proc folder. 
My laptop is very hot now because I can't get control of the fan. Please give me some suggestion! Thanks in advance!!!

---

### Post by Pronco on 2007-11-12
> **psycho_NIX said:**
> Hi i got Toshiba A100-405 PSAA9E, after fresh install of Ubuntu 7.04 my WiFi worked out of box, i could adjust screen brightness by using Fn key. But bluetooth doesn't want to work.
I have tryed omnibook, but it didn't worked for me either. could you plz give me step by step of your howto, since you have also A100.
thnx

You've to specify the Ectype paramter corresponding to your Ectype model 

Try Ectype 14  works for my A100 lappy as I've mentioned above

```
sudo modprobe omnibook ectype=14
```

Perhaps it works 

Thank you!
Pronco

---

### Post by sasanmaleki on 2008-01-07
This post was of a very great help!!! Thank you!

---

### Post by darkpact on 2008-01-29
will this support toshiba models later than July 07? I'm starting to give up on the possibility of built in bluetooth.

---

### Post by pikkio on 2008-02-16
Used this howto on my Satellite A100-097, now Bluetooth works perfectly! Thank you very much!

Still not figured out how to get Fn keys working, though.

---

### Post by ayampanggang on 2008-02-17
im with satellite m50.

everything is detected properly (though my model's not on the list) but strangely, even after enabling bluetooth, hcitool dev doesn't list any bluetooth device

---

### Post by dolny on 2008-03-09
Did anyone manage to get it working for Toshiba P30?

```
[root@endora omnibook]# cat /proc/omnibook/dmi
BIOS Vendor:   TOSHIBA
BIOS Version:  V1.30
BIOS Release:  10/04/2004
System Vendor: TOSHIBA
Product Name:  Satellite P30
Version:       PSP30E-0130088K
Serial Number: Y4575749K
Board Vendor:  TOSHIBA
Board Name:    Null

```

but only two files:

dmi and version

in the /proc/omnibook/ 

dir :(

---

### Post by fb2007 on 2008-04-08
Can you help me also?

I did as you said, downloaded omnibook from trun, make and make install was successful also make load. but when i try to ls in /prc/omnibook directory is empty. 

What could I be doing wrong?


Thanks 




PS. I have toshiba A200 laptop with phoenix bios!

---

### Post by winston_nolan on 2008-05-17
no fix for this yet?
I also used the omnibook module without any success. It's been a year with this problem and it's not cool..i can see windows users laughing at us poor ubuntu users...

any one with any other ideas?

wins

PS. I also have toshiba A200-14e laptop with phoenix bios!

---

### Post by vasilis34 on 2008-05-17
You might have already tried this but just in case. For me in a toshiba A200-19L laptop it's working, using the second method of building the module and loading it with ectype = 12. The strange thing is that if I load the module with the wifi/bluetooth switch off, then the bluetooth isn't working when switced back to on. Except from this I have to remove it with rmmod, turn the switch to on and then load it again with ectype=12.
I hope this might help. Good luck anyway!

---

### Post by marcon00 on 2008-06-02
```
BIOS Vendor:   Phoenix Technologies LTD
BIOS Version:  1.50    
BIOS Release:  11/06/2007
System Vendor: TOSHIBA
Product Name:  Qosmio F40
Version:       PQF46U-01F006
Serial Number: Y7150263Q
Board Vendor:  Intel Corporation
Board Name:    Not Applicable

```


Not working wit 12,13,14. I even tried all the numers for fun !

still getting only two files . I guess there is no support what so ever yet.

---

### Post by Azriphale on 2008-06-02
Unfortunately, you will find that your Qosmio F40 is not listed on the supported laptops page on the original website:

[http://omnibook.sourceforge.net/doku.php?id=laptops](http://omnibook.sourceforge.net/doku.php?id=laptops)

Sorry, I'm unable to help you further. If you want to help development of the module, see [http://omnibook.sourceforge.net/doku.php?id=readme#add_support_for_new_laptops](http://omnibook.sourceforge.net/doku.php?id=readme#add_support_for_new_laptops)

You can send information about your notebook to the author, and he might be able to include support in the future, or if you are up to it, you can have a look yourself.

---

### Post by kriebel on 2008-06-04
One little trick for the Toshiba a200-237 with 8.04 (thanks to Johan Vromans) See also [http://www.vromans.org/johan/articles/Toshiba-Satellite-A200-237/fedora9/omnibook.html](http://www.vromans.org/johan/articles/Toshiba-Satellite-A200-237/fedora9/omnibook.html)

#insmod omnibook.ko userset=1 ectype=12


My bluetooth is sending files to my Toshiba at this moment :)

Hope this helps!

Kriebel

---

### Post by marcon00 on 2008-06-15
Would you believe if i tell you thata after Kernel upgrade to *19 version from ubuntu servers it worked for a while till i rebooted ? :S the icon popped up,but i didnt have time to try it, i figured it would be a permenant thing .. n now its gone .

---

### Post by paste on 2008-09-15
Thanks for the tip.  I used to manually hack the toshiba_apci.c driver file in the kernel every time I wanted to get Bluetooth working for a new version of the kernel.  I have a Toshiba Portégé m400 tablet:
```
$ cat /proc/omnibook/dmi 
BIOS Vendor:   TOSHIBA
BIOS Version:  Version 3.60
BIOS Release:  06/26/2007
System Vendor: TOSHIBA
Product Name:  PORTEGE M400
Version:       Version 1.0
Serial Number: 46069503H
Board Vendor:  TOSHIBA
Board Name:    Version A0
```
Also, as a free tip, if you want a quick way to set default values at system start time (like turning on Bluetooth without having to type commands into a terminal) you can use [upstart]("http://upstart.ubuntu.com/") (if you have Feisty or newer, then upstart is already installed).  Just make a file called /etc/event.d/omnibook and copy and paste into it the following:
```
#/etc/event.d/omnibook
# Start bluetooth, wireless, and whatever else you want at startup!
start on runlevel 2

script
    echo 1 > /proc/omnibook/bluetooth
    echo 1 > /proc/omnibook/wifi
    # put whatever other commands you want to issue in here
end script
```
You can tell upstart to start your new bluetooth job immediately with the command ```
$ sudo start omnibook
``` or you can just wait until the next time you reboot.  I searched high and low for events that upstard can capture immediately on module loads, but to no avail.  Anyway, enjoy!

---

### Post by Rianthas on 2008-09-19
Finally have my brightness hotkeys working, but only my brightness keys working. Lucky for me, it's been my biggest priority. Trying to get my Fn + TV Out hotkey to work is next.

Anyway, trying to modprobe toshiba or toshiba_acpi gives back an error so I haven't been able to get fnfx to work.

To add on to this thread, A305D owners need to modprobe omnibook ectype=13 with whatever is in the svn repo. modprobe omnibook doesn't enable anything, and using ectype=12 instead of 13 will lock up your box, forcing you to shutdown with a hard reset.

Here is /proc/omnibook/dmi

```
BIOS Vendor:   Insyde Corp.
BIOS Version:  1.50   
BIOS Release:  06/09/2008
System Vendor: TOSHIBA
Product Name:  Satellite A305D
Version:       PSAH0U-00Q009
Serial Number: 78401777Q
Board Vendor:  ATI Corp.
Board Name:    Base Board Version
```

---

### Post by dwpa on 2008-10-05
Hi there.  I'm having trouble with my Satellite X205-s9810.  I'm not sure if it is supported or not (only have dmi and version in /proc/omnibook) and I'm unable to open the omnibook.sourceforge.net webpages.  I get a wiki setup error so I don't know if they are having some downtime on their server or what, but I really need to know what a close match would be to my model.  

```
BIOS Vendor:   TOSHIBA
BIOS Version:  V2.30
BIOS Release:  02/12/2008
System Vendor: TOSHIBA
Product Name:  Satellite X205
Version:       PSPB9U-05C02P
Serial Number: 58245371K
Board Vendor:  TOSHIBA
Board Name:    1.00
```

Any help you can give me would be greatly appreciated.  

--dwpa

---

### Post by Iili_ya_ili on 2008-10-17
1

---

### Post by Iili_ya_ili on 2008-10-17
> **dwpa said:**
> Hi there.  I'm having trouble with my Satellite X205-s9810.  I'm not sure if it is supported or not (only have dmi and version in /proc/omnibook) and I'm unable to open the omnibook.sourceforge.net webpages.  I get a wiki setup error so I don't know if they are having some downtime on their server or what, but I really need to know what a close match would be to my model.  

```
BIOS Vendor:   TOSHIBA
BIOS Version:  V2.30
BIOS Release:  02/12/2008
System Vendor: TOSHIBA
Product Name:  Satellite X205
Version:       PSPB9U-05C02P
Serial Number: 58245371K
Board Vendor:  TOSHIBA
Board Name:    1.00
```

Any help you can give me would be greatly appreciated.  

--dwpa

Try this links: (for internet browser).
[http://sourceforge.net/project/showfiles.php?group_id=174260](http://sourceforge.net/project/showfiles.php?group_id=174260)
[http://sourceforge.net/projects/omnibook/](http://sourceforge.net/projects/omnibook/)

And please, help me. I have problems with installing this module on ubuntu (kernel 2.6...). During compilation errors appear and the compillation stops whithout success. Could yoou help me? Or anybody does?

---

### Post by LuisC-SM on 2009-01-10
> **kriebel said:**
> One little trick for the Toshiba a200-237 with 8.04 (thanks to Johan Vromans) See also [http://www.vromans.org/johan/articles/Toshiba-Satellite-A200-237/fedora9/omnibook.html](http://www.vromans.org/johan/articles/Toshiba-Satellite-A200-237/fedora9/omnibook.html)

#insmod omnibook.ko userset=1 ectype=12


My bluetooth is sending files to my Toshiba at this moment :)

Hope this helps!

Kriebel
Hi. I want to thank you for this info.

On openSuSE 11 it works jast as you have said. I'll tryit later on OS11.1 as well)

my dmi file:
> BIOS Vendor:   TOSHIBA
BIOS Version:  V4.50  
BIOS Release:  09/30/20082
System Vendor: TOSHIBA
Product Name:  Satellite P105
Version:       PSPA6U-006005
Serial Number: 36078015W                       
Board Vendor:  TOSHIBA
Board Name:    Not Applicable 

My lsusb:
> Bus 004 Device 002: ID 0930:0508 Toshiba Corp. **[COLOR="Red"]Integrated Bluetooth[/COLOR]** HCI
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04fc:0538 Sunplus Technology Co., Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Thanks a lot and Kind Regards

Luis

PS. Thnxs so much to the original poster for this approach.

---

### Post by Forever unknowN on 2009-01-11
Still got the problem on A200-1AE:

```
# cat /proc/omnibook/dmi
BIOS Vendor:   TOSHIBA
BIOS Version:  V1.80
BIOS Release:  08/21/2007
System Vendor: TOSHIBA
Product Name:  Satellite A200
Version:       PSAECE-01Q00DPL
Serial Number: 47340777K
Board Vendor:  TOSHIBA
Board Name:    1.00
``````
# ls /proc/omnibook
dmi  version
```Don't mind the other modules, just need bluetooth running. Anyone can help? I did step-by-step everything written in here, tried different ectypes and just nothing happens...

---

### Post by LuisC-SM on 2009-01-11
> **Forever unknowN said:**
> Still got the problem on A200-1AE:

```
# cat /proc/omnibook/dmi
BIOS Vendor:   TOSHIBA
BIOS Version:  V1.80
BIOS Release:  08/21/2007
System Vendor: TOSHIBA
Product Name:  Satellite A200
Version:       PSAECE-01Q00DPL
Serial Number: 47340777K
Board Vendor:  TOSHIBA
Board Name:    1.00
``````
# ls /proc/omnibook
dmi  version
```Don't mind the other modules, just need bluetooth running. Anyone can help? I did step-by-step everything written in here, tried different ectypes and just nothing happens...

Have you tried other "ectypes"... (10 to 15) there is also 12-modified.
Most probabily some value will help you. 
Play a little bit with them.
Good luck

Luis

---

### Post by Forever unknowN on 2009-01-11
I tried every ectype :(
If I didn't, I would't ask for help...

Everything works on my computer, except for bluetooth and card reader (AFAIK this card reader won't work under Linux :( )

---

### Post by LuisC-SM on 2009-01-11
> **Forever unknowN said:**
> I tried every ectype :(
If I didn't, I would't ask for help...

Everything works on my computer, except for bluetooth and card reader (AFAIK this card reader won't work under Linux :( )

Sorry to hear that. (My card reader worked just OOTB in OS11 and 11.1)

One question ... (I've not read the whole thread BTW). Do you have a Toshiba BIOS or a Phoenx BIOS..

In case yuu have a toshiba BIOS  then you are in the wrong place' Toshiba BIOS uses the toshiba_acpi.c patched module. I saw some model like yours someplace using the module I 've entioned.

If you have the Phoeix BIOS and you would like to try a different way take a look to [this link]("http://mintguides.blogspot.com/2008/08/report-this-post-reply-with-quote-how.html") and [this one]("http://www.itwriting.com/blog/333-fixing-bluetooth-on-a-toshiba-with-ubuntu.html#comment-35858") which I believe this could save you a lott of time. These could also work with toshiba bios but I can not guaranty they will
At least one of them will be usefull and they are different approaches.

These links are also useful
[http://www.sfires.net/toshiba/](http://www.sfires.net/toshiba/)
[http://schwieters.org/toshset/](http://schwieters.org/toshset/)
this link is the one that brought me here...:)
[http://www.itopen.it/2007/11/22/ubuntu-linux-toshiba-satellite-u300/](http://www.itopen.it/2007/11/22/ubuntu-linux-toshiba-satellite-u300/)
[Jonathan McDougle's]("http://lkml.org/lkml/2007/10/21/141") patch :D
openSuSE forum
[http://forums.opensuse.org/hardware/laptop/404596-problem-reading-sd-cards-bluetooth-not-detected.html](http://forums.opensuse.org/hardware/laptop/404596-problem-reading-sd-cards-bluetooth-not-detected.html)
and this one also is very interesting
[http://the.taoofmac.com/space/HOWTO/Enable%20Toshiba%20Bluetooth%20Support%20In%20Fedora%20Core%204](http://the.taoofmac.com/space/HOWTO/Enable%20Toshiba%20Bluetooth%20Support%20In%20Fedora%20Core%204)

I'm sorry not to be of anymore help

Kind Regards

Luis

PS. If ubuntu does not work 100% on your laptop, try another distro. I have Ubuntu installed in 3 machines, I also have Mandriva and openSuSE but for my laptop (specifically for this model p105sp921) I use openSuSE
. Is the nly one that has given me less problems, and it works just perfect.

---

### Post by Forever unknowN on 2009-01-12
Thanks a lot for your time. I've got Phoenix BIOS, as is standard in (most) A200.

But something weird happened - after about 4 reboots bluetooth started working by itself... Don't know, why not at the first time, but now it works fine (ectype=12). Maybe just my computer is moody? ;p

---

### Post by LuisC-SM on 2009-01-12
> **Forever unknowN said:**
> Thanks a lot for your time. I've got Phoenix BIOS, as is standard in (most) A200.

But something weird happened - after about 4 reboots bluetooth started working by itself... Don't know, why not at the first time, but now it works fine (ectype=12). Maybe just my computer is moody? ;p

Excellent :guitar:

Well. I don't really know if 4 reboots helped any.. I think there is a battery problem with some toshibas. If you turn it off and wait for about 5 minuts sometimes better than rebooting. Another one is to take off the batery and put it back again... That solved me a lot of problems with other toshibas I've had in the past.

The good thing is that it's working and I'm glad it is. You only waited for some days... I had to wait for 2 years to have BT... LOL
Kind Regards

Luis

---

### Post by Forever unknowN on 2009-01-12
I've been waiting for about 1,5 year but attended to that problem only once a 3-4 months time ;p
And I'm really glad it finally works with Phoenix BIOS because many manufacturers use it recently and many people had that common problem ;)

BTW, I've the battery removed since I usually use the computer at home...

---

### Post by mahy on 2009-02-17
Hello,

i have a Toshiba Satellite A300 laptop, and this is the output of "cat /proc/omnibook/dmi"

```
BIOS Vendor:   INSYDE
BIOS Version:  1.50
BIOS Release:  06/27/2008
System Vendor: TOSHIBA
Product Name:  Satellite A300
Version:       PSAG0E-02J027CZ
Serial Number: 78100841Q
Board Vendor:  Intel Corp.
Board Name:    Base Board Version

```

Even with ectype=12, omnibook module doesn't work... I see that such outputs posted previously look considerably different from my output. Am i on a completely wrong page? TIA for any help

---

### Post by LuisC-SM on 2009-02-17
> **mahy said:**
> Hello,

i have a Toshiba Satellite A300 laptop, and this is the output of "cat /proc/omnibook/dmi"

```
BIOS Vendor:   INSYDE
BIOS Version:  1.50
BIOS Release:  06/27/2008
System Vendor: TOSHIBA
Product Name:  Satellite A300
Version:       PSAG0E-02J027CZ
Serial Number: 78100841Q
Board Vendor:  Intel Corp.
Board Name:    Base Board Version

```

Even with ectype=12, omnibook module doesn't work... I see that such outputs posted previously look considerably different from my output. Am i on a completely wrong page? TIA for any help

Yeah... the problem is your BIOS...so most probabily this will not work for you.

There is another thread about toshiba and bluetooth compiling the bluetooth module, that might work... who knws....

Good luck

Luis

P.S. This thread is for Phoenix BIOSes

---

### Post by captainiceman on 2009-02-24
Hi. I'm wondering if anyone else has tried this install and did NOT get the /proc/omnibook directory to create? This is my first install of ANYTHING via terminal, so that may have something to do with it...

Anyway, I followed the steps:
- Downloaded necessary packages
- Downloaded the Omnibook module
- Followed up to sudo make load with no error text anywhere

No directory proc/omnibook exists.

I read through the rest of the thread and people with the Satellite A100/105 seem to say its working for them... 

I'd like to run Ubuntu full time but power supply/brightness is an issue for me for taking my laptop to class for a few hours with no plug.

My model does not have bluetooth, runs XP on the other boot. Should I update the BIOS?


-cap'n

---

### Post by captainiceman on 2009-02-24
Well it was a rookie mistake... still unfamiliar with the file system in linux, so didn't know terminal wasn't at the root directory.

dmi shows this:
BIOS Vendor:   Phoenix Technologies LTD
BIOS Version:  1.80   
BIOS Release:  06/12/2006
System Vendor: TOSHIBA
Product Name:  Satellite A100
Version:       PSAA8C-SK800E
Serial Number: 76061191Q
Board Vendor:  Intel Corporation
Board Name:    Not Applicable

only 'lcd', 'dmi' and 'version' show, and I tried all ectypes. Question still stands--should I update my BIOS (Toshiba's site lists new versions to mine)?

Does it matter what BIOS to get (some are 'Vista' specific)? I run XP on the other boot.

Thanks

cap'n

---

### Post by LuisC-SM on 2009-02-24
> **captainiceman said:**
> .... snipped...

only 'lcd', 'dmi' and 'version' show, and I tried all ectypes. Question still stands--should I update my BIOS (Toshiba's site lists new versions to mine)?

**Does it matter what BIOS to get** (some are 'Vista' specific)? I run XP on the other boot.

Thanks

cap'n

It does matter!!!

Forget about Vista specific changes. Sometimes Intel tells Toshiba to modify their BIOSes and they still write down "Vista specific changes".

I strongly suggest you to upgrade your BIOS to the latest, also to try some booting parameters like acpi_osi=Linux! (This will not hurt you at all)


Good luck

Luis

---

### Post by captainiceman on 2009-02-25
> **LuisC-SM said:**
> It does matter!!!

Forget about Vista specific changes. Sometimes Intel tells Toshiba to modify their BIOSes and they still write down "Vista specific changes".

I strongly suggest you to upgrade your BIOS to the latest, also to try some booting parameters like acpi_osi=Linux! (This will not hurt you at all)


Good luck

Luis

Where would I specify booting parameters?

capn

---

### Post by LuisC-SM on 2009-02-25
> **captainiceman said:**
> Where would I specify booting parameters?

capn

In the boot menu. Is the first screen from Ubuntu when you start your system, just write down the given value and press Enter.

Good luck

Luis

---

### Post by captainiceman on 2009-02-25
> **LuisC-SM said:**
> In the boot menu. Is the first screen from Ubuntu when you start your system, just write down the given value and press Enter.

Good luck

Luis

Thanks for the quick responses, Luis! 

I will try updating the BIOS sometime in the next week and post back.

---

### Post by davidmohammed on 2009-03-07
Has anybody tried this with a Satellite Pro A30?

I've tried ectypes 10 to 15 but still have only the dmi and version files in /proc/omnibook

cat dmi
BIOS Vendor:   TOSHIBA
BIOS Version:  V1.80
BIOS Release:  07/22/2004
System Vendor: TOSHIBA
Product Name:  Satellite A30
Version:       PSA35E-3KK72-EN
Serial Number: X3383029K
Board Vendor:  TOSHIBA
Board Name:    Null

---

### Post by LuisC-SM on 2009-03-07
> **davidmohammed said:**
> Has anybody tried this with a Satellite Pro A30?

I've tried ectypes 10 to 15 but still have only the dmi and version files in /proc/omnibook

cat dmi
BIOS Vendor:   TOSHIBA
BIOS Version:  V1.80
BIOS Release:  07/22/2004
System Vendor: TOSHIBA
Product Name:  Satellite A30
Version:       PSA35E-3KK72-EN
Serial Number: X3383029K
Board Vendor:  TOSHIBA
Board Name:    Null
Hi.

Have you tried [this thread]("http://ubuntuforums.org/showthread.php?t=986075&highlight=toshiba+bluetooth+module")? This is for Phoenix BIOSes and you have a Toshiba one.

Good luck

Luis

---

### Post by davidmohammed on 2009-03-07
> **LuisC-SM said:**
> Hi.

Have you tried [this thread]("http://ubuntuforums.org/showthread.php?t=986075&highlight=toshiba+bluetooth+module")? This is for Phoenix BIOSes and you have a Toshiba one.

Good luck

Luis

Thanks Luis - super speedy reply.


Definitely have a Phoenix Bios - F2'ed into the Bios on boot and it displayed "Phoenix"...

I've cracked this one myself - sort of.  Used ectype=11 or ectype=15

Rookie mistake - when I was trying the 
"sudo depmod-a" followed by "sudo modprobe omnibook ectype=<x>" I forgot to uninstall the omnibook module between tries.

To those rookies outthere - don't forget to "sudo make unload" between each of the commands above.

Also its useful to do a "dmesg | grep omnibook" between each try to see what modules (if any) are loaded.

The side effect of this is that my CD ROM keys have started to work and two of the three hotkeys work - with the exception of the "switch display" hotkey.  That doesn't seem to do anything even if I try using "Keyboard Shortcuts".  Ho hum - one problem down...

---

### Post by LuisC-SM on 2009-03-07
> **davidmohammed said:**
> Thanks Luis - super speedy reply.


Definitely have a Phoenix Bios - F2'ed into the Bios on boot and it displayed "Phoenix"...

-----snipped----.

Yes, you definitely do.... sorry for my mistake  ::oops:

I'm glad you have already fixed it.

Luis

---

### Post by sMash! on 2009-03-15
first, thanks to david for pointing me in the omnibook modules direction!

but i still wonder if i needed this? and being a newbie to linux in general i have no idea what to do...
omnibook apparently 'works' on my machine (the supported list is no longer available i guess, so i cant input an ectype) and these are my results:

root@UBrick:/home/erik# cat /proc/omnibook/dmi
BIOS Vendor:   TOSHIBA
BIOS Version:  V1.30
BIOS Release:  09/10/2004
System Vendor: TOSHIBA
Product Name:  Satellite A75
Version:       PSA70U-0WK00G
Serial Number: 15232261K
Board Vendor:  TOSHIBA
Board Name:    Null
root@UBrick:/home/erik# ls /proc/omnibook
blank  bluetooth  display  dmi  lcd  temperature  throttling  version  wifi
root@UBrick:/home/erik# 

as i said, its there..........just have no idea how to make use of it. other than i can use the terminal to check my cpu temp now with /proc/omnibook/temperature. i think. the goal for me is to be able to display information in applications like Conky.

---

### Post by davidmohammed on 2009-03-16
... strictly speaking this thread is for those who can't use bluetooth...

so braving being flamed - have you tried using sensors_applet and adding the various sensors available (see the following [link]("http://reformedmusings.wordpress.com/2009/01/10/monitor-your-hard-drives-in-ubuntu-810-intrepid/") for an example) to a panel?

---

### Post by sMash! on 2009-03-17
> **davidmohammed said:**
> ... strictly speaking this thread is for those who can't use bluetooth...

so braving being flamed - have you tried using sensors_applet and adding the various sensors available (see the following [link]("http://reformedmusings.wordpress.com/2009/01/10/monitor-your-hard-drives-in-ubuntu-810-intrepid/") for an example) to a panel?

but 'strictly speaking' this was the best post i could find while searching for information on using the omnibook modules to date.

lm-sensors is the root of my problem; the BIOS on my Toshiba A75 says it has acpi support yet neither conky nor the sensors-applet detect any sensors. i'm trying to find a work-around.

as a side note, it seems that either the module is NOT actually working, or i'm not doing something right. everytime i check my temperature with the omni module, the cpu reads 45C. that means, right after boot...after running for an hour....after some processor intensive noodling.

---

### Post by davidmohammed on 2009-03-17
there are a few threads around about sensors not displaying results - such as the following [link]("http://www.lm-sensors.org/ticket/2167").

By default the A75 uses ectype=12 so that's why all your omnibook modules are correctly located in /proc/omnibook.  I trust you have the latest kernel loaded 27.6.27.14? - there have been quite a few acpi fixes in the last few kernel updates.

Sorry can't be much more help.

---

### Post by vos08275 on 2009-04-17
I used this method to get bluetooth up and running perfectly in 8.10 but after updating to the beta of 9.04 it stopped working. I thought repeating the process could do the trick, but still no bluetooth.....
anyone facing the same trouble?
(or even better knowing a solution, lol)

---

### Post by davidmohammed on 2009-04-17
I've done this successfully when upgrading from 8.10 to 9.01

remember to 'make clean' in your omnibook source directory, before make and make install etc.

---

### Post by vos08275 on 2009-04-17
can't I just erase the dir? or should I make everything undone that the HOWTO wants to do?

---

### Post by davidmohammed on 2009-04-17
you could delete and redownload - but that just wastes bandwidth.  make clean removes all the compiled stuff for the old kernel.  Once done, make will create the omnibook module for the new jaunty kernel.

---

### Post by vos08275 on 2009-04-17
much oblige.....
That worked like a charm!

---

### Post by DeLiK on 2009-04-26
Hi excelent thread:

I'm with a:
```
BIOS Vendor:   TOSHIBA
BIOS Version:  V1.60
BIOS Release:  03/16/2006
System Vendor: TOSHIBA
Product Name:  Satellite M60
Version:       PSM60E-024019PT
Serial Number: 75329633K
Board Vendor:  TOSHIBA
Board Name:    Null
```

Got this:
```
/proc/omnibook$ ls
blank      cooling  dmi      lcd          throttling  version
bluetooth  display  hotkeys  temperature  touchpad    wifi

```

And I manage to make bluetooth working with:
```
$ echo 1 > bluetooth
```

The problem is that after 1 min or less, bluetooth goes down but cat bluetooth says this:
```
 $ cat bluetooth 
Bluetooth adapter is present and enabled.

```

And i manage to pair my phone with the computer so BT was REALY working...
...
I'm using Ubuntu 8.04 LTS
2.6.24-23-generic

Any ideas?....

I made the module start on boot, and everytime i reboot i get 1 or 2 min of bluetooth but then... bye bye.. till next reboot... weird....

---

### Post by DeLiK on 2009-05-04
No one can answer?

---

### Post by Albert Que on 2009-05-09
I own a toshiba satellite A200 (phoenix BIOS) running ubuntu 9.04 (Jaunty Jackalope) and had the same problem. 
That worked to me:
[https://bugs.launchpad.net/ubuntu/+source/toshset/+bug/181374](https://bugs.launchpad.net/ubuntu/+source/toshset/+bug/181374)

(search "Tim Richardson  wrote on 2008-07-08")

---

### Post by DeLiK on 2009-05-10
The thing is...

In my case, bluetooth worked... I managed to turn it on.. But suddenly it goes off..

---

### Post by hogsmate on 2009-05-16
thanks guys this helped me a lot 
this is what i got when i did cat /proc/omnibook/dmi
BIOS Vendor:   TOSHIBA
BIOS Version:  V1.30
BIOS Release:  03/26/2007
System Vendor: TOSHIBA
Product Name:  Satellite A200
Version:       PSAE0E-00Y013G4
Serial Number: 47256188K
Board Vendor:  TOSHIBA
Board Name:    1.00

i used ectype=12
but it started working after i rebooted my lap for several times but anyway this works :D 
hope this is helpful to you ):P

---

### Post by Nareto on 2009-06-16
Hello, bluetooth was working fine till I built my own 2.6.30 kernel (needed some drivers). I recompiled the omnibook module (btw, had to apply this [patch]("http://sourceforge.net/tracker/index.php?func=detail&aid=2794118&group_id=174260&atid=868542") (attaching also the file in case the link goes down) to make it compile )
And now the module seams to load correctly, bluetooth turned on but i still get no devices from hcitool

```
omnibook$ cat dmi
BIOS Vendor:   TOSHIBA
BIOS Version:  V1.70
BIOS Release:  09/27/2007
System Vendor: TOSHIBA
Product Name:  Satellite A200
Version:       PSAE6E-05W032IT
Serial Number: X7386950K
Board Vendor:  TOSHIBA
Board Name:    1.00

```
```
$ cat bluetooth 
Bluetooth adapter is present and enabled.

```
```
$ sudo hcitool dev
Devices:

```
```
$ sudo hcitool scan
Device is not available: No such device

```

---

### Post by Nareto on 2009-06-16
I'm adding these outputs
```
$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0930:0508 Toshiba Corp. Integrated Bluetooth HCI
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
```
$ sudo lshw -C communication
  *-usb UNCLAIMED         
       description: Bluetooth wireless interface
       product: Integrated Bluetooth HCI
       vendor: Toshiba Corp.
       physical id: 2
       bus info: usb@3:2
       version: 19.15
       capabilities: bluetooth usb-2.00
       configuration: speed=12.0MB/s

```

could that UNCLAIMED be part of the problem?

---

### Post by Nareto on 2009-06-17
anyone?

---

### Post by d11 on 2009-07-25
I think that my model is not supported help me please.

BIOS Vendor:   TOSHIBA
BIOS Version:  V1.20
BIOS Release:  03/06/2007
System Vendor: TOSHIBA
Product Name:  Satellite A135
Version:       PSAD0U-05400P
Serial Number: 37202473K
Board Vendor:  TOSHIBA
Board Name:    1.00



omnibook: Driver version 2.20090707-trunk.                                                                                                   
omnibook: Unknown model.

---

### Post by Kilroy1218 on 2009-07-30
anyone used this with a p300? i've been trying to try the different ectypes but i dont know if im even doing that 100% correct as im new to linux in general.. been using jaunty for about a month now

---

### Post by event.riga on 2009-09-04
> **Nareto said:**
> I'm adding these outputs
```
$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0930:0508 Toshiba Corp. Integrated Bluetooth HCI
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

``````
$ sudo lshw -C communication
  *-usb UNCLAIMED         
       description: Bluetooth wireless interface
       product: Integrated Bluetooth HCI
       vendor: Toshiba Corp.
       physical id: 2
       bus info: usb@3:2
       version: 19.15
       capabilities: bluetooth usb-2.00
       configuration: speed=12.0MB/s

```could that UNCLAIMED be part of the problem?


So this effectively means that you have your adapter up and running, but don't have a driver loaded, or have it loaded but not working. Bluetooth usb driver is called btusb. If you have it loaded (lsmod | grep bt) then try running bluetoothd with -nd flags which would show you some debugging info (don't forget to kill current bluetoothd before). May be you see some issue in bluez. 
IF you see nothing try rmmod btusb and modprobe btusb and see kernel log.

---

### Post by event.riga on 2009-09-04
> **d11 said:**
> I think that my model is not supported help me please.

BIOS Vendor:   TOSHIBA
BIOS Version:  V1.20
BIOS Release:  03/06/2007
System Vendor: TOSHIBA
Product Name:  Satellite A135
Version:       PSAD0U-05400P
Serial Number: 37202473K
Board Vendor:  TOSHIBA
Board Name:    1.00



omnibook: Driver version 2.20090707-trunk.                                                                                                   
omnibook: Unknown model.


try loading it with different ectype: valid numbers are 1-16
```
modprobe omnibook ectype=<ectype value> bluetooth=1
```

---

### Post by Nareto on 2009-09-04
I think i had finally got it working precisely by loading btusb (now I moved to Archlinux) - sorry for not having posted back

---

### Post by Nareto on 2009-09-04
> **event.riga said:**
> try loading it with different ectype: valid numbers are 1-16
```
modprobe omnibook ectype=<ectype value> bluetooth=1
```

right now - on Arch -  I load it with

/etc/modprobe.d/omnibook.conf
```

options omnibook ectype=12 userset=1 lcd=0 display=0 blank=0 battery=0 ac=0 bluetooth=1
```

and it's working ok

---

### Post by wafflemelon on 2009-11-17
Is this still necessary for the Fan to work under Karmic Koala (9.10)?

---

### Post by Azriphale on 2009-11-17
I don't know. To be honest, I have not actually used this since around about Gutsy.

---

### Post by thebarii on 2009-11-24
Hi!

I have a Toshiba A300 notebook.
Hotkeys, sensor aren't works without omnibook, so i installed the module, and bluetooth, sensor and hotkeys are work
but when i shutdown the system, it turns on after some minutes

$ sudo cat /proc/omnibook/dmi 
BIOS Vendor:   INSYDE
BIOS Version:  2.00
BIOS Release:  08/21/2009
System Vendor: TOSHIBA
Product Name:  Satellite Pro A300
Version:       PSAGRE-002006HU
Serial Number: Y8469476Q
Board Vendor:  TOSHIBA
Board Name:    Base Board Version

$cat /etc/modprobe.d/omnibook.conf 
options omnibook ectype=14

do you have any idea what can i try to fix the problem?

---

### Post by PhaseTwenty on 2009-11-24
I have a Satellite P200 that I'm trying to get the bluetooth running on, but I've had little luck so far.

I got the latest revision of the omnibook source, and followed the directions to install it.  The module seems to load okay but the bluetooth command doesn't load.
```

chris@butts:/proc/omnibook$ ls -l
total 0
-r--r--r-- 1 root root 0 2009-11-24 13:47 ac
-r--r--r-- 1 root root 0 2009-11-24 13:47 battery
-rw-r--r-- 1 root root 0 2009-11-24 13:47 blank
-r--r--r-- 1 root root 0 2009-11-24 13:47 display
-r--r--r-- 1 root root 0 2009-11-24 13:47 dmi
-rw-r--r-- 1 root root 0 2009-11-24 13:47 fan
-rw-r--r-- 1 root root 0 2009-11-24 13:47 hotkeys
-rw-r--r-- 1 root root 0 2009-11-24 13:47 lcd
-r--r--r-- 1 root root 0 2009-11-24 13:47 temperature
-rw-r--r-- 1 root root 0 2009-11-24 13:47 touchpad
-r--r--r-- 1 root root 0 2009-11-24 13:47 version

``````

chris@butts:/proc/omnibook$ cat dmi
BIOS Vendor:   TOSHIBA
BIOS Version:  V1.40
BIOS Release:  04/26/2007
System Vendor: TOSHIBA
Product Name:  Satellite P200
Version:       PSPBGU-046019
Serial Number: 57255349K
Board Vendor:  TOSHIBA
Board Name:    1.00
```I notice that it's reporting a TOSHIBA BIOS but at boot-time I definitely see a Phoenix BIOS.

I found this article [http://linux.dobeyracing.net/how_to/toshiba_p200_laptop/Linux_on_Toshiba_Satellite_P200.php#bt1](http://linux.dobeyracing.net/how_to/toshiba_p200_laptop/Linux_on_Toshiba_Satellite_P200.php#bt1) that refers to my exact model but attempts to modify "ectype" haven't produced any discernible effect.
```

chris@butts:/proc/omnibook$ sudo modprobe omnibook ectype=12
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
chris@butts:/proc/omnibook$ ls -l
total 0
-r--r--r-- 1 root root 0 2009-11-24 13:58 ac
-r--r--r-- 1 root root 0 2009-11-24 13:58 battery
-rw-r--r-- 1 root root 0 2009-11-24 13:58 blank
-r--r--r-- 1 root root 0 2009-11-24 13:58 display
-r--r--r-- 1 root root 0 2009-11-24 13:58 dmi
-rw-r--r-- 1 root root 0 2009-11-24 13:58 fan
-rw-r--r-- 1 root root 0 2009-11-24 13:58 hotkeys
-rw-r--r-- 1 root root 0 2009-11-24 13:58 lcd
-r--r--r-- 1 root root 0 2009-11-24 13:58 temperature
-rw-r--r-- 1 root root 0 2009-11-24 13:58 touchpad
-r--r--r-- 1 root root 0 2009-11-24 13:58 version

```Any ideas on how to proceed?  Googling hasn't yielded a whole lot.

---

### Post by thebarii on 2009-11-25
PhaseTwenty:
have you tryed with ectype=14? 
it looks like is solved my problem, what about i wrote in #92
do you have omnibook.modprobe or omnibook.conf in the /etc/modprobe.d? what is the blacklist?
the post #1 wrote about omnibook.modprobe, but i think that the ".conf" is better... 
good luck

---

### Post by PhaseTwenty on 2009-11-26
Yeah setting the ectype doesn't seem to have any effect unless I'm doing something wrong in another step.

```

chris@butts:/proc/omnibook$ modprobe omnibook ectype=14
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
chris@butts:/proc/omnibook$ ls -l
total 0
-r--r--r-- 1 root root 0 2009-11-26 17:01 ac
-r--r--r-- 1 root root 0 2009-11-26 17:01 battery
-rw-r--r-- 1 root root 0 2009-11-26 17:01 blank
-r--r--r-- 1 root root 0 2009-11-26 17:01 display
-r--r--r-- 1 root root 0 2009-11-26 17:01 dmi
-rw-r--r-- 1 root root 0 2009-11-26 17:01 fan
-rw-r--r-- 1 root root 0 2009-11-26 17:01 hotkeys
-rw-r--r-- 1 root root 0 2009-11-26 17:01 lcd
-r--r--r-- 1 root root 0 2009-11-26 17:01 temperature
-rw-r--r-- 1 root root 0 2009-11-26 17:01 touchpad
-r--r--r-- 1 root root 0 2009-11-26 17:01 version

```Perhaps does it need to be done at the time the module is loading?  There doesn't seem to be any effect if I run this after I run the initial "make load".

edit: also, I do not have omnibook.conf under /etc/modprobe.d/, what do I need to do there?

---

### Post by event.riga on 2009-11-27
Try setting bluetooth=1:
> modprobe omnibook ectype=14 bluetooth=1
You can try to play around with other options, see list with 
> modinfo omnibook

---

### Post by Garibaldi3489 on 2009-12-18
I am having a similar issue getting bluetooth to work on my Toshiba laptop (with Phoenix). I have a Toshiba a205 running Ubuntu 9.10. I have installed the omnibook module and tried
```
sudo modprobe omnibook userset=1 ectype=16 bluetooth=1
```
with all ectype values 1-16 and nothing has worked. Each time, my dmesg output says
```
[    8.513875] omnibook: Driver version 2.20090707-trunk.
[    8.513941] omnibook: Unknown model.
[    8.513996] omnibook: Enabled features: dmi version.
```
and I only have dmi and version in /proc/omnibook. 

If I "cat /proc/omnibook/dmi" I see that my Phoenix version is as follows:
```
BIOS Vendor:   Phoenix Technologies LTD
BIOS Version:  5.20   
BIOS Release:  10/25/2007
System Vendor: TOSHIBA
Product Name:  Satellite A200
Version:       PSAFCU-08H00R
Serial Number: 67019544Q
Board Vendor:  Intel Corporation
Board Name:    Not Applicable
```

Any ideas on how to make this work? 

Thanks!

---

### Post by davidmohammed on 2009-12-18
when I was mucking around trying to get this working I found I had to do [this]("http://ubuntuforums.org/showpost.php?p=6855378&postcount=65").  I presume you are doing something similar between tries?

Also you are using the latest code from sourceforge?

---

### Post by Garibaldi3489 on 2009-12-19
I believe that was my problem! If I were using the modprobe command, would it instead be```
 $ sudo modprobe -r omnibook
``` instead? Anyway, after restarting I was very surprised to find my device detected when running ```
hcitool dev
```. I have since tested it and it seems to be working well! I have written up [a little tutorial on my experiences](http://andrewm.info/blog/6-linux/27-bluetooth-support-for-toshiba-laptops-on-ubuntu) with this and have also put together a little bash script for managing enabling/disabling the bluetooth adapter as well as checking on it's status.


Hopefully that information can be helpful to others who are also trying to enable bluetooth on their Toshiba laptops.

Thanks again!

---

### Post by PhaseTwenty on 2009-12-25
> **davidmohammed said:**
> when I was mucking around trying to get this working I found I had to do [this]("http://ubuntuforums.org/showpost.php?p=6855378&postcount=65").  I presume you are doing something similar between tries?

Also you are using the latest code from sourceforge?
This was my problem as well.  I've been able to successfully connect my bluetooth mouse.

If anyone needs to know how I did it:
I'd followed the directions in the original post pretty closely, except after the module is loaded you have to run
```

$ sudo depmod -a
$ sudo make unload
....
$ sudo modprobe omnibook ectype=12
...

```In order to change the ectype.

I haven't gotten to the point where I make sure to boot with this module; I'll update if anything weird comes up.

---

### Post by gsaggior on 2010-02-09
Hi all,

It seems link to the source files is broken:

svn co [https://omnibook.svn.sourceforge.net/svnroot/omnibook/omnibook/trunk](https://omnibook.svn.sourceforge.net/svnroot/omnibook/omnibook/trunk)
svn: URL 'https://omnibook.svn.sourceforge.net/svnroot/omnibook/omnibook/trunk' doesn't exist


Is there any alternative way to enable the bluetooth radio ?

Thanks !

\GpS

---

### Post by Nareto on 2010-02-09
the correct url is
[https://omnibook.svn.sourceforge.net/svnroot/omnibook/trunk/](https://omnibook.svn.sourceforge.net/svnroot/omnibook/trunk/)

not
[https://omnibook.svn.sourceforge.net/svnroot/omnibook/omnibook/trunk](https://omnibook.svn.sourceforge.net/svnroot/omnibook/omnibook/trunk)

---

### Post by Garibaldi3489 on 2010-02-09
Please take a look at [my guide](http://andrewm.info/software/guides/27-bluetooth-support-for-toshiba-laptops-on-ubuntu) for setting this up. It seems the omnibook team has switched from svn to git. You can now check out the source using:
```
$ git clone git://omnibook.git.sourceforge.net/gitroot/omnibook/omnibook
```

---

### Post by nedflenders on 2010-07-24
Hey Toshiba NB305 owners,

Got a simple solution posted here for ya.

Enable bluetooth:
[http://ubuntuforums.org/showpost.php?p=9631429&postcount=153](http://ubuntuforums.org/showpost.php?p=9631429&postcount=153)

Enjoy.

---

### Post by mitch117 on 2010-09-26
can you provide the supported device list that has the "ectype" numbers? it is no longer available at the sourceforge site or the link in your howto

---

### Post by hell_rider on 2010-10-18
Guys,

Hello all.

I only need to get the LCD brightness control working on my Toshiba Satellite A100 (PSAA9L model) with the unfortunate Phoenix BIOS.

I have followed all the instructions given perfectly. (I think).
I think I am very close to getting this work.  I am probably making a rookie mistake somewhere and missing something silly.  Could you please help ?

I am loading the omnibook module like so, (while I am in the /omnibook/trunk directory) without specifying ectype.

```
$ sudo modprobe omnibook userset=1 lcd=1
```

After the above command, following is the dmesg output.

```
[ 4658.106656] omnibook: Driver version 2.20090707-trunk.
[ 4658.106734] omnibook: Toshiba Satellite A100 detected.
[ 4658.106821] omnibook: Begin table match of bluetooth feature.
[ 4658.106826] omnibook: Try to init ACPI backend
[ 4658.106840] omnibook: ACPI EC device found
[ 4658.151594] omnibook: hook_connect for device AT Translated Set 2 keyboard.
[ 4658.183564] omnibook: Enabling Toshiba Bluetooth ACPI device.
[ 4658.416565] omnibook: ACPI backend init OK
[ 4658.416575] omnibook: Returning table entry nr 0.
[ 4658.418289] omnibook: BTST raw_state: c1
[ 4658.418301] omnibook: dmi feature has no backend table, io_op not initialized.
[ 4658.418307] omnibook: version feature has no backend table, io_op not initialized.
[ 4658.418313] omnibook: Begin table match of lcd feature.
[ 4658.418317] omnibook: Returning table entry nr 5.
[ 4658.418553] omnibook: Enabled features: bluetooth dmi version lcd.
```

Then I issue this command
```
$ ls /proc/omnibook
#Following is the output.  I have got LCD listed here WITHOUT specifying ECTYPE.
bluetooth
dmi
lcd
version
```

Then I issue this command:
```
$ cat /proc/omnibook/dmi
#Following is the output.
BIOS Vendor:   Phoenix Technologies LTD
BIOS Version:  1.80   
BIOS Release:  06/12/2006
System Vendor: TOSHIBA
Product Name:  Satellite A100
Version:       PSAA9L-0ML00C
Serial Number: 76110390Q
Board Vendor:  Intel Corporation
Board Name:    Not Applicable

```

Then I issue this command
```
$ cat /proc/omnibook/lcd
LCD brightness:  0 (max value: 7)
```

In the above output, the value returned is the value of the Gnome Power Manager Brightness applet.

If I use the Gnome Power Manager Brightness applet to slide the brightness value, this is also reflected in the /proc/omnibook/lcd value when you do a cat.
Also when I do an echo to set the value, the value also changes.

Unfortunately, the brightness itself does not change.  My LCD is stuck at max brightness.

I also tried setting different values of ECTYPE.  But that does not work either.  In any case,  based on the information provided in the first post of this thread, if LCD/Bluetooth etc show up in /proc/omnibook without specifying ECTYPE then it means that the laptop is recognised and there is no need to specify ECTYPE.

It seems I am overlooking something very silly or minor here.  Can you guys help me figure it out ??

P.S.
It seems I had installed the toshset package a long time back when I was trying to get this working.  In Synaptic, it still shows as INSTALLED.  Do you think that is interfering with Omnibook.  If I Mark it For Removal, it says acpi-support, powermanagement-interface and ubuntu-desktop will be removed as well.  So I did not uninstall it.  Is that the problem ?

In addition, I have the following packages installed using Synaptic.
sensors-applet, powermgmt-base, apmd, acpi-support, acpid, acpi.  Are any of these interfering with omnibook being able to work ?? I installed these to get the temperature sensors, and CPU scaling/frequency applets working.

Many thanks and regards.

---

### Post by hell_rider on 2010-10-22
Guys,

Some help PLEASE.

Thanks.

---

### Post by mahy on 2010-10-22
> **hell_rider said:**
> Guys,

Some help PLEASE.

Thanks.

Unfortunately I cannot help you, but I've got the same problem on a similar laptop and I filed a bug report at Launchpad some 2 years ago and there's still no improvement. What you can do is to open this page [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/297658](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/297658) and click "this bug affects me" somewhere at the top underneath the title. (If you don't have a Launchpad account, you'll have to open one, it's very quick.) With more people complaining, we might gain more attention from the kernel programmers. Regards,

Mahy

---

### Post by mockingbird on 2010-10-25
modprobe omnibook userset=1 ectype=12
/proc/omnibook# ls
ac  battery  blank  cooling  dmi  hotkeys  lcd  temperature  throttling  touchpad  version
root@moishe-kubuntu:/proc/omnibook# cat cooling
Cooling method : Performance

Toshiba A200-09V

I;m having trouble with my fan, it doesn't turn on as often as it should, and KSensors shows 61C and that's why I'm always throttled to 1000mhz.  Cat throttling does not reflect this.

Does anyone know where the ECTYPE list went?

---

### Post by apexofservice on 2010-11-07
My experience is similar to hell_rider.  

I've got a Tosh Sat M115,  I got the source from the svn trunk.  All compiled (one warning about C style, but nothing broke), installation also went ok (make && make install, modprobe).  I now have three files in /proc/omnibook, dmi, lcd and version.  

Dmi seems to correctly recognize m115 even though I didn't specify ectype. Like many of you, I can't find the current 'supported laptops list'---it seems to have disappeared.  

Like hell_rider, I can cat values into /proc/omnibook/lcd (and I noticed that I can use the slider on the gnome panel) but I don't see actual changes in the screen brightness.  

Eg:
$/proc/omnibook# cat lcd
LCD brightness:  0 (max value: 7)
(The laptop lcd should be off, but there's no change).

Here's my dmi and version.  Does anyone have any ideas?

-------------------
jcrowgey@spooky2:~$ cat /proc/omnibook/version
2.20090707-trunk
jcrowgey@spooky2:~$ cat /proc/omnibook/dmi
BIOS Vendor:   Phoenix Technologies LTD
BIOS Version:  1.60   
BIOS Release:  12/19/2008
System Vendor: TOSHIBA
Product Name:  Satellite M115
Version:       PSMB0U-015007
Serial Number: Y6389892Q
Board Vendor:  Intel Corporation
Board Name:    Not Applicable
--------------------

One last thing, I noticed that the bios still says Version 1.60, but I actually upgraded my BIOS to 1.90 (last night, hoping it would help). Do I need omnibook to update.  I tried to remake the module:

jcrowgey@spooky2:~/omnibook/trunk$ make
make: Nothing to be done for `all'.

So maybe I need to force omnibook to rebuild and then reinstall, I'm not sure. 

Thanks to the original poster and all follow ups.  It's hard to get help for some of these laptops sometimes.

---

