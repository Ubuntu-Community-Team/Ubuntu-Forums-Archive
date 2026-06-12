---
title: "GUI won't start automatically"
date: 2012-08-19
forum: New to Ubuntu
---

### Post by DGINSD on 2012-08-19
So I was doing some experimenting to try and work through some issues with user switching.  I installed GDM and set it as the default display manager to see if it was an issue with lightdm.  The long and short of it was, nothing was fixed by this, so I uninstalled gdm. The next reboot I was hung at the purple Ubuntu screen with the five scrolling dots below, scrolling forever. 

Ctrl+ALT+F1 will bring me to TTY mode login, which I can login to just fine. If I CTRL+ALT+F7, at the top of the screen it says "can not write bytes: broken pipe". Whats more weird if I log in to tty1 and run "sudo start lightdm" my GUI stars up and I'm taken to the unity greeter screen, and all seems to work as normal. Reboot leaves me with the same situation, no GUI.

I've tried: reinstalling lightdm, reinstalling gdm and configuring lightdm as the default, purging gdm, updating-grub 

At this point I'm kind of lost, and frustrated, and don't know what to do? I'd really like to avoid reinstalling, please help.

---

### Post by DGINSD on 2012-08-19
I found the solution here [http://askubuntu.com/questions/74551/lightdm-not-starting-on-boot?rq=1]("http://askubuntu.com/questions/74551/lightdm-not-starting-on-boot?rq=1")

I guess if you install GDM as a alternate display manager and then remove it and use dpkg to reconfigure lightdm as the default, dpkg won't set the /etc/X11/default-display-manager properly with a path to lightdm's bin, in my case /usr/sbin/lightdm. Sounds like something needs to be fixed in dpkg.

On a side note while troubleshooting I found out amd released a new catalyst version 12.8 so I installed it. It seems the watermark issue with supposedly supported chipsets has been fixed (at least in my case), so no more work around needed.

---

### Post by jemadux on 2012-08-19
maybe is a bug

---

