---
title: "Ubuntu 14.04, no sound and sound device listed with realtek sound card"
date: 2015-09-24
forum: New to Ubuntu
---

### Post by dengxinyue0420 on 2015-09-24
Hi,

I just installed Ubuntu 14.04 LTS, and also dual boot Windows 7. My computer has a realtek HD sound card. In Windows, they work fine.
However, in Ubuntu, there is no sound at all. (connected with a headphone)
Firstly, there is no devices showed in setting>sound, neither in input nor output.
Then I checked cards by running 
```
aplay -l 
```
The result is 
```

**** List of PLAYBACK Hardware Devices ****card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I guess this is because I have a monitor connected to NVidia graphic cards, but my monitor doesn't have built-in speakers.
So I try to install linux driver of Realtek HD sound cards, from Realtek website. The version I downloaded is 3.0
But I failed to compile it, I got following error when I tried to run make:
```

/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/pcm_native.c: In function ‘snd_pcm_file_fd’:
/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/pcm_native.c:1647:2: error: implicit declaration of function ‘fget_light’ [-Werror=implicit-function-declaration]
  file = fget_light(fd, fput_needed);
  ^
/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/pcm_native.c:1647:7: warning: assignment makes pointer from integer without a cast [enabled by default]
  file = fget_light(fd, fput_needed);
       ^
/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/pcm_native.c: In function ‘snd_pcm_lib_mmap_iomem’:
/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/pcm_native.c:3453:26: warning: unused variable ‘runtime’ [-Wunused-variable]
  struct snd_pcm_runtime *runtime = substream->runtime;;
                          ^
cc1: some warnings being treated as errors
make[3]: *** [/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/pcm_native.o] Error 1
make[2]: *** [/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore] Error 2
make[1]: *** [_module_/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.19.0-28-generic'
make: *** [compile] Error 2

```

Is there anyone know how to fix this? Thanks in advance!

---

### Post by android4682 on 2015-10-08
Yeah it's a pain in the butt when Ubuntu doesn't want to give you audio.
Did you tried all of this? [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by makefool163.com on 2016-04-19
I had complied success, but no effort also.

this is how to complie realtek code :

1,follow the "readme" to unzip code pack;
2,edit the file "./alsa-driver-RTv5.18/alsa/include/adriver.h"
commit last ifdefine block, just like "#if LINUX_VERSION_CODE < KERNEL_VERSION(3,7,0)" and "#endif"
3,prepare by "./configure --with-card=had-intel"
4,"make" it
5,"sudo make install"

---

