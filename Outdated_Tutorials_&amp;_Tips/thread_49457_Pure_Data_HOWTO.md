---
title: "Pure Data HOWTO"
date: 2005-07-16
forum: Outdated Tutorials &amp; Tips
---

### Post by damotor on 2005-07-16
Hi.
I've successfully installed Pure Data under ubuntu, here are the step you've to follow in order to get it working:
1st: Install the required packages in order to use alsa sound system:
```
sudo aptitude install libesd-alsa0 alsa-oss
```
Now, configure your system to use it:
```
$ sudo gedit /etc/asound.con
```
if you have an AC'97:
```
# .asoundrc for use with ALSA and the dmix plugin, for ALSA-level
# software mixing across all apps.
#
# http://alsa.opensrc.org/index.php?page=AlsaSharing
# http://alsa.opensrc.org/index.php?page=DmixPlugin

pcm.dmix0 {
    type dmix
    ipc_key 219345           # any unique number here
    slave {
            pcm "hw:0,0"
            period_time 0
            buffer_time 0
            period_size 2048    # jm: much smoother than 1024/8192!
            buffer_size 32768
            rate 48000
    }

    bindings {
        0 0   # from 0 => to 0
        1 1   # from 1 => to 1
    }
}

pcm.dsp0 {
  type plug
  slave.pcm "dmix0"
}

# this makes native ALSA apps default to using dmix
pcm.!default {
  type plug
  slave.pcm "dmix0"
}

ctl.dsp0 {
  type hw
  card 0
}

ctl.!default {
  type hw
  card 0
}
```
```
sudo gedit /etc/libao.conf
```
And change ```
default_driver=esd
``` and put insted ```
default_driver=alsa
```
Well, at this time your system is configured, but before running Pure data you need to load some modules so put this inside Puredata.sh:
```
#!/bin/bash
modprobe snd_seq
modprobe snd-pcm-oss
pd
```
And whenever you want execute it just type in a terminal sudo PureData.sh or create a launcher into your desktop.

Happy Creation ;-)

---

### Post by univac on 2007-10-30
where is Puredata.sh located?

---

