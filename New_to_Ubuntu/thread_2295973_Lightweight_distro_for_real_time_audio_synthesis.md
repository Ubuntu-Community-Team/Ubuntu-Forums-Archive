---
title: "Lightweight distro for real time audio synthesis"
date: 2015-09-22
forum: New to Ubuntu
---

### Post by andrea79 on 2015-09-22
Hy everyone! Linux newbie here.

I'm planning a portable workstation for audio programming and real time audio synthesis (environments like Supercollider and PD) plus basic other tasks (web, mail, word processing). The machine will (probably) be a budget Asus laptop, X554LA-XO1236D [CPU i35005U, RAM 4gb, integrated Intel graphics]. Linuxwise i'm leaning towards **Lubuntu**, because:

* It's lightweight. I don't need fancy graphics and real time synthesis can become quite a burden on the machine.
* It's stable. Though i'm of unsure of the LTS (seem kinda old, mid-2014), i might be going for 15.04 and eventually upgrading to LTS 16.04 when will be available.
* While it's still user friendly, it should allow me to configure Jack2 as sound server, completely ignoring PulseAudio. As far as i understand most distros would allow to install Jack on top of their deamon server but that isn't acceptable for me, since it could cause problems with some complex audio routing i need to do. Likewise i've checked some of the audio-oriented distros available but they don't convince me. For example, Ubuntu Studio in full of programs i wouldn't use - like full-fledged DAWs, and Audacity is enough for capturing audio in this case - and still use PulseAudio as sound server.
* Being kinda of a Lite version of Ubuntu i should be able to add repositories from other distros quite easily.

At this point i still have several questions:

1) Am i understanding everything the right way?

2) Will Lubuntu allow me to do what i need in the sound area? I've been told to check if it's an ALSA only distribution, and while i know what ALSA is i don't know what it means to be an ALSA *only* distro.

3) What about realtime kernel? Jack has some nice tutorial about it but there is something i should be aware in this regard with Lubuntu?

4) In your opinion, am i making a good choice? Would you advise something different?

Thank you in advance for your time, have a nice day.

---

### Post by Vladlenin5000 on 2015-09-22
Hi and welcome.

All your questions have a simple answer: You're wrong, so wrong...

First of all, you don't need "lightweight" with such specs.
Secondly, why reinvent the wheel? We already have a nice official Ubuntu derivative aimed to - and equipped with all the tools for (and then more) - the tasks you mentioned: [Ubuntu Studio]("https://ubuntustudio.org/")  
Ubuntu Studio features the low latency kernel you're looking for plus it has by default the lightweight XFCE as the desktop environment.

---

### Post by grahammechanical on 2015-09-22
All official Ubuntu flavours use the same repositories as Ubuntu. We can install the same software whatever flavour of Ubuntu we use. We can also delete software. Lubuntu does not have pulseaudio installed by default.

[https://help.ubuntu.com/community/Lubuntu/Setup](https://help.ubuntu.com/community/Lubuntu/Setup)

See the heading: Problems with the interaction between PulseAudio & Jack. You may find that certain problems have been fixed in versions of Ubuntu Studio released since 2013, or may be not

[http://manual.ardour.org/setting-up-your-system/platform-specifics/ubuntu-linux/](http://manual.ardour.org/setting-up-your-system/platform-specifics/ubuntu-linux/)


[http://steve-conrad.com/blog/?p=45](http://steve-conrad.com/blog/?p=45)


Regards.

---

### Post by sandyd on 2015-09-22
> **andrea79 said:**
> Hy everyone! Linux newbie here.

I'm planning a portable workstation for audio programming and real time audio synthesis (environments like Supercollider and PD) plus basic other tasks (web, mail, word processing). The machine will (probably) be a budget Asus laptop, X554LA-XO1236D [CPU i35005U, RAM 4gb, integrated Intel graphics]. Linuxwise i'm leaning towards **Lubuntu**, because:

* It's lightweight. I don't need fancy graphics and real time synthesis can become quite a burden on the machine.
* It's stable. Though i'm of unsure of the LTS (seem kinda old, mid-2014), i might be going for 15.04 and eventually upgrading to LTS 16.04 when will be available.
* While it's still user friendly, it should allow me to configure Jack2 as sound server, completely ignoring PulseAudio. As far as i understand most distros would allow to install Jack on top of their deamon server but that isn't acceptable for me, since it could cause problems with some complex audio routing i need to do. Likewise i've checked some of the audio-oriented distros available but they don't convince me. For example, Ubuntu Studio in full of programs i wouldn't use - like full-fledged DAWs, and Audacity is enough for capturing audio in this case - and still use PulseAudio as sound server.
* Being kinda of a Lite version of Ubuntu i should be able to add repositories from other distros quite easily.

At this point i still have several questions:

1) Am i understanding everything the right way?

2) Will Lubuntu allow me to do what i need in the sound area? I've been told to check if it's an ALSA only distribution, and while i know what ALSA is i don't know what it means to be an ALSA *only* distro.

3) What about realtime kernel? Jack has some nice tutorial about it but there is something i should be aware in this regard with Lubuntu?

4) In your opinion, am i making a good choice? Would you advise something different?

Thank you in advance for your time, have a nice day.
[LIST=1]
[*]
[*] You are not restricted to distros without pulseaudio. Any ubuntu-based distro with pulseaudio can be converted to a pure jack2 setup with the following. I sometimes find this easier than piping audio through pulseaudio, then to jack2

To do:
```

sudo nano /etc/pulse/client.conf
```

In front of the line that has "autospawn = yes" in it, remove the semicolon, and replace "yes" with "no".

The file now looks like the following
```

# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, see <http://www.gnu.org/licenses/>.

## Configuration file for PulseAudio clients. See pulse-client.conf(5) for
## more information. Default values are commented out.  Use either ; or # for
## commenting.

; default-sink =
; default-source =
; default-server =
; default-dbus-server =

autospawn = no
; daemon-binary = /usr/bin/pulseaudio
; extra-arguments = --log-target=syslog

; cookie-file =

; enable-shm = yes
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB

; auto-connect-localhost = no
; auto-connect-display = no
```
Press control+x to save.

Now, we can install jack2 and qjackctl
```

sudo apt-get install jackd2 qjackctl
```

We also add a configuration file so that alsa-based apps have a place to route their sound
```
nano ~/.asoundrc
```

Copy and paste the following:
```
pcm.rawjack {
    type jack
    playback_ports {
        0 system:playback_1
        1 system:playback_2
    }
    capture_ports {
        0 system:capture_1
        1 system:capture_2
    }
}

pcm.jack {
    type plug
    slave { pcm "rawjack" }
    hint {
    description "JACK Audio Connection Kit"
    }
}
pcm.!default {
    type plug
    slave { pcm "rawjack" }
}
```

Press control+x to save.
Reboot, and start qjackctl. You should probably make it startup by itself by adding it to "startup programs" of whatever desktop environment you are using.
Now, configure qjackctl with your settings and sound card.

[*]Lubuntu uses the default kernel. You can install the lowlatency kernel which is called linux-image-lowlatency
[*]As mentioned above, your laptop is powerful enough to run even the heaviest desktop environments. There is no specific need for you choose a less graphically intensive distro. You will not get xruns unless you are maxing out the CPU.
[/LIST]
Side note: If that's intel audio, I recommend getting an external sound card if you want less than 64ms latency. Anything that's lower than that seems to start gathering xruns, though it might be this laptop.

---

