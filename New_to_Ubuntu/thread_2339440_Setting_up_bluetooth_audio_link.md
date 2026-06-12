---
title: "Setting up bluetooth audio link"
date: 2016-10-08
forum: New to Ubuntu
---

### Post by nginmu on 2016-10-08
I have a virgin install of lubuntu 16.04.1 on a compaq presario v6000 laptop.

I've attached the following usb bluetooth adapter:

 Belkin
Bluetooth USB +EDR Adapter Class 1 v2.1 UHE
Broadcom BCM2046 B1
USB\VID_050D&PID_0017&REV_0291
Model: F8T017
FCC ID K7SF8T017

I can connect to my sony android phone using this adapter & pair, send and receive files ok.

What I'm trying to ultimately achieve is, as simple a link as possible from something like VLC media player on the laptop, through bluetooth, to a small bluetooth adapter labelled as "2-in-1 bluetooth transmitter and receiver BT602". This is the item: [http://www.ebay.co.uk/itm/272376789222](http://www.ebay.co.uk/itm/272376789222)

I'm hoping to use the BT602 in receiver mode, and plug my hifi amp's 3.5mm stereo jack input lead into it, and hear whatever VLC's playing on the laptop.

When I started looking into it on google etc though, I became somewhat lost in discussions of pulseaudio etc..

How should I be going about setting this up as easily as possible? (it just started out as a way of trying to avoid drilling holes and running cables throughout the walls)

---

### Post by nginmu on 2016-10-09
Ok VLC busy playing The Cure, it's coming out of the laptop speakers. Belkin bluetooth USB dongle alive on laptop & successfully paired with BT602 receiver. Hifi plugged into BT602 & volume up.

No sound out of hifi :-(

I tried selecting 'pulseaudio sound server' in VLC's 'Audio Device' menu but it came back with:

```

 [COLOR=#ff0000]Audio output failed:[/COLOR]
 [COLOR=#000000]The audio device "pulse" could not be used:[/COLOR]
 [COLOR=#000000]Connection refused.[/COLOR]


```

Also when I try using the bluetooth manager to 'connect sound sink' I get:

```

Connection Failed: blueman.bluez.errors.DBusFailedError: Protocol not available...

```

If I try the bluetooth 'setup new device' screen I get

```

Device added successfully, but failed to connect

```

'Bluetooth Devices' on the laptop appears to have found two devices despite the fact I'm sat in a field with nothing bar the laptop itself, and the bluetooth audio receiver:

- 00-11-22-33-34-c9 BT602 "headset" (well that's the receiver I'm sure)
- 00-00-00-00-00-00 "unknown" .... ?

I've been trying all my efforts with the BT602 device; the "unknown" one doesn't seem to want to connect.

Help, I'm lost now :-(

(do I need to install/configure pulseaudio or something, or am I going about this entirely the wrong way, etc?)

---

### Post by jeremy31 on 2016-10-09
The failed to connect might mean that module-bluetooth-discover is not loaded in pulseaudio, check ```
pactl list short | grep module-bluetooth
```
If it isn't loaded ```
pactl load-module module-bluetooth-discover
```

Then pair with the device

---

### Post by nginmu on 2016-10-09
```

me@pc:~$ pactl list short | grep module-bluetooth
The program 'pactl' is currently not installed. You can install it by typing:
sudo apt install pulseaudio-utils
me@pc:~$ 

```

Because I've not been sure whether pulseaudio is actually what I need or not, I've never done anything specifically to install it. Would that be the reason for the above response to the command? Should I just go ahead and sudo apt install pulseaudio-utils as it suggests, or should I do something different in the light of the error?

---

### Post by nginmu on 2016-10-09
Ok I went ahead and installed pulseaudio via synaptic. That seemed to include pulseaudio-utils.

Then I got..

```

me@pc:~$ pactl list short | grep module-bluetooth
me@pc:~$ pactl load-module module-bluetooth-discover
Failure: Module initialisation failed
me@pc:~$ 

```

---

### Post by jeremy31 on 2016-10-09
Try a reboot and see if the module loads.  Strange that you had to install pulseaudio and the utils unless it is something with Lubuntu

---

### Post by nginmu on 2016-10-09
Rebooted, same again :-(

```

me@pc:~$ pactl list short | grep module-bluetooth
me@pc:~$ pactl load-module module-bluetooth-discover
Failure: Module initialisation failed
me@pc:~$ 

```

Tried this, but much the same,

```

me@pc:~$ sudo apt install pulseaudio-utils
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pulseaudio-utils is already the newest version (1:8.0-0ubuntu3).
pulseaudio-utils set to manually installed.
0 to upgrade, 0 to newly install, 0 to remove and 4 not to upgrade.
me@pc:~$ 

```

The option for 'pulseaudio sound server' in VLC's audio device menu seems to have disappeared now, along with a slew of other options, leaving just one preselected option "built-in audio analog stereo".

So I went back to synaptic and 'completely removed' pulseaudio, rebooted, checked in VLC again and all the audio device menu options were back again. Pulseaudio sound server along with a whole long list of items (speakers, outputs, mixers, digital and analog etc) all prefaced with HDA Intel, CX20549.......

Don't know where to go from here with it. Wondering if, I've bought a device here that's not linux-friendly?

---

### Post by nginmu on 2016-10-10
Do I need to re-add the pulseaudio back into VLC with this [https://apps.ubuntu.com/cat/applications/vlc-plugin-pulse/](https://apps.ubuntu.com/cat/applications/vlc-plugin-pulse/) ?

Just seems strange.

---

### Post by jeremy31 on 2016-10-27
I would try a new download of lubuntu 16.04.1 and reinstall

---

