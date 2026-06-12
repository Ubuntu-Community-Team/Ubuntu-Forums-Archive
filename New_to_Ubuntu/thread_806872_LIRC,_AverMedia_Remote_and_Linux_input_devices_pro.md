---
title: "LIRC, AverMedia Remote and Linux input devices problem"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by OlegVekhov on 2008-05-25
Hello! I have some knoweledge in Linux and Ubuntu, but LIRC and Remotes are far from my mind...

I have AverMedia AverTV Studio 203 and remote controller for it. The remote is just works, even without LIRC, through /dev/input/eventX (event6 for me). Remote threated as linux input device, and 50% of buttons work and can be mapped via gnome-keybindings-properties.

So I want to try more complex configurations... Where should I start?

I've installed lirc, lircd starts without errors... So when I try, for example, enable IR in totem, it says "unable to read lirc configuration". In rhytmbox plugin activates with success, but no configuration interface is provided, and only keys defined in gnome-keybindings are works.

Here is my hardware.conf from LIRC
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="AverMedia TV card (TVCapture98 TVPhone98) (card 13/41)"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event6"
REMOTE_LIRCD_CONF="avermedia/lircd.conf.avermedia98"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
START_LIRCMD="true"

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

# Receiver settings required by gnome-lirc-properties
RECEIVER_MODEL="A4Tech RF USB Receiver"
RECEIVER_VENDOR="Linux Input Device"

# Remote settings required by gnome-lirc-properties
REMOTE_MODEL="TVCapture98"
REMOTE_VENDOR="AVerMedia"

```

---

