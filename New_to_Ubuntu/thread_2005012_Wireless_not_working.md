---
title: "Wireless not working"
date: 2012-06-16
forum: New to Ubuntu
---

### Post by MasterShadow on 2012-06-16
I'm very frustrated. I looked on many different posts, and places on the internet, but I can't find a fix for my wireless.

I have broadcom corporation bcm4331 

I just put ubuntu 12.04 on my computer, and I can't connect to the internet. I'm currently using my dad's belkin usb tower to connect to the Internet. I would like to use the wireless on my laptop. The button wont even turn on. I went in bios to make sure it was enabled, and it was. What should I do?

---

### Post by wildmanne39 on 2012-06-16
Hi, here is a link for the only directions I have seen where the card actually works.
[http://ubuntuforums.org/showthread.php?p=11971567#post11971567](http://ubuntuforums.org/showthread.php?p=11971567#post11971567)
Thanks

---

### Post by codingman on 2012-06-16
try installing the drivers off the site if there is a linux driver, if not this is the one millionth complaint that I have ever seen on the forums about a not connecting wireless.

---

### Post by anewguy on 2012-06-17
Temporarily hard-wire your laptop to the router, then try the additional drivers/hardware drivers selection and see if it finds a driver for your wireless - is so, enable it.

Dave ;)

---

### Post by afixane on 2012-06-17
1. Search for wired connection
2. Open "Additional Driver"  or "jockey-gtk" from terminal
3. Click "Instal blablabla"

---

### Post by anewguy on 2012-06-17
> **afixane said:**
> 1. Search for wired connection
2. Open "Additional Driver"  or "jockey-gtk" from terminal
3. Click "Instal blablabla"

And that's different from my post how?

---

### Post by afixane on 2012-06-17
> **anewguy said:**
> And that's different from my post how?

Sorry i didn't see your post orz

---

### Post by anewguy on 2012-06-17
> **afixane said:**
> Sorry i didn't see your post orz ;) not a problem - just trying to avoid dups as sometimes that can be confusing to someone trying to solve their problem.

Dave ;)

---

### Post by MasterShadow on 2012-06-17
> **wildmanne39 said:**
> Hi, here is a link for the only directions I have seen where the card actually works.
[http://ubuntuforums.org/showthread.php?p=11971567#post11971567](http://ubuntuforums.org/showthread.php?p=11971567#post11971567)
Thanks

Oh my goodness thank you. I looked everywhere, and nothing worked. This solved it. I had to go to the link the person said they found it at, because they tweaked it a little, and that didn't work with mine. But thank you :)

---

### Post by kurt18947 on 2012-06-17
I wonder if it might be wise for the O.P. to bookmark, print out or otherwise be able to find those directions.  Will kernel updates or other updates break this solution?

---

### Post by wildmanne39 on 2012-06-17
Hi, no kernel updates will not break this fix, but if the person does and fresh install then he will need to do this procedure again, would you please use thread tools at the top of the page to mark the thread solved.

Good to see you anewguy!!!
Thanks

---

### Post by MasterShadow on 2012-06-17
> **kurt18947 said:**
> I wonder if it might be wise for the O.P. to bookmark, print out or otherwise be able to find those directions.  Will kernel updates or other updates break this solution?

I wrote them down, but then I opened up a word document, and copied+paste. I shut down my computer, and when it booted up, the wireless wasn't working, so I had to do everything again.

---

### Post by wildmanne39 on 2012-06-17
Hi, this should make sure that it works on boot.
```
sudo su 
echo wl >> /etc/modules 
exit
```
Thanks

---

### Post by MasterShadow on 2012-06-19
> **wildmanne39 said:**
> Hi, this should make sure that it works on boot.
```
sudo su 
echo wl >> /etc/modules 
exit
```Thanks

Tried it, but it didn't work. I still have to put the other commands in to make the wireless work every time it boots.

---

### Post by wildmanne39 on 2012-06-19
Hi, please post the exact commands that you have to run every time you boot using code tags #.
Thanks

---

### Post by MasterShadow on 2012-06-19
> **wildmanne39 said:**
> Hi, please post the exact commands that you have to run every time you boot using code tags #.
Thanks

    $ sudo apt-get install b43-fwcutter firmware-b43-installer 
$ sudo dpkg-reconfigure firmware-b43-installer 
$ sudo modprobe b43 $ export FIRMWARE_INSTALL_DIR="/lib/firmware" 
$ wget [http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2](http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2) ; tar -xjf broadcom-wl-5.100.138.tar.bz2 
$ sudo b43-fwcutter -w "
$FIRMWARE_INSTALL_DIR" broadcom-wl-5.100.138/linux/wl_apsta.o $ dmesg | tail -2

---

### Post by wildmanne39 on 2012-06-19
Hi, please post:
```
lsmod
```
Thanks

---

### Post by MasterShadow on 2012-06-19
Module                  Size  Used by
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
snd_hda_codec_conexant    52516  1 
snd_hda_intel          32765  5 
snd_hda_codec         109562  2 snd_hda_codec_conexant,snd_hda_intel
rt73usb                27029  0 
arc4                   12473  2 
crc_itu_t              12627  1 rt73usb
joydev                 17393  0 
snd_hwdep              13276  1 snd_hda_codec
rt2x00usb              20061  1 rt73usb
snd_pcm                80845  3 snd_hda_intel,snd_hda_codec
b43                   342643  0 
rt2x00lib              48858  2 rt73usb,rt2x00usb
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
i915                  414663  3 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
mac80211              436455  3 rt2x00usb,b43,rt2x00lib
snd_timer              28931  2 snd_pcm,snd_seq
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                72919  0 
hp_wmi                 13652  0 
snd                    62064  18 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              178679  3 b43,rt2x00lib,mac80211
soundcore              14635  1 snd
sparse_keymap          13658  1 hp_wmi
i2c_algo_bit           13199  1 i915
serio_raw              13027  0 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
wmi                    18744  1 hp_wmi
mac_hid                13077  0 
bcma                   25651  1 b43
video                  19068  1 i915
8139too                23283  0 
8139cp                 26759  0 
ssb                    50691  1 b43

---

### Post by MasterShadow on 2012-06-20
Hey wildmanne39, I don't know what I did, but It's working at boot. Thank you for helping me. I really appreciate it :)

---

### Post by ChiaFreak on 2012-08-17
I'm also having this problem. I have multiple wireless networks, but it just won't connect.  I tried typing  "sudo apt-get install b43-fwcutter firmware-b43-installer" but it says that it's unable to locate either b43-fwcutter or firmware-b43-installer.

---

### Post by wildmanne39 on 2012-08-17
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

