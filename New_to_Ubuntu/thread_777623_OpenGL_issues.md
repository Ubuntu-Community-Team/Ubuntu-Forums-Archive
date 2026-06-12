---
title: "OpenGL issues?"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by Zanshin on 2008-05-01
Hi all - I'm a linux noob who just started with Ubuntu Hardy LTS last week.  

Basic install went fine, dual boot XP, 2 monitors set up easily on twinview.  Basic functionality seems good.  =D>

Problems identified when running OpenGL intensive game Enemy Territory : Quake Wars ( etqw ).  #-o

Symptoms:
-Low FPS of 10 - 20 in game at the lowest graphics settings possible.  Much higher FPS and overall better performance when running it on medium to high (not ultra) game graphics settings in M$ Windoze :shock: this was a shocker to me, after hearing how well others have run it on linux.  
-Windowed or full screen mode seems to make no difference.  This makes me believe there is something in the ubuntu setup or drivers which is not quite right.  
-I'm getting glxgears running around 1800 (if i recall correctly).  My friend with a different linux distro and an nvidia 7800GS was getting about 10 times my FPS in glxgears and runs the game with no issues.  
-System Monitor shows CPUs (2 shown for Hyperthreading) take turns peaking out at 100% most of the time, while memory stays quite low.  (see attachment - CPU dropped when exiting game).  Makes me wonder if the GPU is maxed and offloading to the motherboard CPU.  Don't have a tool to measure GPU processor or memory utilization.  Is there is a tool for analyzing gpu, OpenGL, processing bottlenecks, etc?    

My Rig:
Dell Dimension E510
3.0 GHz Intel P4 w/ HT (530?)
3 GB RAM

***nvidia 7300LE w/ 512 MB RAM onboard, pci-e***
```
The 7300 series supports following advanced features:
Intellisample 4.0 Technology
Scalable Link Interface (SLI) Technology
TurboCache Technology
High dynamic range rendering Technology
UltraShadow II Technology
CineFX 4.0 Engine
Nvidia PureVideo Technology

7300LE Performance Specs:
    * Graphics Bus: PCI Express
    * Memory Interface: 64-bit
    * Memory Bandwidth: 6.4 GB/s
    * Fill Rate: 1.8 billion pixel/s
    * Vertice/s: 338 million
    * Memory Type: DDR-II
```

What have I tried so far:

I believe I've disabled compiz functions and all 3d desktop stuff i could find.  

I've tried nulling out second monitor in xorg.conf metamodes for ingame, but it doesn't appear to make a difference.  Also tried running second Xserver on the second monitor so the game could go fullscreen on first monitor, but didn't seem to provide any improvements either.  

This morning a friend recommended adding the following lines for xorg.co nf:

```
Section "Device"
       Option          "TripleBuffer" "true"
       Identifier      [yours here]
       Driver          "nvidia" [your proprietary driver here]
       BusID           [yours here]
       Option          "RenderAccel"   "true"
       Option          "AddARGBGLXVisuals" "true"
       Option          "AllowGLXWithComposite" "true"
EndSection

Section "DRI"
       Mode    0666
EndSection
```

The notes on triple buffering and DRI 0666 sound good, render accelerator I thought I read was now configured by default, and the other two sound a bit riskier.  Do these really make that much difference and if so, why don't they configure by default?  What is the downside to loading these?  I made an xorg.conf edit earlier on via gedit which I couldn't figure out how to recover from (and had to reinstall) so I'm a bit hesitant to make these changes until I understand better.  

I'm also reading that the Xfce desktop is much smaller/lighter and less resource intensive than Gnome.  If so, is it better to simply change desktops or start from scratch with a Xubuntu install over the current Ubuntu?  

I've been reading a few things on the forums which are making me wonder if there are possible related or contributing issues with Hardy LTS or the latest proprietary nvidia drivers?  Is this fact or speculation?

Is there something else I should be looking at that I'm totally missing right now?  :-k

Thanks for reading all the way through my post!  

Any and all ideas and help much appreciated.

---

### Post by herbster on 2008-05-01
First of all, Quake Wars has had many issues with framerates for many users, myself included. There are a few settings one can tweak, which got mine running its best (in console here):

```
seta com_unlock_timingMethod "1"
seta com_unlock_maxFPS 120
```

I use dual monitors as well, I run the game in a 1920x1200 window on the main monitor so I don't have to disable the second and go fullscreen, and it runs quite well now. However, your 7300 card may not be enough to get a consistent frame rate, this game is wacked that way.

I don't use Ubuntu so I can't help you with anything specific to Hardy, but check to be sure you're using the latest nvidia drivers (should be 169.12 I believe), this can be done by using the nvidia-settings control panel-like app (ALT+F2 and run nvidia-settings). Have you tried using it yet? You say you've got Twinview going fine and all, I'm guessing you're using it to do all that.

Is that shot of your high CPU usage while you're running the game, or just normally? I'm not a fan of the gnome-system-monitor, try running top or htop (sudo apt-get install htop for the latter I believe) so you can see the usage. (An example would be how I use it [here](http://fc05.deviantart.com/fs30/f/2008/083/e/a/Desktop_03_23_08_by_herbster.jpg)).

---

### Post by Zanshin on 2008-05-01
> **herbster said:**
> First of all, Quake Wars has had many issues with framerates for many users, myself included. There are a few settings one can tweak, which got mine running its best (in console here):

```
seta com_unlock_timingMethod "1"
seta com_unlock_maxFPS 120
```

I use dual monitors as well, I run the game in a 1920x1200 window on the main monitor so I don't have to disable the second and go fullscreen, and it runs quite well now. However, your 7300 card may not be enough to get a consistent frame rate, this game is wacked that way.

I don't use Ubuntu so I can't help you with anything specific to Hardy, but check to be sure you're using the latest nvidia drivers (should be 169.12 I believe), this can be done by using the nvidia-settings control panel-like app (ALT+F2 and run nvidia-settings). Have you tried using it yet? You say you've got Twinview going fine and all, I'm guessing you're using it to do all that.

Is that shot of your high CPU usage while you're running the game, or just normally? I'm not a fan of the gnome-system-monitor, try running top or htop (sudo apt-get install htop for the latter I believe) so you can see the usage. (An example would be how I use it [here](http://fc05.deviantart.com/fs30/f/2008/083/e/a/Desktop_03_23_08_by_herbster.jpg)).

-Thanks for the quick response.

-I've been running the unlocked FPS for a long time now and it does help on the windows side.  I have brought that over to the linux side too.

-I'm running twinview with both monitors in 1280x1024.  

-I do suspect the 7300 card as a possible bottleneck, but want to eliminate other issues first before throwing hardware at it.  I can't see spending money on a card that is only slightly better, so I have looked at a new video card (like an 8800GT or 9600GT) but they require a larger power supply than my 305W.  This gets into issues because of the Dell p/s form factor, I'd end up Frankensteining the case, etc etc.  So if i can't get the card working for Linux as it works for Windows, I either build a new PC or keep using Windows.  

-I've got the 169.12 nvidia drivers

-I'm now quite familiar with the nvidia setting gui - it simplifies many things.

-The screenshot of the gnome sys mon shows utilization when running the game from the left to about 3/4 over.  It then drops off because I quit the game and processes drop down to normal utilzation levels.  the only thing running at that time is the desktop (and associated standard processes) and Teamspeak.  

Just thought of something though - any chance that Teamspeak (on OSS drivers) is conflicting with the ALSA drivers used for ingame sounds?  hmmm...

---

### Post by herbster on 2008-05-01
Teamspeak may very well be an issue, and are you using AOSS to wrap it? That will take up more CPU.

That CPU usage is normal for your processor during gameplay, I wouldn't pay mind to that. I have a P4 3.4 EE in my server and it used to be my previous desktop, the usage was fairly similar.

Check here if there's anything you haven't yet configured: [http://4newbies.planetwolfenstein.gamespy.com/ETQW/tweaking.php](http://4newbies.planetwolfenstein.gamespy.com/ETQW/tweaking.php)

When you run something like Compiz, how is it? Nice and smoove all around? Should be on that card. How much VRAM does your card have?

If you've got those commands in my post done and still are getting weak framerates but have the proper drivers, the card is more than likely the issue.

---

### Post by Zanshin on 2008-05-02
I tried padsp and aoss for teamspeak, but those didn't work our for me, so I'm not doing that.

I have also used the lfurita tweak guides in the past, but thanks for not assuming I had.  :mrgreen:

I added the following last night which improved my performance a bit:
```
Section "Device"
       Option          "TripleBuffer" "true"
       Driver          "nvidia" [your proprietary driver here]
       Option          "RenderAccel"   "true"
       Option          "AddARGBGLXVisuals" "true"
       Option          "AllowGLXWithComposite" "true"
EndSection

Section "DRI"
       Mode    0666
EndSection
```

I then disabled in game SMP for rendering for another small improvement.  

Then on a hunch, I disabled the FPS unlock (previously set to 60) which took max fps back to 30 and used standard FPS management.  This evened out the rendering and took out the remaining jerkiness I was seeing.  

So, I had some fairly decent gameplay last night.  

However, although this works, it doesn't seem right that in Linux I must run the lowest quality graphics possible while on Windows I can run both higher graphics quality and higher unlocked FPS.  

Thanks for your comments Herbster.  [FYI - I'm also Zanshin ingame.]

I still have open questions on this.  I'll continue working to optimize, looking at xfce, and anything else i can do, but at least I can play again at some level in Linux.

---

### Post by herbster on 2008-05-02
Zanshin, have you looked in nvidia-settings for the Sync to VBlank option? It's also in the OpenGL settings part. Uncheck all the sync options then try the game (also uncheck Vsync in the in-game settings). Are you using an LCD or CRT? Vsync will surely be locking your FPS as well.

Also you didn't respond to:

> When you run something like Compiz, how is it? Nice and smoove all around? Should be on that card. How much VRAM does your card have?

The game can run just as well in linux, you just need to further configure things and play the trial and error game.

I don't play often, but I'll keep an eye out for ya in game when I do.

---

### Post by Zanshin on 2008-05-08
Gave up on tweaking the 7300LE card.  Even though 512M of mem,the bus width is only 64.  Got a 9600GT.  11000 fps on glxgears.  Much better than the other card, but a lot of trial and error to go through again on this one.  Also, it is on beta drivers only - I'm thinking there may be some issues there.  

had compiz turned off btw.

---

### Post by Scolly on 2008-05-13
OK ME TO SAME CARD TYPE

For some reason i cant get my ETQW Higher then 30fps ... now i understand that this can be unlocked and have used every cmd i know to unlock it bet no luck yet.

The worst part of it is Online play drops as low as 9fps and reaches a maximum of a whopping 18-20 fps (20 if the ping is good say between 60-90 ping):lolflag:

Can anyone help ... just don't know what else to try :confused::confused:

P.S. Have the latest NV drivers possible for the Video card installed and running

PC Specs Are:
----------------------------------------------
Intel Core Duo 2.66 GHZ E6740
2 GB 677mhz DDR2 Ram
NVidia 7300 SE 512MB Video Card
80 GB SATA Drive
Intel Sound Card ( ALSA sound)

OS: Ubuntu Hardy Herion 8.04
DESKTOP: Running KDE ( GNOME seems to switch been "small -BIG" windows ...so KDE works better , i guess ....:KS


This the cmd line forme to start ETQW:
----------------------------------------------:(
gnome-terminal -x /usr/local/games/etqw/./etqw +set r_usedSDLModes 1 +set s_alsa_pcm plughw:0 +set com_unlockFPS "1" +set com_unlock_timingMethod "2" +set com_unlock_maxfps "200"

P.S. I have also try the same cmd line in konsole: :(
/usr/local/games/etqw/./etqw +set r_usedSDLModes 1 +set s_alsa_pcm plughw:0 +set com_unlockFPS "1" +set com_unlock_timingMethod "2" +set com_unlock_maxfps "200"

But no joy .... same issue

Please help me ......lol
](*,) ](*,)
------------------
game run info
------------------
**********************************************

ETQW 1.4.12247.12247  linux-x86 Jan  4 2008 13:52:05
found interface lo - loopback
found interface eth0 - 192.168.1.65/255.255.255.0
CPU: Intel CPU with MMX & SSE & SSE2 & SSE3
ETQW using generic code for SIMD processing
enabled Flush-To-Zero mode
------ Initializing File System ------
Loaded pk4 /usr/local/games/etqw/base/game000.pk4 with checksum 0x1eefa237
Loaded pk4 /usr/local/games/etqw/base/game002.pk4 with checksum 0x5f707685
Loaded pk4 /usr/local/games/etqw/base/pak000.pk4 with checksum 0x442eb08b
Loaded pk4 /usr/local/games/etqw/base/pak001.pk4 with checksum 0x10e16e6
Loaded pk4 /usr/local/games/etqw/base/pak002.pk4 with checksum 0x8dbe7353
Loaded pk4 /usr/local/games/etqw/base/pak003.pk4 with checksum 0x99dfcabb
Loaded pk4 /usr/local/games/etqw/base/pak004.pk4 with checksum 0x7e49f838
Loaded pk4 /usr/local/games/etqw/base/pak005.pk4 with checksum 0x5ccc7213
Loaded pk4 /usr/local/games/etqw/base/pak006.pk4 with checksum 0x9edf1b7d
Loaded pk4 /usr/local/games/etqw/base/pak007.pk4 with checksum 0x74a1a2f
Loaded pk4 /usr/local/games/etqw/base/zpak_english000.pk4 with checksum 0x977c7bd0
Loaded pk4 /usr/local/games/etqw/base/zpak_english001.pk4 with checksum 0x6583cd8
Loaded pk4 /usr/local/games/etqw/base/zpak_english002.pk4 with checksum 0x8dc70e3d
Loaded pk4 /usr/local/games/etqw/base/zpak_french001.pk4 with checksum 0x3bd7a062
Loaded pk4 /usr/local/games/etqw/base/zpak_french002.pk4 with checksum 0x79287190
Loaded pk4 /usr/local/games/etqw/base/zpak_german001.pk4 with checksum 0xa694c3f1
Loaded pk4 /usr/local/games/etqw/base/zpak_german002.pk4 with checksum 0x64bee731
Loaded pk4 /usr/local/games/etqw/base/zpak_korean000.pk4 with checksum 0xd42c084
Loaded pk4 /usr/local/games/etqw/base/zpak_korean001.pk4 with checksum 0x4de6a4e7
Loaded pk4 /usr/local/games/etqw/base/zpak_korean002.pk4 with checksum 0x15d2c9af
Loaded pk4 /usr/local/games/etqw/base/zpak_polish001.pk4 with checksum 0x2575ff8e
Loaded pk4 /usr/local/games/etqw/base/zpak_polish002.pk4 with checksum 0x3ab92dd6
Loaded pk4 /usr/local/games/etqw/base/zpak_russian001.pk4 with checksum 0xf3e91581
Loaded pk4 /usr/local/games/etqw/base/zpak_russian002.pk4 with checksum 0x38b1a37c
Loaded pk4 /usr/local/games/etqw/base/zpak_spanish001.pk4 with checksum 0xd609566c
Loaded pk4 /usr/local/games/etqw/base/zpak_spanish002.pk4 with checksum 0xcf994ada
Current search path:
/home/hardline/.etqwcl/base
/usr/local/games/etqw/base
/usr/local/games/etqw/base/zpak_spanish002.pk4 (119 files)
/usr/local/games/etqw/base/zpak_spanish001.pk4 (13 files)
/usr/local/games/etqw/base/zpak_russian002.pk4 (119 files)
/usr/local/games/etqw/base/zpak_russian001.pk4 (13 files)
/usr/local/games/etqw/base/zpak_polish002.pk4 (119 files)
/usr/local/games/etqw/base/zpak_polish001.pk4 (13 files)
/usr/local/games/etqw/base/zpak_korean002.pk4 (12 files)
/usr/local/games/etqw/base/zpak_korean001.pk4 (12 files)
/usr/local/games/etqw/base/zpak_korean000.pk4 (6 files)
/usr/local/games/etqw/base/zpak_german002.pk4 (119 files)
/usr/local/games/etqw/base/zpak_german001.pk4 (13 files)
/usr/local/games/etqw/base/zpak_french002.pk4 (119 files)
/usr/local/games/etqw/base/zpak_french001.pk4 (13 files)
/usr/local/games/etqw/base/zpak_english002.pk4 (117 files)
/usr/local/games/etqw/base/zpak_english001.pk4 (9 files)
/usr/local/games/etqw/base/zpak_english000.pk4 (1018 files)
/usr/local/games/etqw/base/pak007.pk4 (1510 files)
/usr/local/games/etqw/base/pak006.pk4 (3 files)
/usr/local/games/etqw/base/pak005.pk4 (2172 files)
/usr/local/games/etqw/base/pak004.pk4 (72 files)
/usr/local/games/etqw/base/pak003.pk4 (1133 files)
/usr/local/games/etqw/base/pak002.pk4 (1637 files)
/usr/local/games/etqw/base/pak001.pk4 (1067 files)
/usr/local/games/etqw/base/pak000.pk4 (9350 files)
/usr/local/games/etqw/base/game002.pk4 (3 files)
/usr/local/games/etqw/base/game000.pk4 (3 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
----- Initializing Decls -----
Decompressing the global token cache...3560Kb
------------------------------
execing 'etqwconfig.cfg'
r_useThreadedRenderer is read only.
execing 'localization/english/defaultbinds.cfg'
execing 'etqwbinds.cfg'
couldn't exec 'autoexec.cfg'
Vendor: Device:
thread priority set to 1
Opening IP socket: localhost:-1
Failed to open server license code file for reading.
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
Desktop resolution: 1440x900
SDL_ListModes:
1440x900 1280x800 1280x768 1152x864 1024x768 960x600 896x672 840x525 832x624 800x600 800x512
720x450 640x512 640x480 640x400 640x384 576x432 512x384 416x312 400x300 320x240
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
8/8/8/8 RGBA bits, 24 depth bits, 8 stencil bits
no multisampling
vsync: SDL reports -1078676040 - broken?
------- Initializing renderSystem --------
----- R_InitOpenGL -----
...using GL_ARB_multitexture
...using GL_ARB_texture_cube_map
...using GL_ARB_texture_non_power_of_two
...using GL_ARB_texture_compression
...using GL_EXT_texture_compression_s3tc
...using GL_EXT_texture_filter_anisotropic
   maxTextureAnisotropy: 16.000000
...using GL_1.4_texture_lod_bias
X..GL_EXT_shared_texture_palette not found
...using GL_EXT_texture3D
...using GL_ARB_texture_rectangle
X..GL_EXT_texture_rectangle not found
...using GL_EXT_stencil_wrap
...using GL_EXT_stencil_two_side
...using GL_ARB_vertex_buffer_object
...using GL_ARB_vertex_program
...using GL_ARB_fragment_program
...using GL_EXT_depth_bounds_test
...using GL_ARB_point_sprite
...using GL_ARB_occlusion_query
...using GL_EXT_framebuffer_object
...using GL_EXT_packed_depth_stencil
...using GL_EXT_blend_minmax
...using GL_ARB_multisample
...using GL_ARB_shader_objects
...using GL_ARB_vertex_shader
...using GL_ARB_fragment_shader
...using GL_ARB_fragment_program_shadow
...using GL_ARB_shadow
...using GL_ARB_depth_texture
...using GL_EXT_gpu_program_parameters
...using GL_EXT_timer_query
X..GL_GREMEDY_string_marker not found
X..GL_EXT_texture_compression_latc not found
---------- R_ARB2_Init ----------
Cg available.
---------------------------------
thread priority set to 2
thread priority set to 2
using ARB_vertex_buffer_object memory
renderSystem initialized.
--------------------------------------
72 strings read from localization/english/strings/bindings.lang
485 strings read from localization/english/strings/chat.lang
883 strings read from localization/english/strings/code.lang
2186 strings read from localization/english/strings/game.lang
3199 strings read from localization/english/strings/guis.lang
3375 strings read from localization/english/strings/lifestats.lang
3513 strings read from localization/english/strings/loadtips.lang
3852 strings read from localization/english/strings/locations.lang
4377 strings read from localization/english/strings/maps.lang
4444 strings read from localization/english/strings/tasks.lang
/proc/cpuinfo CPU frequency: 2664 MHz
Couldn't open journal files
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
------ Alsa Sound Initialization -----
dlopen(libasound.so.2)
asoundlib version: 1.0.15
opened Alsa PCM device plughw:0 for playback
device buffer size: 5472 frames (21888 bytes)
allocated a mix buffer of 16384 bytes
--------------------------------------
-------- ALSA Microphone Init --------
device buffer size: 2912 frames (5824 bytes)
microphone initialized
--------------------------------------
initializating SDL Joysticks
initialized 0 controller(s)
-------- Initializing Session --------
----------------- BSE Init ------------------
--------- BSE Created Successfully ----------
session initialized
--------------------------------------
found DLL in pak file: /usr/local/games/etqw/base/game002.pk4/gamex86.so
copy gamex86.so to /home/hardline/.etqwcl/base/gamex86.so
game using generic code for SIMD processing
enabled Flush-To-Zero mode
--------- Initializing Game ----------
gamename: baseETQW-1
gamedate: Dec 13 2007
Initializing global UI namespaces
...23 namespaces
...239 properties
Initializing event system
...898 event definitions
Initializing class hierarchy
...163 classes, 395120 bytes for event callbacks
WARNING: Couldn't load sound 'video/intro_1024x512.theora', defaulting
WARNING: idDeclLocal::ParseLocal Failed to Parse decl 'video/intro' in file 'sounds/cinematics.sndshd' line 0
game initialized.
--------------------------------------
------------- Initialized in 07 -------------
--- Common Initialization Complete ---
terminal support enabled ( use +set in_tty 0 to disabled )
pid: 6564
2664 MHz CPU
2032 MB System Memory
detecting video ram (set sys_videoRam on command line to override) ..
found XNVCtrl extension 1.14
512 MB Video Memory
Async thread started
PunkBuster Client: Attempting to resolve master5.evenbalance.com
preparing audio device for output
PunkBuster Client: Resolved to [66.36.231.175]
PunkBuster Client: PunkBuster Client (v2.053 | A0) Enabled
Opening IP socket: localhost:-1
PunkBuster Client: Game Version [ETQW 1.4.12247.12247  linux-x86 Jan  4 2008 13:52:05]
PunkBuster Client: Not Connected to a Server
------------ Game Shutdown -----------
Shutdown event system
--------------------------------------
--------------- BSE Shutdown ----------------
---------------------------------------------
Shutting down sound hardware
----------- Alsa Shutdown ------------
close mic pcm
close pcm
dlclose
--------------------------------------
Shutting down SDL subsystem
idRenderSystem::Shutdown()
shutdown terminal support

**********************************************

---

### Post by Zanshin on 2008-05-13
> **Scolly said:**
> OK ME TO SAME CARD TYPE

For some reason i cant get my ETQW Higher then 30fps ... now i understand that this can be unlocked and have used every cmd i know to unlock it bet no luck yet.

The worst part of it is Online play drops as low as 9fps and reaches a maximum of a whopping 18-20 fps (20 if the ping is good say between 60-90 ping):lolflag:

Can anyone help ... just don't know what else to try :confused::confused:

P.S. Have the latest NV drivers possible for the Video card installed and running

PC Specs Are:
----------------------------------------------
Intel Core Duo 2.66 GHZ E6740
2 GB 677mhz DDR2 Ram
NVidia 7300 SE 512MB Video Card
80 GB SATA Drive
Intel Sound Card ( ALSA sound)

OS: Ubuntu Hardy Herion 8.04
DESKTOP: Running KDE ( GNOME seems to switch been "small -BIG" windows ...so KDE works better , i guess ....:KS


This the cmd line forme to start ETQW:
***************************************

Ok, let's see how your rig (a little bit better than mine overall) does with the same videocard.  It will be a tradeoff of quality for FPS.  

First you should tweak your ubuntu, then your etqw settings.  
-With no other applications running, what are you getting for glxgears?  
-Did you disable compiz on your desktop?  This thing is an OpenGL cycle hog.  
-Did you set these settings in your xorg.conf?
[SIZE="1"]Section "Device"
       Option          "TripleBuffer" "true"
       Identifier      [yours here]
       Driver          "nvidia" [your proprietary driver here]
       BusID           [yours here]
       Option          "RenderAccel"   "true"
       Option          "AddARGBGLXVisuals" "true"
       Option          "AllowGLXWithComposite" "true"
EndSection

Section "DRI"
       Mode    0666
EndSection[/SIZE]

-Run a single monitor, not twinview, etc.
-Turn off all other desktop applications to prepare for playing the game, including firefox browser, pidgin, etc.  (I think I even read that some folks were shutting off Gnome/xfce/kde desktop and then loading etqw to conserve system resources.)

In-game:
-Have you set the lowest possible settings and unchecked all the ingame graphics settings like sync, shadows, soft particles, etc?
-Run at a lower resolution, like 800 x 600 (?)
-run in full screen, not windowed mode.
-I believe that your maxfps setting needs to be an increment of 30 (30, 60, 90, 120 - and I thought I read 120 was the max, but that could be wrong).  I don't think you'll ever see 120 anyway.  I was playing with it at a max of 60 when I didn't have it locked at 30.  With that card, the locked fps at 30 was having the least jitteriness and the most even gameplay.  Try both locked at 30 (default) and unlocked at 60 to see which gives you better fps vs game steadiness.

I think my best glxgears FPS on that 7400LE card with my 3.0GHz P4 Hyperthreading CPU was a touch over 2000.  On my new card (9600GT) I'm getting about 11000.  My tweaks on the old card only varied glxgears fps by 10s or maybe a couple 100s, but changing the card architecture will vary the glxgears fps by thousands.  I think the bottleneck is the 64 bit bus width, rather than the 128 or 256 bit buses of newer cards.  

Compare the differences between the 7400LE and other models here:  
[http://en.wikipedia.org/wiki/Comparison_of_Nvidia_graphics_processing_units]("http://en.wikipedia.org/wiki/Comparison_of_Nvidia_graphics_processing_units")

---

### Post by Scolly on 2008-05-13
> **Zanshin said:**
> Ok, let's see how your rig (a little bit better than mine overall) does with the same videocard.  It will be a tradeoff of quality for FPS.  

> **Zanshin said:**
> 
First you should tweak your ubuntu, then your etqw settings.  
-With no other applications running, what are you getting for glxgears?  
Ok this was interesting ..... i give youu the old glxgears
-----------------------------------------
521 frames in 5.0 seconds = 104.180 FPS
515 frames in 5.0 seconds = 102.890 FPS
542 frames in 5.0 seconds = 108.298 FPS
539 frames in 5.0 seconds = 107.681 FPS
541 frames in 5.0 seconds = 108.191 FPS
542 frames in 5.0 seconds = 108.257 FPS
542 frames in 5.0 seconds = 108.273 FPS
542 frames in 5.0 seconds = 108.316 FPS
542 frames in 5.0 seconds = 108.285 FPS
539 frames in 5.0 seconds = 107.686 FPS
541 frames in 5.0 seconds = 108.066 FPS
542 frames in 5.0 seconds = 108.321 FPS
542 frames in 5.0 seconds = 108.296 FPS
539 frames in 5.0 seconds = 107.763 FPS
541 frames in 5.0 seconds = 108.125 FPS
542 frames in 5.0 seconds = 108.296 FPS
542 frames in 5.0 seconds = 108.299 FPS
521 frames in 5.0 seconds = 104.011 FPS
534 frames in 5.0 seconds = 106.778 FPS
536 frames in 5.0 seconds = 107.101 FPS
540 frames in 5.0 seconds = 107.854 FPS
540 frames in 5.0 seconds = 107.874 FPS
539 frames in 5.0 seconds = 107.799 FPS
536 frames in 5.0 seconds = 107.082 FPS
-----------------------------------------
And then once ihad changed xorg.conf file with the setting that you had 
bingo .... :guitar:
-----------------------------------------
6753 frames in 5.0 seconds = 1350.471 FPS
7190 frames in 5.0 seconds = 1437.847 FPS
7191 frames in 5.0 seconds = 1438.019 FPS
7113 frames in 5.0 seconds = 1422.519 FPS
7122 frames in 5.0 seconds = 1424.284 FPS
7191 frames in 5.0 seconds = 1438.100 FPS
7192 frames in 5.0 seconds = 1438.216 FPS
7134 frames in 5.0 seconds = 1426.650 FPS
7125 frames in 5.0 seconds = 1424.962 FPS
7190 frames in 5.0 seconds = 1437.821 FPS
7190 frames in 5.0 seconds = 1437.949 FPS
7133 frames in 5.0 seconds = 1426.549 FPS
7126 frames in 5.0 seconds = 1425.082 FPS
7189 frames in 5.0 seconds = 1437.669 FPS
7188 frames in 5.0 seconds = 1437.437 FPS
7130 frames in 5.0 seconds = 1425.906 FPS
7130 frames in 5.0 seconds = 1425.987 FPS
7189 frames in 5.0 seconds = 1437.762 FPS
7189 frames in 5.0 seconds = 1437.688 FPS
7128 frames in 5.0 seconds = 1425.479 FPS
7130 frames in 5.0 seconds = 1425.901 FPS
7188 frames in 5.0 seconds = 1437.559 FPS
7176 frames in 5.0 seconds = 1435.022 FPS
7085 frames in 5.0 seconds = 1416.978 FPS
7132 frames in 5.0 seconds = 1426.383 FPS
7190 frames in 5.0 seconds = 1437.848 FPS
7189 frames in 5.0 seconds = 1437.748 FPS
7131 frames in 5.0 seconds = 1426.184 FPS
7130 frames in 5.0 seconds = 1425.882 FPS
7190 frames in 5.0 seconds = 1437.887 FPS
-----------------------------------------
A Huge difference man ... almost like a diffent card :lolflag: 


> **Zanshin said:**
> 
-Did you disable compiz on your desktop?  This thing is an OpenGL cycle hog.  

Ok .... never had compiz enabled ... found out a little while ago not good for gaming

> **Zanshin said:**
> 
-Did you set these settings in your xorg.conf?
[SIZE="1"]Section "Device"
       Option          "TripleBuffer" "true"
       Identifier      [yours here]
       Driver          "nvidia" [your proprietary driver here]
       BusID           [yours here]
       Option          "RenderAccel"   "true"
       Option          "AddARGBGLXVisuals" "true"
       Option          "AllowGLXWithComposite" "true"
EndSection

Section "DRI"
       Mode    0666
EndSection[/SIZE]


THIS WAS BANG ON ... this sorted glxgears to what it is now ... didnt find any differnce in adding the Section DRI 

Yes i live on the wild side ...tried it with and with out ... no diffs

> **Zanshin said:**
> 
-Run a single monitor, not twinview, etc.


Got 2 cards ( 3 mointors posible ) but the single is how it has been set for a will  

> **Zanshin said:**
> 
-Turn off all other desktop applications to prepare for playing the game, including firefox browser, pidgin, etc.  (I think I even read that some folks were shutting off Gnome/xfce/kde desktop and then loading etqw to conserve system resources.)


WOW ... i wonna know how to do that ... then i could boot staight into ETQW :guitar:

> **Zanshin said:**
> 
In-game:
-Have you set the lowest possible settings and unchecked all the ingame graphics settings like sync, shadows, soft particles, etc?
-Run at a lower resolution, like 800 x 600 (?)
-run in full screen, not windowed mode.
-I believe that your maxfps setting needs to be an increment of 30 (30, 60, 90, 120 - and I thought I read 120 was the max, but that could be wrong).  I don't think you'll ever see 120 anyway.  I was playing with it at a max of 60 when I didn't have it locked at 30.  With that card, the locked fps at 30 was having the least jitteriness and the most even gameplay.  Try both locked at 30 (default) and unlocked at 60 to see which gives you better fps vs game steadiness.


Ok pretty much did every thing on this list and i now have a stable 28-30 FPS in game Hal-ahhh--loo--ya

Thanks for the supper quick response Zanshin .... Rock on brother :guitar::lolflag::guitar:

---

### Post by Scolly on 2008-05-13
> **herbster said:**
> Teamspeak may very well be an issue, and are you using AOSS to wrap it? 

Sorry Guys noticed this on the way out .... had to share don't if it will help but it works so what the hay 

/usr/local/games/etqw/./etqw +set r_usedSDLModes 1 [SIZE="4"]+set s_alsa_pcm plughw:0[/SIZE] 

Should allow the game to capture input from your mic ( with out killing sound for the entire game ... as TEAMSPEAK will do ) so you can here everyone in game and they can hear you. Works just as well trust me ....lol
 
here you can see it finds the mic/sound card and binds to it
***********************************
/proc/cpuinfo CPU frequency: 2664 MHz
Couldn't open journal files
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
------ Alsa Sound Initialization -----
dlopen(libasound.so.2)
asoundlib version: 1.0.15
opened Alsa PCM device plughw:0 for playback
device buffer size: 5472 frames (21888 bytes)
allocated a mix buffer of 16384 bytes
--------------------------------------
-------- ALSA Microphone Init --------            :guitar:
device buffer size: 2912 frames (5824 bytes)      :guitar:
microphone initialized                            :guitar:
--------------------------------------
initializating SDL Joysticks
initialized 0 controller(s)
-------- Initializing Session --------
***********************************

Once you have added this in game menu 
> options > settings > there is a voice tab .... and click 

MIC IN     (this is capturing volume of the voice)
MIC OUT    (this sending volume to other players .... guesing , but i think thats fairly accurate)
GAME VOL    ( this brings the the game noise down when the other chavs playing with you speak )

Cheak the All the boxes Global, team , and fireteam ( so you receave audio from all angles of the game )

and there is even a handy tool witch alows you to test if your mic is working

Like i said Not exactly GLX issue but its was mentioned ....so i thought i would add it Peace out dudes .... rock on :guitar:

---

### Post by Zanshin on 2008-05-18
Your processor is a little better than mine, so I think you may be able to raise your glxgears a tad higher, but maybe not.  

Don't know, but running two cards may be taking cpu cycles away from your glxgears numbers.  You might try running just one.

You might check need to dig around the forums here or at the community.enemyterritory.com site to find the more efficient game startup process - but it will also take more work to get that running.

---

