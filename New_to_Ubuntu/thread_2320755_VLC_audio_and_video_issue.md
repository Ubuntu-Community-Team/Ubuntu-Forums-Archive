---
title: "VLC audio and video issue"
date: 2016-04-17
forum: New to Ubuntu
---

### Post by Ajay_Dasila on 2016-04-17
Hey,  I am using the latest VLC player in Ubuntu Mate 15.10 on Acer Aspire 5745. When I play videos, there are certain lines that appear on screen. I have also observed that these lines are more frequent when the video has more action on screen. I don't know if it's a graphics issue because I think I have installed all the drivers correctly and have fully updated the OS. Also sometimes when I forward or rewind a video, the audio stops. I then have to again rewind/forward it to get the audio back. I have only used  VLC media player.

---

### Post by T.J. on 2016-04-17
The lines you describe are known as "tearing."   It's a side effect of the video player not syncing with the monitor's refresh rate when it renders a frame.  X11 does not require frame updates to match sync rates for hardware reasons.  Tearing can happen on Windows if you disable the theme manager, or on Linux in desktops like Mate (that do not sync updates with the monitor at all), so it is not a "Linux issue" as some might claim.  It's a fairly common issue in computing which is easily fixed. 

READ EVERYTHING FIRST
[B]
Do NOT use compton if you are using the AMD FGRLX or Nvidia proprietary drivers. Each of those has their own options for vsync in their software that you should use instead. FGLRX has "tear free" for example. Using compton with a proprietary driver could cause the desktop to jitter or freeze the system completely, because AMD and Nvidia have a bad habit of replacing the standard graphics libraries with their own. [/B]

Use a terminal to install compton: *sudo apt-get install compton  *or the Software Centre.

Make sure that Mate's compositor is OFF. This is very important. You can only have one active compositor. It's under "windows" in the Mate control panel.  Don't use Mate's compositor.  It's well - it's ancient crap.  It has no sync at all, when sync is one of the major points of a modern compositor.

Then open a terminal and enter "compton --vsync opengl".  This is the safest Compton option and will force proper syncing.  Leave the terminal open and try to play a video. If the video still tears, close the terminal and compton will be shut off. Post me back and we will find another solution for you.

 If everything works as desired, add the command to your Mate startup, logout and login again.   You are done, and it is fixed.  Compton will start every time you log in. 


Notes:

Depending on your video hardware, you may still notice some tearing at the bottom of the monitor.  You can try using "compton --backend glx  --vsync opengl-swc" instead of  "compton --vsync opengl" to fix it.  Be warned, however, the opengl-swc option provides better syncing but can cause some desktops to freeze. If you do freeze, try pressing control+alt+F1 to get a text console, login and then enter "killall compton", then alt+f7 to get back to GUI mode.  It should let you regain control.  On some Ubuntu setups, the text consoles do not always function.  Your only option then is a reset.

After your initial test run is successful to make sure compton won't freeze, you should have no future problems. I use compton everyday to solve the same tearing.

---

### Post by T.J. on 2016-04-17
Once you have compton working, you can tell it to add shadows and transparency, etc to windows and menus with a ".compton.conf" file.  Here is a sample.  

```

# Shadow
shadow = true;
no-dnd-shadow = true;
no-dock-shadow = true;
clear-shadow = true;
shadow-radius = 7;
shadow-offset-x = -7;
shadow-offset-y = -7;
# shadow-opacity = 0.7;
# shadow-red = 0.0;
# shadow-green = 0.0;
# shadow-blue = 0.0;
shadow-exclude = [
    "name = 'Notification'",
    "class_g = 'Conky'",
    "class_g ?= 'Notify-osd'",
    "class_g = 'Cairo-clock'",
    "_GTK_FRAME_EXTENTS@:c"
];
# shadow-exclude = "n:e:Notification";
# shadow-exclude-reg = "x10+0+0";
# xinerama-shadow-crop = true;


# Opacity
menu-opacity = 1;
inactive-opacity = 1;
# active-opacity = 1;
frame-opacity = 1;
inactive-opacity-override = false;
alpha-step = 0.06;
# inactive-dim = 0.2;
# inactive-dim-fixed = true;
# blur-background = true;
# blur-background-frame = true;
blur-kern = "3x3box"
# blur-kern = "5,5,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1"
# blur-background-fixed = true;
blur-background-exclude = [
    "window_type = 'dock'",
    "window_type = 'desktop'",
    "_GTK_FRAME_EXTENTS@:c"
];
# opacity-rule = [ "80:class_g = 'URxvt'" ];


# Fading
fading = false;
# fade-delta = 30;
fade-in-step = 0.03;
fade-out-step = 0.03;
# no-fading-openclose = true;
# no-fading-destroyed-argb = true;
fade-exclude = [ ];


# Use "glx" backend instead of xrender if you are using --backend glx
backend = "xrender"
mark-wmwin-focused = true;
mark-ovredir-focused = true;
# use-ewmh-active-win = true;
detect-rounded-corners = true;
detect-client-opacity = true;
refresh-rate = 0;
vsync = "none";
dbe = false;
paint-on-overlay = true;
# sw-opti = true;
# unredir-if-possible = true;
# unredir-if-possible-delay = 5000;
# unredir-if-possible-exclude = [ ];
focus-exclude = [ "class_g = 'Cairo-clock'" ];
detect-transient = true;
detect-client-leader = true;
invert-color-include = [ ];
# resize-damage = 1;


# GLX backend
# glx-no-stencil = true;
glx-copy-from-front = false;
# glx-use-copysubbuffermesa = true;
# glx-no-rebind-pixmap = true;
glx-swap-method = "undefined";
# glx-use-gpushader4 = true;
# xrender-sync = true;
# xrender-sync-fence = true;


# Window type settings
wintypes:
{
  tooltip = { fade = true; shadow = true; opacity = 0.75; focus = true; };
};

```

---

### Post by Ajay_Dasila on 2016-04-18
**Thank-you** very much. **compton --vsync opengl** did the job for me. No more ***tearing*** now. The audio problem still remains. As I have mentioned, for some videos, whenever I rewind/forward the video, the audio playback stops. Then I again have to rewind/forward the video randomly to gain the audio back. This doesn't happened for all videos but for some. Details of one of them is given below if that helps:

Video 
```
ID                                       : 1 
Format                                : AVC 
Format/Info                          : Advanced Video Codec 
Format profile                       : High@L4 
Format settings, CABAC       : Yes 
Format settings, ReFrames    : 4 frames 
Codec ID                              : avc1 
Codec ID/Info                        : Advanced Video Coding 
Duration                                : 1h 28mn 
Bit rate mode                         : Variable 
Bit rate                                  : 3 007 Kbps 
Maximum bit rate                   : 40.0 Mbps 
Width                                    : 1 776 pixels 
Height                                   : 1 072 pixels 
Display aspect ratio                : 5:3 
Frame rate mode                    : Constant 
Frame rate                             : 25.000 fps 
Color space                            : YUV 
Chroma subsampling             : 4:2:0 
Bit depth                                : 8 bits 
Scan type                               : Progressive 
Bits/(Pixel*Frame)                   : 0.063 
Stream size                            : 1.86 GiB (93%)
```
 
Audio 
```
ID                                           : 2 
Format                                    : AAC 
Format/Info                              : Advanced Audio Codec 
Format profile                           : LC 
Codec ID                                 : 40 
Duration                                   : 1h 28mn 
Bit rate mode                            : Constant 
Bit rate                                     : 224 Kbps 
Channel(s)                                : 2 channels 
Channel positions                      : Front: L R 
Sampling rate                            : 44.1 KHz 
Frame rate                                : 43.066 fps (1024 spf) 
Compression mode                    : Lossy 
Stream size                               : 142 MiB (7%) 
Default                                      : Yes 
Alternate group                           : 1
```

Also, all of them videos were 1080p.

---

### Post by T.J. on 2016-04-18
Great!  Glad to hear Compton fixed it.  As a reminder, be sure to disable Compton first if you decide to switch drivers to AMD's or Nvidia's proprietary one.

I've noted it myself across different versions. I don't have a 100% full-proof fix, because it doesn't happen all the time on my hardware. I've not pinned down the cause, but I suspect VLC of a bug. The audio stack on Linux is one heck of a mess in my opinion.

 You wouldn't happen to have Intel HD sound by chance, using the snd_hda_intel driver with PulseAudio? If you do, I might have a few extra ideas. You can find out by using:  *lsmod | grep snd_hda_intel *in a terminal

You might see something like this:

```

snd_hda_intel          26407  5 
snd_hda_controller     26646  1 snd_hda_intel
snd_hda_codec         104500  4 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_pcm                88662  4 snd_usb_audio,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd                    65244  27 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_pcm,snd_rawmidi,snd_hda_codec_generic,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device



```

 I can make a few suggestions regardless, such as forcing VLC to use PulseAudio rather than Automatic, under Tools on the audio tab. Another suggestion might be to try parole, a player based on GStreamer, instead of libvlc.     Mate already uses GStreamer, anyway.**  You don't want to take the popular suggestion of removing PulseAudio.**  A lot of software in Ubuntu depends on it being there. You may hose your GUI if you try. Besides, depending on your hardware, it may not be capable of mixing entirely on its own.  Sometimes, the audio drivers really suck, and Pulseaudio is the only thing keeping them sane - from a programmer's POV.

We can go back and forth a bit, until we find something solid for you.  I'm happy to help out.

---

### Post by Ajay_Dasila on 2016-04-19
Yes, I think I am using the **snd_hda_intel driver**.

---

### Post by T.J. on 2016-04-19
> **Ajay_Dasila said:**
> Yes, I think I am using the **snd_hda_intel driver**.

Let's just make absolutely sure so I don't waste your precious time.  If you enter  * lspci -vnn | grep snd* in a terminal, you should get a response with this line included:  [I]Kernel driver in use: snd_hda_intel.
[/I]
As a disclaimer, this will have no direct effect if you have a bad codec or a bug in your copy of VLC, but it is certainly worth trying.  Don't worry, this should be perfectly safe to use.  It should not damage anything.

You may be able to resolve your problem or at least mitigate sound problems on Intel HD chipsets, such as skipping or crackling by adjusting the the driver parameters in the file: /etc/pulse/default.pa. Worst case, it does nothing to help, but I have found it essential on my systems that use Intel HD chipsets, due to the interaction of ALSA and Pulseaudio.  


You will need to have administrator permission to do this. Be sure to make a backup copy of the file before you make changes, just in case. 


Edit the line:
[B]load-module module-udev-detect
[/B]
and add "tsched=0" so it will be:

[B]load-module module-udev-detect tsched=0

[/B]In my file on Debian, I add it in two places, just to be sure:

```

### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
load-module module-udev-detect tsched=0
.else
### Use the static hardware detection module (for systems that lack udev support)
load-module module-detect tsched=0
.endif

```

Save it. It will force PulseAudio try to not bulldoze over the sound driver's timing by forcing the scheduler to 0. 

Go into VLCs sound setting and force it to use the PulseAudio sound module. Save that.

Then restart your machine so everything is in effect.  Normally, I'd just log out and back in again, but I do not know every change Ubuntu has made to the session processes with 15.10. It's probably unnecessary to reboot, but it is a guaranteed way to be certain everything updates.


Hopefully, that will do it after it comes back up. Let me know if it persists, and we can try a few more tweaks.

---

### Post by Ajay_Dasila on 2016-04-20
I edited the file **default.pa** situated in **/etc/pulse** as mentioned and changed **vlc** output module to **Pulseaudio audio output**. I then restarted my PC and checked a specific file in which I had detected the problem earlier. But the audio problem on rewinding/forwarding the video still persists!

---

### Post by T.J. on 2016-04-20
Have you tested the same file in another player, such as Dragon, Parole, or kaffiene?  I realise this might not seem important, but it is.  Each one of those three uses a different backend for audio.  It's how we can help pin down where the bug is.

---

### Post by Ajay_Dasila on 2016-04-20
Well, I haven't. Have only used VLC. I am up for those players though and would love to see if anyone of these solves the problem. Will report after trying them. Thanks for your precious time anyway.

---

### Post by T.J. on 2016-04-21
It's not that I am trying to dissuade you from using VLC.  

The reasoning is this.  VLC uses libvlc to decode video.  Dragon uses Phonon, Parole uses Gstreamer, and kaffeine uses libxine.  If you experience the same issue in other players, we might be able to track the bug to specific library or codec.

---

### Post by oldrocker99 on 2016-04-21
The dead air when you FF or rewind in VLC is a known bug. I have so much trouble with it that I use mplayer instead. Once in a while, I get good results from VLC, but it's touch and go. It **was** my go-to media player.

It has been suggested that you reset VLC's preferences, or make sure that PulseAudio is enabled. I've done those myself, and have still had problems.

Just sayin'.

---

### Post by Ajay_Dasila on 2016-04-23
Installed **16.04** and great to see the newly integrated **Marco (Compton GPU Compositor)** window manager. It takes care of the tearing problem.

---

### Post by T.J. on 2016-04-24
Yep, exactly the same setup, except that it uses a Mate dconf key to start Compton for you.

---

