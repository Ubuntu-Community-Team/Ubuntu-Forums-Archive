---
title: "HOWTO: Enemy Territory/Q3 on AMD64 (no chrooting)"
date: 2005-03-15
forum: Outdated Tutorials &amp; Tips
---

### Post by Pse on 2005-03-15
I have made my ET installation work following these steps, please note that some of them may be unnecessesary and it may not work on every system configuration:

1) Get all ia32 packages from synaptic.
2) Install package "linux32" (it's a uname wrapper :-D)
3) Install ia32-libs-more from **Subterrific**'s package: [http://illadvised.com/~jason/ia32-extras-0.1.tar.gz](http://illadvised.com/~jason/ia32-extras-0.1.tar.gz)
4) Get 32-bit OpenGL DRI libs for your graphics card.
4.1) (ATI cards only) Go to [www.ati.com](www.ati.com) and download the 32-bit rpm of your driver (same version as 64-bit).
4.2) (ATI cards only) Unpack "fglrx_dri.so" (should be under "/./usr/X11R6/lib/modules/dri/" inside the package).
4.3) (ATI and nVidia cards) Put it in "/usr/X11R6/lib32/modules/dri". That directory should not exist, so you have to create it.
5) Run the latest ET setup binary (2.56) by doing "linux32 sh et-linux-2.56.x86.run".
6) Follow the setup instructions and complete the installation process.
7) Put **Kareema**'s lines (the bold ones) in your startup script ([game's install path]/et):
```

#!/bin/sh
# Needed to make symlinks/shortcuts work.
# the binaries must run with correct working directory
[b]export LIBGL_DRIVERS_DIR=/usr/X11R6/lib32/modules/dri
export LD_LIBRARY_PATH=/usr/lib32:$LD_LIBRARY_PATH:.[/b]
cd "/mnt/XFS-Drive/games/enemy-territory/"
./et.x86 $*
exit $? 

```
8 ) Fire up the script by doing "linux32 sh et" (it should work without doing "linux32", but I haven't tried it yet).

Step 3 should be optional, but it can't hurt to have a few more 32-bit libs lying around ;) I haven't tried removing them.
Also, setting LD_LIBRARY_PATH should be optional, I haven't tried it yet.

These procedure should also work for Q3, but I haven't tried that...

For those of you running nVidia cards, you could try the following steps (I don't know whether they work or not):

4.1) (nVidia only) Go to [www.nvidia.com](www.nvidia.com) and download the 32-bit linux driver (get the same version as your current 64-bit driver).
4.2) Only unpack it by doing "$ sh NVIDIA-Linux-x86-1.0-7167-pkg1.run --extract-only"
4.3) Copy both the "libGLcore.so.1.0.7167" file and the "libGL.so.1.0.7167" file from "...[place where you unpacked]/NVIDIA-Linux-x86-1.0-7167-pkg1/usr/lib" to "/usr/X11R6/lib32/modules/dri". Create the directory if needed.
Continue with the remaining steps and post back your results, so we can know if it works!

**[EDIT]**I've been told this method is not working on nVidia cards, so I guess that makes this Howto for ATI hardware only.

---

### Post by Wille on 2005-09-12
These instructions didn't work for me (amd64, breezy, nvidia). However, I got ET working by adding

export LD_ASSUME_KERNEL=2.4.2

to the "et" startup script, in addition to what was suggested above, apart from the "dri" directory which doesn't exist w/ nvidia.

---

### Post by fitmik on 2007-03-30
iam on ubuntu 6.10 (linux 2.6.20.3  x86_64) and this worked for me. I just needed to install the ia32 libs and the game now runs with only "et" in the console.
thanks :)

---

### Post by fitmik on 2007-03-31
the game works for me and im on nvidia 6600gt.
but im experiencing very low performance ingame: 20fps on fueldump where i should be at 80 90 fps on my debian 32 bits system.
i thought it would be faster on linux64 but its not the case maybe because it is emulating some things to use the 32bits game :confused: 

Any ideas?

---

### Post by fitmik on 2007-04-16
ok the bug is fixed. i think i messed with the video settings in game (maybe the single multi pass texture option).
The default settings are working well.:D

---

### Post by regx on 2008-08-19
Works great for me on presario r3000.
All I didn't have to do anything, because I previously followed the skype amd 64 h ow to. Both Enemy Territory and the Combat Elite mod run awesome at 1280x1024 on this laptop. Sound works to without any of the sdl scripts. I am blown away! This runs so much better than my desktop.

---

### Post by kb7ypf on 2008-08-20
Hi-

I just installed ET.  It works, but I have no sound.  Here is the following information I get from the terminal:

------- sound initialization -------
/dev/dsp: Input/output error
Could not mmap /dev/dsp
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/kb7ypf/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/kb7ypf/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/kb7ypf/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xae203bb4  
Sys_LoadDll(ui) succeeded!
Found high quality video and fast CPU
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: kb7ypf-desktop
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
execing preset_high.cfg
r_colorbits will be changed upon restarting.
r_depthbits will be changed upon restarting.
r_picmip will be changed upon restarting.
r_mode will be changed upon restarting.
r_texturebits will be changed upon restarting.
RE_Shutdown( 1 )


Hope someone can help me out.  Thanks

---

