---
title: "[SOLVED] codec- installing them from the terminal..."
date: 2008-09-05
forum: New to Ubuntu
---

### Post by dmurat on 2008-09-05
hi all
a sticky thread suggests to paste this code ```
sudo apt-get remove gnash gnash-common icedtea-gcjwebplugin libflash-mozplugin libflashsupport mozilla-plugin-gnash openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar
``` for multimedia purposes to the terminal. but i face such an error ```
E: Couldn't find package non-free-codecs

``` and the only thing i need is the codecs... what can i do?

---

### Post by halitech on 2008-09-05
do you have the medibuntu repo enabled?

---

### Post by dmurat on 2008-09-05
i havent done anything manually to enable it. but i dont know if it is enabled automatically when ubuntu is first set up or something like that...how can i learn whether it is enabled or not? or how can i enable it?

---

### Post by halitech on 2008-09-05
its not set up by default so you will need to enable them to get things working. open a terminal and type (or copy/paste) them in

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by dmurat on 2008-09-05
it works now. thank you very much... codecs and other things are being installed. what does sudo stand for? and why did i have to enable medibuntu? what is it for? just wondered..

---

### Post by halitech on 2008-09-05
Glad its working for you :)

Sudo is short for SuperUserDo, it is the method Ubuntu uses to allow users to do root management tasks.

Ubuntu doesn't ship with codecs for legal reasons so they are stored on seperate servers so that is why you have to enable it and install them seperately

---

### Post by markharding557 on 2008-09-05
sudo is a command that allows a proccess to run as root(administator)and mediubuntu contains things which would get ubuntu sued if they included them by default

---

### Post by 7raTEYdCql on 2008-09-05
Sudo stands for "SUperuser DO", it basically empowers you to the administrator account.

When you enable the apt-get install command basically all that is downloading is getting saves in /var/cache/apt/arvhives. This directory is owned by '/'. Therefore to make any changes to roots account you need to take permission from it. Therefore you need to become the root. Or simply this is an administrative task.

---

### Post by Crafty Kisses on 2008-09-05
> **dmurat said:**
> it works now. thank you very much... codecs and other things are being installed. what does sudo stand for? and why did i have to enable medibuntu? what is it for? just wondered..

OK nice that everything worked out, please mark the thread as solved. :)

---

### Post by dmurat on 2008-09-05
thank you all very much for the help and the explanations, but one more question before marking it as solved =)) i downloaded the codecs and all but when i try to play a song from rhythmbox, there is no sound :\ i mean, the song is playing and the volume is set to the  highest but cant hear no sound :D anything i can do?

*by the way, i know these things sound sooo simple to some people and i would laugh if such question were asked me about windows, but linux is really something different and needs some effort spent to be friends =)

---

### Post by halitech on 2008-09-05
we all started at the same point, some just move along faster ;)


for the sound issue, open a terminal again and post the output of```
aplay -l
```

---

### Post by dmurat on 2008-09-05
here is the output =)) 
```
dmurat@mrt:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

---

### Post by halitech on 2008-09-05
good, you have results so things should be working. what kind of file were you trying to open?

---

### Post by dmurat on 2008-09-05
i plugged in my ipod and tried to play the song stored in the ipod. its an mp3 file

---

### Post by halitech on 2008-09-05
okay open alsamixer (Applications - Sound & Video - alsamixergui) and unmute everything

if alsamixergui is not installed, open a terminal again and type
```
sudo apt-get install alsamixergui
```

---

### Post by dmurat on 2008-09-05
ok i did what you just said.
before doing what you said, i heard the song i tried to play. but its really really low volume. you need to stick your ear to the device to hear it :D

---

### Post by halitech on 2008-09-05
did you find anything muted or with the volume really low?

---

### Post by dmurat on 2008-09-05
Master, PCM, Mic, Mic Boost and Internal Mic are full on volume right now. but the Capture, Mix and External Amplifier are muted and cant turn up their volume (disabled)

---

### Post by halitech on 2008-09-05
you don't want them muted. unmute everything except the mic and then try again

---

### Post by dmurat on 2008-09-05
the thing is, i cant. they are already unmuted (Capture, Mix, External Amplifier) and i cant change it. it is like disableed. you cant play with their controls, cant mute or unmute...anyway, i give up =(((

---

