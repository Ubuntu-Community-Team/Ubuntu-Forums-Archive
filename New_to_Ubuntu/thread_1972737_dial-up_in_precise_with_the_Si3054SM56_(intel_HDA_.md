---
title: "dial-up in precise with the Si3054/SM56 (intel HDA host)"
date: 2012-05-03
forum: New to Ubuntu
---

### Post by sir_cheats_a_lot on 2012-05-03
Has anyone had any luck in precise?   It's been driving me nuts for the last couple weeks.  I've the smartlink driver from the repository installed, along with wvdial, and all dependencies(that I'm aware of) that pertain to it.  for whatever reason wvdial checks for a carrier regardless if the option to disable it is there in the config file.  I'm guessing this is the biggest cause of the trouble.  it dials once, responds with  NO CARRIER!, retrying, then comes back with NO DIALTONE(which is bogus, as I can hear it plainly on the phone itself, when I listen in) and exits.

scan modem's useful output

```
The modem cards detected by "aplay -l"  are: 
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]

The /proc/asound/pcm file reports:
-----------------------
00-00: STAC92xx Analog : STAC92xx Analog : playback 1 : capture 1
00-06: Si3054 Modem : Si3054 Modem : playback 1 : capture 1

about /proc/asound/cards:
------------------------
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd4240000 irq 43

 PCI slot 00:1b.0 has a High Definition Audio Card
 The drivers are in the kernel modules tree at:
 /lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/hda/snd-hda-intel.ko
 The modem codec file for the HDA card is: /proc/asound/card0/codec#1
--------------------------------------------------------
Codec: Motorola Si3054
Address: 1
MFG Function Id: 0x2 (unsol 1)
Vendor Id: 0x10573057
Subsystem Id: 0x00010001
Revision Id: 0x100100
Modem Function Group: 0x1

 The audio card hosts a softmodem chip:  0x10573057

```

Speccy identifies it as the Motorola SM56 Data Fax Modem...but hey what does it know right? :P
anyway, here's my wvdial.conf file(user data omitted) 

```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Password = ****
Phone = 9265000
New PPPD = 1
Stupid Mode = 1
Baud = 115200
Auto DNS = 1
Modem = /dev/ttySL0
ISDN = 0
Carrier Check = 0
Username = *****@******.com

```

I doubt I'll be the last with this problematic card, so lets get this resolved, so everyone else may rest easy ;)  oh, and one important note: this is a laptop, and I'm in a fairly rural area(dial-up is my only choice). . .you know, to prevent people from suggesting I get some form of broadband, or swapping modems(because I obviously can't).
oh, yes, and I've attached the lshw output in a separate txt file to save space...though I doubt it'll be useful.  I just prefer not to need to use my old gateway desktop to get online via crossover cable...bad enough I have to do that on my eMac.  I'd just like to get the internal modem going for a change is all(works fine in windows 8 thankfully).   of course it doesn't help that the smartlink modem daemon/driver hasn't been updated in well over a year...

---

### Post by lkraemer on 2012-05-05
Michigander,
I have an OLD guide on the SM56 posted at:
[http://ubuntuforums.org/showthread.php?t=1100310&highlight=SM56](http://ubuntuforums.org/showthread.php?t=1100310&highlight=SM56)
Posting #4

It has a few sections that need to be updated for the current versions, but most folks are not using modems now.

If you just skip the section noted below:
> 
You also need to do this after wvdial is installed and
after pppconfig is executed:
To enable dialout without Root permission do:
$ su - root (not for Ubuntu)
sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
sudo chmod a+x /usr/sbin/pppd

and take note that the file format has changes for the pap-secrets file, you should be able to follow along.

I'd think that either your pppd file is set up incorrectly, or your login & password is incorrect, or you aren't actually
connecting to the Dialup Service you assume you are dialing into.  What are your error messages when it disconnects?


Also, the loggedinuser needs to be added to dip and dialout.  Plus your RS-232C Port needs the proper permissions to allow
you to use it for communications.

[http://ubuntuforums.org/showthread.php?t=1072561&highlight=OUTBOUND+connections](http://ubuntuforums.org/showthread.php?t=1072561&highlight=OUTBOUND+connections)


Let us know how it's going.


lk - Wurtsmith AFB, Oscoda, MI 1972-1975

ps. Both DAYS of Summer were NICE - July 3rd & 4th..........

---

### Post by sir_cheats_a_lot on 2012-05-05
that's sort of the gripe of the whole situation: there wasn't so much as an error message. An error message I could work with, but nothing, just " no carrier"-which it shouldn't be checking for anyway- followed by a retry "no dialtone".  I think the second message is a result of wvdial failing to hangup, before retrying, which I've never seen happen before.

It's a free dialup service called dialinfree(only available in michigan).  never had a problem with it on my desktop.  never really had an issue with dialup on Ubuntu aside from having to nuke network manager in older versions of Ubuntu to get it dialup working at all with the serial modem.  no idea why it was the case, but something changed between dapper and hardy that made it that way.

in any case, I noticed something last night; curiously enough my chap-secrets file is pretty much empty and unconfigured.  I edited it a bit, saved, retried the connection, still no love. *sighs* 

the log file I made for wvdial:
```
--> WvDial: Internet dialer version 1.61
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT9265000
--> Waiting for carrier.
ATDT9265000
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT9265000
--> Waiting for carrier.
ATDT9265000
NO DIALTONE
--> No dial tone.
--> Disconnecting at Sat Apr 28 15:27:47 2012

```

while I'm at it, wvdialconf.log
```
 sudo wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   S4   S5   S6   S7   
Modem Port Scan<*1>: S8   S9   S10  S11  S12  S13  S14  S15  
Modem Port Scan<*1>: S16  S17  S18  S19  S20  S21  S22  S23  
Modem Port Scan<*1>: S24  S25  S26  S27  S28  S29  S30  S31  
WvModem<*1>: Cannot get information for serial port.
ttySL0<*1>: ATQ0 V1 E1 -- OK
ttySL0<*1>: ATQ0 V1 E1 Z -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttySL0<*1>: Modem Identifier: ATI -- SmartLink Soft Modem
ttySL0<*1>: Speed 4800: AT -- OK
ttySL0<*1>: Speed 9600: AT -- OK
ttySL0<*1>: Speed 19200: AT -- OK
ttySL0<*1>: Speed 38400: AT -- OK
ttySL0<*1>: Speed 57600: AT -- OK
ttySL0<*1>: Speed 115200: AT -- OK
ttySL0<*1>: Speed 230400: AT -- OK
ttySL0<*1>: Speed 460800: AT -- OK
ttySL0<*1>: Max speed is 460800; that should be safe.
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttySL0.
Modem configuration written to /etc/wvdial.conf.
ttySL0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"


```

Permissions shouldn't be an issue since wvdial/pppconfig/pon/off has to be run with sudo anyway.  I don't use gnome-ppp, as I've never been able to get the stupid app to work correctly(been trying since it was first introduced to the repository years ago).  I just stick to pon and wvdial, as typically they work just fine.   my account is part of dip and dialout(done automatically in precise to my surprise).
I'll fiddle with it some more later, as I'm not home right now.

---

### Post by sir_cheats_a_lot on 2012-05-05
I rechecked dmesg one last time, and found something. . .maybe it's nothing, but, perhaps something not holding my breath however:
```
[  212.263770] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
```

truly disturbing...I just downloaded puppy linux today, and it auto-detected everything and the modem works out of the box?  what's their secret?  do you think it might be possible to copy and paste settings?  I'm going to do some more poking around I think. 	:rolleyes:

---

### Post by sir_cheats_a_lot on 2012-05-07
I suppose I have multiple options right now, and they are as follows:

1. give up - install puppy. works for immediate results, but has downsides, such as having to reinstall about 100+Mb worth of packages.

2. give up - wait for my usb => serial cable($1.85 at ebay) that I just bought on ebay to arrive, and use my new external modem($5 at goodwill).

3. keep trying. though the previous two are looking more attractive at the moment :lolflag:

---

### Post by sir_cheats_a_lot on 2012-05-07
quick update, still no luck.   just got gkdialer installed, which at least provided me with an error message.
from the syslog:

```
May  7 14:43:03 sok-MT6705 pppd[3684]: pppd 2.4.5 started by root, uid 0
May  7 14:43:04 sok-MT6705 chat[3687]: abort on (BUSY)
May  7 14:43:04 sok-MT6705 chat[3687]: abort on (NO CARRIER)
May  7 14:43:04 sok-MT6705 chat[3687]: abort on (VOICE)
May  7 14:43:04 sok-MT6705 chat[3687]: abort on (NO DIALTONE)
May  7 14:43:04 sok-MT6705 chat[3687]: abort on (NO DIAL TONE)
May  7 14:43:04 sok-MT6705 chat[3687]: abort on (NO ANSWER)
May  7 14:43:04 sok-MT6705 chat[3687]: send (ATZ^M)
May  7 14:43:04 sok-MT6705 chat[3687]: expect (OK)
May  7 14:43:04 sok-MT6705 chat[3687]: ATZ^M^M
May  7 14:43:04 sok-MT6705 chat[3687]: OK
May  7 14:43:04 sok-MT6705 chat[3687]:  -- got it
May  7 14:43:04 sok-MT6705 chat[3687]: send (ATDT9265000^M)
May  7 14:43:04 sok-MT6705 chat[3687]: expect (CONNECT)
May  7 14:43:04 sok-MT6705 chat[3687]: ^M
May  7 14:43:04 sok-MT6705 chat[3687]: ATDT9265000^M^M
May  7 14:43:21 sok-MT6705 chat[3687]: NO CARRIER
May  7 14:43:21 sok-MT6705 chat[3687]:  -- failed
May  7 14:43:21 sok-MT6705 chat[3687]: Failed (NO CARRIER)
May  7 14:43:21 sok-MT6705 pppd[3684]: Script /usr/sbin/chat -v -f /etc/chatscripts/dialinfree finished (pid 3686), status = 0x5
May  7 14:43:21 sok-MT6705 pppd[3684]: Connect script failed
May  7 14:43:22 sok-MT6705 pppd[3684]: Exit.
```

---

### Post by crjackson on 2012-05-07
I sure hope you get this figured out soon, dial-up has always been a problem for me wih Ubuntu.  I have several friends that I installed ubunu for and setup their dial up connections.  I have advised all of them not to upgrade to the latestes distro due to the dial up problems.

I don't have the time or knowledge to support this problematic issue.  I sure wish the developers would recognize the need for out of the box dial up support.  I'm personally leaning towards a different OS since the last 2 release have left me less that happy.

---

### Post by sir_cheats_a_lot on 2012-05-07
I didn't really have too many problems with dialup until lucid was released. but I had skipped all the releases between 8.04 and 10.04, so I've no idea exactly when it was changed.  with dapper you had to add the noauth option yourself(it wasn't there by default), then with feisty fawn and hardy you had to totally remove network manager(which wasn't a big deal for me), then with lucid though, I had to do all of that plus completely disable/remove ubuntu one, and everything relating to it.  now...it just seems to not work at all, regardless of all that.  but that was another time with a different computer(i also had an external modem for that).    with precise, though.. they've totally cut out dialup, wvdial isn't even included with the default install.  thankfully though they did leave it and it's dependency on the install disc, along with a copy of the smartlink daemon.  still, ppp0 isn't even listed in network manager anymore.  I'd prefer not to downgrade all the way to hardy again...that's a lot of very old software there, which will only equate to new headaches getting newer versions of what I need installed.  I've got a second laptop(boots from a flash drive) to configure yet as well(it's running mint).   Just wanted to get my main out of the way first.   winmodem support has been very hit and miss in Ubuntu though, I've never had this much trouble getting it going before.  I've not been too thrilled with Ubuntu since Unity and Ubuntu one's introduction myself.   I've tried numerous dialers, no luck yet, might try kppp(It's a 60MB download though w/depends) next. 
   If I do end up giving up on it I'll be going to puppy, since it did fire up and detect and successfully connect with this laptop's modem without complaint.  I've even been eyeballing plain old Debian, though I've not tested it, beyond making sure the dvd works.   I don't know, it frustrates me just enough to keep picking away at it, but not quite enough to drive me away entirely...yet.   the whole reason I got that new USR external modem, and usb to serial adapter(expected between 7-14 days from now), was for my eMac, which I just upgraded to OS X 10.5.8(leopard).  I could use it for this, but I'd much rather just get this one working, and hopefully help others with it.   you know I'm not sure what irritates me more: the fact that dialup is now an after thought or that "sudo mount -a" no longer works.  both are very freaking inconvenient!

---

### Post by sir_cheats_a_lot on 2012-05-09
I guess for now I'm giving up Ubuntu, under protest, mind you.  I've imaged my install, however, in case I lose my mind and want to come back. *sighs*   I just wish I didn't have to use something else.  oh well... I've been meaning to explore other distros anyway. ):P

---

### Post by sir_cheats_a_lot on 2012-05-10
hmm...interesting..Windows 8 keeps a log for my modem.  wounder if there's anything useful there...

ah, what the hell, I'll pop it in here and see if someone can make sense of it...definitely can't hurt any.  I just doubt there's much there that I could use for Ubuntu.  suppose I could copy and paste that one string into wvdial.conf in place of the default intit2 string.

```
05-10-2012 01:05:37.878 - File: C:\Windows\system32\tapisrv.dll, Version 6.2.8250   
05-10-2012 01:05:37.878 - File: C:\Windows\system32\unimdm.tsp, Version 6.2.8250   
05-10-2012 01:05:37.878 - File: C:\Windows\system32\unimdmat.dll, Version 6.2.8250   
05-10-2012 01:05:37.878 - File: C:\Windows\system32\uniplat.dll, Version 6.2.8250   
05-10-2012 01:05:37.894 - File: C:\Windows\system32\drivers\modem.sys, Version 6.2.8250   
05-10-2012 01:05:37.910 - File: C:\Windows\system32\modemui.dll, Version 6.2.8250   
05-10-2012 01:05:37.941 - File: C:\Windows\system32\mdminst.dll, Version 6.2.8250   
05-10-2012 01:05:37.941 - Modem type: Motorola SM56 Data Fax Modem
05-10-2012 01:05:37.941 - Modem inf path: mdmmotsm.inf
05-10-2012 01:05:37.941 - Modem inf section: SM56_HDAUDIO_MODEM_INSTALL
05-10-2012 01:05:37.941 - Matching hardware ID: hdaudio\func_02&ven_1057&dev_3057&subsys_00010001
05-10-2012 01:05:37.975 - 115200,8,N,1, ctsfl=1, rtsctl=2
05-10-2012 01:05:37.975 - Initializing modem.
05-10-2012 01:05:37.975 - DSR is low while initializing the modem. Verify modem is turned on.
05-10-2012 01:05:37.985 - Send: AT<cr>
05-10-2012 01:05:38.206 - Recv: AT<cr>
05-10-2012 01:05:38.206 - Command Echo
05-10-2012 01:05:38.206 - Recv: <cr><lf>OK<cr><lf>
05-10-2012 01:05:38.206 - Interpreted response: OK
05-10-2012 01:05:38.217 - Send: AT&F&D2&C1V1S0=0E0<cr>
05-10-2012 01:05:38.425 - Recv: AT&F&D2&C1V1S0=0E0<cr>
05-10-2012 01:05:38.425 - Command Echo
05-10-2012 01:05:38.657 - Recv: <cr><lf>OK<cr><lf>
05-10-2012 01:05:38.657 - Interpreted response: OK
05-10-2012 01:05:38.667 - Send: ATS7=60\T0L0M1\N7%C1\Q3*LS1X4<cr>
05-10-2012 01:05:39.378 - Recv: <cr><lf>OK<cr><lf>
05-10-2012 01:05:39.378 - Interpreted response: OK
05-10-2012 01:05:39.378 - Waiting for a call.
05-10-2012 01:05:39.389 - Send: ATS0=0<cr>
05-10-2012 01:05:39.607 - Recv: <cr><lf>OK<cr><lf>
05-10-2012 01:05:39.607 - Interpreted response: OK
05-10-2012 01:05:39.607 - 921600,8,N,1, ctsfl=1, rtsctl=2
05-10-2012 01:05:39.607 - Initializing modem.
05-10-2012 01:05:39.618 - Send: AT<cr>
05-10-2012 01:05:39.828 - Recv: <cr><lf>OK<cr><lf>
05-10-2012 01:05:39.828 - Interpreted response: OK
05-10-2012 01:05:39.839 - Send: AT&F&D2&C1V1S0=0E0<cr>
05-10-2012 01:05:40.305 - Recv: <cr><lf>OK<cr><lf>
05-10-2012 01:05:40.305 - Interpreted response: OK
05-10-2012 01:05:40.315 - Send: ATS7=60\T0L0M1\N7%C1\Q3*LS1X4<cr>
05-10-2012 01:05:41.025 - Recv: <cr><lf>OK<cr><lf>
05-10-2012 01:05:41.025 - Interpreted response: OK
05-10-2012 01:05:41.025 - Dialing.
05-10-2012 01:05:41.036 - Send: ATDT#######<cr>
05-10-2012 01:06:10.052 - Recv: <cr><lf>CONNECT 44000/LAPM<cr><lf>
05-10-2012 01:06:10.052 - Interpreted response: Connect
05-10-2012 01:06:10.053 - Connection established at 44000bps.
05-10-2012 01:06:10.053 - Error-control on.
05-10-2012 01:06:10.053 - Data compression off or unknown.
05-10-2012 01:06:40.053 - Read: Total: 2588, Per/Sec: 87, Written: Total: 3475, Per/Sec: 117
05-10-2012 01:08:40.053 - Read: Total: 294213, Per/Sec: 2450, Written: Total: 30673, Per/Sec: 228
05-10-2012 01:10:40.054 - Read: Total: 664238, Per/Sec: 3083, Written: Total: 75987, Per/Sec: 377
05-10-2012 01:12:40.055 - Read: Total: 1096566, Per/Sec: 3633, Written: Total: 85932, Per/Sec: 83

```

---

### Post by sir_cheats_a_lot on 2012-05-10
```
HKR, Init,                    1,, "AT<cr>"
HKR, Init,                    2,, "AT&F&D2&C1V1S0=0E0<cr>"

[INTERNAL]
HKR,, DeviceType,             1, 02

[MfgAddReg]
HKR,, InactivityScale,        1, 3c,00,00,00
HKR, Monitor,                 1,, "ATS0=0<cr>"
HKR, Monitor,                 2,, "None"
HKR, Hangup,                  1,, "ATH<cr>"
HKR, Answer,                  1,, "ATA<cr>"
HKR,, Reset,,                 "AT&F<cr>"
HKR, Settings, Prefix,,       "AT"
HKR, Settings, Terminator,,   "<cr>"
HKR, Settings, DialPrefix,,   "D"
HKR, Settings, DialSuffix,,   ";"
HKR, Settings, SpeakerVolume_Low,,   "L0"
HKR, Settings, SpeakerVolume_Med,,   "L2"
HKR, Settings, SpeakerVolume_High,,  "L3"
HKR, Settings, SpeakerMode_Off,,     "M0"
HKR, Settings, SpeakerMode_Dial,,    "M1"
HKR, Settings, SpeakerMode_On,,      "M2"
HKR, Settings, SpeakerMode_Setup,,   "M3"
HKR, Settings, FlowControl_Off,,     "\Q0"
HKR, Settings, FlowControl_Hard,,    "\Q3"
HKR, Settings, FlowControl_Soft,,    "\Q1"
HKR, Settings, ErrorControl_On,,     "\N7"
HKR, Settings, ErrorControl_Off,,    "\N0"
HKR, Settings, ErrorControl_Forced,, "\N6"
HKR, Settings, Compression_On,,      "%%C1"
HKR, Settings, Compression_Off,,     "%%C0"
HKR, Settings, Pulse,,        "P"
HKR, Settings, Tone,,         "T"
HKR, Settings, Blind_Off,,    "X4"
HKR, Settings, Blind_On,,     "X3"
HKR, Settings, CallSetupFailTimer,,  "S7=<#>"
HKR, Settings, InactivityTimeout,,   "\T<#>"
HKR, Settings, Modulation_CCITT,,    "*LS1"
HKR, Settings, Modulation_Bell,,     "*LS0"

HKR, Fax, HardwareFlowControl,, "1"
HKR, Fax, SetupCommand,, "ATS7=60/Q3"
HKR, Fax\Class1\AdaptiveAnswer\AnswerCommand, 1,,"AT"
HKR, Fax\Class1\AdaptiveAnswer\AnswerCommand, 2,,"AT&FS0=0E0V1&D2"
HKR, Fax\Class1\AdaptiveAnswer\AnswerCommand, 3,,"ATL1M1/Q3"
HKR, Fax\Class1\AdaptiveAnswer\AnswerCommand, 4,,"ATX4"
HKR, Fax\Class1\AdaptiveAnswer\AnswerCommand, 5,,"AT+FCLASS=1"
HKR, Fax\Class1\AdaptiveAnswer\AnswerCommand, 6,,"AT+FAA=1"
HKR, Fax\Class1\AdaptiveAnswer\AnswerCommand, 7,,"ATA"
HKR, Fax\Class1\AdaptiveAnswer, ModemResponseFaxDetect,, "FAX"
HKR, Fax\Class1\AdaptiveAnswer, ModemResponseDataConnect,, "CONNECT"
HKR, Fax\Class1\AdaptiveAnswer, ModemResponseDataDetect,, "DATA"
HKR, Fax\Class1\AdaptiveAnswer, ModemResponseFaxConnect,, "CONNECT"
```

I found this in the file "mdmmotsm.inf"; though I have no idea how much of this can even be applied to a solution.  I do know that "AT&F&D2&C1V1S0=0E0" comes back as an okay string when used in wvdial.conf though...so maybe the rest can be applied in some way. I left out the "<cr>" part as I've no idea if it'd work correctly with it in.

---

