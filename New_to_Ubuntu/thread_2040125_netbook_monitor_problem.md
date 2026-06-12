---
title: "netbook monitor problem"
date: 2012-08-10
forum: New to Ubuntu
---

### Post by kytx2012 on 2012-08-10
Hi folks! I am rather new to linux and experience a very weird problem. When I turn on my netbook the monitor turns off at the very beginning of the boot process. It's not blank, it is TURNED OFF, the backlight is not working and no image on the screen. However the systems starts fine, I can blindly type my login and password and get into system (can hear greeting sound).

Now the weird part:
When I press netbook's power off button, thescreen turnes on and I can see my xubuntu shutting down)))

When I boot xubuntu from livecd it works fine, even with no lags (which is a great bonus - see below why)
My netbook is ASUS eee PC 1201HA. It has an embedded graphics card Intel GMA 500. It does not support OpenGL well, so previously Ubuntu 10.10 (GNOME 2) and PC BSD 9.0 with Xfce were badly lagging, but working. Now I finally found a distro to work smoothly on this machine, but can not use it!

Version of Xubuntu I try is 12.04 lts. I'm dual-booting with Windows 7 (ever has, no problem with other linux/bsd systems), use GRUB2

Any ideas, please?

pardon my English, it's not my first language.

---

### Post by irv on 2012-08-10
Do you have a port on it for an external monitor? The reason I ask is could it be possible that it is sending the video signal to it and not to the netbook screen?
And is it possible that you have a hot key on the keyboard to switch between external and onboard video? Just some thoughts.

---

### Post by kytx2012 on 2012-08-10
Hi irv, hotkeys seem to work only in Windows. I tried pressing it. I have no monitor available to test signal on VGA port right now. Can you think of a config file to make it use laptop monitor as the primary one? I would use live cd to edit it.

---

### Post by irv on 2012-08-10
> **kytx2012 said:**
> Hi irv, hotkeys seem to work only in Windows. I tried pressing it. I have no monitor available to test signal on VGA port right now. Can you think of a config file to make it use laptop monitor as the primary one? I would use live cd to edit it.

I am not sure. Take a look at this and see if this helps.
[http://kevin.vanzonneveld.net/techblog/article/change_more_display_settings_in_ubuntu/]("http://kevin.vanzonneveld.net/techblog/article/change_more_display_settings_in_ubuntu/")

---

### Post by kytx2012 on 2012-08-10
that article is about a gui tool for changing advanced xorg settings. I cannot use it without my monitor working. It's late now. Tomorrow I'll try to use xorg.conf from livecd for my installation on hard disk.

---

### Post by kytx2012 on 2012-08-12
I found no xorg.conf neither in installation nor in livecd O_o
I also tried Ubuntu 12.04 and there is same problem, even worse: when I shut down the monitor is still dark. Assuming irv was correct in his guess about putting output signal to external port instead of built-in monitor, I will try to change it by editing config files...

---

### Post by kytx2012 on 2012-08-13
I tested my laptop with external monitor today. Now I see picture on both monitors, but picture on the built-in monitor is shifted to the left. I think the problem might be in motherboard or video settings or that sort of stuff.

---

### Post by irv on 2012-08-13
> **kytx2012 said:**
> I tested my laptop with external monitor today. Now I see picture on both monitors, but picture on the built-in monitor is shifted to the left. I think the problem might be in motherboard or video settings or that sort of stuff.

I have one flat LCD in my house hook on an old PC and every time I run Ubuntu 10.10 on it, it boot with just part of a screen. Now the external LCD has a refresh setting on it so I go to the monitor's menu and do a refresh and it fixes it. Now I know your laptop screen does not have a menu like that, but maybe there is a way to refresh the screen. The only thing I could see was under Monitor settings there is a Launcher placement where you can switch between All displays and laptop and a Sticky edges on or off.
If there is a refresh command you could issue I don't know. Maybe someone else does?

---

### Post by kytx2012 on 2012-08-13
I'll try it tomorrow, today I only had time for a brief test. By the way, just an observation, I installed Mint 13 with Cinnamon, which is a Ubuntu derivate, and it detected my screen ok (didn't detect external screen though =)) )

Back to xubuntu. I haven't found so far any guide how to manually fix this setting, only using gui tools.

---

### Post by irv on 2012-08-13
> **kytx2012 said:**
> I'll try it tomorrow, today I only had time for a brief test. By the way, just an observation, I installed Mint 13 with Cinnamon, which is a Ubuntu derivate, and it detected my screen ok (didn't detect external screen though =)) )

Back to xubuntu. I haven't found so far any guide how to manually fix this setting, only using gui tools.

After doing a little more investigating if you don't find an answer I would file a bug report. This can be done by issuing a ubuntu-bug at the command and follow the screen prompts. do this while you have a half screen and take some screen shots to attach.

---

### Post by kytx2012 on 2012-08-14
I had a closer look at the problem tonight and shortly what I can say is:
xubuntu does not recognize my built-in monitor right, it likely treats  it as a secondary monitor and external vga port - as the primary  monitor.
when booted with external monitor, I have picture cloned on both  screens, my built-in monitor has the only available resolution of  1024x768 (looks like shifted to the left), but the widescreen external  monitor has the right resolution on it
After booting I can unplug the external monitor and the internal monitor will keep working fine (1024x768 ) until reboot
I ave no way to re-detect monitors in monitor settings window
livecd works fine, the problem appears every time I try to boot from hdd

irv, if you know how to file a bug report you are very welcome to do it, I will provide you with any details you need.

PS: Mint 13 (Cinnamon and Xfce editions tested), which is a close  derivate of Ubuntu, recognizes my internal monitor just fine. Shame on  you, Canonical!

---

### Post by irv on 2012-08-14
> **kytx2012 said:**
> I had a closer look at the problem tonight and shortly what I can say is:
xubuntu does not recognize my built-in monitor right, it likely treats  it as a secondary monitor and external vga port - as the primary  monitor.
when booted with external monitor, I have picture cloned on both  screens, my built-in monitor has the only available resolution of  1024x768 (looks like shifted to the left), but the widescreen external  monitor has the right resolution on it
After booting I can unplug the external monitor and the internal monitor will keep working fine (1024x768 ) until reboot
I ave no way to re-detect monitors in monitor settings window
livecd works fine, the problem appears every time I try to boot from hdd

irv, if you know how to file a bug report you are very welcome to do it, I will provide you with any details you need.

PS: Mint 13 (Cinnamon and Xfce editions tested), which is a close  derivate of Ubuntu, recognizes my internal monitor just fine. Shame on  you, Canonical!
I can't file a bug report because it has to be done on the machine the bug is on. When you type ubuntu-bug it will collect information and send it to launch pad. Please read this webpage.
[https://help.ubuntu.com/community/ReportingBugs/]("https://help.ubuntu.com/community/ReportingBugs/")
This is the only way this problem will be fixed. They will keep you informed via email.

---

