---
title: "Radeon HD 6310 Graphics not to running well"
date: 2018-03-17
forum: New to Ubuntu
---

### Post by martinelligl on 2018-03-17
Hi there, I'm new here but i use Linux for at last 8 years. In my current situation, I made my old notebook **Acer Aspire 5250**-0866 without screen run my Ubuntu Budgie with an external monitor on its VGA output.
Well, its fine. Runs system ok, since my Dell Vostro 5410 broke. But Graphics is not well. The Resolution is 1024x768 by default from the Graphics AMD® Palm driver.
So, its **Graphics board is an AMD Radeon HD 6310**. I try to download the generic and specific drivers from AMD page, but when I go run the file it says that my XServer is to new.
I searched for ways to resolve that, but none of than fitted to me. Can anyone help me? Downgrade only the Xorg or the ubuntu version? **How can I install its driver?**

P.S.: sorry about my english if there are grammar, sintatical or semantical errors.

---

### Post by martinelligl on 2018-03-17
This is the result when i try to install the drivers file from AMD page.

```

sudo ./AMD-Catalyst-15.9-Linux-installer-15.201.1151-x86.x86_64.run 
Created directory fglrx-install.rxNjCm
Verifying archive integrity... All good.
Uncompressing AMD Catalyst(TM) Proprietary Driver-15.201.1151........................................
.................................................................................................................................................
..................................................................................................................................................
.................................................................................................................................................
.................................................................................................................................................
.................................................................................................................................................
.................................................................................................................................................
.................................................................................................................................................
.................................................................................................................................................
...............................................................................................................................
.................................................................................................................
.....................................................................................
=====================================================================
 AMD Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================


error: Detected X Server version 'XServer 1.19.5_64a' is not supported. Supported versions are X.Org 6.9 or later, up to XServer 1.10 (default:v2:x86_64:lib:XServer 1.19.5_64a:none:4.13.0-36-generic:)
Installation will not proceed.


Removing temporary directory: fglrx-install.rxNjCm



```

---

### Post by mörgæs on 2018-03-18
Hi, welcome to the fora.

[Catalyst]("https://help.ubuntu.com/community/BinaryDriverHowto/AMD") is a thing of the past. Here is something about [newer drivers]("https://help.ubuntu.com/community/RadeonDriver").

---

### Post by martinelligl on 2018-03-19
[IMG]https://pasteboard.co/HcFwBdD.png[/IMG][IMG]https://pasteboard.co/HcFwBdD.png[/IMG]So, my video driver is correct? So why the videoframe are slow?
[https://pasteboard.co/HcFwBdD.png](https://pasteboard.co/HcFwBdD.png)

---

### Post by wildmanne39 on 2018-03-19
Thread moved to New to Ubuntu, because installation and upgrade sub-forum is for questions about upgrading and installation of your new Ubuntu OS.

---

### Post by martinelligl on 2018-03-19
Thanks.. Sorry.. I'm new on forum. :)

---

### Post by mörgæs on 2018-03-20
> **martinelligl said:**
> So why the videoframe are slow?
[https://pasteboard.co/HcFwBdD.png](https://pasteboard.co/HcFwBdD.png)

I don't know the AMD APUs and their performance. Maybe someone else can enlighten us...?

---

### Post by martinelligl on 2018-03-24
Can anybody help? This is boring. Slowmotion video. =(

---

### Post by Yellow Pasque on 2018-03-25
> **martinelligl said:**
> Can anybody help? This is boring. Slowmotion video. =(

Be more specific.
Are you trying to play a movie/video? (If so, what program are you using?)
Are you trying to play a game? (If so, which one?)
Is it slow when you move windows around or browse the web?
Did you expect a different resolution than 1024x768?

---

### Post by martinelligl on 2018-03-26
So [IMG]https://pasteboard.co/HdFTSs6.png[/IMG]I'm trying to run movies like avengers, thor, etc. 1080p movies, and I use Kodi and SMPlayer.
I'm not a gamer anymore. 
No, window dont freeze when I change from one to another.
And I'm using 1280x1024 resolution, that I forced with xrandr trought command line, but when I start the system the resolution is 1024x768... things become too big O_O.

How can I put this xrandr commands to execute on start system, lets say, before I go logging?

[https://pasteboard.co/HdFTSs6.png](https://pasteboard.co/HdFTSs6.png)

---

### Post by Yellow Pasque on 2018-03-26
Do you have mesa-vdpau-drivers installed?
```
sudo apt-get install mesa-vdpau-drivers vdpauinfo
```
Look at output of vdpauinfo:
```
vdpauinfo
```

Next, you need to make sure your video player is using VDPAU. I'm not familiar with Kodi. I know smplayer has this setting under "General" -> Video tab -> Output Driver. Make sure it is set to vdpau for best result.

---

### Post by oldrocker99 on 2018-03-26
> **mörgæs said:**
> I don't know the AMD APUs and their performance. Maybe someone else can enlighten us...?

Accoding to this review, the top-end A12 is about is faster an an i7, with far better graphics. 

[http://cpuboss.com/cpus/Intel-Core-i7-6700K-vs-AMD-A12-7th-Gen-A12-9700P](http://cpuboss.com/cpus/Intel-Core-i7-6700K-vs-AMD-A12-7th-Gen-A12-9700P). And, it $150, far, far less than the i7.:grin:

Unquestionably worth serious consideration for desktop builders.

---

### Post by Yellow Pasque on 2018-03-26
The RadeonHD 6310 wasn't used on "top-end" APU's. It was for low power chips: 
[https://en.wikipedia.org/wiki/List_of_AMD_accelerated_processing_unit_microprocessors#Brazos:_%22Desna%22,_%22Ontario%22,_%22Zacate%22_(2011)](https://en.wikipedia.org/wiki/List_of_AMD_accelerated_processing_unit_microprocessors#Brazos:_%22Desna%22,_%22Ontario%22,_%22Zacate%22_(2011))
That's beside the point though. They should still be able to play back H.264 1080p

---

### Post by martinelligl on 2018-03-28
> **Temüjin said:**
> Do you have mesa-vdpau-drivers installed?
```
sudo apt-get install mesa-vdpau-drivers vdpauinfo
```
Look at output of vdpauinfo:
```
vdpauinfo
```

Next, you need to make sure your video player is using VDPAU. I'm not familiar with Kodi. I know smplayer has this setting under "General" -> Video tab -> Output Driver. Make sure it is set to vdpau for best result.

Thanks. Here is vdpauinfo:

```

vdpauinfo
display: :0   screen: 0
API version: 1
Information string: G3DVL VDPAU Driver Shared Library version 1.0


Video surface:


name   width height types
-------------------------------------------
420    16384 16384  NV12 YV12 
422    16384 16384  UYVY YUYV 
444    16384 16384  Y8U8V8A8 V8U8Y8A8 


Decoder capabilities:


name                        level macbs width height
----------------------------------------------------
MPEG1                          --- not supported ---
MPEG2_SIMPLE                    3  9216  2048  1152
MPEG2_MAIN                      3  9216  2048  1152
H264_BASELINE                  41  9216  2048  1152
H264_MAIN                      41  9216  2048  1152
H264_HIGH                      41  9216  2048  1152
VC1_SIMPLE                      1  9216  2048  1152
VC1_MAIN                        2  9216  2048  1152
VC1_ADVANCED                    4  9216  2048  1152
MPEG4_PART2_SP                  3  9216  2048  1152
MPEG4_PART2_ASP                 5  9216  2048  1152
DIVX4_QMOBILE                  --- not supported ---
DIVX4_MOBILE                   --- not supported ---
DIVX4_HOME_THEATER             --- not supported ---
DIVX4_HD_1080P                 --- not supported ---
DIVX5_QMOBILE                  --- not supported ---
DIVX5_MOBILE                   --- not supported ---
DIVX5_HOME_THEATER             --- not supported ---
DIVX5_HD_1080P                 --- not supported ---
H264_CONSTRAINED_BASELINE       0  9216  2048  1152
H264_EXTENDED                  --- not supported ---
H264_PROGRESSIVE_HIGH          --- not supported ---
H264_CONSTRAINED_HIGH          --- not supported ---
H264_HIGH_444_PREDICTIVE       --- not supported ---
HEVC_MAIN                      --- not supported ---
HEVC_MAIN_10                   --- not supported ---
HEVC_MAIN_STILL                --- not supported ---
HEVC_MAIN_12                   --- not supported ---
HEVC_MAIN_444                  --- not supported ---


Output surface:


name              width height nat types
----------------------------------------------------
B8G8R8A8         16384 16384    y  NV12 YV12 UYVY YUYV Y8U8V8A8 V8U8Y8A8 A4I4 I4A4 A8I8 I8A8 
R8G8B8A8         16384 16384    y  NV12 YV12 UYVY YUYV Y8U8V8A8 V8U8Y8A8 A4I4 I4A4 A8I8 I8A8 
R10G10B10A2      16384 16384    y  NV12 YV12 UYVY YUYV Y8U8V8A8 V8U8Y8A8 A4I4 I4A4 A8I8 I8A8 
B10G10R10A2      16384 16384    y  NV12 YV12 UYVY YUYV Y8U8V8A8 V8U8Y8A8 A4I4 I4A4 A8I8 I8A8 


Bitmap surface:


name              width height
------------------------------
B8G8R8A8         16384 16384
R8G8B8A8         16384 16384
R10G10B10A2      16384 16384
B10G10R10A2      16384 16384
A8               16384 16384


Video mixer:


feature name                    sup
------------------------------------
DEINTERLACE_TEMPORAL             y
DEINTERLACE_TEMPORAL_SPATIAL     -
INVERSE_TELECINE                 -
NOISE_REDUCTION                  y
SHARPNESS                        y
LUMA_KEY                         y
HIGH QUALITY SCALING - L1        y
HIGH QUALITY SCALING - L2        -
HIGH QUALITY SCALING - L3        -
HIGH QUALITY SCALING - L4        -
HIGH QUALITY SCALING - L5        -
HIGH QUALITY SCALING - L6        -
HIGH QUALITY SCALING - L7        -
HIGH QUALITY SCALING - L8        -
HIGH QUALITY SCALING - L9        -


parameter name                  sup      min      max
-----------------------------------------------------
VIDEO_SURFACE_WIDTH              y        48     2048
VIDEO_SURFACE_HEIGHT             y        48     1152
CHROMA_TYPE                      y  
LAYERS                           y         0        4


attribute name                  sup      min      max
-----------------------------------------------------
BACKGROUND_COLOR                 y  
CSC_MATRIX                       y  
NOISE_REDUCTION_LEVEL            y      0.00     1.00
SHARPNESS_LEVEL                  y     -1.00     1.00
LUMA_KEY_MIN_LUMA                y  
LUMA_KEY_MAX_LUMA                y  

```

Here is a print of Kodi config video:

[https://pasteboard.co/HdZyo0i.png](https://pasteboard.co/HdZyo0i.png)

---

### Post by Yellow Pasque on 2018-03-28
It all looks good. Now the question - What type of video are you trying to watch? If it's HEVC/H.265, it's going to be slowmotion because the GPU is too old to support that and the CPU is not up to the task.

---

