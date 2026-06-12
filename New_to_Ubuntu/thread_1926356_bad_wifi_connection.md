---
title: "bad wifi connection?"
date: 2012-02-16
forum: New to Ubuntu
---

### Post by Lalaith on 2012-02-16
Hi all, 

I'm running Ubuntu 11.10 alongside with Windows 7. I recently moved to a place where the internet connection is not running well and most of the time is slow. I have seen that with w7 my internet connection is faster than it does with Ubuntu.

I thought that the syncronization of files with UbuntuOne might be slowing down the connection, so I did
```

top

```looked for the process of syncUbuntuOne (I can't recall the name but it was something like this) and did

```

kill 2328

``` wich was the number of the process printed in top.

But didn't notice any change. So maybe it's time to do something properly. My questions are:

- Is there any command that shows you the speed of the connection? Is there any way I can compare it with the speed I have with w7?
- Is there any command that allows you to see wich processes are using internet?
- Am I pointing right or you think there's a better way to face this?

Finally, a little bit of info: before I moved here I didn't have any problems with the speed in any OS, but didn't use UbuntuOne sync either.

I guess you will ask me to print what does "lspci" says, so here it is:
```

                                  00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:01.1 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation Device 1050 (rev a1)
04:00.0 Network controller: Intel Corporation Centrino Wireless-N 100
05:00.0 Ethernet controller: Atheros Communications AR8151 v2.0 Gigabit Ethernet (rev c0)


```Thank you!

---

### Post by I2k4 on 2012-02-16
No terminal experience or experience with UbuntuOne (I use DropBox), but why not try 

[www.speedtest.net](www.speedtest.net)

on both W7 and Ubuntu and compare?  I've never experienced any comparative performance problem - essentially the same ISP download/upload performance on either OS.  I've checked Speedtest.net against my ISP's (Bell Canada) speed tester, and the tests are the same.  You might also try connecting via ethernet instead of wi-fi and run the same speed test - if the wi-fi is slower than ethernet, the problem may be with your wi-fi modem or its settings.

---

### Post by Lalaith on 2012-02-17
Thanks for your reply. Speedtest is really useful.

What happened:

In Windows I have a speed around 0.5 Mbps in up and download.
In Ubuntu, when I can surf well I have a download speed of around 5 Mbps and upspeed around 0.5 Mbps. But 10 minutes after I tested, my internet connection slewed down, I ran a new speed test and the results where up and down speeds of 0.03 Mbps.
I then rebooted an checked again the windows speed: nothing had changed, it was still 0.5 Mbps.

(Ping signals always stays around 70 ms at all tests).

Something is wrong with Ubuntu... configuration? weid process? Can anybody give me a clue?

Thanks

---

### Post by I2k4 on 2012-02-17
I'll leave it to more knowledgeable Ubuntu users as to difference with Windows.  

Another thing to try, since you seem to be in a weak signal area, is to test if your ISP has a DNS problem. You can set the wi-fi modem/router to use an alternative DNS service.

Google offers a good free one:

[http://code.google.com/speed/public-dns/](http://code.google.com/speed/public-dns/)

Also OpenDNS I think still has a free service, and there are several guides online for setting up various router/modem brands and finding other alternative local DNS - usually a matter of using a browser to access a set up page in the router/modem and entering the numbers for the alternative DNS.

I'll mention one other thing that hurt wi-fi performance on my Acer netbook, the Atheros wi-fi card has a "power saving" setting that must be completely disabled for best performance.

---

### Post by Lalaith on 2012-02-20
Thanks I2K4 for helping =)

I'll have to learn about DNS, do you think it can be the cause?

I've learnt a command, iwconfig, that displays info about the wifi connection. There it states: "power management: off", so I guess I don't have a problem with the power management of the card. :)

Next I'll do is check if the stats that give "iwconfig" remain the same when I have good and bad connection...

---

### Post by kurt18947 on 2012-02-20
This is not helpful per se but there was a person with a similar problem.  Speed would be good for a few minutes then drop a lot.  It might be worth searching in the networking & wireless forum.  I don't recall the wifi card in question there or if there was a solution, just recall a similar problem.

---

### Post by wildmanne39 on 2012-02-20
Hi, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by bogan on 2012-02-21
Hi! **lalaith**,

As a matter of interest , I also get wide variations in my WiFi connection using Ubuntu 11.10, whereas in Win7 it seems fairly constant.

With actual downloads I get shown speeds of anything from 150 KB/s to 850 KB/s.

Whilst the Network manager often varies between 100% and 38%.

I just ran [www.speedtest]("http://www.speedtest") in 11.10 and in Win7, and both showed the same speeds: 

6.8 MB/s download and 0.35 MB/s upload, with a Ping of 24 ms.

Figures that are a figment of imagination as far as actual performance is concerned.

**Edit**: I do not use UbuntuOne.

Chao!, **bogan**

---

### Post by Lalaith on 2012-02-21
Hi, 

kurt 18947: I'll search for threads of the subforum you said there was something... any additional info can be helpful.

bogan, what do you mean with "Figures that are a figment of imagination as far as actual performance is concerned.":confused: And how can you see how much is the network manager working? When I'm on a public wifi net I don't notice the slowing (although it exists on Ubuntu, I've proved it). the problem is when I'm using a bad signal =(.

This are the outputs that wildmanne39 asked for.

```
neus@Asus-Neus:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux Asus-Neus 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:44:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
neus@Asus-Neus:~$ lspci -nnk | grep -iA2 net
04:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 100 [8086:08ae]
    Subsystem: Intel Corporation Centrino Wireless-N 100 BGN [8086:1005]
    Kernel driver in use: iwlagn
--
05:00.0 Ethernet controller [0200]: Atheros Communications AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1851]
    Kernel driver in use: atl1c
neus@Asus-Neus:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Stadtbibliothek"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:22:55:ED:CF:C1   
          Bit Rate=5.5 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=26/70  Signal level=-84 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:186   Missed beacon:0

neus@Asus-Neus:~$ rfkill list all
0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
neus@Asus-Neus:~$ lsmod
Module                  Size  Used by
msr                    12908  0 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282548  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
nvidia              11713772  0 
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
arc4                   12529  2 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  2 
snd_hda_codec         104931  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  2 snd_hda_intel,snd_hda_codec
i915                  571221  3 
iwlagn                314257  0 
snd_seq_midi           13324  0 
drm_kms_helper         42558  1 i915
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
joydev                 17693  0 
mac80211              462046  1 iwlagn
drm                   236290  4 i915,drm_kms_helper
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
i2c_algo_bit           13423  1 i915
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              199630  2 iwlagn,mac80211
mei                    41480  0 
soundcore              12680  1 snd
video                  19412  1 i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
psmouse                73882  0 
asus_nb_wmi            12517  0 
asus_wmi               20035  1 asus_nb_wmi
mxm_wmi                12979  0 
sparse_keymap          13890  1 asus_wmi
serio_raw              13166  0 
wmi                    19256  2 asus_wmi,mxm_wmi
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
atl1c                  41643  0 
ahci                   26002  2 
libahci                26861  1 ahci

```

Thnks to all!

---

### Post by kurt18947 on 2012-02-21
Here's one with an older Intel WiFi chip:

[http://ubuntuforums.org/showthread.php?t=1917065&highlight=speed+drops](http://ubuntuforums.org/showthread.php?t=1917065&highlight=speed+drops)

It appears that sometimes switching to WiCD helps, sometimes it doesn't so there's probably more than one problem lurking.

---

### Post by I2k4 on 2012-02-21
> **Lalaith said:**
> Thanks I2K4 for helping =)

I'll have to learn about DNS, do you think it can be the cause?

I suggested it because you said you'd moved to a weak signal area, and DNS is worth checking.  I suggest trying Google's free DNS to see, since it works pretty well almost everywhere and might do better where your ISP is weak.  

Although I've reset my modem/router you can simply reset your individual computer - scroll down to Google's Ubuntu instructions here:

[http://code.google.com/speed/public-dns/docs/using.html](http://code.google.com/speed/public-dns/docs/using.html) 

This will probably not affect the difference you are experiencing between Windows and Ubuntu, but could improve overall internet performance as Google's page describes.

---

### Post by wildmanne39 on 2012-02-21
Hi, please try this if it helps we will need to make it permanent:
```
sudo ifconfig wlan0 down
sudo rmmod -f iwlagn
sudo modprobe iwlagn 11n_disable=1
sudo ifconfig wlan0 up

```
Do not reboot after running these commands.
Thanks

---

### Post by bogan on 2012-02-21
Hi!,** lalaith**,

You Posted: >  what do you mean with[QUOTE] "Figures that are a figment of imagination as far as actual performance is concerned.":confused: [/QUOTE]  What I mean is that the fastest actual download I have seen is roughly 10 Mb per minute. ie 0.17 Mb/s, whereas speedtest claims 6.7 Mb/s.    
> And how can you see how much is the network manager working?  Have look at this Thumbnail.:  [ATTACH]213041[/ATTACH]

The number of chords shown on the NM Icon indicates the strength of the signal, and putting the Mouse cursor on it - without Clicking - shows the Network connection and signal strength.

In 11.10, logged-in to Ubuntu it does not work for some reason, but it still works in Gnome Classic, as you can see.

You can also run:>  iwlist scan  At the moment mine shows : >  Quality=58/70  Signal level=-52 dBm.  58/70 = 82%. 

Chao!,** bogan**.

---

### Post by Lalaith on 2012-02-21
Yeees! It worked! \\:D/

I tried what wildmanne39 suggested and the performance is much better now. I did some newbie mistakes writing lln_disable instead of 11n_disable, so I went from ](*,) to :guitar: soo fast! (guess it happens all the time with computers).

Could you explain a bit what we've done with this commands? 

To make it permanent, ist it ok if I write this in a script, make it executable and automatically run it on everyboot up? Maybie it's a newbie way but it's time to learn =)

Thanks to all of you for the suggestions and the time spent here. =)

---

### Post by wildmanne39 on 2012-02-21
Hi, this will make it permanent.
```
gksudo gedit /etc/modprobe.d/iwlagn.conf
```
Add a single line:
```
options iwlagn 11n_disable=1
```
save and close gedit, then reboot.

What this does is turn off the N speed in the intel chip because the driver for the intel cards does not handle N speed well but unless you have a connection above 54mbs it will not make a difference any way.
Thanks

---

