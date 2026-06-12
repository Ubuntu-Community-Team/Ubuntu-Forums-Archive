---
title: "portaudio"
date: 2008-04-16
forum: Packaging and Compiling Programs
---

### Post by elmick on 2008-04-16
Hi,

Im trying desperatly to get portaudio working so i can write audio programs. Im trying the tutorial from 
[http://www.portaudio.com/trac/wiki/TutorialDir/Compile/Linux](http://www.portaudio.com/trac/wiki/TutorialDir/Compile/Linux) to compile a simple test program. I can write ok programs but dont know a lot about linking, libraries etc. I tried this:

```
mick@mick-laptop:~/audioprog$ gcc -lrt -lpthread -o testsaw patest_saw.c libportaudio.a
libportaudio.a(pa_unix_util.o): In function `PaUnixThread_New':
/home/mick/portaudio/src/os/unix/pa_unix_util.c:338: undefined reference to `floor'
libportaudio.a(pa_unix_oss.o): In function `PaOssStream_Configure':
/home/mick/portaudio/src/hostapi/oss/pa_unix_oss.c:1151: undefined reference to `ceil'
collect2: ld returned 1 exit status
```



Then When I try to include alsa:
```
mick@mick-laptop:~/audioprog$ gcc -lalsa -lrt -lpthread -o testsaw patest_saw.c libportaudio.a

/usr/bin/ld: cannot find -lalsa
```

I dont know much about alsa or oss either,

Can anyone help?

Thanks,
Mick.

---

### Post by jaddle on 2008-04-16
You'll need -lm (math) first of all, in order to use floor and ceil. A quick 'man floor' will show that it's in that library.

The alsa error is probably just because you don't have the libalsa-dev package installed. But that said, you shouldn't need it to compile portaudio programs. Portaudio itself is linked with alsa, so you don't need to do it yourself (unless you also use some alsa calls directly, but that kind of defeats the purpose of portaudio!)

---

### Post by elmick on 2008-04-16
Hi,

Thanks a lot, thats it working!. ok i get you mean about libalsa aswell

Cheers,
Mick.

---

### Post by forent on 2013-04-06
> **elmick said:**
> Hi,

Thanks a lot, thats it working!. ok i get you mean about libalsa aswell

Cheers,
Mick.

i dont know what you mean about libalsa, I have installed libasound, libasound2. but it return 
```
/usr/bin/ld: cannot find -lalsa
collect2: ld returned 1 exit status

```
:confused::confused: please help me asap

---

### Post by jaddle on 2013-04-06
> **forent said:**
> i dont know what you mean about libalsa, I have installed libasound, libasound2. but it return 
```
/usr/bin/ld: cannot find -lalsa
collect2: ld returned 1 exit status

```
:confused::confused: please help me asap

When you say -lalsa, you're telling the compiler to link the program you're compiling with the alsa library. To do that, you need the alsa headers - i.e. the stuff in the -dev packages.

libasound lets you *run* programs linked with alsa. libasound-dev lets you *compile* programs that are linked with alsa. If you're writing a portaudio program though, in most cases your program isn't linked (directly) to alsa - it links to portaudio. So you probably don't need to link to alsa at all. Try just getting rid of the -lalsa line entirely. 

If it turns out that you do need to link to alsa for some reason, then you have to install the -dev alsa packages.

Hope that's a bit more clear!

---

### Post by forent on 2013-04-06
i have try everything to make portaudio run well.
i run this code
gcc -lrt -lasound -lpthread -o testing paex_saw.c libportaudio.a
and it return
```
root@ubuntu:~/Documents/portaudio/Project# gcc -lrt -lasound -lpthread -o testing paex_saw.c libportaudio.a
libportaudio.a(pa_unix_util.o): In function `PaUtil_GetTime':
/home/rifkiwijaya/Documents/portaudio/src/os/unix/pa_unix_util.c:163: undefined reference to `clock_gettime'
libportaudio.a(pa_unix_util.o): In function `PaUtil_StartThreading':
/home/rifkiwijaya/Documents/portaudio/src/os/unix/pa_unix_util.c:184: undefined reference to `pthread_create'
libportaudio.a(pa_unix_util.o): In function `PaUtil_CancelThreading':
/home/rifkiwijaya/Documents/portaudio/src/os/unix/pa_unix_util.c:205: undefined reference to `pthread_join'
/home/rifkiwijaya/Documents/portaudio/src/os/unix/pa_unix_util.c:203: undefined reference to `pthread_cancel'
libportaudio.a(pa_unix_util.o): In function `PaUnixThread_Terminate':
/home/rifkiwijaya/Documents/portaudio/src/os/unix/pa_unix_util.c:441: undefined reference to `pthread_join'
/home/rifkiwijaya/Documents/portaudio/src/os/unix/pa_unix_util.c:437: undefined reference to `pthread_cancel'
libportaudio.a(pa_unix_util.o): In function `PaUnixThread_New':
/home/rifkiwijaya/Documents/portaudio/src/os/unix/pa_unix_util.c:305: undefined reference to `pthread_create'
/home/rifkiwijaya/Documents/portaudio/src/os/unix/pa_unix_util.c:371: undefined reference to `floor'
```

when i test /portaudio/bin/patest1 it return
```
root@ubuntu:~/Documents/portaudio/bin# ./patest1
patest1.c
Ring modulate input for 20 seconds.
ALSA lib setup.c:565:(add_elem) Cannot obtain info for CTL elem (MIXER,'AC97 2ch->4ch Copy Switch',0,0,0): No such file or directory
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib setup.c:565:(add_elem) Cannot obtain info for CTL elem (MIXER,'AC97 2ch->4ch Copy Switch',0,0,0): No such file or directory
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround41
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround50
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround51
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround71
ALSA lib setup.c:565:(add_elem) Cannot obtain info for CTL elem (PCM,'IEC958 Playback PCM Stream',0,0,0): No such file or directory
ALSA lib setup.c:565:(add_elem) Cannot obtain info for CTL elem (PCM,'IEC958 Playback PCM Stream',0,0,0): No such file or directory
ALSA lib setup.c:565:(add_elem) Cannot obtain info for CTL elem (PCM,'IEC958 Playback PCM Stream',0,0,0): No such file or directory
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.modem
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.modem
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
Press any key to end.
ALSA lib pcm.c:7339:(snd_pcm_recover) underrun occurred
Expression 'err' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 3281
Expression 'ContinuePoll( self, StreamDirection_In, &pollTimeout, &pollCapture )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 3808
Expression 'PaAlsaStream_WaitForFrames( stream, &framesAvail, &xrun )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 4180

```

i have include portaudio.h and all file in portaudio/include but it still can't fix that :confused: help me please..

---

### Post by jaddle on 2013-04-06
You'll probably need to add -lm to link to the math library which has 'floor'. Also, put the libraries at the end of the command - for some reason, gcc cares about the order!

Try: 

```
gcc -o testing paex_saw.c libportaudio.a -lrt -lasound -lpthread -lm
```

By the way, I haven't actually tested the above line - I don't have this stuff on my computer right now, since it's been ages since I used it, but I expect the above line will work better.

---

### Post by forent on 2013-04-06
wooow.. it works...thanks a bunch...

Can't do this without you jaddle, thanks...
Thanks ubuntuforums.

---

