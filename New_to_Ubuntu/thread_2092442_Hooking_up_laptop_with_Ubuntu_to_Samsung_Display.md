---
title: "Hooking up laptop with Ubuntu to Samsung Display"
date: 2012-12-07
forum: New to Ubuntu
---

### Post by elhancho on 2012-12-07
I have windows installed on my laptop, which is also hooked up to a larger Samsung display. It works perfectly on Windows, but once I installed Ubuntu on my laptop, I couldn't figure out how to hook it up to the display like I had done in Windows. A couple times when I booted Ubuntu and had my Samsung monitor on since I had just been using Windows, it would flash with the loading screen for Ubuntu on my monitor for a few seconds, which confused me even more. Please help!!!!

---

### Post by verzx on 2012-12-07
Use a program called synergy, you can use the computer which you want to use the mouse and keyboard from and move from one screen to another. It's really good and easy to setup.

Here it is:

[http://synergy-foss.org/](http://synergy-foss.org/)

---

### Post by BertN45 on 2012-12-07
> **elhancho said:**
> I have windows installed on my laptop, which is also hooked up to a larger Samsung display. It works perfectly on Windows, but once I installed Ubuntu on my laptop, I couldn't figure out how to hook it up to the display like I had done in Windows. A couple times when I booted Ubuntu and had my Samsung monitor on since I had just been using Windows, it would flash with the loading screen for Ubuntu on my monitor for a few seconds, which confused me even more. Please help!!!!
It should be standard in Ubuntu too. Go to System Settings -> Display. If your Display is not recognized, press Detect Display and your second and first display should be visible, drag the display to the right location and press the "ON" button so both displays are used.

---

### Post by BertN45 on 2012-12-07
> **elhancho said:**
> I have windows installed on my laptop, which is also hooked up to a larger Samsung display. It works perfectly on Windows, but once I installed Ubuntu on my laptop, I couldn't figure out how to hook it up to the display like I had done in Windows. A couple times when I booted Ubuntu and had my Samsung monitor on since I had just been using Windows, it would flash with the loading screen for Ubuntu on my monitor for a few seconds, which confused me even more. Please help!!!!
It should be standard in Ubuntu too. Go to System Settings -> Display. If your Display is not recognized, press Detect Display and your second and first display should be visible, drag the display to the right location and press the "ON" buttons so both displays are visible.

---

### Post by elhancho on 2012-12-07
> **BertN45 said:**
> Go to System Settings -> Display. If your Display is not recognized, press Detect Display and your second and first display should be visible, drag the display to the right location and press the "ON" buttons so both displays are visible.

I tried this, but it didn't do anything when I pushed "Detect Displays". I have the monitor plugged into my laptop and its turned on, but it still won't detect it.

---

### Post by BertN45 on 2012-12-07
Maybe I got the sequence wrong, did you press the "ON" buttons? I did not use the double display the last couple of months. What version of Ubuntu are you using?

---

### Post by elhancho on 2012-12-07
Please exuse me if I do not fully understand you, but I'm not really sure what "power" buttons you are talking about? Are they the ones that are in the "Displays" window, because I already had those on because they are the default. I don't mean to be mean, but I only have one monitor that I am hooking up to my laptop, and it already works when I boot windows on my laptop (I have it set up so that I can dual-boot Windows and Linux), but for some reason it just doesn't want to cooperate on Ubuntu. Thanks for your help! (Also, I'm using Ubuntu 12.04.1 LTS.)

---

### Post by tgalati4 on 2012-12-08
What graphics chip are you running on your laptop?  Are you running an open-source video driver or a proprietary driver?  Windows drivers are provided by the video chip vendor and tend to work out-of-the-box.  Getting a second display to work at full resolution with the same sleep/resume and dual-boot reliability will take some research.

---

### Post by elhancho on 2012-12-08
I'm not sure what graphics chip I'm using, but it's the one that came already in the laptop. I have an HP Pavilion dv7.

---

### Post by audiomick on 2012-12-08
> **elhancho said:**
> I'm not sure what graphics chip I'm using, but it's the one that came already in the laptop. I have an HP Pavilion dv7.

Open a terminal and do
```
sudo lshw -C video
```
You will be asked for your password. Type it in and hit enter. You wont see what you are typing when you type the password.

The command lshw means "list hardware", and the -C video tells it to restrict itself to the video components. It will give you a listing including the model name of your video card. Post the output here. Use the # button at the top of the posting windows to put code tags around it.

---

### Post by elhancho on 2012-12-09
> **audiomick said:**
> Open a terminal and do
```
sudo lshw -C video
```You will be asked for your password. Type it in and hit enter.

I did this, and this is the output:



*-display               
       description: VGA compatible controller
       product: Madison [Radeon HD 5000M Series]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:16 memory:a0000000-afffffff memory:c4400000-c441ffff ioport:4000(size=256) memory:c4440000-c445ffff
  *-display
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:46 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:5050(size=8)



I have no idea what all of it means, but hopefully someone else will be able to make sense of it.

---

### Post by tgalati4 on 2012-12-09
Your laptop has 2 graphics chips:

An Intel Core Graphics chip, running and i915 driver.

And you have an ATI Radeon HD 5000M graphics chip.  Running the fglrx_pci driver.

To verify this, list the modules (drivers) you are running:

```
lsmod
```

Does your laptop have two graphics ports?  Perhaps a VGA (15 pin, blue) port and a white, multipin DVI port.

Not to scare you, but you may need to read this thread and start to understand the tweaking that may be required to get your combination to work.

[http://ubuntuforums.org/showthread.php?t=158686](http://ubuntuforums.org/showthread.php?t=158686)

This came from a simple google search:  ubuntu dual display fglrx_pci

---

### Post by elhancho on 2012-12-09
> **tgalati4 said:**
> 
To verify this, list the modules (drivers) you are running:

```
lsmod
```Does your laptop have two graphics ports?  Perhaps a VGA (15 pin, blue) port and a white, multipin DVI port.

I typed lsmod in the terminal and this is what I came up with:


Module                  Size  Used by
michael_mic            12540  8 
arc4                   12473  4 
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 38139  12 
bnep                   17830  2 
binfmt_misc            17292  1 
usblp                  17885  0 
i915                  419161  7 
hp_accel               25728  0 
lis3lv02d              19268  1 hp_accel
hp_wmi                 13652  0 
intel_ips              17822  0 
sparse_keymap          13658  1 hp_wmi
wmi                    18744  1 hp_wmi
input_polldev          13648  1 lis3lv02d
drm_kms_helper         45466  1 i915
drm                   197599  3 i915,drm_kms_helper
snd_usb_audio         101566  1 
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
i2c_algo_bit           13199  1 i915
btusb                  17948  2 
video                  19068  1 i915
psmouse                86486  0 
joydev                 17393  0 
serio_raw              13027  0 
snd_usbmidi_lib        24603  1 snd_usb_audio
fglrx                2909855  0 
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_idt      60251  1 
lib80211_crypt_tkip    17275  0 
snd_hda_intel          32765  5 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_seq_midi           13132  0 
wl                   2646601  0 
snd_rawmidi            25424  2 snd_usbmidi_lib,snd_seq_midi
snd_hwdep              13276  2 snd_usb_audio,snd_hda_codec
snd_seq_midi_event     14475  1 snd_seq_midi
lib80211               14040  2 lib80211_crypt_tkip,wl
bluetooth             158438  23 rfcomm,bnep,btusb
snd_pcm                80845  4 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  24 snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_rawmidi,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
mei                    36570  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41906  0 
hid                    77392  1 usbhid
uas                    17828  0 
usb_storage            39646  4 
r8169                  56321  0 



As for the graphics ports, I have a blue VGA and an HDMI port. Before I used the HDMI port to connect to the monitor in Windows.

---

### Post by tgalati4 on 2012-12-09
And what is the model and native resolution of the Samsung display?

---

### Post by elhancho on 2012-12-09
The model is the Samsung SyncMaster T260HD and the native resolution is 1080p 1920 x 1200 at 60 Hz.

---

### Post by tgalati4 on 2012-12-09
I have an older version of that monitor, and I use dual-monitor all the time with my thinkpad.  But I use a DVI port as my thinkpad does not have an HDMI out.

So in reading the mega-thread that I posted above, there are some limitations using the fglrx driver and the arrangement of your monitors.

I have 12.10 running on another machine, but I don't have dual monitors set up so I cannot help any more at this point.  Others will have to chime in for the commands to use.  There are several suggestions in the thread that I posted earlier.

---

### Post by elhancho on 2012-12-09
Thanks for your help!

---

### Post by tgalati4 on 2012-12-09
More dual display stuff to read:

[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

---

