---
title: "USB modem not detected everytime"
date: 2012-10-21
forum: New to Ubuntu
---

### Post by Aparna R on 2012-10-21
I got stuck up with a problem in net connection in newly installed Ubuntu 12.04 . I am using Qual-Comm HS-USB modem to connect to internet. It was not detected initially after installation of OS.How ever,it got detected and could connect to Internet after following the steps shown here: [http://askubuntu.com/questions/143989/3g-usb-modem-not-working-in-12-04But](http://askubuntu.com/questions/143989/3g-usb-modem-not-working-in-12-04But) most of the time on starting the system it not detecting the device as a modem. It need to reboot the system,so that it got detected. I dont understand what to do.

Any help would be appreciated.

thanks

---

### Post by NikTh on 2012-10-21
> **Aparna R said:**
> and could connect to Internet after following the steps shown here: [http://askubuntu.com/questions/143989/3g-usb-modem-not-working-in-12-04But](http://askubuntu.com/questions/143989/3g-usb-modem-not-working-in-12-04But) 


Hi , 

Three solutions provided to the answer of askubuntu. Which of the 3 solutions you followed ? 

The [sakis3g script]("http://www.sakis3g.org/") , I think is the most automate option. 
Did you try it ? 
Look here a thread : [http://ubuntuforums.org/showthread.php?t=1580427](http://ubuntuforums.org/showthread.php?t=1580427) , little old but might help.
Thanks

---

### Post by varunendra on 2012-10-21
Hi Aparna, and Welcome to the forums !

In addition to answer to Nik's questions, I think you should also post the outputs of (after connecting the modem and waiting for about 6-8 seconds):
```
lsusb
lsmod
dmesg | tail -20
```

Although the askubuntu link you followed is quite informative and detailed, but there can be many factors which can affect the modem in different ways. Hopefully the above outputs may give us some useful clues.

I have a Micromax 3G modem (provided by BSNL) which disconnets itself every 15-20 minutes with one ISP (namely- Tata Docomo), and I have to go through a "pull out > wait 20-sec. > replug > wait 10 sec" cycle to reconnect it. However, it remains connected all night long with another one (Airtel, with same connection type - GPRS, since 3G is not available where I live). So I 'believe' the ISP service quality + signal quality can also affect its behaviour.

So, who is your ISP and which connection type are you using? Also, these modems often contain both windows and linux drivers (including firmware) on a secured area of their flash memory which is detected as 'cdrom' by the system. Does your modem has these drivers and can you access them?

---

### Post by Aparna R on 2012-10-22
> **NikTh said:**
> Hi , 

Three solutions provided to the answer of askubuntu. Which of the 3 solutions you followed ? 

The [sakis3g script]("http://www.sakis3g.org/") , I think is the most automate option. 
Did you try it ? 
Look here a thread : [http://ubuntuforums.org/showthread.php?t=1580427](http://ubuntuforums.org/showthread.php?t=1580427) , little old but might help.
Thanks

I tried all answers except that about sakis3g script.
And now I tried sakis3g
but when i run it in terminal,It shows:
*Segmentation fault (core dumped)*
then appears the options box,It disappears when I chose an option and click Ok.with the same message in terminal.
nothing more happens.

Thanks

---

### Post by Aparna R on 2012-10-22
> **varunendra said:**
> Hi Aparna, and Welcome to the forums !

In addition to answer to Nik's questions, I think you should also post the outputs of (after connecting the modem and waiting for about 6-8 seconds):
```
lsusb
lsmod
dmesg | tail -20
```

Although the askubuntu link you followed is quite informative and detailed, but there can be many factors which can affect the modem in different ways. Hopefully the above outputs may give us some useful clues.

I have a Micromax 3G modem (provided by BSNL) which disconnets itself every 15-20 minutes with one ISP (namely- Tata Docomo), and I have to go through a "pull out > wait 20-sec. > replug > wait 10 sec" cycle to reconnect it. However, it remains connected all night long with another one (Airtel, with same connection type - GPRS, since 3G is not available where I live). So I 'believe' the ISP service quality + signal quality can also affect its behaviour.

So, who is your ISP and which connection type are you using? Also, these modems often contain both windows and linux drivers (including firmware) on a secured area of their flash memory which is detected as 'cdrom' by the system. Does your modem has these drivers and can you access them?


Well.My ISP is BSNL,WLL CDMA connection.
and yes,this device detected as CDROM in ubuntu 10.04 automatically,and there were both windows and linux drivers as you said.But what happend in ubuntu 12.04?

the output of commands :
> 
**lsusb**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 05c6:f000 Qualcomm, Inc. 

**lsmod**
Module                  Size  Used by
snd_hda_codec_realtek   174055  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
psmouse                72846  0 
serio_raw              13027  0 
snd_rawmidi            25424  1 snd_seq_midi
i915                  414603  3 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
parport_pc             32114  1 
snd_timer              28931  2 snd_pcm,snd_seq
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
ppdev                  12849  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         45466  1 i915
asus_atk0110           17742  0 
drm                   197692  4 i915,drm_kms_helper
mac_hid                13077  0 
snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13199  1 i915
soundcore              14635  1 snd
video                  19068  1 i915
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
usbserial              37173  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  56321  0 
usb_storage            39646  0 

**dmesg | tail -20**
[   91.536127] scsi5 : usb-storage 5-2:1.0
[   92.545136] scsi 5:0:0:0: CD-ROM            Qualcomm MMC Storage      2.31 PQ: 0 ANSI: 2
[   92.557119] sr2: scsi-1 drive
[   92.558749] sr 5:0:0:0: Attached scsi CD-ROM sr2
[   92.559033] sr 5:0:0:0: Attached scsi generic sg3 type 5
[  131.741157] zenity[2928]: segfault at 32 ip 080551ad sp bfd01c00 error 4 in zenity[8048000+14000]
[  136.832863] init: failsafe main process (907) killed by TERM signal
[  136.900111] type=1400 audit(1350896413.193:25): apparmor="STATUS" operation="profile_replace" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=3122 comm="apparmor_parser"
[  136.904685] type=1400 audit(1350896413.197:26): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=3123 comm="apparmor_parser"
[  136.905374] type=1400 audit(1350896413.197:27): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3123 comm="apparmor_parser"
[  136.905734] type=1400 audit(1350896413.197:28): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=3123 comm="apparmor_parser"
[  136.921863] type=1400 audit(1350896413.213:29): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince" pid=3124 comm="apparmor_parser"
[  136.929982] type=1400 audit(1350896413.221:30): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince//launchpad_integration" pid=3124 comm="apparmor_parser"
[  136.931788] type=1400 audit(1350896413.221:31): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince//sanitized_helper" pid=3124 comm="apparmor_parser"
[  136.933672] type=1400 audit(1350896413.225:32): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince-previewer" pid=3124 comm="apparmor_parser"
[  136.938551] type=1400 audit(1350896413.229:33): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince-previewer//launchpad_integration" pid=3124 comm="apparmor_parser"
[  136.939922] type=1400 audit(1350896413.229:34): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince-previewer//sanitized_helper" pid=3124 comm="apparmor_parser"
[  137.300642] init: plymouth-stop pre-start process (3237) terminated with status 1
[  158.171547] show_signal_msg: 21 callbacks suppressed
[  158.171556] zenity[4123]: segfault at 32 ip 080551ad sp bfae12d0 error 4 in zenity[8048000+14000]

Now what I do?:confused:

---

### Post by varunendra on 2012-10-22
> **Aparna R said:**
> ..and yes,this device detected as CDROM in ubuntu 10.04 automatically,and there were both windows and linux drivers as you said.But what happend in ubuntu 12.04?
This wonderful post by A.S. on askubuntu describes the reason as well as required actions in a very detailed manner : [http://askubuntu.com/questions/182037/usb-modem-could-not-mount-on-12-04](http://askubuntu.com/questions/182037/usb-modem-could-not-mount-on-12-04)

However, your dmesg output suggests that the modem is probably not getting past the stage of being identified as a cdrom. As such, you should be able to mount it manually if it is not already mounted. Please check :
```
mount | grep sr
```
to see if it is already mounted somewhere. If not, try to mount it using either disk-utility or manually (e.g., to mount it at /cdrom) :
```
sudo mount -t iso9660 /dev/sr2 /cdrom
```

If however, it fails to mount or is completely missing, then try the troubleshooting steps involving disabling of *usb_modeswitch* in the above link. [s]I couldn't identify any modem drivers in your *lsmod* output, so you may skip the step 3 in the linked askubuntu post.[/s][COLOR="DarkRed"]EDIT: Ah.. I almost missed it, there is "**usbserial**" in your lsmod output. That should be the driver currently handling your modem. Just use it in the 3rd step.[/COLOR]

Once you can mount it and access the drivers, try installing them and see if it performs any better.

If everything else fails, the last resort would be to put those commands, that let you use the modem as you mentioned in your first post, in a script so that you don't have to restart everytime to get it detected.

---

### Post by Aparna R on 2012-10-24
> **varunendra said:**
> This wonderful post by A.S. on askubuntu describes the reason as well as required actions in a very detailed manner : [http://askubuntu.com/questions/182037/usb-modem-could-not-mount-on-12-04](http://askubuntu.com/questions/182037/usb-modem-could-not-mount-on-12-04)

However, your dmesg output suggests that the modem is probably not getting past the stage of being identified as a cdrom. As such, you should be able to mount it manually if it is not already mounted. Please check :
```
mount | grep sr
```
to see if it is already mounted somewhere. If not, try to mount it using either disk-utility or manually (e.g., to mount it at /cdrom) :
```
sudo mount -t iso9660 /dev/sr2 /cdrom
```

If however, it fails to mount or is completely missing, then try the troubleshooting steps involving disabling of *usb_modeswitch* in the above link. [s]I couldn't identify any modem drivers in your *lsmod* output, so you may skip the step 3 in the linked askubuntu post.[/s][COLOR="DarkRed"]EDIT: Ah.. I almost missed it, there is "**usbserial**" in your lsmod output. That should be the driver currently handling your modem. Just use it in the 3rd step.[/COLOR]

Once you can mount it and access the drivers, try installing them and see if it performs any better.

Thanks,that was a great help.But problem not solved yet.
The driver provided only for ubuntu 10.04 version
I tried to download the driver for ubuntu 12.04.But I didnot get anywhere.:confused:

> If everything else fails, the last resort would be to put those commands, that let you use the modem as you mentioned in your first post, in a script so that you don't have to restart everytime to get it detected.


I dont know how to make the script also.:(

---

### Post by varunendra on 2012-10-25
If the driver folder can be compressed (preferably in 7-zip format which will be available after you install p7zip package) to make it small enough, you may attach it here so I can analyse it myself (and hopefully see if I can make it compatible with 12.04).

As for the script thing, please first let us know which of the solutions worked for you and how exactly you implemented it (i.e., what exact commands you used and where you put them). If you can't remember the exact commands or steps, just let us know the method you used. We'll verify other things accordingly.

And when the modem works, please post the outputs of :
```
lsmod
dmesg | tail -20
```
That should give me a correct direction to work in.

Also, how does it behave on a live session? If additions and changes to system files seem to have been messed up too much, it is always a good idea to start fresh :)

**PS:**
Just so you know what I,m trying to figure out ATM is -
[LIST=1]
[*]Whether or not the modem is detected as a modem at all (everytime or sometimes - verification may need command outputs at multiple occasions)
[*]Which driver is currently handling your modem correctly - 'option' or 'usbserial' or something else.
[*]If there is some discrepancy in the implementation of solutions you've tried so far. Can it be the reason for the intermittent behaviour of the modem?
[/LIST]

**PPS:**
[COLOR="DarkRed"]I may or may not be able to respond for next 3-4 days, so if anybody watching this thread have any opinion/advice, please jump in and share it with us. Thanks in advance![/COLOR]

---

### Post by bra|10n on 2012-10-25
I expect that the correct driver is already present (at least here on 12.10)...
```
# Siptune LM-75 ("LinuxModem")
ATTRS{idVendor}=="05c6", ATTRS{idProduct}=="f000", RUN+="usb_modeswitch '%b/%k'"

```I am not sure what the OP has done to get this working, but if the following has not been added to /etc/rc.local then this is the first step.
```
modprobe usbserial vendor=0x05c6 product=0xf000
```Add the above line above "exit 0" in the file. Logout/in connect the device and see if it is detected.

---

### Post by Aparna R on 2012-10-26
> **varunendra said:**
> If the driver folder can be compressed (preferably in 7-zip format which will be available after you install p7zip package) to make it small enough, you may attach it here so I can analyse it myself (and hopefully see if I can make it compatible with 12.04).

As for the script thing, please first let us know which of the solutions worked for you and how exactly you implemented it (i.e., what exact commands you used and where you put them). If you can't remember the exact commands or steps, just let us know the method you used. We'll verify other things accordingly.

And when the modem works, please post the outputs of :
```
lsmod
dmesg | tail -20
```That should give me a correct direction to work in.

Also, how does it behave on a live session? If additions and changes to system files seem to have been messed up too much, it is always a good idea to start fresh :)

**PS:**
Just so you know what I,m trying to figure out ATM is -
[LIST=1]
[*]Whether or not the modem is detected as a modem at all (everytime or sometimes - verification may need command outputs at multiple occasions)
[*]Which driver is currently handling your modem correctly - 'option' or 'usbserial' or something else.
[*]If there is some discrepancy in the implementation of solutions you've tried so far. Can it be the reason for the intermittent behaviour of the modem?
[/LIST]

I exactly followed the instruction mentioned in the link referred in the first post.
now the contents of my  **/usr/bin/usbModemScript **file
```
#!/bin/bash
  echo 05c6 9004 > /sys/bus/usb-serial/drivers/option1/new_id
```and **/etc/udev/rules.d/option.rule**s contains
```
ATTRS{idVendor}=="05c6", ATTRS{idProduct}=="9004", RUN+="/usr/bin/usbModemScri$
 ATTRS{idVendor}=="05c6", ATTRS{idProduct}=="9004", RUN+="/sbin/modprobe option"
```
But at times when modem not detected I cant see a 'option' directory inside  /sys/bus/usb-serial/drivers.
I also added the details to wvdial.conf 
                          ```
[Dialer BSNL]
Inherits = Modem0
Init1 = ATZ
Init3 = AT+CRM=1;+CPS=33;+CMUX=1;+CTA=0                            <!--         @page { margin: 2cm }         P { margin-bottom: 0.21cm; direction: ltr; color: #000000; widows: 2; orphans: 2 }         A:link { color: #0000ff; so-language: zxx }     -->        
Stupid Mode = 1
Phone = #777
Area Code = 044
Username = 
Password = 

[Modem0]
Init3 = ATM0
Init1 = ATZ
SetVolume = 0
Modem = /dev/ttyUSB0
Baud = 460800
FlowControl = CRTSCTS
Dial Command = ATDT

```I dont understand how much this is useful;because it again prompts for username and password on "edit connections" box under "mobile broadband" tab when I add it as a moblile broadband connection when system detected the device as a modem.

The output of the commands at times when modem get detected
```
**lsmod**
Module                  Size  Used by
ppp_deflate            12878  0 
zlib_deflate           26622  1 ppp_deflate
bsd_comp               12842  0 
ppp_async              17307  1 
crc_ccitt              12595  1 ppp_async
snd_hda_codec_realtek   174055  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
i915                  414603  3 
psmouse                72846  0 
serio_raw              13027  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
option                 25580  0 
usb_wwan               19779  1 option
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
parport_pc             32114  1 
ppdev                  12849  0 
asus_atk0110           17742  0 
soundcore              14635  1 snd
i2c_algo_bit           13199  1 i915
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
video                  19068  1 i915
mac_hid                13077  0 
usbserial              37173  9 option,usb_wwan
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  56321  0 
``````
**dmesg |tail -20**
[   16.631372] hda_codec: ALC887: BIOS auto-probing.
[   16.927358] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
[   16.942145] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   16.944775] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   16.959069] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   16.967427] input: HDA Intel Line-Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   44.143514] audit_printk_skb: 36 callbacks suppressed
[   44.143521] type=1400 audit(1351269352.435:24): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=1790 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[  133.813572] PPP BSD Compression module registered
[  133.846044] PPP Deflate Compression module registered
[  137.062942] type=1400 audit(1351269445.355:25): apparmor="STATUS" operation="profile_replace" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=2075 comm="apparmor_parser"
[  137.074441] type=1400 audit(1351269445.367:26): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=2076 comm="apparmor_parser"
[  137.079117] type=1400 audit(1351269445.371:27): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2076 comm="apparmor_parser"
[  137.079499] type=1400 audit(1351269445.371:28): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=2076 comm="apparmor_parser"
[  137.112883] type=1400 audit(1351269445.407:29): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince" pid=2077 comm="apparmor_parser"
[  137.123273] type=1400 audit(1351269445.415:30): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince//launchpad_integration" pid=2077 comm="apparmor_parser"
[  137.125479] type=1400 audit(1351269445.419:31): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince//sanitized_helper" pid=2077 comm="apparmor_parser"
[  137.127033] type=1400 audit(1351269445.419:32): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince-previewer" pid=2077 comm="apparmor_parser"
[  137.132154] type=1400 audit(1351269445.427:33): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince-previewer//launchpad_integration" pid=2077 comm="apparmor_parser"
[  137.889247] init: plymouth-stop pre-start process (2191) terminated with status 1
```also I am attaching the driver software.

Thanks :)

---

### Post by Aparna R on 2012-10-27
> **bra|10n said:**
> 
I am not sure what the OP has done to get this working, but if the following has not been added to /etc/rc.local then this is the first step.
```
modprobe usbserial vendor=0x05c6 product=0xf000
```Add the above line above "exit 0" in the file. Logout/in connect the device and see if it is detected.

I did it,but it still the same:(
why we need to add this??

---

### Post by bra|10n on 2012-10-27
> **Aparna R said:**
> I did it,but it still the same:(
why we need to add this??

Because as far as I understand the module usbserial has already loaded and so when you plug in your usb modem it doesn't know that it's there...

You could try my suggestion to see if it works for you. I recently converted to a Telstra 4G USB device and it is automatically detected and works fine.

To finish the setup I have used you will need to create the following file,
```
# Qual-Comm HS-USB ("LinuxModem")

TargetVendor=  0x05c6
TargetProduct= 0xf000

MessageContent="5553424312345678000000000000061b000000020000000000000000000000"
CheckSuccess=20   

```Call it **05c6:f000** and save it in /etc/usb_modeswitch.d
Now logout/in, plug in the USB modem and wait 90sec to see if you see a Mobile Broadband connection popup.

If nothing happens, try the following in a terminal;
```

sudo rmmod usbserial
sudo modprobe usbserial
sudo usb_modeswitch -v 05c6 -p f000
```This essentially unloads the usbserial module, reloads it, and then scans specifically for your device.
Now run **lsusb** in a terminal and look for a new product id. Hopefully instead of seeing your device as a CDROM, it will appear as a modem if the switching has taken place. 
If this works post back the results.

---

### Post by Aparna R on 2012-10-29
> **bra|10n said:**
> Because as far as I understand the module usbserial has already loaded and so when you plug in your usb modem it doesn't know that it's there...

You could try my suggestion to see if it works for you. I recently converted to a Telstra 4G USB device and it is automatically detected and works fine.

To finish the setup I have used you will need to create the following file,
```
# Qual-Comm HS-USB ("LinuxModem")

TargetVendor=  0x05c6
TargetProduct= 0xf000

MessageContent="5553424312345678000000000000061b000000020000000000000000000000"
CheckSuccess=20   

```Call it **05c6:f000** and save it in /etc/usb_modeswitch.d
Now logout/in, plug in the USB modem and wait 90sec to see if you see a Mobile Broadband connection popup.

If nothing happens, try the following in a terminal;
```

sudo rmmod usbserial
sudo modprobe usbserial
sudo usb_modeswitch -v 05c6 -p f000
```This essentially unloads the usbserial module, reloads it, and then scans specifically for your device.
Now run **lsusb** in a terminal and look for a new product id. Hopefully instead of seeing your device as a CDROM, it will appear as a modem if the switching has taken place. 
If this works post back the results.


If I did in the right way...the output of the last commnand was:

```
**sudo usb_modeswitch -v 05c6 -p f000**
Looking for default devices ...
   found matching product ID
   adding device
 Found device in default mode, class or configuration (1)
Accessing device 002 on bus 005 ...
Getting the current device configuration ...
 OK, got current device configuration (1)
Using first interface: 0x00
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 No driver found. Either detached before or never attached

```
:(
You have not specified any extension for the file **05c6:f000**I save it as plain /text format...
Any specifications??

thanks..

---

### Post by bra|10n on 2012-10-29
Save the file exactly as I described, no extension necessary. 
Now goto /lib/udev/rules.d and open the file **40-usb_modeswitch.rules** and find the following entry;
```
# Siptune LM-75 ("LinuxModem") 
ATTRS{idVendor}=="05c6", ATTRS{idProduct}=="f000", RUN+="usb_modeswitch '%b/%k'"
```copy it and paste it directly underneath, and edit it to look like the following;
```
# Qual-Comm HS-USB 
ATTRS{idVendor}=="05c6", ATTRS{idProduct}=="f000", RUN+="usb_modeswitch '%b/%k'"
```Now please re read my earlier post (#12) and note the order in which to do things. 
Please post back the results, including the outputs I requested...

---

### Post by varunendra on 2012-10-30
Sorry for being so late, but it seems you are already getting much better help from *bra|10n* than I could have possibly offered (to be honest, most of what *bra|10n* is trying is above my head 8-[). So at this point, I think I should sit back and just watch the progress.

However, comparing the lsmod output of your post #5 ('option' module is missing in it) with mine and considering the following posts: > **Aparna R said:**
> 
I exactly followed the instruction mentioned in the link referred in the first post.
now the contents of my  **/usr/bin/usbModemScript **file
```
#!/bin/bash
  echo 05c6 9004 > /sys/bus/usb-serial/drivers/option1/new_id
```and **/etc/udev/rules.d/[COLOR=Red]option[/COLOR].rule**s contains
```
ATTRS{idVendor}=="05c6", ATTRS{idProduct}=="9004", RUN+="/usr/bin/[COLOR=Blue]**usbModemScri$**[/COLOR]
 ATTRS{idVendor}=="05c6", ATTRS{idProduct}=="9004", RUN+="/sbin/modprobe **[COLOR=Red]option[/COLOR]**"
```But at times [COLOR=Red]when modem not detected I cant see a '**option**' directory inside  /sys/bus/usb-serial/drivers[/COLOR]...
..
..
The output of the commands at times when modem get detected
```
**lsmod**
Module                  Size  Used by
[COLOR=Red]**option**[/COLOR]                 25580  0 
usb_wwan               19779  1 [COLOR=Red]**option**[/COLOR]
..
..
[COLOR=Red]**usbserial**[/COLOR]              37173  9 **[COLOR=Red]option[/COLOR]**,usb_wwan
```

> **Aparna R said:**
> 
```
**sudo usb_modeswitch -v 05c6 -p f000**
Looking for default devices ...
..
Looking for active driver ...
 No driver found. Either detached before or never attached

```
..rings a bell to me. Accordingly, please check **lsmod** again to see if the module 'option' is being loaded or not. If not, please try :
```
echo "option" | tee -a /etc/modules
```
Then reboot. This will add the entry "**option**" in the **/etc/modules** file so that it loads everytime at startup. It should not conflict with whatever *bra|10n* has suggested so far. So do it in addition to what he has suggested.

After doing everything, when you post outputs of what *bra|10n* asked above, please also post the output of **lsmod**.



**PS:**
1) The part highlighted in **[COLOR=Blue]blue[/COLOR]** is a typo or what? It should have been "**[COLOR=Blue]usbModemScript[/COLOR]**".
2) I downloaded the attached driver and tried myself. Making it compatible with 12.04 seems beyond my capabilities at the moment, sorry.

---

### Post by bra|10n on 2012-10-31
> **varunendra said:**
> Sorry for being so late, but it seems you are already getting much better help from *bra|10n* than I could have possibly offered (to be honest, most of what *bra|10n* is trying is above my head 8-[). So at this point, I think I should sit back and just watch the progress.


@varunendra,
Not at all, I'm no expert...
I was reluctant to post with an alternate method to the one you had already begun, but thought perhaps my first post might have been useful to either you or the OP. 

Continuing on from my 2nd last post I think the issue is that the USB device is not switching to 'modem mode', hence why I wanted to unload, reload and rescan the device. However the OP failed to provide the output of **lsusb** after doing this, which I believe would have shown a new product id, necessary to load the driver. My limited understanding is the output the OP provided in the last posting is the product id still seen as a CD-ROM, not in modem mode.

I'm happy for you to continue along your route to a solution if you are confident of an outcome for the OP. From my perspective, and this being over my head also, I need the OP to execute the commands as I have done successfully here to progress to the end of what worked here.
cheers

---

### Post by varunendra on 2012-10-31
> **bra|10n said:**
> 
I was reluctant to post with an alternate method to the one you had already begun,..I had no 'methods' in mind, it was a 'hunt & shoot' approach :).

> **bra|10n said:**
> Continuing on from my 2nd last post I think the issue is that the USB device is not switching to 'modem mode', hence why I wanted to unload, reload and rescan the device...that is definitely a clever move, let's wait for *Aparna's* feedback.

---

### Post by Aparna R on 2012-11-01
i did all as you said...
but still a problem some where.
the output of commands you requested

> **lsmod**

Module                  Size  Used by
snd_hda_codec_realtek   174055  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
psmouse                72846  0 
serio_raw              13027  0 
snd_seq_midi_event     14475  1 snd_seq_midi
i915                  414603  3 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
asus_atk0110           17742  0 
bnep                   17830  2 
parport_pc             32114  1 
snd_timer              28931  2 snd_pcm,snd_seq
drm_kms_helper         45466  1 i915
bluetooth             158438  7 bnep
ppdev                  12849  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   197692  4 i915,drm_kms_helper
snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13199  1 i915
mac_hid                13077  0 
soundcore              14635  1 snd
video                  19068  1 i915
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
[COLOR="red"]option                 25580  0 [/COLOR]
[COLOR="Red"]usb_wwan               19779  1 option[/COLOR]
[COLOR="red"]usbserial              37173  2 option,usb_wwan[/COLOR]
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            39646  0 
r8169                  56321  0 

> **lsusb**
Bus 005 Device 003: ID 05c6:f000 Qualcomm, Inc.

> Originally Posted by bra|10n  
If nothing happens, try the following in a terminal;
```
sudo rmmod usbserial
sudo modprobe usbserial
sudo usb_modeswitch -v 05c6 -p f000
```

Now when I run the first command,I am getting the output:
> [COLOR="red"]ERROR: Module usbserial is in use by option,usb_wwan[/COLOR]
I run it many times after reboots and re-logins..

> Originally Posted by varunendra  
1) The part highlighted in blue is a typo or what? It should have been "usbModemScript".
yes,,it was a typo..sorry :)

also I am pasting here the contents of file /var/log/syslog
when i plugout/plugin the device.

> kernel: [  246.416061] usb 5-2: USB disconnect, device number 2
kernel: [  248.392022] usb 5-2: new full-speed USB device number 3 using uhci_hcd
mtp-probe: checking bus 5, device 3: "/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-2"
mtp-probe: bus: 5, device: 3 was not an MTP device
kernel: [  248.576363] scsi5 : usb-storage 5-2:1.0
kernel: [  249.582070] scsi 5:0:0:0: CD-ROM            Qualcomm MMC Storage      2.31 PQ: 0 ANSI: 2
 kernel: [  249.596051] sr2: scsi-1 drive
kernel: [  249.596314] sr 5:0:0:0: Attached scsi CD-ROM sr2
kernel: [  249.596480] sr 5:0:0:0: Attached scsi generic sg3 type 5
usb_modeswitch: switching device 05c6:f000 on 005/003


If all goes well,I could see the device listed here in the list of devices in the "Add new mobile connection" box.

Thank you friends,you are really helping me to figure out my problem.

regards,

---

### Post by varunendra on 2012-11-01
I really don't think I deserve any 'thanks' yet... :( However, *bra|10n* is definitely moving towards a logical solution.

Some quick observations and suggestions -
First, a few more corrections please - > **Aparna R said:**
> 
now the contents of my  **/usr/bin/usbModemScript **file
```
#!/bin/bash
  echo 05c6 [COLOR=Red]**9004**[/COLOR] > /sys/bus/usb-serial/drivers/option1/new_id
```and **/etc/udev/rules.d/option.rule**s contains
```
ATTRS{idVendor}=="05c6", ATTRS{idProduct}=="[COLOR=Red]**9004**[/COLOR]", RUN+="/usr/bin/usbModemScri$
 ATTRS{idVendor}=="05c6", ATTRS{idProduct}=="[COLOR=Red]**9004**[/COLOR]", RUN+="/sbin/modprobe option"
```
..Each [COLOR=Red]**9004**[/COLOR] should be [COLOR=Blue]**f000**[/COLOR] if I'm understanding correctly this time (earlier I didn't notice them, perhaps because of my poor understanding).

Next, a few explanations -
> **Aparna R said:**
> ```
**lsmod**

Module                  Size  Used by
..
[COLOR=red]option                 25580  0 [/COLOR]
[COLOR=Red]usb_wwan               19779  1 option[/COLOR]
[COLOR=red]usbserial              37173  2 option,usb_wwan[/COLOR]
..
```That is what it should be like.

> **Aparna R said:**
> Now when I run the first command,I am getting the output:
```
[COLOR=red]ERROR: Module usbserial is in use by option,usb_wwan[/COLOR]
```It's normal since 'option' is using it. You'll have to unload 'option' instead with:
```
sudo modprobe -rfv option
```which would unload both usb_wwan and usbserial along with option. But even that will only work if 'option' itself is not in use, that is, either the modem is not detected as a modem or is unplugged (at least that's what is happening here).

Next, a few more questions - 
1)
> **Aparna R said:**
> ../var/log/syslog
when i plugout/plugin the device.```
kernel: ..
kernel: [  249.596314] sr 5:0:0:0: Attached scsi CD-ROM sr2
kernel: [  249.596480] sr 5:0:0:0: Attached scsi generic sg3 type 5
usb_modeswitch: switching device 05c6:f000 on 005/003
```
..and ?? Perhaps dmesg could show what happened after that:
```
dmesg | tail -20
```

2) Are we dealing with wvdial or NM at the moment ? I'd suggest to remove or disable one and proceed with the other. Leaving both enabled may cause conflicts. I prefer NM, but go with whatever you are comfortable with.

3) Is "plugging-out > wait > plugging-in" cycle as I mentioned in my first post working now or do you still have to reboot?

For reference, here's my dmesg output:
```
 dmesg | tail -20
[18513.797962] ..
..
[18713.199305] usb 2-1.2: new high-speed USB device number 25 using ehci_hcd
[18713.308878] scsi29 : usb-storage 2-1.2:1.0
[18714.309119] scsi 29:0:0:0: CD-ROM            USBModem Disk             2.31 PQ: 0 ANSI: 2
[18714.317042] sr3: scsi-1 drive
[18714.317385] sr 29:0:0:0: Attached scsi CD-ROM sr3
[18714.318109] sr 29:0:0:0: Attached scsi generic sg2 type 5
[18715.812901] usb 2-1.2: USB disconnect, device number 25
[18716.012186] usb 2-1.2: new high-speed USB device number 26 using ehci_hcd
[18716.130943] option 2-1.2:1.0: GSM modem (1-port) converter detected
[18716.131217] usb 2-1.2: GSM modem (1-port) converter now attached to ttyUSB0
[18716.131536] option 2-1.2:1.1: GSM modem (1-port) converter detected
[18716.131731] usb 2-1.2: GSM modem (1-port) converter now attached to ttyUSB1
[18716.132082] option 2-1.2:1.2: GSM modem (1-port) converter detected
[18716.132367] usb 2-1.2: GSM modem (1-port) converter now attached to ttyUSB2
[18716.132813] scsi30 : usb-storage 2-1.2:1.3
[18717.134034] scsi 30:0:0:0: Direct-Access     USBModem Disk             2.31 PQ: 0 ANSI: 2
[18717.134965] sd 30:0:0:0: Attached scsi generic sg2 type 0
[18717.144017] sd 30:0:0:0: [sdb] Attached SCSI removable disk
```And let me also mention again that I still have to use that unplug > replug cycle every 15-30 minutes (when I'm on TataDocomo GSM), regardless of whether I'm on Win7 or Ubuntu on the same lappy. But at least it gets detected everytime after following the replug cycle (sometimes many times in a row!). Point is, maybe some modems and/or services are too buggy to cope with. This leads to yet another question-

4) Have you tried the modem on any other OS (preferably on windows, to which these products are usually dedicated)? If yes, how was the performance & consistency there?


With this, I'll leave it to *bra|10n* again (or anyone watching and interested) as I may get lost again for a couple of days.

Good luck!

**PS :**
Oh, and there's a tip also-
Please use 'Code' tags (**#** symbol at the top of edit box) instead of 'Quote' tags for outputs. It is the correct way to post commands and their outputs as it preserves their formatting, keeps the post look short & clean and also makes the codes easier to quote :)

---

### Post by bra|10n on 2012-11-01
Aparna R,
I think the best thing to do is start over again. 
I'm not familiar with the approach that varunendra has taken and as he said it's likely the two method's are conflicting. 
I suggest that you save all files you have created in a folder somewhere and start over clean. 
As varunendra will be unavailable for the next few days it makes sense to start over using my method to see if we can't get a solution.
Let me know what you want to do from here...

---

### Post by Aparna R on 2012-11-02
Well,
let me check all again....
will reply in few days.
BTW,my modem is a CDMA one,not GSM.

regards,

---

### Post by Aparna R on 2012-11-29
sorry for being late...
the problem is still unsolved.I dont use ubuntu for weeks,thinking to revert to ubuntu 10 itself..:(

this may be a sum up of what we had done:

Initially we had

```
$ **lsusb**
Bus 005 Device 002: ID 05c6:[COLOR="Red"]9004[/COLOR] Qualcomm, Inc.
``` 

then created the files:

```
**/usr/bin/usbModemScript**
 #!/bin/bash
  echo 05c6 [COLOR="red"]9004[/COLOR] > /sys/bus/usb-serial/drivers/option1/new_id
```


```
**etc/udev/rules.d/option.rules**

ATTRS{idVendor}=="05c6", ATTRS{idProduct}=="[COLOR="red"]9004[/COLOR]", RUN+="/usr/bin/usbModemScri$
 ATTRS{idVendor}=="05c6", ATTRS{idProduct}=="[COLOR="red"]9004[/COLOR]", RUN+="/sbin/modprobe option"

```

and the command gave the output:
```
$ **usb-devices**
T:  Bus=05 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=05c6 ProdID=[COLOR="red"]9004[/COLOR] Rev=00.00
S:  Manufacturer=Qualcomm, Incorporated
S:  Product=Qualcomm CDMA Technologies MSM
C:  #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
```

created the file:
```
**/etc/usb_modeswitch.d/05c6:f000**

# Qual-Comm HS-USB ("LinuxModem")

TargetVendor=  0x05c6
TargetProduct= 0x[COLOR="red"]f000[/COLOR]

MessageContent="5553424312345678000000000000061b000000020000000000000000000000"
CheckSuccess=20
```

and run the commands
```
sudo rmmod usbserial
sudo modprobe usbserial
sudo usb_modeswitch -v 05c6 -p f000
```
but it gave the same output as before.But when I changed the product id to '9004' here in the above file and in all other places,produced a different output.
```
**usb_modeswitch -v 05c6 -p 9004**

Looking for default devices ...
   found matching product ID
   adding device
 Found device in default mode, class or configuration (1)
Accessing device 002 on bus 005 ...
Getting the current device configuration ...
 OK, got current device configuration (1)
Using first interface: 0x00
Using endpoints 0x01 (out) and 0x81 (in)
Not a storage device, skipping SCSI inquiry

USB description data (for identification)
-------------------------
Manufacturer: Qualcomm, Incorporated
     Product: Qualcomm CDMA Technologies MSM
  Serial No.: not provided
-------------------------
Warning: no switching method given.
-> Run lsusb to note any changes. Bye.

```

and
```
 **dmesg | tail -20**

[ 1951.184058] usb 5-2: USB disconnect, device number 2
[ 1954.152028] usb 5-2: new full-speed USB device number 3 using uhci_hcd
[ 1954.410704] Initializing USB Mass Storage driver...
[ 1954.412453] scsi4 : usb-storage 5-2:1.0
[ 1954.412631] usbcore: registered new interface driver usb-storage
[ 1954.412636] USB Mass Storage support registered.
[ 1954.449882] usbcore: registered new interface driver uas
[ 1955.418074] scsi 4:0:0:0: CD-ROM            Qualcomm MMC Storage      2.31 PQ: 0 ANSI: 2
[ 1955.432060] sr2: scsi-1 drive
[ 1955.432335] sr 4:0:0:0: Attached scsi CD-ROM sr2
[ 1955.432519] sr 4:0:0:0: Attached scsi generic sg3 type 5


Looking for default devices ...
 No devices in default mode found. Nothing to do. Bye.
```


huh...If we could solve this problem that would be great.There is no upgraded driver version available,but i am interested in making driver compatible to the OS by trying ourselves,we can learn the things..atleast.:)

regards.

---

### Post by varunendra on 2012-11-29
Hi Aparna!

The confusion still prevails. You are saying -
> Initially we had
```
$ **[COLOR="Red"]lsusb[/COLOR]**
Bus 005 Device 002: ID 05c6:**[COLOR="Red"]9004[/COLOR]** Qualcomm, Inc.
```
While the first report of lsusb in 'this' thread was in [post #5]("http://ubuntuforums.org/showthread.php?p=12310614"), according to which -
> lsusb
..
Bus 005 Device 003: ID 05c6:**[COLOR="Red"]f000[/COLOR]** Qualcomm, Inc. 

I believe 'lsusb' can't be wrong, but am not sure of anything at this point. So I'd suggest exactly what bra|10 suggested in post #20 -
> I think the best thing to do is start over again. 

Accordingly, please 'move' all the custom files you have created so far and start over again with a clean environment. Shouldn't take long if things are clear.

If I'm not missing anything, these are all the files we have created so far -
post #10 :
/usr/bin/usbModemScript
/etc/udev/rules.d/option.rules

post #11 :
/etc/rc.local [COLOR="DarkRed"](modified the existing file)[/COLOR]

post #13 :
/etc/usb_modeswitch.d/05c6:f000

post #18 (implied post #14, 15) :
/lib/udev/rules.d/40-usb_modeswitch.rules [COLOR="DarkRed"](created? When??)[/COLOR]
/etc/modules [COLOR="DarkRed"](modified the existing file)[/COLOR]

Anything missing..? *(phew..!)*


So.... we can either try to move/remove custom files and undo changes, then start fresh,

Or,

We can do a fresh install of 12.04 and start 'truly' fresh. (using this approach which has been tested successfully a few times - [http://ubuntuforums.org/showpost.php?p=11899627&postcount=11](http://ubuntuforums.org/showpost.php?p=11899627&postcount=11))

Please let me know what you prefer and we may proceed accordingly.

--Varun

---

### Post by Aparna R on 2012-11-30
> **varunendra said:**
> Hi Aparna!

The confusion still prevails. You are saying -

While the first report of lsusb in 'this' thread was in [post #5]("http://ubuntuforums.org/showthread.php?p=12310614"), according to which -


I believe 'lsusb' can't be wrong, but am not sure of anything at this point. So I'd suggest exactly what bra|10 suggested in post #20 -

sorry sorry it was my mistake..big mistake .I wrongly edited.it is:
```
$ lsusb
Bus 005 Device 002: ID 05c6:f000 Qualcomm, Inc.
```

> Accordingly, please 'move' all the custom files you have created so far and start over again with a clean environment. Shouldn't take long if things are clear.

If I'm not missing anything, these are all the files we have created so far -
post #10 :
/usr/bin/usbModemScript
/etc/udev/rules.d/option.rules

post #11 :
/etc/rc.local [COLOR="DarkRed"](modified the existing file)[/COLOR]

post #13 :
/etc/usb_modeswitch.d/05c6:f000

post #18 (implied post #14, 15) :
/lib/udev/rules.d/40-usb_modeswitch.rules [COLOR="DarkRed"](created? When??)[/COLOR]
/etc/modules [COLOR="DarkRed"](modified the existing file)[/COLOR]

Anything missing..? *(phew..!)*


So.... we can either try to move/remove custom files and undo changes, then start fresh,

Or,

We can do a fresh install of 12.04 and start 'truly' fresh. (using this approach which has been tested successfully a few times - [http://ubuntuforums.org/showpost.php?p=11899627&postcount=11](http://ubuntuforums.org/showpost.php?p=11899627&postcount=11))

Please let me know what you prefer and we may proceed accordingly.

--Varun

Thanks,I prefer to remove all the files to have a fresh start.
Where to begin then?

---

### Post by varunendra on 2012-12-01
> **Aparna R said:**
> Thanks,I prefer to remove all the files to have a fresh start.
Where to begin then?
Hmm.. I'd have preferred to start "truly fresh", but as you wish :)

Copy-paste the following in a new file, and save it as "cleanup.sh" (or whatever name you like) in your home directory -
```
#!/bin/bash

# create backup directory -
mkdir oldfiles

# move custom files to the created directory -
sudo mv /usr/bin/usbModemScript oldfiles/
sudo mv /etc/udev/rules.d/option.rules oldfiles/
sudo mv /etc/usb_modeswitch.d/05c6:f000 oldfiles/

# backup system files -
cp /etc/rc.local oldfiles/
cp /lib/udev/rules.d/40-usb_modeswitch.rules oldfiles/
cp /etc/modules oldfiles/

# undo changes in system files -
sudo sed -i '/product=0xf000/ d' /etc/rc.local
sudo sed -i '/^# Qual-Comm HS-USB/,+2 d' /lib/udev/rules.d/40-usb_modeswitch.rules
sudo sed -i '/^option/ d' /etc/modules

# generate current-status report file -
exec > ~/Desktop/aparna.txt 2> /dev/null

echo -e "====bin===="
ls /usr/bin/usb*

echo -e "\n\n====udvrules===="
ls /etc/udev/rules.d

echo -e "\n\n====usbmodsw===="
ls /etc/usb_modeswitch.d

echo -e "\n\n====rc.local===="
cat /etc/rc.local

echo -e "\n\n====lb-udv-rules-40-usbmdsw===="
cat /lib/udev/rules.d/40-usb_modeswitch.rules

echo -e "\n\n====etc-modules===="
cat /etc/modules

# end of cleanup
```
Now make it executable via gui or via command -
```
chmod +x cleanup.sh
```

Then run it by either **double-click > "Run"**, or in terminal -
```
./cleanup.sh
```

It will create a file named "aparna.txt" on your desktop. Leave it there. Reboot > plug-in your modem, then run the following (you may copy-paste to avoid typo) one-by-one -
```
cd ~/Desktop
echo -e "\n\n========" >> aparna.txt
lsusb >> aparna.txt

echo -e "\n\n========" >> aparna.txt
usb-devices | grep -iA10 -B2 05c6 >> aparna.txt

echo -e "\n\n========" >> aparna.txt
lsmod | grep -e option >> aparna.txt

echo -e "\n\n========" >> aparna.txt
dmesg | tail -20 >> aparna.txt

echo -e "\n\n========" >> aparna.txt
cat /var/log/syslog | grep -ie modem -e modeswitch -e option >> aparna.txt

tar -cjf aparna.tar.bz2 aparna.txt
```
The last command will create an archive named "aparna.tar.bz2" on your desktop. Attach this file in your next post (use "Manage Attachments" button below edit-box) so we can see the status after cleaning up.

---

### Post by Aparna R on 2012-12-02
> **varunendra said:**
> Hmm.. I'd have preferred to start "truly fresh", but as you wish :)


:)

thanks a lot..
Will reply soon

---

### Post by Aparna R on 2012-12-07
done.:p
please i need the things a little bit faster.
for me final solution solution is to just change the ubuntu verion.
thanks.

---

### Post by Aparna R on 2012-12-07
please find the attachment

---

### Post by bra|10n on 2012-12-07
> **Aparna R said:**
> done.:p
please i need the things a little bit faster.
for me final solution solution is to just change the ubuntu verion.
thanks.

For a "working out-of-the-box solution" support for these devices needs to be built into the kernel. 
So unless you already know of an Ubuntu version (or different distro) where your USB modem works straight away, I think just changing versions or distro's will not solve your problem. Using the newest available kernel version will greatly increase your chances of success.

@varunendra,

I looked at the results of your script Aparna R posted above and the modem seems to be loaded and recognised as 05c6:f000. 
However I suggest there is no instruction associated with this device so the system doesn't know what to do with it... refer to post #12.
I think you'll need to confirm if the file **05c6:f000** exists in Aparna R's */etc/usb_modeswitchd* folder. If not I'd say this is the issue.
If not, there are a number of 05c6:**** files that can be copied and adapted. 
Perhaps look at all of them and see how they differ before creating a 05c6:f000 file (of course changing all **** to f000)

Regards.

---

### Post by Aparna R on 2012-12-25
I solved the problem by reverting to the old version ubuntu 10 itself,where it works fine.
Thank you for the support and help.

---

