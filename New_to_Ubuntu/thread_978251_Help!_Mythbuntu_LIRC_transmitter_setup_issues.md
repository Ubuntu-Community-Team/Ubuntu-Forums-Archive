---
title: "Help! Mythbuntu LIRC transmitter setup issues"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by gelli on 2008-11-10
Hello all, I am new to this forum/linux/ubuntu/etc and I must say I like the look of what I see, I am however very frustrated after trying to get my mythbuntu system setup without help. I have got most of the system setup, but cannot seem to figure out the LIRC transmitter bit working. My remote (Windows MCE USB by Anyware/Mediagate GP-IR02BK)seems ok with maybe a few keymapping issues. I tried IR transmitter from the bundled remote  and cannot get it working. My main problem is understanding how all the LIRC/Transmitter/receiver config and script files stick together. My cable box is a Scientific Atlanta Explorer 3250 and I simply want to change the channels on it. Below is my hardware.conf file, maybe someone can tell me if theres anything wrong! Any help is appreciated. 
Wantobee linux expert....:)

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Remotes (new version Philips et al.)"
REMOTE_MODULES="lirc_dev lirc_mceusb2"
REMOTE_DRIVER=""
REMOTE_DEVICE=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Microsoft Windows Media Center V2 (usb) : Scientific Atlanta Cable box"
TRANSMITTER_MODULES="lirc_dev lirc_mceusb2"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF="scientificatlanta/general.conf"
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

---

### Post by gelli on 2008-11-11
Ok no response?? Maybe I was not clear??
Mythbuntu 8.04 LIRC is failing to load!

~$ sudo /etc/init.d/lirc restart verbose
 * Stopping remote control daemon(s): LIRC   [fail] 
 * Loading LIRC modules                      [ OK ] 
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf

I am still unsure what is wrong. My assumption to how this stick together is .....
The /etc/lirc/lircd.conf file looks at the /etc/lirc/hardware.conf file which looks at the 2 Files....
/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb (Remote)
/usr/share/lirc/transmitters/scientificatlanta/general.conf (Transmitter)

The change-channel-lirc.pl file then looks at the Remote name in the transmitter file above.

Seen as though my remote(receiver) works, I cannot explain the LIRC failure above. If LIRC fails to load, then my remote should not work??

---

### Post by gelli on 2008-11-20
OK!! Still no assistance!! I will just talk to myself!
I upgraded my ubuntu to 8.10 Intrepid and had no luck!!

root@Mythbuntu_Main:/home/gelliott# sudo /etc/init.d/lirc start
 * Loading LIRC modules                                                       [ OK ] 
 * Starting remote control daemon(s) : LIRC                                   [fail] 

I ran IRW and tested the remote and it works fine!!

I ran a $ dmesg and picked out all the LIRC references(See below).
Can anyone tell me if they see anything wrong??

[   20.114844] lirc_dev: IR Remote Control driver registered, major 61
[   20.283764] lirc_mceusb2: Philips eHome USB IR Transceiver and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.44 $
[   20.283768] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[   20.480096] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[   20.637673] lirc_dev: lirc_register_plugin: sample_rate: 0
[   20.641673] lirc_mceusb2[3]: Topseed Technology Corp. eHome Infrared Transceiver on usb2:3[   20.283764] lirc_mceusb2: Philips eHome USB IR Transceiver and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.44 $
[   20.283768] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[   20.480096] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[   20.637673] lirc_dev: lirc_register_plugin: sample_rate: 0
[   20.641673] lirc_mceusb2[3]: Topseed Technology Corp. eHome Infrared Transceiver on usb2:3
[   22.315177] usbcore: registered new interface driver lirc_mceusb2

---

### Post by Keith_Beef on 2008-11-22
I understand your frustration! I'm trying to get a Streamzap to work in Intrepid Ibex (Ubuntu 8.10).

I can find no really obviously broken mechanism, configuration files seem to be correct, yet I can't control any programs. This makes me think that I need to tell each program to listen to the IR remote controller, but I can't find out how.

I linked /dev/lirc to /dev/lirc0 when I saw messages that /dev/lirc did not exist.

```
cd /dev
sudo ln -s lirc0 lirc
```

Then I started irrecord and followed the instructions to generate a config file for the controller / receiver.

```
sudo irrecord test

```

This got me a file named test, when I compare this to the stock /usr/share/lirc/remotes/streamzap/lircd.conf.streamzap configuration file, there is not much difference (well, I named all the buttons in lower case...).

```
diff /usr/share/lirc/remotes/streamzap/lircd.conf.streamzap test
..snip..
30c32,33
<           0                        0x00
---
>           power                    0x0A
>           mute                     0x0B
40,47c43,51
<           POWER                    0x0A
<           MUTE                     0x0B
<           CH_UP                    0x0C
<           VOL_UP                   0x0D
<           CH_DOWN                  0x0E
<           VOL_DOWN                 0x0F
<           UP                       0x10
<           LEFT                     0x11
---
>           0                        0x00
>           vol_up                   0x0D
>           vol_down                 0x0F
>           ch_up                    0x0C
>           ch_down                  0x0E
>           cursor_up                0x10
>           cursor_down              0x14
>           cursor_right             0x13
>           cursor_left              0x11
```

This is very reassuring, but still doesn't get me a functioning set-up.

I still can't get lircd to start, for example.

```

$ sudo /etc/init.d/lirc restart --verbose
 * Stopping remote control daemon(s): LIRC                                                                                  [fail] 
 * Loading LIRC modules                                                                                                     [ OK ] 
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf
```

But when I look inside hardware.conf, I can't see anything out of place...

```
$ more /etc/lirc/hardware.conf
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Streamzap PC Remote"
REMOTE_MODULES="lirc_streamzap"
REMOTE_DRIVER="default"
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD=true

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

# Remote settings required by gnome-lirc-properties
REMOTE_MODEL="PC Remote"
REMOTE_VENDOR="Streamzap"

# Receiver settings required by gnome-lirc-properties
RECEIVER_MODEL="PC Remote"
RECEIVER_VENDOR="StreamZap"
```

And I think that the kernel modules are loaded, anyway.

```
$ lsmod | grep lirc
lirc_streamzap         22916  0 
lirc_dev               22216  1 lirc_streamzap
usbcore               175376  8 lirc_streamzap,usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd
```

Oh, but here's a thing, I think lircd really is running already!
```
ps -edf | grep lirc
nobody    6838     1  0 14:04 ?        00:00:00 /usr/sbin/inputlircd /dev/input/event0 /dev/input/event1 /dev/input/event3 /dev/input/event4 /dev/input/event5 /dev/input/event6
```

So what's going on, here?

K.

---

### Post by gelli on 2008-11-24
After abit more fiddling, I think my LIRC is loading fine!

I am however still not getting any responce on my IR Blaster/Transmitter.

root@Mythbuntu_Main:/home/gelliott# irsend SEND_ONCE SAE8000 Power

Looked for any response from this command and nothing!!

I have not seen if anyone has got the Mediagate GP-IR02BK Remote blaster working with Mythbuntu 8.10 and if they are , what drivers they are using!

Cheers for your interest! Sorry that I am unable to help you with your issues, Im just a novice here. 

I wish these Mythbuntu guys would do a better job of explaining how the LIRC files/services all stick together, that way you can try to figure out where you going wrong! I could rant all day about how this all stick together!

---

### Post by Hobgoblin on 2008-11-24
> **gelli said:**
> Ok no response?? Maybe I was not clear??
Mythbuntu 8.04 LIRC is failing to load!

~$ sudo /etc/init.d/lirc restart verbose
 * Stopping remote control daemon(s): LIRC   [fail] 
 * Loading LIRC modules                      [ OK ] 
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf


I had this problem, or very similar.

The first time I installed LIRC I didn't bother choosing a device in the setup scripts because my system wasn't listed and I figured I would be setting it up manually.

I completely removed LIRC and it's config files then installed again but this time selected the nearest match for the remote device.

Hope I'm making sense, it's been a long night and it's nearly bedtime.

---

### Post by Keith_Beef on 2008-12-21
> **Hobgoblin said:**
> I had this problem, or very similar.

The first time I installed LIRC I didn't bother choosing a device in the setup scripts because my system wasn't listed and I figured I would be setting it up manually.

I completely removed LIRC and it's config files then installed again but this time selected the nearest match for the remote device.

Hope I'm making sense, it's been a long night and it's nearly bedtime.

I removed all LIRC packages and Elisa packages. Then I reisntalled LIRC followed by Elisa.

No joy...

Administration -> Infrared Remote Control finds the Stramzap on /dev/lirc0 and when I press buttons the Configuration Test area displays strings corresponding to the keys I press... so that side of things is working.

But Elisa does not react, nor does oxine. :(

My .elisa-0.5/elisa_0_5_6.conf contains this line:
```
input_providers = ['winremote.streamzap_input:StreamzapInput', 'lirc.lirc_input:LircInput']
```
so I don't see what else I can do...

K.

---

### Post by nerver on 2009-03-03
Hey gelli,

Did you ever manage to get the transmitter working for this remote? I just bought the same one the other day (GP-IR02BK) and while the receiver works fine out of the box I cannot for the life of me get the transmitter to work. I've tried everything I can think of so if you've managed to get yours working I'd love to hear how you did it.

Cheers,
-Sean

---

### Post by DLotus on 2010-06-18
Hello everyone,
I also recently bought a GP-IR02BK remote/blaster. The remote works great with 10.04 Mythbuntu 64bit, however I'm still having problems getting the blaster portion to work. I bought this to replace the blaster from the hauppauge HD-PVR due to the known problems everyone is having with the hauppauge blaster with it freezing / locking up the box.

Thanks for the input

dlotus

---

### Post by nerver on 2010-06-22
Hey DLotus,

I'm pretty sure the transmitter for this remote just does not work with lirc using the mceusb drivers. I tried for quite some time last year and was never able ot get it going. If you have the option, I'd recommend taking it back and getting one of the Microsoft remote/transmitters (they work out of the box with no issues) or a different brand that works out of the box (I think most do, the GP-IR02BK is the only one I've had issue with so far).

Sorry I couldn't be of more help.
-Sean

---

