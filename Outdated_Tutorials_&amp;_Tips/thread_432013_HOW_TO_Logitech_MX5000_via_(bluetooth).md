---
title: "HOW TO: Logitech MX5000 via (bluetooth)"
date: 2007-05-03
forum: Outdated Tutorials &amp; Tips
---

### Post by spockrock on 2007-05-03
Ok I can't take the credit for this, I found out how to get my mx5000 working via bluetooth from bug reports.  I thought I would share with you all.

[Got all the info from here thanks to kryilian and amedee](https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/32415)

Ok so first thing you should notice when you have a Logitech bluetooth device is at login (gdm) that more or less it does not work.  However unplugging and replugging in the adapter puts the device in USB emulation mode but you can not use bluetooth to transfer files for example or use other blue tooth devices with in this mode.  

So after going through bluetooth bug reports I finally got my MX5000 working in feisty.

What you need:
you need either a spare keyboard and mouse or need to know your keyboard and mouses mac address.  For those of use who dual boot Vista and Ubuntu you can get your devices mac address (if you are using the set over bluetooth of course) 

For those who are using a spare keyboard and mouse, or do not use vista you can skip this part.  Now you are in vista if you are using the set over bluetooth you should see the bluetooth logo in your systray, when you double click it, you should get a window, displaying all the bluetooth devices connected.  In the device properties you should see the devices MAC addresses, now write them down, in fact if you want write down any other devices mac address you intend to use like your wii mote ;p.

[IMG]http://img.photobucket.com/albums/v605/redemma/feisty/mac.jpg[/IMG]

now write them down.

Ok if you want to do this the spare keyboard and mouse way, what you do is obviously plug the spare keyboard and mouse in, and the bluetooth mouse and keyboard.  Once you get to gdm you obviously have to use the spare keyboard.  What you need to do is first set your device in discoverable mode, ie with a phone do it through the settings, or press the connect button on your logitech keyboard or mouse.  Now enter hcitool scan in terminal, this should find your device and output the its mac address.  I had it once not able to find the device, so I just re-entered the command in terminal, and it found my keyboard and mouse.  So just be warned you may need to do it a couple of times.


Now you have your devices mac addresses you now just need to do the following.....

Those who do not have the spare keyboard and mouse, unplug the usb adapter and plug it back in to get the set in the usb emulation mode, log in and then open up terminal.

Those using the spare keyboard and mouse might notice the bluetooth logo in the gnome notification area.  Now open terminal and enter;

```
hcitool dev
```
and I get an output like this; 
```
hci0    00:07:61:40:CC:77
```

now what you can do is this, I found that the automatic startup wont connect unless you manually connect at least once.  So to do this put the keyboard and mouse in discoverable mode (little red buttons on the bottom of the keyboard and mouse)
in terminal enter this; 
```
sudo hidd -search
```
this will connect any discoverable bluetooth devices, like your wiimote if you put it in discovery mode as well.  Once they are connected continue to make your keyboard and mouse connect automatically.

this basically to my understanding is the bluetooth adapters id and mac address.  Not what you want to do is open up /etc/default/bluetooth so;
```
gksudo gedit /etc/default/bluetooth
```
or
```
sudo nano /etc/default/bluetooth
```

now look for a section that looks like this
```

############ HIDD
#
# To have Bluetooth mouse and keyboard support, get the
# Linux 2.6.6 patch or better from bluez.org, and set 
# HIDD_ENABLED to 1.
HIDD_ENABLED=0
HIDD_OPTIONS="--master --server"
# to make hidd always use a particular interface, use something
# like this, substituting the bdaddr of the interface:
# HIDD_OPTIONS="-i AA:BB:CC:DD:EE:FF --server"
#
# remove '--master' if you're having trouble working with Ericsson
# T630 phones with hidd operational at the same time.
```

So now what you need to do is change the HIDD_ENABLED and HIDD_OPTIONS
you need to change the HIDD_ENABLED to HIDD_ENABLED=1, now this is where it gets a little tricky...this is the HIDD_OPTIONS line that worked for me.....but others have used different lines to get this to work;

my settings, that got my mx5000 to work;
```
HIDD_ENABLED=1
HIDD_OPTIONS="-i hci0 --connect 00:07:61:32:70:6F --connect 00:07:61:33:CF:33 --master --server"

```

however these HIDD_OPTIONS have worked, according to others in the bug report;
```

HIDD_OPTIONS="--master --connect 00:07:61:34:xx:xx--connect 00:07:61:37:xx:xx --server"
HIDD_OPTIONS="--connect 00:07:61:07:XX:XX --connect 00:07:61:06:YY:YY --connect 00:07:61:06:ZZ:ZZ --master --server"
[code]

bascially if you get a similar output as me when doing hcitool dev try my line, do not forget use your devices mac address to connect.

OK ..... there is one more change I made, I have no Idea if this change made a difference or not but open up /etc/init.d/bluetooth, however you wish to do; now look for this section;

[code]
  restart|force-reload)
	log_daemon_msg "Restarting $DESC"
	stop_hid || true
	stop_pan || true
	start-stop-daemon --stop --quiet --exec $HCID || true
	sleep 1
	if test "$BLUETOOTH_ENABLED" == "0"; then
		log_progress_msg "disabled. see /etc/default/bluetooth"
		log_end_msg 0
		exit 0
	fi
	start-stop-daemon --start --quiet --exec $HCID -- $HCID_OPTIONS || true
	log_progress_msg "$HCID_NAME"
	start_pan || true
	start_hid || true
	restart_rfcomm
	log_end_msg 0
    ;;
  *)
```

I added the line enable_hci_input || true after the start_hid || true line err, like this;

```

  restart|force-reload)
	log_daemon_msg "Restarting $DESC"
	stop_hid || true
	stop_pan || true
	start-stop-daemon --stop --quiet --exec $HCID || true
	sleep 1
	if test "$BLUETOOTH_ENABLED" == "0"; then
		log_progress_msg "disabled. see /etc/default/bluetooth"
		log_end_msg 0
		exit 0
	fi
	start-stop-daemon --start --quiet --exec $HCID -- $HCID_OPTIONS || true
	log_progress_msg "$HCID_NAME"
	start_pan || true
	start_hid || true
	enable_hci_input || true
	restart_rfcomm
	log_end_msg 0
    ;;
  *)
```

now you can restart bluetooth via 
```
sudo /etc/init.d/bluetooth restart
```

hopefully this will get your mouse and keyboard working.  Ok so now you should have a working bluetooth keyboard and mouse.

Ok I haven't found a way to get my mx1000 working properly and the same for the keyboard, but you if open up keyboard preferences, the hit the layout tab, and then pick the Logtiech itouch cordless keyboard (model Y-RB6) as the model, you can use the regular Logitech itough cordless keyboard, which properly detects the volume touch sliders raise volume as XF86VolumeRaise, but for some reason does not work when trying to raise the volume, however, if you use the other model I suggest it detects the raise slider as XF86Launch1, but at least you can raise and lower your volume.  Also the FMode keys do work however but the word, excel and powerpoint do not work and neither do the smart keys... :\  and also none of the top shortcut keys except for the email button, which works.

Ok now  I can use my keyboard and mouse in grub, (once it did complain about wanting a passkey) I just entered something random and then was able to freely do what I wished in grub.

The only other thing is that, when I restart from windows, I loose the keyboards bluetooth connection.

Also if you want to send and receive files via blue tooth its easy, first install gnome-bluetooth
```
sudo apt-get install gnome-bluetooth
```

then run gnome obex server, send as you would from the other device to recieve and to send files from your computer just right click pick send to and in the send as field pick bluetooth


*** ALSO NOTE *** I found that updating the dongles firmware makes the keyboard behave strangely, media keys and some keypad buttons do not work, that is available on the logitech website.

---

### Post by edmondt on 2007-05-03
Good guide! my hcitool dev returns "hci0    11:11:11:11:11:11" maybe its real :D I'll give it a try and report back...

---

### Post by edmondt on 2007-05-04
My device id was not 11:11:11:11:11:11

I have to plug in the bluetooth stick, uncheck bluetooth device management in system/admin/services, then check again, and use a spare keyboard and mouse (good thing I'm on a laptop) to open the terminal and execute "hcitool dev"

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=31737&stc=1&d=1178289466[/IMG]

I got "hci0    00:07:61:40:B9:94". I press the connect button on my MX mouse and enter "hcitool scan", then I got:

        00:07:61:36:37:FA       Logitech MX1000 mouse
        00:12:37:9D:BD:17      Pocket PC

Wow I found my mouse...

But I couldn't seem to get it to work yet...
HIDD_ENABLED=1
HIDD_OPTIONS="-i hci0 --connect 00:07:61:36:37:FA --master --server"

I tried the method you mention, including modification to /etc/init/d/bluetooth, not working yet... but I'll keep trying.

---

### Post by edmondt on 2007-05-04
This post in the bug report ([https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/32415](https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/32415)) made my mouse work! I followed no. 3) hidd -i hci0 --connect 00:07:61:36:37:FA and now my mouse is working :) My mouse pointer is faster and smoother than before :)

1/ check /etc/default/bluetooth
HIDD_ENABLED=1
and add "-i hci0" in HIDD_OPTIONS :
HIDD_OPTIONS="-i hci0 --master --server"

2/
add in /etc/init.d/bluetooth, in "start)" and "restart|force-reload)" sections :
 enable_hci_input || true

3/ I had to force the very first pairing with this script (launch with sudo)
hid2hci --tohci
sleep 1
/etc/init.d/bluetooth restart
sleep 1
#Connect the mouse
hidd -i hci0 --connect 00:07:61:36:37:FA
#Connect the keyboard
hidd -i hci0 --connect xx:xx... kb adress

Now everything works, even after reboot, no need to reconnect using the command "hidd -i hci0 --connect 00:07:61:36:37:FA" Weeeeeeeeee!

---

### Post by ghell on 2007-05-10
I don't use my MX5000 or MX1000 in bluetooth mode, I use the standard RF Radio mode (bluetooth mode is only  when you hold the red button when inserting the dongle) because I find it more stable and it works before my OS loads.

I still can't get my keyboard and mouse to work on boot. I can only install via the Alternate installer (in which the keyboard works fine) as the LiveCD kills off my mouse and keyboard somewhere between the desktop appearing and all the icons, panels etc appearing.

I did not have any of these problems on fedora, even with bluetooth enabled (but not used, as the dongle was not in bluetooth mode it was just totally unaware that my keyboard/mouse/dongle was capable of bluetooth).

Anyone have any idea 1) why it doesn't work out of the box (it starts working and then dies) and 2) how to get it to work without using bluetooth mode?

---

### Post by martijn_bakker on 2007-05-10
As to why it's not working per default:

When your system recognises the BT dongle as a BT adapter, it switches the adapter from USB emulation mode (which is used at boot time) to BT adapter. After that, any bluetooth hardware wish to use (including the mouse and keyboard) will have to be connected. The HOWTO above specifies how you can have these connections established by default. Your solution of not starting BT services effectively keeps the BT dongle in USB mode (which is fine, realy, except you can't connect to other BT hardware from the same machine, not even if you have another BT interface). Unfortunately, the UBUNTU install CD seems to be the only install/live CD that actually enables bluetooth by default (and thus it does not support BT mouse and/or keyboard after GDM starts, but does support communication with all BT devices, including phones, PDA's and such, after they have been connected properly)

As to how to get it working without BT mode: remove BT support ( sudo apt-get remove bluez-utils )

---

### Post by Peno on 2007-05-12
it works ;-)

thanks for sharing this!!!

---

### Post by TOML1 on 2007-05-25
i have tried that, and when i do hcitool dev i get a blank beside Devices


my logitech MX5000 works, after repluging in the reciver, just fine though, would that be the only solution to my problem?

---

### Post by spockrock on 2007-05-26
when you unplug and plug it back in the dongle goes into a USB emulation mode, the reason why you get a blank output fromt he hcitool dev, is because you are in the USB emulation mode, and not in bluetooth mode.

Do you have a spare keyboard temperoraly so you find your keyboard and mouses bt address, so you can configure your bluetooth settings to automatically connect to them on startup?

---

### Post by fatmcgav on 2007-06-04
Hi there,

Just a quick question for you. 

With this set-up, do all the media keys, etc on the keyboard work ok? Need any further config???

Any info appreicated.

Cheers
Fatmcgav

---

### Post by spockrock on 2007-06-08
> **fatmcgav said:**
> Hi there,

Just a quick question for you. 

With this set-up, do all the media keys, etc on the keyboard work ok? Need any further config???

Any info appreicated.

Cheers
Fatmcgav

I'd say that 90% of the extra keys work, the volume slider, mute, play, stop, forward, reverse, media keys work for sure.


Ok correction, I recently deleted my /home partition and it seems to have gotten rid of my multimedia key functionality, yeah I dunno.... but they keys stoped working I cant say why.

---

### Post by zygoat_D on 2007-06-25
ok ive been through this like 20 times and i cant get it to work! i think the problem might be with the /etc/init.d/bluetooth part all it says for me start stop restart force reload.   can some one please help me



do i need to dl the patch 2.6.6 or whatever i didn't cuz it seems to me that ver.7.04 is quite a bit higher dont know if the patch ver is different than the os ver. if i do need this where do i get it?

thanks for the help

---

### Post by spockrock on 2007-06-27
> **zygoat_D said:**
> ok ive been through this like 20 times and i cant get it to work! i think the problem might be with the /etc/init.d/bluetooth part all it says for me start stop restart force reload.   can some one please help me



do i need to dl the patch 2.6.6 or whatever i didn't cuz it seems to me that ver.7.04 is quite a bit higher dont know if the patch ver is different than the os ver. if i do need this where do i get it?

thanks for the help

I am sorry I missed what you said.... what version of ubuntu are you running??

---

### Post by zygoat_D on 2007-06-28
i am running 7.04

---

### Post by spockrock on 2007-06-28
I setup this tutorial on 7.04, so there should not be any need for any kernel updates.

---

### Post by zygoat_D on 2007-06-29
> **zygoat_D said:**
>  i think the problem might be with the /etc/init.d/bluetooth part all it says for me start stop restart force reload.

whats up with that part then. and why wouldn't it work. i went through everything you said but no luck!?!

---

### Post by spockrock on 2007-07-01
can you post the contents so I can take a look???

---

### Post by spockrock on 2007-07-10
Ok I made a small change, I found that you need to manually connect your keyboard and mouse at least once to make bluetooth automatically connect after that.  I dunno its what I found after getting a new keyboard and mouse.

ALSO really important, do not use the bluetooth, firmware patch available for your dongle from logitechs site, I found it made my media keys and number keys not work properly.

---

### Post by MetalGeek on 2007-07-19
Okay, here is my problem:
I followed the guide in the original post, but my mx5000 keyboard would never connect by itself (it would work in GRUB, after I entered a passkey), but to get it to connect, I would have to run:
```
sudo hidd --search
```

Then when I alter etc/default/bluetooth (listed below), and restart bluetooth, it messes around with my keyboard input.
"up" will output A, "left" will output B, etc. And the actual letters will either not work, or have some unexpected effect. Sometimes the letters will work, but will act as though shift were being held down (characters come out as caps, or their alternate characters)
This corrects when i revert the bluetooth file to the backup, or (strangely enough) after a few minutes of use.
Anyway, here is my bluetooth file. Any help would be greatly appreciated:

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
[b]
HIDD_ENABLED=1
HIDD_OPTIONS="-i hci0--connect 00:07:61:3D:80:97 --connect 00:07:61:36:FB:4E --master  --server"[/b]
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

---

### Post by spockrock on 2007-07-21
I have reset my keyboard in gnome as a generic keyboard and it detects the keyboard properly with the multimedia keys.  I am not sure, if it will help but try changing your keyboard model in gnome, through the keyboard application. (gnome-keyboard-properties)

---

### Post by liquid circuit on 2007-07-22
I also sometimes have to do a hidd --search inorder to get my MX5000 keyboard/MX1000 Bluetooth mouse to connect.  Otherwise X won't start (since their is no Core pointer/keyboard connected).  I am running a dual-boot with WinXP, and I suspect it may be related to switching between the two OSes.  Each time I boot back into WinXP I have to re-pair my keyboard (but not the mouse oddly enough).  And if I then boot back into Ubuntu, I have to hidd --search for my mouse (usually the keyboard connects with no problem, but SOMETIMES it doesn't).

Summary:
WinXP:   BT Mouse usually works without any futzing about
Ubuntu:  BT Keyboard usually works without any futzing about.
======
...sigh...

Anybody have any ideas what is going on here??  Having a backup mouse/keyboard wired up detracts from the sense of "freedom" the wireless is supposed to give me.

---

### Post by quicksilver1024 on 2007-07-22
My tab key doesn't work...
:(

---

### Post by hardjowikromo on 2007-07-26
O btw its :

sudo hidd --search

Been wasting freegin half an hour to figure out what i did wrong :P

---

### Post by TheRealRockeT on 2007-07-28
For anyone who is STILL having trouble getting their keyboard to connect after following the HOWTO, I recommend editing /etc/init.d/bluetooth and, in both the start and restart sections, moving the line "enable_hci_input || true" so it appears before the line "start_hid || true":

```
  start)
        log_daemon_msg "Starting $DESC"

        if test "$BLUETOOTH_ENABLED" == "0"; then
                log_progress_msg "disabled. see /etc/default/bluetooth"
                log_end_msg 0
                exit 0
        fi

        start-stop-daemon --start --quiet --exec $HCID -- $HCID_OPTIONS || true
        log_progress_msg "hcid"
        start_uarts || true

        enable_hci_input || true
        start_hid || true
        start_rfcomm || true
        start_pan || true
        log_end_msg 0
    ;;
```

```
  restart|force-reload)
        log_daemon_msg "Restarting $DESC"
        stop_hid || true
        stop_pan || true
        disable_hci_input || true
        start-stop-daemon --stop --quiet --exec $HCID || true
        sleep 1
        if test "$BLUETOOTH_ENABLED" == "0"; then
                log_progress_msg "disabled. see /etc/default/bluetooth"
                log_end_msg 0
                exit 0
        fi
        start-stop-daemon --start --quiet --exec $HCID -- $HCID_OPTIONS || true
        log_progress_msg "$HCID_NAME"
        enable_hci_input || true
        start_pan || true
        start_hid || true
        restart_rfcomm
        log_end_msg 0
    ;;
```

I also added the line "disable_hci_input || true" in the restart section, I'm not sure if it affects anything.



@edmondt: Cheers for posting the script on page 1 of this thread (you had it in step 3). It enables HCI mode before calling hidd, I modified my startup scripts to do the same, and it worked! Thanks very much!

---

### Post by Adman on 2008-03-29
hey guys

im having a peculiar problem -- my keyboard just randomly switches off in specific apps - like Matlab.  I have read that it may be to do with the keyboard layout being incorrect --> System --> Pref --> Keyboard --> Layout.

The keyboard is the Logitech MX5000 -- which isn't listed as one of the choices.

Can anyone help _please_ ;)

---

### Post by Bonger1901 on 2008-04-28
Thanks spockrock, I don't have to reconnect my bluetooth stick every startup now. :) It still takes a couple of seconds before my keyboard and mouse react but I can live with that.

edit: Hmph I haven't changed anything but I still have to reconnect it now. :/

---

### Post by oligray on 2008-05-16
do all the extra buttons on the mouse and keyboard work..and the screen on the keyboard.

---

### Post by AGMaster on 2008-08-13
I got an even better way of finding you MAC address, Turn your mouse/keyboard over and hey presto, there it is!

Nice tutorial BTW!

---

### Post by felipe1982 on 2008-09-04
found this on google. it helped me configure MX5000 on openSUSE 11.0 Thanks for the tips.

Volume control and mute work. Button for LIBRARY opens Amarok (cool). No other special keys/features work.

---

### Post by honda_666 on 2008-09-05
That iz PERFECT !!! 

THANK YOU VERY MUCH !!!

REGARDS

PS : I'm using Ubuntu 8.04 and i've just did these steps :

hcitool dev

: After that ;

sudo hidd -s

this connets to device which you pressed connect button ;

So making this 2 times gives you both of their addresses...

so then  ;

gksudo gedit /etc/default/bluetooth

Then here i added 

HIDD_ENABLED=1
HIDD_OPTIONS="-i hci0 --connect 00:07:61:32:70:6F --connect 00:07:61:33:CF:33 --master --server"

then it worked PERFECTLY :D

Have A Nice Linux ALL :D

---

### Post by honda_666 on 2008-09-06
PS : As i described above ;

After that these media keys worked :

Mute
Play
Pause
Stop
Forw
Rev

You need to try for more , i think everything is working fine :)

---

### Post by terrypen on 2008-09-27
I've been working on this for about 2 weeks off an on. I have rebuilt Ubuntu about 5 times because of lockups on my HP Pavilion zv6000 laptop. In between all the rebuilds, I have been trying to get the my bluetooth mouse Model M-RBB93. Of course, the only time I have been able to get it to work is the very first install of Ubuntu. 
Here are my steps that it took to get it working.

1. Open terminal and type ```
sudo hcitool scan
```, don't hit Enter yet. Make sure the mouse is in pairing mode (I had to push the button on mine for a couple seconds until the green light was flashing), then hit Enter.
It should see your mouse with the MAC and display that.
2. If number one worked then right click on the bluetooth icon in the "system tray" and select Preferences.
3. Click on the Services tab and highlight the Input Service.
4. Put the mouse in pairing mode again and then select Add on the Input Service window.
5 Mine paired and started working.

6. I still edited the /etc/default/bluetooth as mentioned in several HOW TO forums. I also got rid of the --master from that line.

I think that the main difference that I did was getting the mouse in pairing mode and then using the bluetooth Input Services tab.

Hope this helps someone else.
Thanks for all the input on this forum.

Terry

---

### Post by fr.theo on 2008-10-10
I also have Ubuntu Hardy and followed these steps but just wanted to add one little thing that helped me.

hcitool dev

: After that ;

[COLOR="Magenta"]PRESS THE RED CONNECTION BUTTONS ON THE BACK OF YOUR DEVICES BEFORE YOU ENTER THE NEXT COMMAND IN TERMINAL.[/COLOR]

sudo hidd -s

this connets to device which you pressed connect button ;

So making this 2 times gives you both of their addresses...

so then ;

gksudo gedit /etc/default/bluetooth

Then here i added

HIDD_ENABLED=1
HIDD_OPTIONS="-i hci0 --connect 00:07:61:32:70:6F --connect 00:07:61:33:CF:33 --master --server"

This was an Awesome Tutorial though.

---

### Post by locoloic on 2008-10-20
> **edmondt said:**
> 
3/ I had to force the very first pairing with this script (launch with sudo)
hid2hci --tohci
sleep 1
/etc/init.d/bluetooth restart
sleep 1
#Connect the mouse
hidd -i hci0 --connect 00:07:61:36:37:FA
#Connect the keyboard
hidd -i hci0 --connect xx:xx... kb adress

Now everything works, even after reboot, no need to reconnect using the command "hidd -i hci0 --connect 00:07:61:36:37:FA" Weeeeeeeeee!

Hello,
Can I add the above code into /etc/default/bluetooth or /etc/init.b/bluetooth or do I need to create it as a whole new script? 

I'm going to do the following to get it to run at startup:

[i]
You need to save the script as [name].sh. Give it whatever name you want.
You first need to copy the script to /etc/init.d:
sudo cp [name].sh /etc/init.d
Now, make it executable:
sudo chmod +x /etc/init.d/[name].sh
To make the script run at startup:
sudo update-rc.d [name].sh defaults
[/i]

Only question: at the top it says to launch as SUDO - how do I add the SUDO command to a script, and how do I insert the password? Seems like it would be risky to have the SU password in a startup script, unencoded.

---

### Post by snaggapuss on 2008-11-15
ok not sure if keyboard works, mouse seems to function
when I try to restart bluetooth I get this message

 * Restarting bluetooth                                                         Can't get device information: No route to host
/etc/init.d/bluetooth: 294: enable-hci-input: not found

These are the things i've done on the default /bluetooth
HID daemon
HIDD_ENABLED=1
HIDD_OPTIONS="-i hci0 --connect 00:07:61:8B:9D:5D connect 00:07:61:98:97:52 --master --server"

and on the init.d
start-stop-daemon --start --quiet --exec $HCID -- $HCID_OPTIONS || true
	log_progress_msg "hcid"
	start_pan || true
	start_hid || true
	enable-hci-input || true
	restart_rfcomm
	log_end_msg 0

an interesting thing is that the bluetooth preferences (bluetooth button up on bar) shows only the mouse mx1000,  I am not sure what i did but the keyboard showed up when i was able to browse device( cant do this now for some reason) when it did show it had a locked symbol by the side

any help to resolves this gratefully recieved

---

### Post by snaggapuss on 2008-11-15
ok keyboard still doesnt work, tried the "enable_hci_input || true" so it appears before the line "start_hid || true": suggest by real rocket t that freaked me out when i tried restarting, so removed that.
When I come to login screen cant login with keyboard have to use ps keyboard, once logged in Bluetooth preferences show in browzing device the keyboard but it is locked, If i click on connect i get the response
Couldn't display "obex:// [00:07:61:BB:9D:5D]" error host down Please select another viwer & try again
 removal of bluetooth dongel gets the keyboard up and running

ok late at night so going to hit the sack, hopefully some one will read this and have the answers for me:confused:

---

### Post by samuraiche on 2008-11-30
I got my keyboard and mouse working after reboot by doing the following:

First of all to enable bluetooth mode of your keyboard and mouse you have to press the red button on the usbstick and plug it in while the red button is pressed. You'll notice that bluetooth icon apears in on the top right panel. Then run Terminal> **hcitool dev**:
which gives:
Devices:**hci0	00:07:55:ZZ:YY:XX** -> this means your bluetooth is connected and recognized :)

Write in terminal **hidd** but don't hit Enter yet.Take the keyboard in your hands, turn it around and you'll see a little red button press it few times and in terminal hit enter to run hidd. You'll notice hidd will try to find any bluetooth device in the range and normally it'll find your keyboard.If not found try pressing the red button again and running hidd few times too.

If it's found right click on the bluetooth icon on the top right panel > Setup new device > Forward and now you should see you keyboard in the list. Select the keyboard and press Forward. The wizard will politely ask you to enter a pin-code on your keyboard.After you enter the pin the keyboard will be connected and now you should be able to use it.

The same thing with the mice. Though I had to press the red button many times before it was found.

Hope this helps :

cheers

---

### Post by meccokushi on 2008-12-07
Ok, i have just upgraded to 8.10 Intrepid and some things are majorly different...  

Here is my /etc/default/bluetooth:

[INDENT]# Defaults for bluez

# start bluetooth on boot?
# compatibility note: If this variable is not found bluetooth will
# start
BLUETOOTH_ENABLED=1

# This setting will switch HID devices (e.g mouse/keyboad) to HCI mode, that is
# you will have bluetooth functionality from your dongle instead of only HID.
# Note that not every bluetooth dongle is capable of switching back to HID
# mode, see [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=355497](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=355497)
HID2HCI_ENABLED=1
HID2HCI_UNDO=1[/INDENT]

I have found that to get it to work on start up changing to the follow works:
HID2HCI_ENABLED=0
HID2HCI_UNDO=0
but bluetooth for other devices is no longer available, which is what i'm going for.

here is my /etc/init.d/bluetooth:

[INDENT][SIZE="2"]#! /bin/sh
### BEGIN INIT INFO
# Provides: bluetooth
# Required-Start:    $local_fs $syslog $remote_fs dbus
# Required-Stop:     $local_fs $syslog $remote_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start bluetooth daemons
### END INIT INFO
#
# bluez    Bluetooth subsystem starting and stopping
#
# originally from bluez's scripts/bluetooth.init
#
# Edd Dumbill <ejad@debian.org>
# LSB 3.0 compilance and enhancements by Filippo Giunchedi <filippo@debian.org>
#
# Updated for bluez 4.7 by Mario Limonciello <mario_limonciello@dell.com>
#
# startup control over dund and pand can be changed by editing
# /etc/default/bluetooth

PATH=/sbin:/bin:/usr/sbin:/usr/bin
DESC=bluetooth

DAEMON=/usr/sbin/bluetoothd
HCIATTACH=/usr/sbin/hciattach

HID2HCI=/usr/sbin/hid2hci
HID2HCI_ENABLED=1
HID2HCI_UNDO=1

UART_CONF=/etc/bluetooth/uart

RFCOMM=/usr/bin/rfcomm
RFCOMM_NAME=rfcomm
RFCOMM_CONF=/etc/bluetooth/rfcomm.conf
SDPTOOL=/usr/bin/sdptool

test -f /etc/default/bluetooth && . /etc/default/bluetooth
test -f /etc/default/rcS && . /etc/default/rcS

. /lib/lsb/init-functions

set -e

run_sdptool()
{
	test -x $SDPTOOL || return 1

	if ! test -z "$SDPTOOL_OPTIONS" ; then
		oldifs="$IFS"
		IFS=";"
		for o in $SDPTOOL_OPTIONS ; do
			#echo "execing $SDPTOOL $o"
			IFS=" "
			if [ "$VERBOSE" != "no" ]; then
				$SDPTOOL $o
			else
				$SDPTOOL $o >/dev/null 2>&1
			fi
		done
		IFS="$oldifs"
	fi

}

enable_hci_input()
{
       if [ "$VERBOSE" != no ]; then
               log_progress_msg "hid_devices"
               $HID2HCI --tohci
       else
               $HID2HCI --tohci >/dev/null 2>&1
       fi
}

disable_hci_input()
{
       if [ "$VERBOSE" != no ]; then
               log_progress_msg "hid_devices"
               $HID2HCI --tohid
       else
               $HID2HCI --tohid >/dev/null 2>&1
       fi
}

start_uarts()
{
	[ -f $HCIATTACH ] && [ -f $UART_CONF ] || return
	grep -v '^#' $UART_CONF | while read i; do
               if [ "$VERBOSE" != no ]; then
                       $HCIATTACH $i
               else
                       $HCIATTACH $i >/dev/null 2>&1
               fi
	done
}

stop_uarts()
{
	killall hciattach > /dev/null 2>&1 || true
}

start_rfcomm()
{
	if [ -x $RFCOMM ] && [ -f $RFCOMM_CONF ] ; then
		# rfcomm must always succeed for now: users
		# may not yet have an rfcomm-enabled kernel
                if [ "$VERBOSE" != no ]; then
                       log_progress_msg "rfcomm"
                       $RFCOMM -f $RFCOMM_CONF bind all || true
                else
                       $RFCOMM -f $RFCOMM_CONF bind all >/dev/null 2>&1 || true
                fi
	fi
}

stop_rfcomm()
{
	if [ -x $RFCOMM ] ; then
               if [ "$VERBOSE" != no ]; then
                       log_progress_msg "rfcomm"
                       $RFCOMM unbind all || true
               else
                       $RFCOMM unbind all >/dev/null 2>&1 || true
               fi
	fi
}

restart_rfcomm()
{
	if [ -x $RFCOMM ] && [ -f $RFCOMM_CONF ] ; then
               if [ "$VERBOSE" != no ]; then
                       log_progress_msg  "rfcomm"
                       $RFCOMM unbind all || true
                       $RFCOMM -f $RFCOMM_CONF bind all || true
               else
                       $RFCOMM unbind all >/dev/null 2>&1|| true
                       $RFCOMM -f $RFCOMM_CONF bind all >/dev/null 2>&1 || true
               fi
	fi
}

case "$1" in
  start)
	log_daemon_msg "Starting $DESC"

	if test "$BLUETOOTH_ENABLED" = "0"; then
		log_progress_msg "disabled. see /etc/default/bluetooth"
		log_end_msg 0
		exit 0
	fi

	start-stop-daemon --start --quiet --exec $DAEMON || true
	log_progress_msg "bluetoothd"

	run_sdptool || true

	start_uarts || true

	if test "$HID2HCI_ENABLED" = "1"; then
		enable_hci_input || true
	fi
	start_rfcomm || true
	log_end_msg 0
    ;;
  stop)
	log_daemon_msg "Stopping $DESC"
	if test "$BLUETOOTH_ENABLED" = "0"; then
		log_progress_msg "disabled."
		log_end_msg 0
		exit 0
	fi
	stop_rfcomm || true
	if test "$HID2HCI_UNDO" = "1"; then
		disable_hci_input || true
	fi
	start-stop-daemon --stop --quiet --exec $DAEMON || true
	log_progress_msg "bluetoothd"
	stop_uarts || true
	log_end_msg 0
	;;
  restart|force-reload)
	$0 stop
	$0 start
	;;
  status)
	status_of_proc "$DAEMON" "$DESC" && exit 0 || exit $?
	;;
  *)
	N=/etc/init.d/bluetooth
	# echo "Usage: $N {start|stop|restart|reload|force-reload|status}" >&2
	echo "Usage: $N {start|stop|restart|force-reload|status}" >&2
	exit 1
	;;
esac

exit 0

# vim:noet[/SIZE][/INDENT]

So i am lost as to what to edit... will update with anything i find, but if anyone can help... awesome.

-Eric

---

### Post by Kilmarac on 2008-12-16
I hate to be a bumper, but I have the same issue just trying to get it to reconnect on reboot.  Using 8.10

---

### Post by killabee44 on 2008-12-20
I am a newbie using 8.10 as well. I was able to get my keyboard and mouse to stay connected by editing:

/etc/default/bluetooth:

HID2HCI_ENABLED=0

Made the same change in /etc/init.d/bluetooth



(Credit goes to Peabody over at kubuntuforums.net)


Now I am having a problem with getting the numberpad on my keyboard to work. I guess the numlock key doesnt work. 

If anyone can shed some light on the solution please do! Thanks.

Killabee44

---

### Post by spockrock on 2008-12-21
Hi Gents,

Ok so I had to do a fresh re-install of Hardy, and this is how I setup my mx50000 reboot and all.  Sorry I am not at my computer so the best I can do is go by memory, and screen shots from a VM.

First grab a second keyboard and mouse, plug them in, turn on the computer and login.  At this point you should see that the bluetooth mouse and keyboard are not connected, but the bluetooth icon is in your systray.

Click on the bluetooth icon in the systray and click pick setup new device, at this point you want to click the red button on the bottom of the mouse and click forward.  You should then see any bluetooth devices that are discoverable, your mouse.  Click on it follow along.  It should add the mouse and you should be able to use it as normal.  Now what you want to do is, do the same with the keyboard, the only difference between is that you will have to enter a pin.  Now to make sure the mouse and keyboard connect after a reboot, right click on the bluetooth icon and pick the preferences option and under visibility options pick always visible, that's all I did and it works like a charm.

---

### Post by killabee44 on 2008-12-21
I found the fix to my numberpad not working (I am using 8.10 intrepid). It was a simple setting. 

System Settings> keyboard and mouse> under NumLock on KDE Startup select "Turn On"


Also, under System Settings> Regional & Language> Keyboard Layout> Keyboard Model: I selected Logitech Cordless Desktop

That's it. My keypad works now. I believe it was the "turn on numlock" setting that did it. Why they would have the numlock off by default is beyond me. Anyhow, I hope this helps someone.

Killabee44

---

### Post by scarf on 2008-12-21
> **killabee44 said:**
> I am a newbie using 8.10 as well. I was able to get my keyboard and mouse to stay connected by editing:

/etc/default/bluetooth:

HID2HCI_ENABLED=0

Made the same change in /etc/init.d/bluetooth


so, is that it for 8.10?  no need to mess with any mac addresses?  it seems something is missing here......

---

### Post by killabee44 on 2008-12-22
Yep, that's all I did. I did not have to do anything with the mac addresses.

---

### Post by tankerkevo on 2008-12-22
For those currently having issues with bluetooth in Intrepid please see the following link. Please post your issues in the bug tracker along with version and hardware information. If everyone having issues reports them we will likely see a quicker resolution.

[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/306721](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/306721)



Killabee,

if you could provide the version information on your system that would help greatly as there's several of us trying to find out what we need to revert to in order to get back up and running.

Specifically your bluez, bluez-gnome, gnome-bluetooth, and kernel versions would be helpful.

Thanks!

TankerKevo

---

### Post by killabee44 on 2008-12-22
tankerkevo,

I am really very new to all this.I looked for the bluez app but could not find it. I know it is installed though because I found it in adept. I just installed bluez-gnome and gnome-bluetooth. I will see what I can do with those and post back. Thanks.

---

### Post by killabee44 on 2009-01-10
Sorry I didn't reply sooner but have been very busy and had to use my windows partition much of the time. 

Well, after a few reboots I had to re-connect using the red buttons on the bottom of my keyboard and mouse. So, forget the happiness I felt :(. I am still trying to find  a permanent solution to this problem using Intrepid 8.10. The weird thing is that I cannot find a bluetooth setting anywhere in the K menu. 

I would like to get my MX1000 mouse's buttons working properly. Right now the scroll buttons as well as the buttons next to the scroll wheel (when you lean it right or left) do not work. Is there no solid solution to get this thing working properly yet? Any input would be appreciated. Thanks.

btw.. 
Here is my /etc/default/bluetooth file: 

# Defaults for bluez

# start bluetooth on boot?
# compatibility note: If this variable is not found bluetooth will
# start
BLUETOOTH_ENABLED=1

# This setting will switch HID devices (e.g mouse/keyboad) to HCI mode, that is
# you will have bluetooth functionality from your dongle instead of only HID.
# Note that not every bluetooth dongle is capable of switching back to HID
# mode, see [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=355497](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=355497)
HID2HCI_ENABLED=0
HID2HCI_UNDO=1

As far as the bluez, bluez-gnome, gnome-bluetooth files go, I only found folders for those. Could it be that I looked in the wrong places? Please clarify.

Killabee44

---

### Post by scarf on 2009-01-10
> **killabee44 said:**
> Yep, that's all I did. I did not have to do anything with the mac addresses.

yes but i still don't see any bluetooth devices listed in the little bluetooth app (system > prefs > bluetooth), so i think they are still not using bluetooth connection.

---

### Post by killabee44 on 2009-01-10
Scarf,

I do not see a bluetooth setting at all. Maybe there is something I need to install, but I would think that bluetooth would be a standard to include (I am using Intrepid 8.10). Can anyone using Intrepid shed any light on where the bluetooth settings are located?

Also, I am curious as to why the keyboard and mouse work if they are not using bluetooth. Is the MX5000 combo capable of using 2.4mhz when bluetooth is not available? If so, it is something I did not know. It is somehting I suspected, but I looked around and did not find any info on this.

---

### Post by scarf on 2009-01-11
> **killabee44 said:**
> Scarf,

I do not see a bluetooth setting at all. Maybe there is something I need to install, but I would think that bluetooth would be a standard to include (I am using Intrepid 8.10). Can anyone using Intrepid shed any light on where the bluetooth settings are located?

i am just talking about the thing in system > preferences > bluetooth.  i have told it to always display an icon.  now, right-click on the icon, go to setup new device, and it isn't detecting any logitech keyboard/mouse.


> **killabee44 said:**
> Also, I am curious as to why the keyboard and mouse work if they are not using bluetooth. Is the MX5000 combo capable of using 2.4mhz when bluetooth is not available? If so, it is something I did not know. It is somehting I suspected, but I looked around and did not find any info on this.

this is the same reason the keyboard works in your BIOS, etc. before any bluetooth support is loaded.  there is some fallback protocol to use or something, i think i read about it in a previous post. (i don't know anything about bluetooth ;))

---

### Post by killabee44 on 2009-01-11
I am using 8.10 and when I click on Kmenu> Applications >system I do not see a preferences icon, only a "system settings" one. Now when I clicked on Kmenu then went up top to the search bar and typed in bluetooth I see two options. One is "Bluetooth File Sharing" and the other is "KDEBluetooth4". When I click on the KDEBluethooth4 nothing happens.

After all this I am still trying to find the damn bluetooth icon.. lol.

That makes sense about the fallback, so that the kbd would work in the bios.

---

### Post by scarf on 2009-01-12
> **killabee44 said:**
> I am using 8.10 and when I click on Kmenu> Applications >system I do not see a preferences icon, only a "system settings" one. Now when I clicked on Kmenu then went up top to the search bar and typed in bluetooth I see two options. One is "Bluetooth File Sharing" and the other is "KDEBluetooth4". When I click on the KDEBluethooth4 nothing happens.

oh sorry that is because i am using the gnome version of ubuntu.  the command that is executed is /usr/bin/bluetooth-properties

---

### Post by killabee44 on 2009-01-12
Ok, when I excecute that command I get a bluetooth preferences window but all it shows are three bullet options to choose from: General tab: Notification area: 

     never display icon
     only display when adapter present (selected)
     Always display Icon

I changed it to "always display icon" but I still see no icon. I will reboot.

---

### Post by scarf on 2009-01-18
> **killabee44 said:**
> Ok, when I excecute that command I get a bluetooth preferences window but all it shows are three bullet options to choose from: General tab: Notification area: 

     never display icon
     only display when adapter present (selected)
     Always display Icon

I changed it to "always display icon" but I still see no icon. I will reboot.

it will probably only work in a GNOME session.  trying changing your session at the login window.

---

### Post by scarf on 2009-01-18
ok my mouse has been laggy, intermittently.  for example, i move the mouse across the screen, i stop moving the physical mouse in my hand, but the cursor on the screen keeps moving, playing catch up.

it appears to happen when there is some intensive process running.  however, this is a new system with amd 9950 cpu and 4 gb of ram, so i don't see how that is a problem.

do you think this is related to the mouse not connecting via bluetooth?  if so, i would really like to get this fixed, because it's very annoying and i can't use the system very well when this mouse lag is going on.

---

### Post by killabee44 on 2009-01-19
Honestly, I don't know what is causing that. Seems unrelated to the other issue. I havent seen this or read about it while searching for an answer to the bluetooth connection problems.

---

### Post by scarf on 2009-08-10
i don't think the bluetooth API is necessary, as the bluetooth connection for this keyboard is handled by the USB dongle that comes with it.  so my comments above regarding the bluetooth app and icon, etc., can probably be ignored.  i understand now that that is for computers with a built-in bluetooth radio.

---

### Post by scarf on 2010-02-09
i recently updated to jaunty 9.04 and now my number pad is not working.

it wasn't controlling the mouse either, but it just seems that NumLock was off, as when i pressed the "4" it moved the (keyboard) cursor to the left, "6" moved the cursor to the right, etc.

however, this keyboard isn't supposed to have a NumLock.  there's no NumLock key.  the number pad is kind of just "always on".

i was able to fix it by pushing the calculator button twice.  now the number pad is producing numbers.  not sure if it'll survive a reboot.

although it would be nice to just find out if there is a way to toggle NumLock and obtain this standard functionality which was left out of these keyboards.  i tried pushing the calculator button some more but it seems to just be spitting out numbers now.

---

### Post by deibu76 on 2010-04-02
I got bluetooth connectivity to work with my MX5000's USB dongle a few months ago under Karmic after checking out this thread, so I'd like to send out a big THANK YOU all the helpful advice many of you have given on this thread!

When I got a new computer in January, I never managed to get it to work again - although I admit I didn't spend much time trying - the RF connection has been good enough most of the time, and I spent a lot of time in Windows 7 for a while :oops:.

Anyway, just thought I'd mention that the MX5000's bluetooth dongle works with no trouble at all out-of-the-box with a fresh Lucid beta install and the latest bluez package updates.  The keyboard & mouse pair up with no trouble.  No need to install blueman, although it works fine with the latest blueman package as well.

On the keyboard, the number pad is working as intended and a few of the button functions work - the "E-Mail" button loads Evolution.  The touch functions for volume & media controls also work great!  

The mouse functions all seem to be working properly as well!  Zoom still doesn't function on either the keyboard's touch-function or by clicking & scrolling the mouse way, but that's not a big deal to me since I accidentally hit it all the time, and I'm more used to Ctrl-+/Ctrl-- in Firefox & now Chrome.  

Also managed to pair w/ my Blackberry Curve and I'm in the process of setting up the remote control functionality.

Not sure if this belongs in the Lucid thread, but I thought I'd let everyone know that this problem seems to be solved.

---

### Post by Automat2 on 2010-04-07
deibu76, does the LCD panel and the four little buttons under the panel work?

---

### Post by guyver on 2010-05-02
When I do the "sudo hidd -search" command, I get an error stating command not found.

I'm using a fresh install of 10.04 and the bluetooth software endlessly tries looking for my bluetooth mouse (even though I have clicked on the button at the bottom of my mouse to make it discoverable).

I have tried the following "solutions" with no success:

[http://ubuntuforums.org/showpost.php?p=9209694&postcount=9](http://ubuntuforums.org/showpost.php?p=9209694&postcount=9)

[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/550288/comments/10](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/550288/comments/10)

Any help would be greatly appreciated.

---

### Post by deibu76 on 2010-05-29
> **Automat2 said:**
> deibu76, does the LCD panel and the four little buttons under the panel work?

Sorry I've taken so long to respond...  

I think in USB mode you get the temperature, but in bluetooth mode the display shows nothing but "Logitech MX 5000" and those buttons do nothing.  I managed to "customize" the LCD display on my last laptop w/ Karmic about 6 mos. ago - nothing special - just a static custom phrase like "Hello Dave" or "Finger My Keys"... lol.  Never tried to get any kind of "dynamic" displays - like room temperature, email alerts, playlist or anything like that.  Besides room temp, I've never really found the LCD useful so it hasn't been worth fooling around with (to me, at least) so I don't miss it much at all.  

Since the previous post, I have had some problems syncing w/ the keyboard (the mouse works fine).  Sometimes the keyboard does not work at login, so I have to use the laptop keyboard instead.  After logging in, I press the sync button on the bottom of the keyboard & go to the bluetooth panel icon and select "Connect" - then the keyboard will say "Connected" - but the bluetooth app will ask me to enter a passcode and the keyboard will say "Not connected" a few seconds later.  The solution has been to just remove the keyboard from the device list and use the "Setup new device" wizard and it finds it & sets it right back up.

OTOH, I definitely don't miss having to deal with Logitech's bloated drivers & annoying software in Windows!

---

### Post by Automat2 on 2010-06-16
> **deibu76 said:**
> 
 Besides room temp, I've never really found the LCD useful so it hasn't been worth fooling around with (to me, at least) so I don't miss it much at all.  

Apart from the temperature, I miss the name of the account you're using and the date and time. I have both  panels on auto-hide so I have to move the mouse to the top. LOL!

With regards to the procedure of reconnecting the keyboard, I have to do that too. Remove the keyboard from the list of devices already paired and re-pair it again.

But I haven't been able to connect the keyboard, or the mouse, on Lucid unless is via BT. I don't know why it was possible on Karmic and not on Lucid.

---

### Post by deibu76 on 2010-06-19
> **Automat2 said:**
> Apart from the temperature, I miss the name of the account you're using and the date and time. I have both  panels on auto-hide so I have to move the mouse to the top. LOL!

With regards to the procedure of reconnecting the keyboard, I have to do that too. Remove the keyboard from the list of devices already paired and re-pair it again.

But I haven't been able to connect the keyboard, or the mouse, on Lucid unless is via BT. I don't know why it was possible on Karmic and not on Lucid.

Tonight I tried to get the display working and finally found this thread, which I believe was what I used to get it working under Karmic - [http://ubuntuforums.org/showthread.php?t=860707&page=2]("http://ubuntuforums.org/showthread.php?t=860707&page=2").  It didn't work though - I read through the thread and figured out it only worked for USB and not BT mode.

Also, noticed the "Super" (or "Windows") key does not work either.

---

