---
title: "No menu bar, just desktop with wallpaper"
date: 2015-03-06
forum: New to Ubuntu
---

### Post by joseph50 on 2015-03-06
Hello everyone,

I'm giving Linux a try after a 15 year hiatus from it. I've got an older Toshiba Satellite 305D laptop that I thought ubuntu would be able to breathe a little life into.

Anyway, I installed the latest version of ubuntu from the main website, and did the recommended updates and installs... and when I boot up, all I get is a blank desktop: no application bar, no nothing. When I right click, I can create a folder, so there's that. I've been able to access a terminal application, but there are also no controls to close the window or resize it.

I've done some searching on the forums and tried resizing my screen resolution, fixing possible broken installs, reinstalling/fixing "Unity" (I'm not quite sure what Unity is, but it comes up in every thread I've seen about this), making another Admin account and logging in with it, but nothing seems to work.

Any suggestions? Thanks so much!

Joseph

---

### Post by Frogs Hair on 2015-03-06
Hello and Welcome

Can you get terminal access using Ctrl+Alt +T ? Another thing to try is log into the guest session which requires no password and if that works log out and try your user account again.

---

### Post by kerry_s on 2015-03-06
it's probably that opengl error.
run this in terminal:
gsettings reset org.compiz.core:/org/compiz/profiles/unity/plugins/core/ active-plugins
sudo reboot

if that don't work try:
dconf reset -f /org/compiz/
sudo reboot

---

### Post by DuckHook on 2015-03-06
Your laptop is a low-powered one with integrated graphics running at 300-350 MHz and stealing its VRAM from system memory while maxing out at 512 MB but may be as low as 128MB depending on what Toshiba chose to set it at. In short, it's not really up to the job of giving you a good video experience with Unity or modern 3D demands.

I would suggest installing Xubuntu or Lubuntu on this machine, which should not only solve the broken desktop problem, but also give you a faster and more responsive user experience.

---

### Post by JeQhdMD on 2015-03-07
+1 on Duckie's post.    If your laptop doesn't have at least 512 meg of ram, even Xubuntu may run slow . . . if that be the case, Lubuntu or Bodhi v3. (based on Ubuntu core, but running the very lightweight e19) desktop may be your best bet and a good place to start.

See here:  [http://www.bodhilinux.com/](http://www.bodhilinux.com/)

---

### Post by kerry_s on 2015-03-07
> **DuckHook said:**
> Your laptop is a low-powered one with integrated graphics running at 300-350 MHz and stealing its VRAM from system memory while maxing out at 512 MB but may be as low as 128MB depending on what Toshiba chose to set it at. In short, it's not really up to the job of giving you a good video experience with Unity or modern 3D demands.

I would suggest installing Xubuntu or Lubuntu on this machine, which should not only solve the broken desktop problem, but also give you a faster and more responsive user experience.

googling the specs says it's:
amd sempron 2ghz x 2
2->4gb ram
ati graphics 512mb

plenty strong to run unity.

---

### Post by DuckHook on 2015-03-07
*kerry_s* is right. I stand corrected.

I initially thought the chokepoint would be the 3100 video chip, but further checking of that chip shows that it's a derivative of HD3200 which should be strong enough to run Unity. Sorry for mix-up.

You may still wish to look at your documentation to see:

A. How much DRAM Toshiba assigned to VRAM, and
B. How much DRAM you have overall.

256 MB VRAM is acceptable for Unity, all 512 would be great, but 128 would not give good experience. You may be able to increase VRAM allocation in BIOS.

---

### Post by llamabr on 2015-03-07
I can't answer any of your questions.  But on old hardware, I run windowmaker, which runs much faster, and is suitable for old hardware.  Windowmaker has a livecd, which you canhttp://wmlive.sourceforge.net/http://wmlive.sourceforge.net/

---

### Post by grahammechanical on 2015-03-07
May I suggest something? Right click the wallpaper and select Change Desktop Background. That will open System Settings. From there you can get to Software & Updates. Then open the Additional Drivers tab and select the open source video driver.

It could be that AMD/ATI have dropped support from their video driver for that video adapter. The latest versions of Ubuntu install the latest stable versions of proprietary video drivers when we tick the box "Install third party software." If you need a proprietary video driver you may need to search the Ubuntu Software Centre for an older, legacy driver.

Regards.

---

