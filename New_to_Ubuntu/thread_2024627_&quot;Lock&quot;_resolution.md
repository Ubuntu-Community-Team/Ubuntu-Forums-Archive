---
title: "&quot;Lock&quot; resolution"
date: 2012-07-13
forum: New to Ubuntu
---

### Post by quirino77 on 2012-07-13
If i turn on the PC with the monitor off, when i turn on the monitor, it says "format not supported". I have to first turn on the monitor, than the pc. After booted, i can turn the monitor off and on with no problem.

What can it be? Could i "lock" the resolution Ubuntu will use? Maybe it could avoid this problem.

The monitor, actually, is a led TV.

Thank's.

---

### Post by quirino77 on 2012-07-15
Anyone?

---

### Post by NikTh on 2012-07-15
> **quirino77 said:**
> 
The monitor, actually, is a led TV.

Hi , 
hmm .. led TV , i assume the connection is HDMI.. well ,  can you configure your TV for scaling ? My TV has an option (from menu>picture) for single scan , search for something like that.. or configure the picture to 16:9  , you must do that at time you are in.. connected (so tv keep that option) .. 

For resolution from Ubuntu try xrandr.. 
Open a terminal and write 

```
xrandr
``` post the results here . 
Put the results inside [CODE] tags by highlighting the text and click on # symbol on top of message pane. 
Thanks

---

### Post by quirino77 on 2012-07-15
Thank's for your help.

You assumed right. Its HDMI. I don't think this make difference, but between the PC and TV, there is a Home Theater.
No upscale option on my TV. Already on 16:9. The image looks fine, 1920x1080, full screen. The only problem is if i turn on the PC with tv off.


```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 175, current 1920 x 1080, maximum 1920 x 1080
default connected 1920x1080+0+0 0mm x 0mm
   1920x1080      50.0     51.0     52.0     53.0     54.0     55.0* 
   1680x1050      56.0     57.0  
   1600x1024      58.0  
   1440x900       59.0  
   1440x480       60.0  
   1400x1050      61.0     62.0     63.0  
   1360x768       64.0     65.0     66.0  
   1280x1024      67.0     68.0     69.0  
   1280x960       70.0     71.0  
   1280x720       72.0     73.0  
   1152x864       74.0     75.0     76.0     77.0     78.0     79.0     80.0  
   1024x768       81.0     82.0     83.0     84.0     85.0     86.0  
   960x720        87.0     88.0  
   960x600        89.0  
   960x540        90.0  
   928x696        91.0     92.0  
   896x672        93.0     94.0  
   840x525        95.0     96.0     97.0     98.0     99.0  
   832x624       100.0  
   800x600       101.0    102.0    103.0    104.0    105.0    106.0    107.0    108.0    109.0    110.0  
   800x512       111.0  
   720x480       112.0  
   720x450       113.0  
   720x400       114.0  
   700x525       115.0    116.0    117.0    118.0  
   680x384       119.0    120.0  
   640x512       121.0    122.0    123.0  
   640x480       124.0    125.0    126.0    127.0    128.0    129.0    130.0  
   640x400       131.0  
   640x350       132.0  
   576x432       133.0    134.0    135.0    136.0    137.0    138.0    139.0  
   512x384       140.0    141.0    142.0    143.0    144.0  
   416x312       145.0  
   400x300       146.0    147.0    148.0    149.0    150.0  
   360x200       151.0  
   320x240       152.0    153.0    154.0    155.0  
   320x200       156.0  
   320x175       157.0  
```

---

### Post by NikTh on 2012-07-15
Hi , 
i see that you already have the full resolution 
> 
   ```
1920x1080      50.0     51.0     52.0     53.0     54.0     55.0*
```I don't think that if you lock another resolution will solve your problem. This is the native resolution of TV , and this you must have. 

What is your graphics card ? 
Open a terminal and give this command 
```
lspci -nnk | grep -iA2 vga
``` 
Thanks

---

### Post by quirino77 on 2012-07-15
Thank's NikTh.

I don't know if locking resolution will solve my problem. I was going to lock this on full hd. It was the only thing i could imagine to try to fix. Maybe Ubuntu, with TV off is using another resolution. If this is happening, locking the resolution will avoid this problem. Do you know how to lock?

How can i see on another terminal (or via SSH since i got no video with this problem) the resolution Ubuntu is using on Unity?

I have a GForce GTX 560 TI. But here it is:

```
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF110 [GeForce GTX 560 Ti] [10de:1200] (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device [1043:838b]
	Kernel driver in use: nvidia
```

---

### Post by NikTh on 2012-07-16
> **quirino77 said:**
> Thank's NikTh.

I don't know if locking resolution will solve my problem. I was going to lock this on full hd. It was the only thing i could imagine to try to fix. Maybe Ubuntu, with TV off is using another resolution. If this is happening, locking the resolution will avoid this problem. Do you know how to lock?

How can i see on another terminal (or via SSH since i got no video with this problem) the resolution Ubuntu is using on Unity?

I have a GForce GTX 560 TI. But here it is:

```
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF110 [GeForce GTX 560 Ti] [10de:1200] (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device [1043:838b]Kernel driver in use: nvidia
```
Hi , 
you have nvidia - driver installed (and working i assume) , open  nvidia-setting window and set the resolution from there. It will lock  it. Don't forget to Apply changes. 
I don't think it will help if we use x-server's tools (like xrandr) , now you have nvidia driver installed. 
And i think that its not for sure Ubuntu (or resolution of OS)  responsible for this weird problem. Maybe TV cannot locate Hdmi's signal  when its off.. (and then you turn it on).. not sure.. just a thought. 
Thanks.

---

### Post by quirino77 on 2012-07-16
I will try nvidia-settings as soon as i get home.

Not sure if this is the TV because if i turn on TV, turn on PC, then all is ok. After this point (with PC on), i can turn off/on TV as many times as i want with no problem. The only problem is when i turn ON PC with TV OFF.

---

### Post by quirino77 on 2012-07-16
Well, it looks like it was already "locked". At least, no "auto" resolution was set. It was on 1920x1080. Only the refresh rate was "auto" and i set to 60Hz(1).

How can i see the resolution runnig on TTY7 (Unity), from another TTY or from SSH?

---

### Post by NikTh on 2012-07-16
> **quirino77 said:**
> Well, it looks like it was already "locked". At least, no "auto" resolution was set. It was on 1920x1080. Only the refresh rate was "auto" and i set to 60Hz(1).

How can i see the resolution runnig on TTY7 (Unity), from another TTY or from SSH?
Hi,
I really don't know how you can do this. Wait for a more experience user. I think with ssh can be done , but i don't know how.

---

