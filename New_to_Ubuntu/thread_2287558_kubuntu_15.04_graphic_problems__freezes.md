---
title: "kubuntu 15.04 graphic problems / freezes"
date: 2015-07-20
forum: New to Ubuntu
---

### Post by z-mail-i on 2015-07-20
Hello Community,

i have switched to kubuntu about 2Months ago.
my System is:
HW:
 DELL LATITUDE E6510
processor: Intel Core i7-720QM (1.6GHz, 6M cache)
graphic: 512MB Nvidia Quadro NVS 3100M Graphic Card
SW:
Kubuntu 15.04 64bit

sometimes i have some wired graphical problems:
shortly after i booted the system the animations for firefox page-scrolling or application-window switching are buggy -
it seems that the display is not repainted everytime it should - so it flickers or some parts of the screen does not update until i move the window or the mouse courser of this area.
if i normally shutdown and restart the computer its all back to normal.

the second wired thing that sometimes happens is that the computer freezes - so it does not react on keys - but audio or a skype call continus to play/work. also the mouse cursor does move. but nothing else reacts.
up till now the only way i know to get out this state is to hard-shutdown (with holdiing the powerbutton long).

i don't know if the mentioned problems are related...

iam realtive new to the (k)ubuntu / linux world. but iam familiar with basci command-line work.

so my main question is - how to start debugging this?
what are possible ways to get nearer to the problem?

thanks for your help

sunny greetings
stefan

---

### Post by z-mail-i on 2015-07-23
Hello Community,

today i had about 6 freezes.
most of them occurred when i was working on some libreoffice (original openoffice) calc sheets -
the behaivor was the same as previous written:
screen freezes - mouse cursor is moveable -
 the (audio) song from webpage opend in firefox is playing normally till end then it stops (so the new loading of a song does not work)
it seems that no key-strokes or mouse clicks are working.
--> Is there a Special Key-Combi like the Ctrl + Alt + Delete in Windows?

eventually it has something to do with Java? (as fare as i know LibreOffice runs in the JRE)

the System is up to date with all normal Software Center updates.

my graphic card is:
```
 [FONT=monospace][COLOR=#000000]stefan@stefan-latitude:~$ lspci | grep VGA [/COLOR]
01:00.0 VGA compatible controller: NVIDIA Corporation GT218M [NVS 3100M] (rev a2)[/FONT]
```

hopefully someone can give me a tip how to find the reason for this behaviour.

sunny greetings
stefan

---

### Post by sgian on 2015-07-24
Have you tried the proprietary driver for your graphics card?  Sometimes that can fix graphics issues.

If trying the proprietary driver doesn't fix the issue, then I suggest using the long term support version of Ubuntu.  The most recent is Ubuntu 14.04 LTS.  It is supposed to be more stable and is supported for a longer time than the regular releases, and it probably has better support for your older hardware.  Not everything can be supported, so when they add support for new hardware on new kernels, sometimes to save space they have to drop support for older hardware that is no longer used as much.  If 14.04 doesn't work, try the previous LTS version, one of them will have your hardware supported.

---

### Post by Vladlenin5000 on 2015-07-24
> **sgian said:**
> Have you tried the proprietary driver for your graphics card?  Sometimes that can fix graphics issues.

+1

Your graphics chips seems to be one of those that really need it...

---

### Post by z-mail-i on 2015-07-27
Thanks for your suggestions sgian and Vladlenin5000!

i will try to switch to the proprietary driver.

to do this i think the right way is :
system settings - Driver Manager -
than it will search for possible options - and let you choose one of this:
[ATTACH=CONFIG]263416[/ATTACH]
i will select and change to the recommend one.
and will report back if it worked.

iam just curios about this - because sometimes it just works for days without problems (with the nouveau driver)....
is there some logfiles or other places where i can look what failed in the events i described above?
(i just want to learn what is going on inside of the system)

sunny greetings
stefan

---

### Post by z-mail-i on 2015-07-27
Hey :-)
i applied the driver selection and restarted my system - 
now i got some DPI problems.
all the fonts are a huge  amount to big..
i found a forum reply that seems to solve this -
but it is for an older os version and the config file to change is not there anymore..
[http://ubuntuforums.org/showthread.php?t=2201820&p=13039317#post13039317](http://ubuntuforums.org/showthread.php?t=2201820&p=13039317#post13039317)
in this it is mentioned to force the dpi settings to 96DPI with and change in 
```
/usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
```
but i only have 
```
stefan@stefan-latitude:/usr/share/lightdm/lightdm.conf.d$ ls -l
total 8
-rw-r--r-- 1 root root  43 Apr 14 11:03 40-kde-plasma-kf5.conf
-rw-r--r-- 1 root root 164 Jul 31  2014 90-nvidia.conf
```

so i don't know where to add the dpi option.. (non of those two files have the xserver-command=X in them.)

[edit]
i have tested to what happens if i set 
System Settings - Fonts - Force Font DPI: 96
and restarted.
most of my applications seems back to normal.
but (up till now - only) my FileManager 'Double Commander' has a problem with this - in some way it only uses the system settings and the force setting gets not applied to some of the views - so it has some big fonts in the file windows...
work-around is to set the font size to smallest possible value (6) in the program configuration..
[/edit]

second thing i found is 
[https://www.mythtv.org/wiki/Specifying_DPI_for_NVIDIA_Cards](https://www.mythtv.org/wiki/Specifying_DPI_for_NVIDIA_Cards)
but i don't know if that is the right approach for a normal system..

hopefully someone can help me with this.

sunny greetings
stefan

---

