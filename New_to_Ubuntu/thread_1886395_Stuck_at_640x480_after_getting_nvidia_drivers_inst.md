---
title: "Stuck at 640x480 after getting nvidia drivers installed 11.10 (fx5200)"
date: 2011-11-24
forum: New to Ubuntu
---

### Post by mcfee on 2011-11-24
After a fresh install of 11.10 and updating everything 
Ubuntu asked me to ,I installed nvidia drivers,  After rebooting i'm stuck at 640x480 resolution and cant detect my monitor, I read something about hwinfo and entered it but the info here I cant edit it, i'm new to this whole terminal thing in linux. They said something about changing the hz according to my monitor but i cant scroll up to edit this info:confused:

im using a fx5200 gpu
dell optiplex gx260

please any help to get me back on track with the ability to select a higher resolution .

ps that hwinfo might not be whats right for me i dont know if you need me to copy info from my terminal please tell me how i can copy paste this info as the ctrl+c from windows doesnt seem to work much thanks.

*Im helpless here and for some reason this topic isn't as popular as others*.

Does anyone have any Ideas?

---

### Post by wolfen69 on 2011-11-24
Do
```
gksu nvidia-settings
```
and see if you can set your resolution there. Hit apply, then save.

---

### Post by mcfee on 2011-11-24
-Gtk warning* cannot open display- after reading some basic tutorials it also told me to use gksu gedit /etc/x11/xorg.conf but I get the same warning.

---

### Post by wolfen69 on 2011-11-24
Try [this.]("http://www.linuxquestions.org/questions/linux-newbie-8/gtk-warning-cannot-open-display-187901/#post965556")

---

### Post by mcfee on 2011-11-24
sadly no, maybe it has to do with it not being gnome as was mentioned in that post not sure.

echo "export DISPLAY=:0" >> ~/.bashrc or export DISPLAY=:0 not a valid identifier as of now im stuck in 640x480 thats with drivers installed but when uninstalled all is well but i need to use the gpu so the workaround was meant for me to edit some numbers in the monitor section of that gksu but I still cant get to that place . I understand linux is a tough os to troubleshoot but man spent hours on this to no avail .:sad:

---

### Post by mcfee on 2011-11-24
[LEFT]Does everyone just lurk around here and never post.
[/LEFT]

---

### Post by wolfen69 on 2011-11-25
> **mcfee said:**
> [LEFT]Does everyone just lurk around here and never post.
[/LEFT]
We are all volunteers here and do the best we can. Please be patient and continue to find answers on your own in the meantime. If you need someone to immediately help you, you can always get [paid support]("http://www.ubuntu.com/business/desktop/services"). Thanks.

---

### Post by Iowan on 2011-11-25
> **mcfee said:**
> [LEFT]Does everyone just lurk around here and never post.
[/LEFT]
Do you REALLY want unhelpful posts just to pad the thread?

---

### Post by fantab on 2011-11-25
What is the Maximum or optimal resolution of your MONITOR? 

Lets say it is 1920x1080.

We first need to find out if your system or driver supporting higher resolutions. If it is then perhaps we can force it.

Run the following commands in the terminal.

```
sudo apt-get install xresprobe

sudo ddcprobe
```**If you find your desired resolution then proceed as below or wait until you find the solution to your issue.**

Then find out the name of your interface, like VGA1 or HDMI1 or HDMI2 etc. Also make note of the Resolution and refresh rate. (I assume you know these already).

```
$xrandr
```Now replace the resolution and refresh rate in the command below with your own.

```
$gtf 1920 1080 59.9
```From the output copy every thing after the word "Modeline"
What you copy will be something like this: [COLOR=DarkRed]"1920x1080_59.90"  172.51  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync[/COLOR]

Having done that run this one after another in Terminal using your outputs.

```
$xrandr --newmode "1920x1080_59.90"  172.51  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync
$xrandr --addmode HDMI2 "1920x1080_59.90"
$xrandr --output HDMI2 --mode "1920x1080_59.90"
```This should give you your desired monitor resolution. This is only temporary. 

To make this permanent you will have to write a script. 

Let us know if this works and I will post the script.

---

### Post by mcfee on 2011-11-25
The $xrandr part gave me cant open display. so I skipped it moved on to $gtf got all the info copied it when I got to $xrandr --newmode  "1280x1024_64.00" and so on I pressed Enter and it came up Command not found as well as Cant open display. When I do try these fixes I'm installing drivers then uninstalling them after it doesn't work to revert to normal this Fx5200 GPU and the 173 drivers have a problem and it seems you have to manually enter your supported resolutions and what not. So far do you know why those commands are unavailable.

Thanks.

---

### Post by fantab on 2011-11-25
Post the output of 

```
lspci
```

Also tell us in detail how you've installed your Graphics Driver.

---

### Post by Zibodiz on 2011-12-13
Hi all,
I'm a bit of a noob with Ubuntu, but I've been working with it for a couple years.  I've run into this same problem.  I've done a lot of forum-hopping, and can't seem to find anything that helps.  When Ubuntu was first installed, the graphics defaulted to a resolution like 1024x768 or something, but after enabling the proprietary driver (NVIDIA accelerated graphics driver [version 173]) and restarting, the resolution reset to 640x480, and I haven't been able to adjust it further.  Everything I've encountered matches the OP.  I've tried switching to the version 96 driver via the "Additional Drivers" dialogue in the System Settings menu, but that made no difference.  I then disabled all of them, and still no difference.  I really don't care about 3d acceleration, as this machine is only for getting online & working in LibreOffice Writer, so I'd be okay with the generic driver that defaults on the system.  I can't seem to get it back, though -- when I disable all of the proprietary drivers, I am still limited to 640x480.  Although I should point out that if you disable the proprietary drivers, xRandR works.  If any of the drivers are enabled, I get the "Cannot open Monitor 0" (or something like that)... any ideas?  I'm considering just reinstalling Ubuntu and leaving the graphics drivers alone.
Thanks for all your help!

---

### Post by norite on 2012-06-08
BUMP

I'm having exactly the same problem - I just installed a nvidia geforce 6200 512Mb card today, installed the drivers and i'm stuck with a bloody 640*480 desktop been trawling forums all evening, installing, reinstalling, rebooting. Before this i had an ATI rage 128Mb and it worked just great.

This incredibly frustrating and annoyingly stupid. Help please. i have other things i need to be doing.

I have noticed, when i get the initial kubuntu startup screen, it seems to be the right resolution, but as soon as it gets to the log in screen it goes to 640*480

---

### Post by fantab on 2012-06-09
Post Deleted: I was trying to post, but not here.

---

### Post by pickledeggs on 2012-09-16
> **fantab said:**
> What is the Maximum or optimal resolution of your MONITOR? 

Lets say it is 1920x1080.

We first need to find out if your system or driver supporting higher resolutions. If it is then perhaps we can force it.

Run the following commands in the terminal.

```
sudo apt-get install xresprobe

sudo ddcprobe
```**If you find your desired resolution then proceed as below or wait until you find the solution to your issue.**

Then find out the name of your interface, like VGA1 or HDMI1 or HDMI2 etc. Also make note of the Resolution and refresh rate. (I assume you know these already).

```
$xrandr
```Now replace the resolution and refresh rate in the command below with your own.

```
$gtf 1920 1080 59.9
```From the output copy every thing after the word "Modeline"
What you copy will be something like this: [COLOR=DarkRed]"1920x1080_59.90"  172.51  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync[/COLOR]

Having done that run this one after another in Terminal using your outputs.

```
$xrandr --newmode "1920x1080_59.90"  172.51  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync
$xrandr --addmode HDMI2 "1920x1080_59.90"
$xrandr --output HDMI2 --mode "1920x1080_59.90"
```This should give you your desired monitor resolution. This is only temporary. 

To make this permanent you will have to write a script. 

Let us know if this works and I will post the script.

Hi, I had the exact problem and this worked, what is the script?

---

### Post by fantab on 2012-12-27
The Script is [**HERE**]("http://ubuntuforums.org/showpost.php?p=11503588&postcount=4").

---

