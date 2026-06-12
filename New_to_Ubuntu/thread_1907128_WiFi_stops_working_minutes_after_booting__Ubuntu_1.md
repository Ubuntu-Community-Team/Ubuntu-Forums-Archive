---
title: "WiFi stops working minutes after booting / Ubuntu 11.10 / Realtek RTL8192E"
date: 2012-01-10
forum: New to Ubuntu
---

### Post by mak.allen on 2012-01-10
Hi all,

I recently installed Ubuntu 11.10 through Wubi. Before I had a chance to explore the system properly I came across the following problem. I would be extremely grateful for any help from you guys! :)

When Ubuntu starts, my wireless network (only source of internet on my laptop...) is immediately detected and works beautifully for a moment. Then, after something like 5 or 7 minutes suddenly stops working. The connection icon still indicates "connected", "iwconfig wlan0" looks like I'm connected (correct ESSID etc.), however no sites can be accessed on Firefox and "ping www.google.com" fails (for other sites as well etc.). If I then disconnect from my network and try to reconnect, at each reconnection attempt my password is rejected despite being correct (could this be some sort of timeout?), also eventually no networks are seen (and a few are visible from Win7). Logging out and in makes no difference, rebooting makes things work again for a moment, but this is hardly a solution.

WiFi works no problem under Win7.

I did not install any extra drivers, as far as I understand the driver for this card is now part of the distribution. I ran the command listing loaded modules (lsmod I think) and it listed actually two driver-looking names, rtl819xe and rtl-sth-else-but-sounding-similar, could it be that two drivers are loaded and then fight each other? What can I do to fix it? Any other ideas as to what the problems may be?

Many apologies that the details are a little fudged, it is just that I have to write it from Windows, as in Linux by the time I ran the terminal and a few commands my internet is out! But I can provide specific details once I know what to look for.

My Linux experience is pretty much zero, though I've used computers since I was three... :)

I'd be EXTREMELY grateful for any help to the problem, as I actually have to learn Linux now (and I'm pretty keen) and Internet would just be infinitely useful in the task!

---

### Post by mak.allen on 2012-01-11
I've now run "lsmod" and here is the output (it is still just a wild guess of mine that this might be the problem):

```

Module                  Size  Used by
michael_mic            12540  8
arc4                   12473  4
bnep                   17923  2
rfcomm                 38408  8
parport_pc             32114  0
ppdev                  12849  0
lp                     17455  0
parport                40930  3 parport_pc,ppdev,lp
binfmt_misc            17292  1
joydev                 17393  0
snd_hda_codec_realtek   254125  1
snd_hda_intel          24262  2
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0
uvcvideo               67271  0
videodev               85626  1 uvcvideo
snd_rawmidi            25241  1 snd_seq_midi
btusb                  18160  1
bluetooth             148839  23 bnep,rfcomm,btusb
psmouse                73673  0
snd_seq_midi_event     14475  1 snd_seq_midi
serio_raw              12990  0
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
r8192e_pci            234281  0
rtl8192se              94139  0
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
rtlwifi                95614  1 rtl8192se
i915                  505108  2
mac80211              272785  2 rtl8192se,rtlwifi
drm_kms_helper         32889  1 i915
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   192226  3 i915,drm_kms_helper
cfg80211              172392  2 rtlwifi,mac80211
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
ahci                   21634  1
libahci                25727  1 ahci
sky2                   49317  0

```
So as you see, there is:
r8192e_pci
rtl8192se
rtlwifi

and my card is rtl8192e, as far as I know rtl8192se is a different card... So is this wrong?

I also ran iwconfig after the internet died with the following result:
```

maciek@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  ESSID:"O2wirelessF0B925"  
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:26:44:F0:B9:25   
          Bit Rate=1 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management period:0us  mode:All packets received
          Link Quality=88/100  Signal level=-78 dBm  Noise level=-114 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Any help suggestions? Pleease :)

---

### Post by anewguy on 2012-01-11
I don't know anything about your particular adapter, but I suppose you could temporarily remove the se module and see if it makes a difference:

sudo rmmod rtl8192se 

In the mean time, Google can be your friend:

ubuntu rtl8192e

While some of the results aren't for version 11, they can give you ideas of things to look for and try.

Dave ;)

---

### Post by mak.allen on 2012-01-11
sudo rmmod rtl8192se does not work unfortunately :(

I did my share of googling, but no one seems to have this problem. There were a fair share of people who couldn't get internet in the first place, but no one with this problem.

Any other ideas of what could help? Many many thanks for all help in advance!

---

### Post by anewguy on 2012-01-11
I mentioned google as it was the first thing i did before answering.  One of the first posts returned was about your exact problem with an older release of ubuntu.  I mentioned google because unless we are familiar with a problem, it's what most of us do, along with a lot of reading, to answer questions.

You say the rmmod did not work - did you mean the rmmod itself did not work, or that it did not help with the problem?

dave ;)

---

### Post by SteveButt on 2012-01-11
Hi, This issue also affects me and I have also noticed that I can get ping working but find DNS telnet ssh etc do not work. I received the driver from Realtek but this does not compile under 3.X kernels

I have a Zydas based USB stick so can fall back to this but happy to test anything

Steve

---

### Post by ianchai on 2012-01-20
> **mak.allen said:**
> I did my share of googling, but no one seems to have this problem. There were a fair share of people who couldn't get internet in the first place, but no one with this problem.

I have this problem and you can see my struggles with it at [http://askubuntu.com/questions/95582/broadcom-bcm4313-works-poorly-on-a-hp-pavilion-g4-1212tu]("http://askubuntu.com/questions/95582/broadcom-bcm4313-works-poorly-on-a-hp-pavilion-g4-1212tu")

No solution yet :(

---

### Post by ianchai on 2012-01-20
> **ianchai said:**
> I have this problem and you can see my struggles with it at [http://askubuntu.com/questions/95582/broadcom-bcm4313-works-poorly-on-a-hp-pavilion-g4-1212tu]("http://askubuntu.com/questions/95582/broadcom-bcm4313-works-poorly-on-a-hp-pavilion-g4-1212tu")

No solution yet :(

Ok, this is very weird... I've been on WiFi for over half an hour and it's still working... did the problem just magically solve itself in a recent Ubuntu update? :confused:

---

### Post by ianchai on 2012-01-20
> **ianchai said:**
> Ok, this is very weird... I've been on WiFi for over half an hour and it's still working... did the problem just magically solve itself in a recent Ubuntu update? :confused:

It has been several hours and it's still working!!! Yay! \\:D/

---

### Post by ianchai on 2012-01-21
> **ianchai said:**
> It has been several hours and it's still working!!! Yay! \\:D/

I rejoiced too early. It seemed to keep working with the WiFi in my office, but when I came home, I found it doesn't work with my WiFi at home, even though another LINUX box as well as my wife's Windows 7 netbook and my Android phone works with that home WiFi. :( :confused:

Curiouser and curiouser.

---

### Post by varunendra on 2012-01-23
> **ianchai said:**
> I rejoiced too early. It seemed to keep working with the WiFi in my office, but when I came home, I found it doesn't work with my WiFi at home, even though another LINUX box as well as my wife's Windows 7 netbook and my Android phone works with that home WiFi.
[I]ianchai,
[/I]
As per the link you have posted here, your wireless adapter is** broadcom, not a realtek** one. Accordingly, if your problem hasn't been fixed yet (although you seem close with mikewhatever's help) please follow this guide to solve the problem: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

If that doesn't help, and you need further help on the forums, I would suggest you to start a new thread with a relevant topic, provide all the details you have experienced with this issue so far, plus output of these commands for problem analysis:
**_When you are connected via wifi_:**
```
ifconfig
iwconfig
lspci -nnk | grep -iA2 net
lsmod
uname -rm
cat /etc/network/interfaces
cat /etc/resolv.conf
cat /etc/nsswitch.conf
cat /etc/modprobe.d/blacklist.conf | grep -iE 'b43 | bcm'
```**_and When you get disconnected_:**
```
dmesg | grep -iE 'net | wlan | b43 | bcm | brcm'
iwlist scan
rfkill list all
```


**_PS_:**
If you do post a new thread regarding this issue, please post a link to it here so I can follow. Thank you.

---

### Post by Sigma1 on 2012-01-23
I've had similar problems on a Lenovo laptop my daughter uses. I found a solution for 11.04 here: [http://www.chayx.net/2011/06/how-to-install-realtek-rtl8188ce-wifi-drivers-thinkpad-edge-13-on-ubuntu-natty-1104.html](http://www.chayx.net/2011/06/how-to-install-realtek-rtl8188ce-wifi-drivers-thinkpad-edge-13-on-ubuntu-natty-1104.html)
It worked nicely for the early 11.04 kernels. I don't know how it is for the more recent ones, or the 3. kernel in 11.10.

---

### Post by ianchai on 2012-01-23
> **varunendra said:**
> [I]ianchai,
[/I]
As per the link you have posted here, your wireless adapter is** broadcom, not a realtek** one. Accordingly, if your problem hasn't been fixed yet (although you seem close with mikewhatever's help) please follow this guide to solve the problem: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

...

**_PS_:**
If you do post a new thread regarding this issue, please post a link to it here so I can follow. Thank you.

Thanks. Yes, I just tried mikewhatever's solution and hope to be out of the woods now :D

Sorry about the confusion about the wireless adapter in question.

---

### Post by ianchai on 2012-02-25
> **ianchai said:**
> Thanks. Yes, I just tried mikewhatever's solution and hope to be out of the woods now :D

Sorry about the confusion about the wireless adapter in question.

User ts3 over at Ubuntu Forums wrote a solution which worked for me, finally, after so long a struggle. So if you're facing the same problem as me, check it out at [http://ubuntuforums.org/showthread.php?t=1889170](http://ubuntuforums.org/showthread.php?t=1889170)

Here's his summary:

The b-43 installer does not support BCM4313 (4727)
The bcmwl-kernel-source driver (found in the Ubuntu Software Center) supports it but first one needs to make sure that
b43 and the option to activate the STA Broadcom drivers through System Settings -> Additional Drivers are uninstalled/disabled
that those drivers (b43, bcma, brcsmac) are blacklisted and
that the wl driver that works is NOT blacklisted
See the link for details.

---

### Post by sunson565 on 2012-06-27
> **Sigma1 said:**
> I've had similar problems on a Lenovo laptop my daughter uses. I found a solution for 11.04 here: [http://www.chayx.net/2011/06/how-to-install-realtek-rtl8188ce-wifi-drivers-thinkpad-edge-13-on-ubuntu-natty-1104.html](http://www.chayx.net/2011/06/how-to-install-realtek-rtl8188ce-wifi-drivers-thinkpad-edge-13-on-ubuntu-natty-1104.html)
It worked nicely for the early 11.04 kernels. I don't know how it is for the more recent ones, or the 3. kernel in 11.10.
[Sigma1]("http://ubuntuforums.org/member.php?u=149480") Thank you very much :)
I have a similar problem on ubunto 12.04, with rtl8191seva, and the solution on the post worked great!

---

