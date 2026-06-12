---
title: "[SOLVED] Complete newb needs some help"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by Sigmarius on 2008-11-06
I just installed Ubuntu on my Dell 600m laptop.

I can get online if I plug an ethernet cable into the port, but I can't get online wirelessly.

I downloaded the drivers, extracted them, and now I don't know what to do from there.

The file is the ipw2200-1.2.2.  I've read the install file, but I don't understand most of what it's saying.

Can someone give me some complete idiot proof directions as to what to from here?

I know how to get to the terminal, so you don't have to explain that part.

Assume that I know nothing else about Ubuntu, or how it works.

Thanks ahead of time for any help I can get.

---

### Post by Sorivenul on 2008-11-06
Are you sure it's actually an ipw2200 card?  I have one and it works out of the box in almost every distribution, especially 8.04 and 8.10.  

So we can better help you, please post the output of:
```
lspci
```

---

### Post by chrisod on 2008-11-06
I've got the 600m and mine does have the 2200. It just worked in both 7.x and 8.04.

---

### Post by Jagermage on 2008-11-06
Ok, this is Sigmarius.

I had to register a new account.  For some reason, whenever I try to login to the forums, to post a reply, or whatever, it brings me back to the login screen, and won't let me do anything.

I think I'm running Ubuntu 8.10 (intrepid?)

Here's the output:

00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

---

### Post by th89 on 2008-11-06
Try going to System > Administration > Hardware Drivers and see if your wireless card is listed. If it is, enable it and reboot to use the drivers. This is the easiest way to do it, if you can.

---

### Post by Sigmarius on 2008-11-09
Ok.

First off, let me say thanks for all the help I've gotten so far, even if it hasn't actually worked.

Secondly, can anyone tell me why, when I try to log in to the forums, it usually doesn't let me?  Normally, I log in at the front page, and it gives me the welcome message.  I do a search, or go into a thread, and it logs me out.  When I go to reply or check my PMs, it takes me to the login screen.  I login, and get the "Thank you for logging in.  Click here if your browser doesn't automatically redirect you." I wait a few seconds, and it takes me back to the login screen.

This has happened on 3 different computers, 1 running ubuntu 8.10, one running 64-bit Vista, and the other running XP.  It's also happened using Firefox, Google Chrome, and IE.

ANYWAY......

Back to the issue of the drivers for my laptop, the one running 8.10 Ubuntu..

I did the "System>Administration>Hardware Drivers" thing, and it came up with nothing.

I did a "Hardware Testing" run, and this is what it gave me for network settings.  I was NOT hooked into an ethernet cable when I did this, so I had no internet connection at the time.

"Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
Intel Corporation PRO/Wireless 2200BG [Celexico 2]
Network Connection (rev 05)"

I downloaded the drivers for my broadcom, and extracted them to the desktop.  I have no idea what to do from there.

At least, I think they are the drivers.  The extracted folders (there were two things I downloaded) are called "ipw2200-1.2.2" and "ipw2200-fw-3.0).

The folder "ipw2200-1.2.2" has the text file "install" in it, but I don't understand most of what it's saying.

Thanks again for the help everyone.

---

### Post by Sorivenul on 2008-11-09
Can you post the output of:
```
lsmod
```

The ipw2200 drivers and such that you have are for your Intel PRO/Wireless card, and should not have to be recompiled or anything.  The problem here seems to be the Broadcom.  I believe the module we are looking for is "b44".  This should be the module that supports your card.  Post the output and we'll go from there.

---

### Post by Sigmarius on 2008-11-10
Here ya go:

Module                  Size  Used by 
isofs                  40100  0 
udf                    88356  1 
crc_itu_t              10112  1 udf 
radeon                147616  2 
drm                    86056  3 radeon 
rfcomm                 44432  0 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge 
bnep                   20480  2 
l2cap                  30464  6 rfcomm,bnep 
bluetooth              61924  6 rfcomm,sco,bnep,l2cap 
ppdev                  15620  0 
acpi_cpufreq           15500  0 
cpufreq_conservative    14600  0 
cpufreq_powersave       9856  0 
cpufreq_userspace      11396  0 
cpufreq_stats          13188  0 
cpufreq_ondemand       14988  1 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand 
container              11520  0 
sbs                    19464  0 
pci_slot               12552  0 
sbshc                  13440  1 sbs 
wmi                    14504  0 
af_packet              25728  6 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter 
x_tables               22916  1 ip_tables 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp 
joydev                 18368  0 
pcmcia                 43052  0 
dcdbas                 15008  0 
evdev                  17696  10 
psmouse                45200  0 
serio_raw              13444  0 
pcspkr                 10624  0 
snd_intel8x0           37532  3 
snd_ac97_codec        111652  1 snd_intel8x0 
ac97_bus                9856  1 snd_ac97_codec 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss 
snd_pcm                83204  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss 
video                  25104  0 
output                 11008  1 video 
snd_seq_dummy          10884  0 
ipw2200               151244  0 
ieee80211              38088  1 ipw2200 
ieee80211_crypt        13572  1 ieee80211 
yenta_socket           31756  2 
rsrc_nonstatic         19072  1 yenta_socket 
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi 
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
button                 14224  0 
snd_timer              29960  2 snd_pcm,snd_seq 
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
battery                18436  0 
ac                     12292  0 
snd                    63268  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt 
soundcore              15328  1 snd 
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm 
intel_agp              33724  1 
agpgart                42184  2 drm,intel_agp 
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp 
ext3                  133384  1 
jbd                    55444  1 ext3 
mbcache                16004  1 ext3 
sr_mod                 22212  1 
cdrom                  43168  1 sr_mod 
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod 
sg                     39732  0 
ata_piix               24580  3 
pata_acpi              12160  0 
b44                    35984  0 
ata_generic            12932  0 
libata                177312  3 ata_piix,pata_acpi,ata_generic 
ssb                    40580  1 b44 
mii                    13440  1 b44 
uhci_hcd               30736  0 
ehci_hcd               43276  0 
scsi_mod              155212  4 sr_mod,sd_mod,sg,libata 
usbcore               148848  3 uhci_hcd,ehci_hcd 
dock                   16656  1 libata 
thermal                23708  0 
processor              42156  3 acpi_cpufreq,thermal 
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon 
font                   16512  1 fbcon 
bitblit                13824  1 fbcon 
softcursor              9984  1 bitblit 
fuse                   60828  3

---

### Post by Sorivenul on 2008-11-10
After some more research, the b44 module should be fine, as it simply handles your ethernet, and your problems are wireless.
The problem is, your wireless should be working out of the box, AFAIK.
What version of Ubuntu are you using?  Hardy?  Intrepid? A kernel version would do fine.
```
uname -a
```
In the meantime try:
```
sudo rmmod ipw2200
```
```
sudo modprobe ipw2200
```
```
sudo /etc/init.d/networking restart
```

EDIT:
Just a thought, but is the wireless card even active?
```
iwconfig
```

---

### Post by Sigmarius on 2008-11-10
Ok.

I'm using Intrepid.

The first command, the "rmmod" one, did nothing except repeat the username line.

The second command, did nothing, except repeat the username line thing.

The network restart gave me the following, after testing some stuff:

"No DHCPOFFERS received.
No working leases in persistent database - sleeping."

When I look at my network manager thing, the only network I can detect is "Io", a feedback network, whatever that is.

I have the "function button+f2" ability to turn my internal wireless card on and off.  I've tried detecting and connecting to a wireless network both before and after pressing the combination, just to make sure.

Thanks again for your help.

---

### Post by Sorivenul on 2008-11-10
If you only see "lo" that is the problem.
Try: 
```
sudo ifconfig eth1 up

```and
```
sudo ifconfig eth0 up
```
One of these should bring up your wireless card.

Then:
```
iwconfig
```
This time it should return something like:
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Home Network"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1C:DF:3A:C3:33   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=80/100  Signal level=-49 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8   Missed beacon:4

```

---

### Post by Sigmarius on 2008-11-10
Neither of the first two commands did anything except repeat the "sigmarius@Arcxis:~$" line.

Is that "ifconfig" supposed to be "ipconfig"?  I tried that, and it asked me for the password, but then told me "ipconfig" command not found.

---

### Post by Sorivenul on 2008-11-10
Neither of the first two command should have done anything but return the line you describe.  This means they are not returning errors.  
Post the output of "iwconfig" (without quotes) now and we'll see what's going on.

---

### Post by Sigmarius on 2008-11-10
Ok.  I guess that's good on the first part.  Here's the output:

> lo        no wireless extensions. 

eth0      no wireless extensions. 

pan0      no wireless extensions. 

eth1      radio off  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

I'm gonna go out on a limb and guess that means that my card isn't on..

I'll turn it on (though I thought it WAS on), and try it again, and see what happens.

---

### Post by Sorivenul on 2008-11-10
> **Sigmarius said:**
> 
eth1      radio off  ESSID:off/any  
         
I'm gonna go out on a limb and guess that means that my card isn't on..

I'll turn it on (though I thought it WAS on), and try it again, and see what happens.

Good assumption.  :)
Turn it on and repost your output like you said.

---

### Post by Sigmarius on 2008-11-10
So, I hit the button that should turn it on, and ran the command line again.

Nothing.

I rebooted, and after a bit of research on the web, found out that maybe, just maybe, it got turned off in the BIOS when I installed Ubuntu (granted, the guy was talking about a windows re-install, but hey, it could happen, maybe).  I went into the BIOS, and it says that the wireless is enabled.

I rebooted after that, and still nothing with the "iwconfig".

So....now what?

---

### Post by Sorivenul on 2008-11-10
First, you will need to redo the "sudo ifconfig eth1 up" step, just to be sure your interface is enabled.  
What it sounds like is referred to as an "rf_kill" switch.  Yours is off for some reason.  
Try:
```
for i in 'find /sys -name "rf_kill" ; do echo 0 > $i ; done
```
After that redo "sudo /etc/init.d/networking restart" and repost output of "iwconfig".

---

### Post by Sigmarius on 2008-11-10
Hey, I just noticed that when I hit the "function + f2" buttons, and then re-run the "iwconfig", there's a change.

On the line on my previous post that says "eth1 radio off" it changes to "eth1 unassociated".

I'm guessing this matters, right?

---

### Post by Sorivenul on 2008-11-10
> **Sigmarius said:**
> Hey, I just noticed that when I hit the "function + f2" buttons, and then re-run the "iwconfig", there's a change.

On the line on my previous post that says "eth1 radio off" it changes to "eth1 unassociated".

I'm guessing this matters, right?

Very much so.  Unassociated means the card is on, but not connected to your wireless network.

Get it to that state again.  Then do:
```
iwlist eth1 scan
```

This should display the networks in your area.  Find yours.  And now the graphical part, as best I can help:

Right click the Network Manager icon in the panel (the one that should tell you about your wired/wireless connections).  Click Edit Connections...  Select the "Wireless" tab.  Click Add.  Make sure "Connect Automatically" is selected and set your connection attributes. The "SSID" section should be the printed name from the result of the "iwlist" command.  If you don't know some of the others, post what you can about your home networking setup and you should get some feedback.

---

### Post by psycosmyth on 2008-11-10
This sounds familiar. are you using a cable type modem with your router?
We need to know if there are any other devices on your network.

---

### Post by Sigmarius on 2008-11-10
Yes, I am using a cable modem.

On my network, by which I mean plugged into my wireless router, are the following:

Phalanx, my desktop that I am currently using.
My xbox 360 (turned off)

My laptop (Arcxis) is the one running Intrepid (ubuntu 8.10), and the one I'm trying to connect wirelessly.

I added the wireless network, but it's not showing up on my network manager.  I'm in the process of rebooting to see what happens.

---

### Post by Sigmarius on 2008-11-10
So, after the reboot, I couldn't get it to connect.

I went to the terminal, and ran the "iwlist eth1 scan" command.

The first time, came back with nothing.

The second time, showed me my wireless network.

Ran it again, nothing.  Ran about 2 dozen more times...nothing.

I closed the terminal, ran it again, nothing on the first go.

Second time, came back with my network.

Third time and several more after that, came back with my network, though the "Extra: Last beacon: xxxxx ms ago" kept growing, ending at 14756 ms.

After that, keeps coming back with "eth1   No scan results".

But if I wait a minute and do it again, it comes back with my network.

---

### Post by hyper_ch on 2008-11-10
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by Sigmarius on 2008-11-10
My apologies.

---

### Post by psycosmyth on 2008-11-11
easy on the newb hyper! He may have an issue with the modem it's self and not sure about config. I don't know much about that brand. Some cable modems act odd when accessed by a Linux based system. I can only connect by using Dreamlinux on my Mom's PC. You might want to explore restricted kernels to see if this can be resolved.

---

### Post by Sigmarius on 2008-11-11
I had a buddy of mine look at my laptop yesterday, and he told me the following:

"That driver, from what I understand, and I could be wrong, couldn't be installed as a module, it has to be put directly into the kernel, so you need to find a tutorial that tells you how to recompile the kernel."

He also said that my "eth1 wasn't listed in my interface file. (/etc/network/interfaces)"

Is he right?  I'm running 8.10 (Intrepid).  I'm wondering if I should just downgrade back to 8.4.

So far as my modem, I'm running the Motorola SB5101.

My wireless router is a Belkin (which I'm told sucks) F5D7230 v 4.9.

As I put in a previous post, I noticed that, when I run the command to detect a wireless network, it does show up, for about 15, 20 seconds, and then comes back with a no network detected thing for about the same amount of time.

---

### Post by Sorivenul on 2008-11-11
> **Sigmarius said:**
> I had a buddy of mine look at my laptop yesterday, and he told me the following:

"That driver, from what I understand, and I could be wrong, couldn't be installed as a module, it has to be put directly into the kernel, so you need to find a tutorial that tells you how to recompile the kernel."

He also said that my "eth1 wasn't listed in my interface file. (/etc/network/interfaces)"

Is he right?  I'm running 8.10 (Intrepid).  I'm wondering if I should just downgrade back to 8.4.

So far as my modem, I'm running the Motorola SB5101.

My wireless router is a Belkin (which I'm told sucks) F5D7230 v 4.9.

As I put in a previous post, I noticed that, when I run the command to detect a wireless network, it does show up, for about 15, 20 seconds, and then comes back with a no network detected thing for about the same amount of time.

Okay.

The ipw2200 module is included by default in Ubuntu this is why you were able to load and unload the module with "modprobe" and "rmmod".  

I have no interfaces other than the loopback device in my /etc/network/interfaces either, but can connect fine.

Have you tried the instructions I posted before to graphically set up your connection with NetworkManager now that you can see it sometimes?

---

### Post by Sigmarius on 2008-11-11
I added the network to the network manager, using the gui.  However, it doesn't seem to be connecting at all.

Is there some sort of notification that it's supposed to give me saying that it's connected?

---

### Post by Sorivenul on 2008-11-11
> **Sigmarius said:**
> I added the network to the network manager, using the gui.  However, it doesn't seem to be connecting at all.

Is there some sort of notification that it's supposed to give me saying that it's connected?

It should pop up a "bubble" saying something like "Now Connected to 'HOME NETWORK'".  And obviously the wireless "bars" should be there in the NetworkManager applet.  See my screenshot.

---

### Post by Sigmarius on 2008-11-11
Yeah, I don't get that.

One thing I'm going to try:  A lot of my friends, and my wife, have a hard time connecting to my wireless network.  My wife's windows laptop works for a few minutes, and then she has to repair the connection.

I'm beginning to think that my router might be screwing up, especially with the "cycling" of my laptop detecting the network and not detecting it.

I'm going to take my laptop to Panera Bread or something, and see if I can get it to connect to a network.

However, if the problems I'm having are definitely my laptop, and not my router, then please, continue to offer suggestions.

Like I said, I don't get any notification or anything saying it's connected.

And yes, I added it to the list, and punched in my password for the WPA protection.  Though, and I'm guessing it's supposed to do this, after I saved the network, and went back into a while later, I noticed that the password was nothing but random numbers and letters when I hit "show password".  I'm guessing it's showing me the numbers and letters it used to encrypt the signal.

But, I'm just guessing.

Anyway, again, thanks for your continued help.

---

### Post by Sorivenul on 2008-11-11
If a lot of folks are having issues with your router it could very well be the problem, and not your laptop or Ubuntu. I'll be interested to hear the results.

As for the WPA and random characters when you check the password, that's normal.  

Good luck!

---

### Post by Sigmarius on 2008-11-12
Alright, so.

I took my laptop to a friends house.  I added his wireless network to the list.  I waited about 10 seconds, and nothing happened.

I was just about to go back and start fiddling with it when it told me I was connected.

This tells me that obviously, it has been my router this entire time.

So, I'm sorry to have wasted everyone's time, and thank you for all the help you gave me.

I'm not sure how to mark it, but I guess we can mark this one solved.

Thanks again.

---

### Post by Sorivenul on 2008-11-12
Glad to hear you figured it out, but I'm sorry about your router.  

To mark the thread solved go to the top of the page and look for a red link that says "Thread Tools".  Click it and a menu should drop down with an option to mark the thread as solved.

Oh, and you didn't waste anybody's time, especially if you learned something from the process.  Cheers!

---

