---
title: "Siano Mobile Silicon DVB T Stick NO USEABLE TERRESTRIAL CARD FOUND"
date: 2019-06-02
forum: New to Ubuntu
---

### Post by zorion on 2019-06-02
[COLOR=#000000][FONT=sans-serif]Hi, before explaining my problem, I want to report that despite spending time going back and forth between different distros but I am noob in terms of commands. (And I do not know much English either.)[/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]These are some threads that are related to the subject, but that I do not understand because of my lack of knowledge about it.[/FONT][/COLOR]

[https://www.linuxquestions.org/quest...ng-4175592978/]("https://www.linuxquestions.org/questions/slackware-14/conceptronic-digital-hdtv-receiver-not-working-4175592978/")

[https://ubuntuforums.org/showthread.php?t=2260467](https://ubuntuforums.org/showthread.php?t=2260467)

[https://forums.openpli.org/topic/597...0/#entry883693]("https://forums.openpli.org/topic/59797-vu-zero-4k-and-usb-isdbt-tuner-mygica-s270/#entry883693")

[COLOR=#000000][FONT=sans-serif]Some data:[/FONT][/COLOR]

[COLOR=#000000][FONT=monospace][COLOR=#54FF54]**zorion@zorion-desktop**[/COLOR]:[COLOR=#5454FF]**~**[/COLOR]$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 187f:0600 Siano Mobile Silicon 
Bus 002 Device 002: ID 0480:0900 Toshiba America Inc 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0000:0538 
Bus 003 Device 002: ID 04d9:a09a Holtek Semiconductor, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

[/FONT][/COLOR][COLOR=#000000][FONT=monospace][COLOR=#54FF54]**zorion@zorion-desktop**[/COLOR]:[COLOR=#5454FF]**~**[/COLOR]$ dmesg | grep DVB 
[ 18.216267] dvbdev: [COLOR=#FF5454]**DVB**[/COLOR]: registering new adapter (Siano Rio Digital Receiver) 
[ 18.216380] usb 2-4: [COLOR=#FF5454]**DVB**[/COLOR]: registering adapter 0 frontend 0 (Siano Mobile Digital MDTV Receiver)... 
[ 18.216414] smsdvb:smsdvb_hotplug: [COLOR=#FF5454]**DVB**[/COLOR] interface registered.

[/FONT][/COLOR][COLOR=#000000][FONT=monospace][COLOR=#18B218][ 17.340357] [/COLOR][COLOR=#B26818]smsmdtv:smscore_init_ir[/COLOR]: IR port has not been detected 
[COLOR=#18B218][ 17.340359] [/COLOR][COLOR=#B26818]smsusb:smsusb_probe[/COLOR]: Device initialized with return code 0 
[COLOR=#18B218][ 18.216267] [/COLOR][COLOR=#B26818]dvbdev[/COLOR]: DVB: registering new adapter (Siano Rio Digital Receiver) 
[COLOR=#18B218][ 18.216380] [/COLOR][COLOR=#B26818]usb 2-4[/COLOR]: DVB: registering adapter 0 frontend 0 (Siano Mobile Digital MDTV Receiver)... 
[COLOR=#18B218][ 18.216414] [/COLOR][COLOR=#B26818]smsdvb:smsdvb_hotplug[/COLOR]: DVB interface registered. 
[COLOR=#18B218][ 18.216627] [/COLOR][COLOR=#B26818]usbcore[/COLOR]: registered new interface driver smsusb

[/FONT][/COLOR][COLOR=#000000][FONT=monospace][COLOR=#54FF54]**zorion@zorion-desktop**[/COLOR]:[COLOR=#5454FF]**~**[/COLOR]$ lsmod | grep sms
[COLOR=#FF5454]**sms**[/COLOR]dvb 28672 0
dvb_core 126976 1 [COLOR=#FF5454]**sms**[/COLOR]dvb
[COLOR=#FF5454]**sms**[/COLOR]usb 24576 0
[COLOR=#FF5454]**sms**[/COLOR]mdtv 65536 2 [COLOR=#FF5454]**sms**[/COLOR]usb,[COLOR=#FF5454]**sms**[/COLOR]dvb
rc_core 45056 1 [COLOR=#FF5454]**sms**[/COLOR]mdtv

[/FONT][/COLOR][COLOR=#000000][FONT=monospace][COLOR=#54FF54]**zorion@zorion-desktop**[/COLOR]:[COLOR=#5454FF]**~**[/COLOR]$ w_scan -c ES
w_scan -c ES 
w_scan version 20170107 (compiled for DVB API 5.10)
using settings for SPAIN
DVB aerial
DVB-T Europe
scan type TERRESTRIAL, channellist 4
output format vdr-2.0
output charset 'UTF-8', use -C <charset> to override
Info: using DVB adapter auto detection.
/dev/dvb/adapter0/frontend0 -> "Siano Mobile Digital MDTV Receiver" doesnt support TERRESTRIAL -> SEARCH 
NEXT ONE.
main:4007: FATAL: ***** NO USEABLE TERRESTRIAL CARD FOUND. *****
Please check wether dvb driver is loaded and
verify that no dvb application (i.e. vdr) is running.
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]
[/FONT][/COLOR][COLOR=#000000][FONT=sans-serif]And from here I do not know how to pass.[/FONT][/COLOR]

---

