---
title: "Extend battery life?"
date: 2014-05-13
forum: New to Ubuntu
---

### Post by sc0tty2 on 2014-05-13
new to ubuntu - best tweaks???

basically I have moved over from windows xp since it's no longer supported. I'm running a i7, 6gb ram and 500GB HDD on my laptop. the battery is okay but I want to know the best tweaks that I can do to get the most out of my battery and ubuntu.

I have searched but there's a lot of misguided information. I have had a look on google too.

what are the best tweaks that I can do to extend my battery life?

TL:DR - best tweaks for ubuntu and laptop battery life.

thank you. :)

---

### Post by philinux on 2014-05-13
Welcome to the forums,

Number 1, turn the brightness down. Makes a huge difference.

I know it's pretty obvious.

---

### Post by sc0tty2 on 2014-05-13
thanks for your reply.

this is what I have done so far...

1: turned down the brightness down to 0.
2: uninstalled amazon.
3: only installed apps I need: XBMC, VLC, Gimp, Firefox.
4: turned off online search through unity.
5: turned bluetooth off.
6: turned off wifi.

---

### Post by matt_symes on 2014-05-13
Hi

Check out powertop. Make sure you get a newer version.

You may be able to find it in the software center or to install it from the terminal

```
sudo apt-get install --install-suggests  powertop
```

This is on 14.04

```
matthew-S206:/home/matthew:4 % powertop --version

PowerTOP versionv2.5, compiled on Nov 27 2013
matthew-S206:/home/matthew:4 %
```

Using that program, you can check out power usage, wake-up events, and tweak various settings.

*"--install-suggests*" above will also install cpufrequtils and laptop-mode-tools along with a bunch of dependencies.

cpufrequtils and laptop-mode-tools are worth having a look at as well. cpufrequtils allows you to set cpu frequencies.

Personally i have a script configure for my machine that i run when i need to conserve battery life.

Kind regards

---

### Post by sc0tty2 on 2014-05-13
again, thanks for the reply. 

just installed powertop with the command you said, ran "sudo powertop" and it's saying this:

[img]http://i.minus.com/iWxeekWkAcQf2.png[/img]

there's a load more if I scroll down, 400 etc numbers.

---

### Post by matt_symes on 2014-05-13
Hi

Move along to the tunables tab. There you can set some *cough* tunables :)

Kind regards

---

### Post by sc0tty2 on 2014-05-13
okay, done that.

turned them all to good but left my usb mouse and keyboard to bad. will change that when not running them.

anything else????

---

### Post by philinux on 2014-05-13
Check the hours left now in the battery indicator top right. Keep an eye on that now and again see what you're getting.

Just with brightness turned down to mid level here on an acer 1410 i can get up to 6 hours.

---

### Post by sc0tty2 on 2014-05-13
okay. thank you!

I have changed the tunables to "good" in powertop but it's still showing my webcam is being used. it says <r> to activate/refresh but how do I refresh? I'm not sure what to press.

this is amazing, really fast replies! thank you!!

edit:

it's much better now.

all I have to remember is to keep setting the "tunables" off when I'm on the battery.

this is what I have done so far.....

1: turned down the brightness down to 0.
2: uninstalled amazon.
3: only installed apps I need: XBMC, VLC, Gimp, Firefox.
4: turned off online search through unity.
5: turned bluetooth off.
6: turned off wifi.
7: removed USB mouse.
8: removed USB keyboard.
9: turned on all "good" with tunables.
10: install CPU frequency and set it to 0.80ghz.

if there's anything else, please let me know. :)

---

### Post by matt_symes on 2014-05-13
Hi

Have a read up on laptopmode-tools. It is a set of tools for laptop power saving amongst other things. 

You will lose the teaks you have made in powertop unless you save them.

What you need to be looking out for are stability issues.

You can also do things like force your chip into the lowest frequency settings. This will not step up the cpu frequency even if the kernel thinks it may be needed. You can use indicator-cpufreq for this.

```
sudo apt-get install indicator-cpufreq

```
Kind regards.

---

### Post by sc0tty2 on 2014-05-13
thank you!

I have tried lapto-mode-tools before but I wasn't too share what to do with them.

I have enabled all "power top's" tunables but don't know how to save them permenantly. any idea? google hasn't helped. I followed ^ but it didn't work.

any more help would be awesome.

you guys are amazing! thank you. :)

edit: I have set CPU frequency to 0.80. I'm sure it'll change when I'm on my battery but I'll just change it once I'm on the battery.

again, thank you.

---

### Post by su:bhatta on 2014-05-13
This has always given me good support :
[http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html](http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html)

---

