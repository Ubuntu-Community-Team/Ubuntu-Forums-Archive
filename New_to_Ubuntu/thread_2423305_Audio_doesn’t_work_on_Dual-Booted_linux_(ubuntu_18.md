---
title: "Audio doesn’t work on Dual-Booted linux (ubuntu 18.04 and 19.04)"
date: 2019-07-20
forum: New to Ubuntu
---

### Post by zp1 on 2019-07-20
I am pretty new to the linux and dual booting so I will accept any new information. 

Yesterday I dual-booted my windows laptop Asus-UX433FA, and I started with installing Ubuntu 18.04. I am having some problems but main one is Audio one. I cant play any sound neither on speakers or headphones. I tried with reinstalling alsomixer and pulsefire(as i remember) but that did not help. 
Today I tried upgrading to 19.04 because I read somewhere that new version solves my problem. Update obviously didn’t help, and neither did same methods as above.

When I play video on youtube I hear some noises like scratching for 2 seconds and then everything muted.

Any suggestions?

---

### Post by Frogs Hair on 2019-07-24
Hello and Welcome

I don't have a solution, but the  fowling command will display information about the sound card/device.

```
lspci -v | grep -i audio
```

---

### Post by kesetyan on 2019-07-31
> **zp1 said:**
>  I cant play any sound neither on speakers or headphones. I tried with reinstalling alsomixer and pulsefire(as i remember) but that did not help

I faced a similar problem and searching the internet when I could not get sound from 'Line In', I found a solution that resolved the situation for me.  With luck, it might be what you need. 

My problem was caused by something called 'Loopback' not operating. To initiate loopback for the current session, open the terminal and type "[COLOR=#0000ff]**pactl load-module module-loopback**[/COLOR]" and press the 'Return' key (just type what I have shown in blue - don't include the double speech marks).

If you require loopback enabled automatically every time you boot the system then a simple scriptfile makes this possible as follows:
Open the terminal and type "[COLOR=#0000ff]**sudo sh -c ' echo "load-module module-loopback" >> /etc/pulse/default.pa '**[/COLOR]" and press the 'Return' key (again just type what I have shown in blue - don't include the leading and final double speech marks but include those within the blue text.  Depending how you have set up your system, you may have to enter your password in the terminal and press return after this command.

Good luck.

---

### Post by grahammechanical on 2019-08-06
Could you confirm that audio is actually switched on? Go to System Settings and open the Sound dialog. You might need to set the output volume to ON. You may have more than audio device and the wrong one may be activated.

On my machine I have onboard audio and I can also play audio through Audio Adapter that is part of the Graphic Adapter. When the earphones are plugged in they will show up as a device that can be selected in the Sound Device for sound output dialog.

Regards.

---

