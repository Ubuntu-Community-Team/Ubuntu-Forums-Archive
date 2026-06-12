---
title: "File-copy progress window is missing when data is pasted on desktop"
date: 2018-07-16
forum: New to Ubuntu
---

### Post by wrongusername2 on 2018-07-16
Hi,
               In case of 18.04, FM's title bar contains file-copy progress window.  This icon will not appear when the target is Desktop. Here is an example.
Connect EXT hard drive, and then copy a folder from EXT hard drive and paste it on desk-top. FM window (showing Ext-hard drive) will not show file-copy progress window, and there is no FM window for TARGET. 
Is there a way to see file-copy progress window?


Since there is no file-copy progress window, only way to stop the file-copy operation is by turning off external hard drive. 


Thanks

---

### Post by monkeybrain20122 on 2018-07-16
There is no file-copy progress window for nautilus in 18.04 if you mean the little box with the progress bar. Instead there is a circle thingy on the right top corner of the file browser where the radius swipes out an increasing white sector as the copy progresses, the transfer finishes when the whole circle turns white then disappears

---

### Post by wrongusername2 on 2018-07-20
> **monkeybrain20122 said:**
>  Instead there is a circle thingy on the right top corner of the file browser 

White circle will not be displayed if you paste on the desktop directly (without going through the short-cut shown in FM).

---

### Post by mIk3_08 on 2018-07-20
> **wrongusername2 said:**
> White circle will not be displayed if you paste on the desktop directly (without going through the short-cut shown in FM).


I think it will only shows up wrongusername2 when you copy a bulk of file in Desktop nautilus. small files won't shows cause the speed of file transfer is more faster than showing up the progress indicator in nautilus.

---

### Post by wrongusername2 on 2018-07-21
> **mIk3_08 said:**
>  small files won't shows cause the speed of file transfer is more faster than showing.
I eliminated those possibilities. 
I was coping 35gb of data and it went for several minutes.

---

### Post by mIk3_08 on 2018-07-21
can you install inxi in your ubuntu machine
in terminal type this command;
```
sudo apt-get install inxi
```
once installed run this command in terminal; 
```
inxi -F
```
then show us all the result here in thread

---

### Post by wrongusername2 on 2018-07-21
Output of

```
inxi -F
```

Ouput

```
[1;34mSystem:   [0;37m [1;34mHost:[0;37m afterwindows-t460 [1;34mKernel:[0;37m 4.15.0-23-generic x86_64 [1;34mbits:[0;37m 64[0;37m
[1;34m          [0;37m [1;34mDesktop:[0;37m Gnome 3.28.1 [1;34mDistro:[0;37m Ubuntu 18.04 LTS[0;37m
[1;34mMachine:  [0;37m [1;34mDevice:[0;37m laptop [1;34mSystem:[0;37m LENOVO [1;34mproduct:[0;37m 20FMS4Y700 [1;34mv:[0;37m ThinkPad T460 [1;34mserial:[0;37m N/A[0;37m
[1;34m          [0;37m [1;34mMobo:[0;37m LENOVO [1;34mmodel:[0;37m 20FMS4Y700 [1;34mv:[0;37m SDK0J40697 WIN [1;34mserial:[0;37m N/A[0;37m
[1;34m          [0;37m [1;34mUEFI:[0;37m LENOVO [1;34mv:[0;37m R06ET57W (1.31 ) [1;34mdate:[0;37m 11/17/2017[0;37m
[1;34mBattery   [0;37m [1;34mBAT1:[0;37m [1;34mcharge:[0;37m 20.6 Wh 92.4% [1;34mcondition:[0;37m 22.3/23.5 Wh (95%)[0;37m
[1;34mCPU:      [0;37m [1;34mDual core[0;37m Intel Core i7-6600U (-MT-MCP-) [0;37m[1;34mcache:[0;37m 4096 KB[0;37m
[1;34m          [0;37m [1;34mclock speeds:[0;37m [1;34mmax:[0;37m 3400 MHz [1;34m1:[0;37m 500 MHz [1;34m2:[0;37m 500 MHz [1;34m3:[0;37m 500 MHz[0;37m
[1;34m          [0;37m [1;34m4:[0;37m 500 MHz[0;37m
[1;34mGraphics: [0;37m [1;34mCard:[0;37m Intel HD Graphics 520[0;37m
[1;34m          [0;37m [1;34mDisplay Server:[0;37m x11 (X.Org 1.19.6 ) [1;34mdriver:[0;37m i915[0;37m
[1;34m          [0;37m [1;34mResolution:[0;37m 1920x1080@59.97hz[0;37m
[1;34m          [0;37m [1;34mOpenGL: renderer:[0;37m Mesa DRI Intel HD Graphics 520 (Skylake GT2)[0;37m
[1;34m          [0;37m [1;34mversion:[0;37m 4.5 Mesa 18.0.5[0;37m
[1;34mAudio:    [0;37m [1;34mCard[0;37m Intel Sunrise Point-LP HD Audio [1;34mdriver:[0;37m snd_hda_intel[0;37m
[1;34m          [0;37m [1;34mSound:[0;37m Advanced Linux Sound Architecture [1;34mv:[0;37m k4.15.0-23-generic[0;37m
[1;34mNetwork:  [0;37m [1;34mCard-1:[0;37m Intel Ethernet Connection I219-LM [1;34mdriver:[0;37m e1000e[0;37m
[1;34m          [0;37m [1;34mIF:[0;37m enp0s31f6 [1;34mstate:[0;37m down [1;34mmac:[0;37m c8:5b:76:5e:0f:4c[0;37m
[1;34m          [0;37m [1;34mCard-2:[0;37m Intel Wireless 8260 [1;34mdriver:[0;37m iwlwifi[0;37m
[1;34m          [0;37m [1;34mIF:[0;37m wlp4s0 [1;34mstate:[0;37m up [1;34mmac:[0;37m e4:a7:a0:b2:09:cb[0;37m
[1;34mDrives:   [0;37m [1;34mHDD Total Size:[0;37m 3000.6GB (2.8% used)[0;37m
[1;34m          [0;37m [1;34mID-1:[0;37m /dev/sda [1;34mmodel:[0;37m WDC_WD10JPVX [1;34msize:[0;37m 1000.2GB[0;37m
[1;34m          [0;37m [1;34mID-2:[0;37m USB /dev/sdb [1;34mmodel:[0;37m 003_HN [1;34msize:[0;37m 2000.4GB[0;37m
[1;34mPartition:[0;37m [1;34mID-1:[0;37m / [1;34msize:[0;37m 916G [1;34mused:[0;37m 80G (10%) [1;34mfs:[0;37m ext4 [1;34mdev:[0;37m /dev/sda2[0;37m
[1;34mRAID:     [0;37m No RAID devices: /proc/mdstat, md_mod kernel module present[0;37m
[1;34mSensors:  [0;37m [1;34mSystem Temperatures: cpu:[0;37m 34.0C [1;34mmobo:[0;37m N/A[0;37m
[1;34m          [0;37m [1;34mFan Speeds (in rpm): cpu:[0;37m 0[0;37m
[1;34mInfo:     [0;37m [1;34mProcesses:[0;37m 241 [1;34mUptime:[0;37m 8 min [1;34mMemory:[0;37m 1132.3/15896.9MB[0;37m
[1;34m          [0;37m [1;34mClient:[0;37m Shell (bash) [1;34minxi:[0;37m 2.3.56[0;37m [0;37m
[0m
```

---

