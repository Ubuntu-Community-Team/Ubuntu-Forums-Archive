---
title: "no sound"
date: 2012-03-25
forum: New to Ubuntu
---

### Post by biju1256 on 2012-03-25
Hi,

After booting there is no initial sound. I had checked the Speaker icon in the topbar. Sometime it starts as MUTE automatically. I have to manually unmute it and increase the volume.

Help me in resolving this problem.


rgds,
biju

---

### Post by kazztan0325 on 2012-03-25
Hi biju1256,

Sorry, I am also not sure how to resolve your problem, but I guess possibly following webpage would help you.

**"Howto- Resolve nosound problem on Ubuntu 12.04 and Older"**
[http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/]("http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/")

Regards,
kazz

---

### Post by biju1256 on 2012-03-25
Dear Kazz,

Done as mentioned but after restarting the system i dont hear any sound. But if i play any song in the VLC player it plays properly.

rgds,
Biju

---

### Post by kazztan0325 on 2012-03-25
Hmm..., it is strange...
You have no sound after rebooting, but VLC can play songs properly...

Sorry, Biju.
I have no idea to fix your problem at present.

---

### Post by d4m1r on 2012-03-25
What version of Ubuntu are you using? Are you using built in laptop speakers or is it a desktop and you have external speakers?

We need as much information as you can give us....

---

### Post by kazztan0325 on 2012-03-29
Hi biju1256,

Does your PC have dual-boot system?
(e.g. 'Windows 7' and 'Ubuntu 11.10')

Now I remember I have read following things somewhere else.

- If user turned wireless off on Windows side, and reboot PC as leaving it off then boot Ubuntu, it is possible wireless would not work on Ubuntu side.

- If user muted sound on Windows side, and reboot PC as leaving it is muted then boot Ubuntu, it is possible sound would start as mute on Ubuntu side.

Regards,
kazz

---

### Post by Curtis6767 on 2012-03-29
I posted a similar question[ here]("http://ubuntuforums.org/showthread.php?t=1947922").

I have decided that for now to leave well enough alone. I'd like to get the music at log in, but I've already spent too much time trying to resolve this minor annoyance.

---

### Post by biju1256 on 2012-03-30
Hi Kazz,

Yeah My PC has dual boot...(Win 7 and Ubuntu)
But i had never muted the sound or the speaker in windows. But the problem continues..

rgds,
Biju

---

### Post by idoitprone on 2012-03-30
> **biju1256 said:**
> Hi Kazz,

Yeah My PC has dual boot...(Win 7 and Ubuntu)
But i had never muted the sound or the speaker in windows. But the problem continues..

rgds,
Biju

you are not giving enough information. You have to give details of your current system since this problems can be divided up into three parts

Desktop environment is set to muted

Pulse audio 
boots muted

or

alsa is booting to muted.

Unless you provide details of your system, it can be anything, but I placing bets that alsa if screwing up again
[https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/352732](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/352732)
this bug report may give you a start

---

### Post by mal1958 on 2012-03-30
Biju, a few have asked for some details here. To help you we need to know some stuff about your computer and the flavor\version of Ubuntu you are using.

   Things like: type of computer (dell, HP, Asus, Acer, Gateway, Homebrew, or the like.
   Processor (AMD or Intell)and the type of proc.  (Athelon, athelon x2 x3, Phenom, for the AMD side, or Core 2, core 4, i3 i5 i7 for the Intell)
   Speed
   Memory
   Video and sound types (chipset if integrated with the MB or card make and model)
   Flavor of Ubuntu (Ubuntu, lubuntu, xubuntu, kubuntu, Mint, or the like)  And version of the OS (9.04, 9.10, 10.04, 10.10, Etc...)

   We can help you but only if you help us with as much detail as possible.  Welcome to the forum.

---

### Post by biju1256 on 2012-04-01
Hi Bunny,
I am not that tech savy...
I meant, after every boot the sound remains muted or there wont hear any sound.. so i have to manually increase the sound or in hv to unmute it.

I am using DELL Latitude.. with Intel Pentium.

hop this info would be useful.


rgds,
Biju

---

### Post by kazztan0325 on 2012-04-01
Hi Biju,

I guess, in your case it happens with something like a Bug of sound driver.

I found some bug reports on Launchpad.

**Pages matching ""DELL Latitude" "sound muted"" in Launchpad**
[https://launchpad.net/+search?field.text=%22DELL+Latitude%22+%22sound+muted%22&field.actions.search=Search]("https://launchpad.net/+search?field.text=%22DELL+Latitude%22+%22sound+muted%22&field.actions.search=Search")

Are there any bugs which are similar to your case in above?
If so (even if not), would you please tell us when you have time?
Thank you.

Kazz

---

### Post by Peripheral Visionary on 2012-04-01
For me the problem was PulseAudio. Removing it restored everything, relying on good ol' tried-and-true ALSA.

---

### Post by kazztan0325 on 2012-04-02
= This is a temporary off topic =

> **biju1256 said:**
> Hi Bunny,
...

Hi biju1256,
I think, you should not say "Hi _Bunny_," as greeting anymore, because there are other members: @d4m1r; @Curtis6767; @idoitprone; @mal1958; @Peripheral Visionary  on this thread, all of them would like to help you and posted their comments.
So you should say "Hi all" or "Hi there" etc when you greet on this thread, I think.

---

### Post by tushar maroo on 2012-04-02
open your terminal 
enter command: alsamixer
then press enter
press tab to go through all menus listed and from use of arrow keys you can set the default volume level for each sound related device there........
then press escape to close.
hope this will solve your problem :)

---

### Post by hughr2005 on 2012-04-05
try:

```

amixer set unmute

```

and set it to run at startup.

---

### Post by hughr2005 on 2012-04-05
by that I mean, add it to /etc/rc.d

---

### Post by hughr2005 on 2012-04-05
I'm not on an Ubuntu machine at the moment, so I can't check, but does anyone know if there is any references to alsamixer in /etc/rc.d?


Note: I may have gotten mixed up with my startup scripts, whether or not I have I mean the scripts that run on startup.

---

### Post by biju1256 on 2012-04-06
Hi,

Opened the terminal and used the code as stated i.e.alsamixer.
Tried increasing and decreasing the sound level but in vain.

Restarted the system, but the sound was in mute.


rgds,
Biju

---

### Post by kazztan0325 on 2012-04-10
Does anyone know other ways to be possible to solve biju1256's "no sound" problem?

---

### Post by idoitprone on 2012-04-10
maybe this thread may work

[http://www.mp3car.com/linuxice/138398-pulseaudio-defaults-to-mute-at-startup.html](http://www.mp3car.com/linuxice/138398-pulseaudio-defaults-to-mute-at-startup.html)

or this

[http://superuser.com/questions/73401/ubuntu-boots-up-in-mute](http://superuser.com/questions/73401/ubuntu-boots-up-in-mute)

then try this thread

[http://ubuntuforums.org/showthread.php?t=1145603&page=2](http://ubuntuforums.org/showthread.php?t=1145603&page=2)
problem when ubuntu botch pule audio config

---

### Post by Curtis6767 on 2012-04-10
> **Peripheral Visionary said:**
> For me the problem was PulseAudio. Removing it restored everything, relying on good ol' tried-and-true ALSA.

Peripheral, how did you determine that Pulse Audio was the problem? It is installed on my 12.04 system. What commands did you use to run a diagnostic for it?

Thanks

---

### Post by Peripheral Visionary on 2012-04-10
> **Curtis6767 said:**
> Peripheral, how did you determine that Pulse Audio was the problem? It is installed on my 12.04 system. What commands did you use to run a diagnostic for it?

Thanks

I'm a rookie, actually, but here's where I got the idea: My "Linux mentor" had Xubu 10.04 freshly installed and had **no sound at all** even after adding the multimedia codecs and such. But Linux Mint 9 Xfce - which is built on Xubuntu 10.04, worked perfectly out of the box. The difference? No PulseAudio. When he put Xubu 10.04 on my computer, I had the same issue and when he removed PulseAudio and rebooted, bingo. Trouble-free sound - even without the extra multimedia codecs. We concluded that PulseAudio "was the problem," but as rank amateurs I think it wasn't fair to jump to that conclusion... nevertheless, removing PulseAudio fixed his sound issue, and his.

---

### Post by idoitprone on 2012-04-10
> **Curtis6767 said:**
> Peripheral, how did you determine that Pulse Audio was the problem? It is installed on my 12.04 system. What commands did you use to run a diagnostic for it?

Thanks

it actually a known bug with pulseaudio. There is patch that been pulse by lennart poettry the creator of pulse audio to fix. Usually with pulseaudio, it is a configuration problem

---

### Post by Curtis6767 on 2012-04-11
Apparently I don't have Pulse installed, unless Alsa is part of Pulse.

When I clicked on the folder to see what was inside, it opened up alsa mixer.

I also have another file named 'alsa' so I'm not really sure what's going on there.

Thanks for the responses. Didn't mean to hijack the thread.

---

### Post by idoitprone on 2012-04-11
> **Curtis6767 said:**
> Apparently I don't have Pulse installed, unless Alsa is part of Pulse.

When I clicked on the folder to see what was inside, it opened up alsa mixer.

I also have another file named 'alsa' so I'm not really sure what's going on there.

Thanks for the responses. Didn't mean to hijack the thread.

A simple way to find out

```
dpkg -l | grep pulse
```

---

### Post by biju1256 on 2012-04-14
Hi all,

I found this link.

[http://ubuntuforums.org/showthread.php?t=1145603](http://ubuntuforums.org/showthread.php?t=1145603)

but unable to find the commands to be used.. pls help..

rgds,
Biju

---

### Post by kazztan0325 on 2012-04-19
Hi biju1256,

Please let us know the model name of your Latitude.
e.g. "Latitude _E5420_", "Latitude _E6520_", etc.
I think it ought to be printed on somewhere of surface of your machine.

And please let us know which version of Ubuntu are you using.
e.g. "Ubuntu _11.10_", "Ubuntu _11.04_", "Ubuntu _10.10_", etc.
I think you ought to know it if you have made dual-boot of your machine by your hands.

---

