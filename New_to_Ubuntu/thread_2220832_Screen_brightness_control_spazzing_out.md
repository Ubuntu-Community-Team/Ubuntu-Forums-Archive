---
title: "Screen brightness control spazzing out?"
date: 2014-04-29
forum: New to Ubuntu
---

### Post by jason84 on 2014-04-29
Hello 

I an still really new with linux even though I had 12.04 for a little bit. So since xp ran out I decided to put 14.04 lts on my MSI U123 netbook. So had 12.04 lts on a jump drive then found 14.04 lts. So I upgraded to it when I logged in I try to adjust the brightness of the screen with either the short cut keys or through settings as soon as I touch it it starts to jump all over the place and keeps going til I hit CTRL ALT DEL.

Any ideas would be greatly appreciated. Thank you.

---

### Post by Toz on 2014-04-29
Hello and welcome to the forums.

Can we get a more detailed view into your setup? Can you open a terminal window, run the following commands, and please post back the results?

1. Your current kernel boot line:
```
cat /proc/cmdline
```
2. Information about your video card(s):
```
lspci -k | grep -iA2 VGA
```
3. Information about your known backlight interfaces:
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```
4. A listing of your loaded kernel modules:
```
lsmod
```
5. Your /var/log/Xorg.0.log file:
```
pastebinit /var/log/Xorg.0.log
```
...and post back the link that is generated.

---

### Post by jason84 on 2014-05-05
@Toz. Thank you for the reply. Sorry it took so long to get back. I got side tracked.

Answers to questions.

```
BOOT_IMAGE=/boot/vmlinuz-3.13.0-24- generic root=UUID=5e5712af-87d6-49fa-812f-f25
    fce5ba813 ro quiet splash vt.handoff=7
```

I had some trouble with this code. so I just ran and selected the video card out of it.. I hope.

```
user@user:~$ lspci -k
 00:00.0 Host bridge: Intel Corporation Mobile 945GSE Express Memory Controller Hub (rev 03)
 	Subsystem: Micro-Star International Co., Ltd. [MSI] Device 100a
  	Kernel driver in use: agpgart-intel
 
 00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
  	Subsystem: Micro-Star International Co., Ltd. [MSI] Device 100a
  	Kernel driver in use: i915
 
 00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
```

3. I am not sure about this code. I tried a few ways but just kept getting syntax error near unexpected token 'in'

```
user@user:~$ lsmod
  Module                  Size  Used by
  nls_iso8859_1          12617  0  
  cfg80211              409394  0  
  bnep                   18895  2  
  rfcomm                 53664  0  
  bluetooth             342263  10 bnep,rfcomm
  snd_hda_codec_realtek    51029  1  
  snd_hda_intel          42730  3  
  snd_hda_codec         164067  2 snd_hda_codec_realtek,snd_hda_intel
  gpio_ich               13229  0  
  msi_wmi                13130  0  
  snd_hwdep              13272  1 snd_hda_codec
  snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
  sparse_keymap          13708  1 msi_wmi
  snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
  snd_seq_midi           13132  0  
  i915                  705396  3  
  snd_seq_midi_event     14475  1 snd_seq_midi
  snd_rawmidi            25135  1 snd_seq_midi
  psmouse                91033  0  
  serio_raw              13230  0  
  snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
  lpc_ich                16864  0  
  drm_kms_helper         46907  1 i915
  coretemp               13195  0  
  r8187se               155125  0  
  snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
  drm                   243792  4 i915,drm_kms_helper
  snd_timer              28584  2 snd_pcm,snd_seq
  eeprom_93cx6           13168  1 r8187se
  snd                    60871  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
  i2c_algo_bit           13197  1 i915
  wmi                    18673  1 msi_wmi
  soundcore              12600  1 snd
  video                  18903  1 i915
  mac_hid                13037  0  
  parport_pc             31981  0  
  ppdev                  17391  0  
  lp                     13299  0  
  parport                40836  3 lp,ppdev,parport_pc
  ums_realtek            17733  0  
  usb_storage            48417  1 ums_realtek
  r8169                  61562  0  
  mii                    13654  1 r8169
```
 
5. Again had trouble using this code. I tried the sudo command also.  command not found.


I am looking forward to understanding and learning more about linux so I really appreciate everyones help..

Thank you.

Jason

---

### Post by Toz on 2014-05-05
It would really be helpful if you could get an answer to #3. Try copying/pasting this command:
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```

---

### Post by jason84 on 2014-05-07
Ok i figured out what I was doing wrong the last time I had an extra space..

Here is the answer for #3

user@user:~$ for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
 
  /sys/class/backlight/acpi_video0
 0
 8
 0
 user@user:~$  




Thank you so much for the help Toz

---

### Post by Toz on 2014-05-07
Good thanks.

Can you please try booting your system with the **video.use_native_backlight=1** kernel parameter? To do so, please follow the "Temporarily Add a Kernel Boot Parameter for Testing" instructions from the [Kernel Boot Parameters wiki]("https://wiki.ubuntu.com/Kernel/KernelBootParameters").

Once you've booted the system with this kernel parameter, can you please once more return the results of:
```
cat /proc/cmdline
```
...and
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```

Also test your backlight functions.

---

### Post by jason84 on 2014-05-15
user@user:~$ cat /proc/cmdline  
 BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=5e5712af-87d6-49fa-812f-f25fce5ba813 ro quiet splash video.use_native_backlight=1  
 user@user:~$ for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done  
 

  /sys/class/backlight/acpi_video0  
 0  
 8  
 0  
 user@user:~$  


It booted up at full brightness, then I tried to adjust the brightness and it did the same thing. It fluctuates from high to low and so on. It also booted with a pop up saying "system program problem detected".

---

### Post by Toz on 2014-05-15
Okay. This time, can you temporarily boot with two kernel parameters:      

**video.use_native_backlight=1 i915.invert_brightness=1** 

(note that there is a space in between them). Once booted, again post back the results from the commands in post #6 and try the function keys.

---

### Post by jason84 on 2014-05-15
user@user:~$ cat /proc/cmdline  
 BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=5e5712af-87d6-49fa-812f-f25fce5ba813 ro quiet splash vt.handoff=7 video.use_native_backlight=1 i915.invert_brightness=1  
 user@user:~$ for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done  
 

  /sys/class/backlight/acpi_video0  
 0  
 8  
 0  
 user@user:~$  


Boots up dim. without the startup warning. but same results when I adjust the settings.

---

### Post by Toz on 2014-05-15
One more try. Just: 

**i915.invert_brightness=1**

Lets see what happens. Post back results again.

---

### Post by jason84 on 2014-05-27
Ok that booted up to full brightness. Which is great. I tried adjusting it again and it acted up. So what I am thinking is adding that bit of code into the grub permanently. Is that what you where thinking? Then just leave it alone.

---

### Post by jason84 on 2014-05-27
Dang it. I typed the code in again for the temp to start up and then make the edit permanent. Now it comes up dim all the time. I tried just booting with out the edit and it comes up dim also. i typed it in right after the "splash" just exactly like i did before and how you have it typed and it boots up dim.?????

---

### Post by jeremy31 on 2014-05-27
I would rather not interfere with something Toz is working on, but if you go to /sys/class/backlight/acpi_video0 in file manager and watch the icons when you try to use hotkeys to change brightness, do the values on brightness and actual_brightness change a lot?

---

### Post by Toz on 2014-05-27
> **jason84 said:**
> Dang it. I typed the code in again for the temp to start up and then make the edit permanent. Now it comes up dim all the time. I tried just booting with out the edit and it comes up dim also. i typed it in right after the "splash" just exactly like i did before and how you have it typed and it boots up dim.?????

Can you post back:
```
cat /proc/cmdline
```
...and lets see what you have in your kernel boot line.

I'm starting to think that it may best at this point in time to open a bug report against the linux package:
```
ubuntu-bug linux
```
...should get you started. It looks like its something that needs to be fixed in either the kernel or the power-manager.

---

### Post by Toz on 2014-05-27
> **jeremy31 said:**
> I would rather not interfere with something Toz is working on, but if you go to /sys/class/backlight/acpi_video0 in file manager and watch the icons when you try to use hotkeys to change brightness, do the values on brightness and actual_brightness change a lot?

Good point.

Following up on this line of thought, another thing you could try is to manually enter a brightness value directly into the interface file and see if that works:
```
echo X | sudo tee /sys/class/backlight/acpi_video0/brightness
```
...where X is a value between 0 and 8.

---

