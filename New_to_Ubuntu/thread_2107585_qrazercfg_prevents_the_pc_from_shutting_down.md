---
title: "qrazercfg prevents the pc from shutting down?"
date: 2013-01-22
forum: New to Ubuntu
---

### Post by Nerdsinc on 2013-01-22
I recently installed Ubuntu 12.10 with a Razer mouse. Upon downloading the "Razer device configuration tool", I found out that my computer never shut down. I got to the screen where it says "Ubuntu" with 4 or 5 dots, but the computer never shuts down. I tried pressing Ctrl-Alt-F2 to see what was going on, but all it said was something about Daemon and qrazercfg and then something about "ignore"...

Recently, I've only been able to replicate where it said that around 5-6 times, (sometimes it says nothing or my keyboard doesn't work) but the problems with shutting down only occurred after I installed "Razer device configuration tool"

Thanks for helping :D

Nerdsinc

[Edit] On a side note, I'm looking to install Linux on my school netbook... As the hardware in that thing is abysmal, I'm looking to install a light Linux alternative to the (ultra) slow Windows 7 Enterprise on it. Xubuntu and Lubuntu came to mind as I heard that XFCE and LXDE were lightweight desktop environments... What do you guys recommend?

---

### Post by Bashing-om on 2013-01-22
Nerdsinc; Hi ! Welcome to the forum.

I do not have experience with the Razor mouse... but as there is a config associated with it, perhaps the shut down procedure can be adjusted in that config file?

As the mouse is a component of Xserver, some hints as to what is causing the misbehaviour might be in the .xsessions-errors log or in /var/log/xorg.0.log files.

Lighter weight distro: I am running lubuntu on an old Dell laptop (kid's), and it screams !


[INDENT][INDENT][INDENT][INDENT]hth 
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by cepal on 2013-01-23
> **Nerdsinc said:**
> 

[Edit] On a side note, I'm looking to install Linux on my school netbook... As the hardware in that thing is abysmal, I'm looking to install a light Linux alternative to the (ultra) slow Windows 7 Enterprise on it. Xubuntu and Lubuntu came to mind as I heard that XFCE and LXDE were lightweight desktop environments... What do you guys recommend?

I'd recommend you to try both, xubuntu and lubuntu. I am using lubuntu within Virtualbox inside my corporate awful Windows. I've had to face a few issues, but I prefer lubuntu to xubuntu because XFCE is growing features AND resources use (some CPU but mostly RAM consumption), while LXDE is still pretty lightweight. And has all the features I need. I only had to write my own little hack for switching keyboards, still lacking the icon showing currently active keyboard layout, but I can live with that! But there are ways how to make even Unity or KDE to not consume too much, I am just happy with LXDE :-). However, you have to accept you would be lacking the special features lately integrated within UNITY (I even never tried them, so I've forgotten the bits I've seen mentioned here and there about UNITY).

As for your original issue, as a first thing, yo might wish to remove the splash from grub options (so during shutdown you'd actually see console, not the graphical nonsense). You should read syslog (/var/log/syslog) readout, maybe the Xorg logs as mentioned by Bashing-om, while the system is still running, you can also check dmesg (a command dumping kernel log which is not logged into any logfile by default).

You can maybe try first to shut down the X window system, not the whole PC and see if it manages to shut, then you can try to poweroff - there you'd see if it's the Xs or something lower what's causing the issues.

Did you install any aditional repos? Is your system fully updated?

You can also try to boot into recovery (single) mode and see if the PC can properly shut down from that / the command line to shut down is "shutdown -h now" - "-h" means "halt", equals to fully switch off, other option would be "-r" (for reboot), "now" means now, you can delay it, e.g. putting "5m" instead of "now" would shut down in 5 minutes, but why would you do that? That's rather for servers. Also ubuntu has one nice alias, "poweroff", which does the same as "shutdown -h now" :-), but on other systems/distros/etc. you might get confused not finding the poweroff command.

---

