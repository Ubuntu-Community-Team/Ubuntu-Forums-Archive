---
title: "Running darwinia Demo 2 Dapper"
date: 2006-08-23
forum: Outdated Tutorials &amp; Tips
---

### Post by s_h_a_d_o_w_s on 2006-08-23
This howto is for running the darwinia demo 2.

1. First, we have a dependency to satisfy.

```
sudo apt-get install libgtk1.2
```

2. Download the .sh installation file [here]("http://www.darwinia.co.uk/downloads/demo_linux.html").

3. Run the file.
```
(example)cd /home/(uname)/Desktop/darwinia-demo2-1.3.0.sh

```
```
sudo sh darrwinia-demo2-1.3.0.sh
```

That will install the file. Make sure to check the button for a desktop entry in Applications -> Games -> darwinia-demo2

4. Try out the game in thre above-specified location. Chances are it won't work. It happened to me, it's easily fixable. To fix the problem:

Open nautilus to /home/(username)/.darwinia/demo2/

and open up "preferences.txt" with gedit.

You have to change two of the values. Change "ManuallyScaleTextures = 0"
from 0 to 1, and "RenderLandscapeMode = 2" from 2 to 1. Here is what my preferences.txt looks like, yours should look the same: 

```
ServerAddress = 127.0.0.1
BypassNetwork = 1
IAmAServer = 1
TextLanguage = english
TextSpeed = 15
HelpEnabled = 0
SoundLibrary = software
SoundMixFreq = 22050
SoundMasterVolume = 255
SoundChannels = 32
SoundHW3D = 0
SoundSwapStereo = 0
SoundMemoryUsage = 1
SoundBufferSize = 512
SoundDSP = 0
ScreenWidth = 1024
ScreenHeight = 768
ScreenWindowed = 0
ScreenZDepth = 24
ScreenColourDepth = 32
ScreenRefresh = 60
RenderLandscapeDetail = 1
RenderWaterDetail = 1
RenderBuildingDetail = 1
RenderEntityDetail = 1
RenderCloudDetail = 1
RenderPixelShader = 1
ControlMouseButtons = 3
ControlMethod = 1
RenderLandscapeMode = 1
ManuallyScaleTextures = 1
UserProfile = DemoUser
RenderSpecialLighting = 1
StartMap = launchpad
```

5. Have fun! Run the game at Applications -> Games -> darwinia-demo2

If there are any problems, post them here. Also, search for blackbox.txt with nautilus. You will find the blackbox darwinia error output. Yoiu can copy/paste it.

---

### Post by s_h_a_d_o_w_s on 2006-08-23
So, has anyone tried it?

---

### Post by s_h_a_d_o_w_s on 2006-08-27
oh well.

---

### Post by HanZo on 2006-08-27
why is it called demo2? it's still v.1 isn't it?
I played it some time ago and I must say the idea behind it is really good... unfortunately the game can become a bit tiring after some time... it takes ages to complete some levels and so I did never finish it... despite the fact that I even bought it.
anyway try the demo! I highly suggest it!

---

### Post by Crashmaxx on 2006-08-27
I just got a black screen, but had sound. Here is what the blackbox said:

> 
=========================
DARWINIA BLACK BOX REPORT
=========================

VERSION : linux-demo2-1.3.0
ERROR   : 'Got a fatal signal: 11
'

=========================
====== PREFERENCES ======
=========================

ServerAddress = 127.0.0.1
BypassNetwork = 1
IAmAServer = 1
TextLanguage = english
TextSpeed = 15
HelpEnabled = 0
SoundLibrary = software
SoundMixFreq = 22050
SoundMasterVolume = 255
SoundChannels = 32
SoundHW3D = 0
SoundSwapStereo = 0
SoundMemoryUsage = 1
SoundBufferSize = 512
SoundDSP = 0
ScreenWidth = 1024
ScreenHeight = 768
ScreenWindowed = 0
ScreenZDepth = 24
ScreenColourDepth = 32
ScreenRefresh = 60
RenderLandscapeDetail = 1
RenderWaterDetail = 1
RenderBuildingDetail = 1
RenderEntityDetail = 1
RenderCloudDetail = 1
RenderPixelShader = 1
ControlMouseButtons = 3
ControlMethod = 1
RenderLandscapeMode = 2
ManuallyScaleTextures = 0
UserProfile = DemoUser
RenderSpecialLighting = 1
StartMap = launchpad

=========================
====== STACKTRACE =======
=========================

retAddress = 0xb7e11d7d
retAddress = 0xb7e12277
retAddress = 0xb7decaea
retAddress = 0x807f94b
retAddress = 0x807fe8a
retAddress = 0x80ade1b
retAddress = 0x80ba26b
retAddress = 0x80b9dd9
retAddress = 0x80b3799
retAddress = 0x80b408d
retAddress = 0x80a25b8
retAddress = 0xb7b46ea2
retAddress = 0x804cc91


gdb stack trace:

GNU gdb 6.4-debian
Copyright 2005 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "i486-linux-gnu".
(gdb) Reading symbols from /usr/local/games/darwinia-demo2/lib/darwinia.bin.x86...(no debugging symbols found)...done.
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(gdb) Attaching to program: /usr/local/games/darwinia-demo2/lib/darwinia.bin.x86, process 16322
(no debugging symbols found)
Reading symbols from /usr/local/games/darwinia-demo2/lib/libSDL-1.2.so.0...done.
Loaded symbols for /usr/local/games/darwinia-demo2/lib/libSDL-1.2.so.0
Reading symbols from /usr/lib/libGL.so.1...done.
Loaded symbols for /usr/lib/libGL.so.1
Reading symbols from /usr/lib/libGLU.so.1...done.
Loaded symbols for /usr/lib/libGLU.so.1
Reading symbols from /usr/local/games/darwinia-demo2/lib/libvorbisfile.so.3...done.
Loaded symbols for /usr/local/games/darwinia-demo2/lib/libvorbisfile.so.3
Reading symbols from /usr/lib/libstdc++.so.5...done.
Loaded symbols for /usr/lib/libstdc++.so.5
Reading symbols from /lib/tls/i686/cmov/libm.so.6...done.
Loaded symbols for /lib/tls/i686/cmov/libm.so.6
Reading symbols from /usr/local/games/darwinia-demo2/lib/libgcc_s.so.1...done.
Loaded symbols for /usr/local/games/darwinia-demo2/lib/libgcc_s.so.1
Reading symbols from /lib/tls/i686/cmov/libc.so.6...done.
Loaded symbols for /lib/tls/i686/cmov/libc.so.6
Reading symbols from /lib/tls/i686/cmov/libpthread.so.0...done.
[Thread debugging using libthread_db enabled]
[New Thread -1215211840 (LWP 16322)]
[New Thread -1225667664 (LWP 16331)]
Loaded symbols for /lib/tls/i686/cmov/libpthread.so.0
Reading symbols from /lib/tls/i686/cmov/libdl.so.2...done.
Loaded symbols for /lib/tls/i686/cmov/libdl.so.2
Reading symbols from /usr/lib/libX11.so.6...done.
Loaded symbols for /usr/lib/libX11.so.6
Reading symbols from /usr/lib/libXext.so.6...done.
Loaded symbols for /usr/lib/libXext.so.6
Reading symbols from /usr/lib/libXxf86vm.so.1...done.
Loaded symbols for /usr/lib/libXxf86vm.so.1
Reading symbols from /usr/lib/libdrm.so.2...done.
Loaded symbols for /usr/lib/libdrm.so.2
Reading symbols from /usr/lib/libstdc++.so.6...done.
Loaded symbols for /usr/lib/libstdc++.so.6
Reading symbols from /usr/local/games/darwinia-demo2/lib/libvorbis.so.0...done.
Loaded symbols for /usr/local/games/darwinia-demo2/lib/../lib/libvorbis.so.0
Reading symbols from /usr/local/games/darwinia-demo2/lib/libogg.so.0...done.
Loaded symbols for /usr/local/games/darwinia-demo2/lib/../lib/libogg.so.0
Reading symbols from /lib/ld-linux.so.2...done.
Loaded symbols for /lib/ld-linux.so.2
Reading symbols from /usr/lib/libXau.so.6...done.
Loaded symbols for /usr/lib/libXau.so.6
Reading symbols from /usr/lib/libXcursor.so.1...done.
Loaded symbols for /usr/lib/libXcursor.so.1
Reading symbols from /usr/lib/libXrender.so.1...done.
Loaded symbols for /usr/lib/libXrender.so.1
Reading symbols from /usr/lib/libXfixes.so.3...done.
Loaded symbols for /usr/lib/libXfixes.so.3
Reading symbols from /usr/lib/libasound.so.2...done.
Loaded symbols for /usr/lib/libasound.so.2
Reading symbols from /lib/tls/i686/cmov/libnss_compat.so.2...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_compat.so.2
Reading symbols from /lib/tls/i686/cmov/libnsl.so.1...done.
Loaded symbols for /lib/tls/i686/cmov/libnsl.so.1
Reading symbols from /lib/tls/i686/cmov/libnss_nis.so.2...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_nis.so.2
Reading symbols from /lib/tls/i686/cmov/libnss_files.so.2...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_files.so.2
0xffffe410 in __kernel_vsyscall ()
(gdb)   2 Thread -1225667664 (LWP 16331)  0xffffe410 in __kernel_vsyscall ()
  1 Thread -1215211840 (LWP 16322)  0xffffe410 in __kernel_vsyscall ()
(gdb) 
Thread 2 (Thread -1225667664 (LWP 16331)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7bf18c4 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb783b836 in snd_pcm_wait_nocheck () from /usr/lib/libasound.so.2
#3  0xb7841c58 in snd_pcm_wait () from /usr/lib/libasound.so.2
#4  0xb7841d34 in snd_pcm_write_areas () from /usr/lib/libasound.so.2
#5  0xb785b5c4 in snd_pcm_mmap_writei () from /usr/lib/libasound.so.2
#6  0xb7839966 in snd_pcm_writei () from /usr/lib/libasound.so.2
#7  0xb7e4dd33 in ALSA_PlayAudio (this=0x93ea568) at SDL_alsa_audio.c:270
#8  0xb7e48137 in SDL_RunAudio (audiop=0x93ea568) at SDL_audio.c:232
#9  0xb7e9310b in SDL_RunThread (data=0x93d9b08) at SDL_thread.c:218
#10 0xb7e9331f in RunThread (data=0xfffffffc) at SDL_systhread.c:82
#11 0xb7b25341 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#12 0xb7bfb4ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread -1215211840 (LWP 16322)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7bbd95b in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7b673c9 in strtold_l () from /lib/tls/i686/cmov/libc.so.6
#3  0xb7b67741 in system () from /lib/tls/i686/cmov/libc.so.6
#4  0x08088748 in ?? ()
#5  0x08088a42 in ?? ()
#6  0x08088860 in ?? ()
#7  <signal handler called>
#8  0xb7b9d9dc in memcpy () from /lib/tls/i686/cmov/libc.so.6
#9  0xb7e11826 in __glXInitVertexArrayState () from /usr/lib/libGL.so.1
#10 0xb7e11d7d in __glXInitVertexArrayState () from /usr/lib/libGL.so.1
#11 0xb7e12277 in __glXInitVertexArrayState () from /usr/lib/libGL.so.1
#12 0xb7decaea in glDrawArrays () from /usr/lib/libGL.so.1
#13 0x0807f94b in ?? ()
#14 0x0807fe8a in ?? ()
#15 0x080ade1b in ?? ()
#16 0x080ba26b in ?? ()
#17 0x080b9dd9 in ?? ()
#18 0x080b3799 in ?? ()
#19 0x080b408d in ?? ()
#20 0x080a25b8 in ?? ()
#21 0xb7b46ea2 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#22 0x0804cc91 in ?? ()
#0  0xffffe410 in __kernel_vsyscall ()
(gdb) Detaching from program: /usr/local/games/darwinia-demo2/lib/darwinia.bin.x86, process 16322


---

### Post by s_h_a_d_o_w_s on 2006-09-02
Are yousure your preferences.txt is the same as the one posted above? If it is, try setting some values that may take up high ressources to lower values.

---

### Post by deeek on 2006-09-29
Thanks for the great howto.  I had been trying to get this game to work.

---

### Post by s_h_a_d_o_w_s on 2006-10-21
Your very wlcome. I ahd to scour the web for hours, though the answer was simple enough.

---

### Post by s_h_a_d_o_w_s on 2006-10-21
> **Crashmaxx said:**
> I just got a black screen, but had sound. Here is what the blackbox said:

In your blackbox you seem to have frgotten to change "Manually Scale Txtures value" from 0 to 1. That should fix it. This was ur preferences.txt:


=========================
====== PREFERENCES ======
=========================

ServerAddress = 127.0.0.1
BypassNetwork = 1
IAmAServer = 1
TextLanguage = english
TextSpeed = 15
HelpEnabled = 0
SoundLibrary = software
SoundMixFreq = 22050
SoundMasterVolume = 255
SoundChannels = 32
SoundHW3D = 0
SoundSwapStereo = 0
SoundMemoryUsage = 1
SoundBufferSize = 512
SoundDSP = 0
ScreenWidth = 1024
ScreenHeight = 768
ScreenWindowed = 0
ScreenZDepth = 24
ScreenColourDepth = 32
ScreenRefresh = 60
RenderLandscapeDetail = 1
RenderWaterDetail = 1
RenderBuildingDetail = 1
RenderEntityDetail = 1
RenderCloudDetail = 1
RenderPixelShader = 1
ControlMouseButtons = 3
ControlMethod = 1
RenderLandscapeMode = 2
ManuallyScaleTextures = 0 _***<- needs to be 1:mrgreen:***_
UserProfile = DemoUser
RenderSpecialLighting = 1
StartMap = launchpad

---

### Post by Zyphrexi on 2007-02-20
I get this upon attempting to run (running on feisty btw)

```
.
./lib/darwinia.bin.x86: ./lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

```

any hacks around this?

---

