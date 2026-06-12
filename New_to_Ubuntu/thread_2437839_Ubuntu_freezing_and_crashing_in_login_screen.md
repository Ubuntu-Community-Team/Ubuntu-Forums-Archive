---
title: "Ubuntu freezing and crashing in login screen"
date: 2020-03-01
forum: New to Ubuntu
---

### Post by lucherd on 2020-03-01
I'm going to explain what is happening at the end of the post, because I guess the reason may be in the backstory I will write down first:

I'm new to Ubuntu, installed it months ago but got away from my computer, but I turned it on again last week and it was working fine just like I had left it.
I didn't get to install my stuff back then, so I went to install some games I wanted and learn about the system, so I went on installing Hearthstone, and it required Wine.
I already heard about Wine before because my friend that teached me some things barely told me about it. I went to install Wine Staging as I read that it was better for Hearthstone's constant updates. IE8 installed, the corefonts, some libraries here and there and it was just fine, Hearthstone and Minecraft running smoothly, Hearthstone buggy because of the Wine condition I guess.
While I was at it I was kind of telling my brother about how weird was it because obviously nothing worked on first try, and he asked me to change the system language because we are brazilian, and I'm the only one who speaks english, and I installed Ubuntu in english just because I wanted to and the computer is mine, and so I did, and instead of restarting the computer to change it to portuguese, I just turned it off for that day after the installation.
After all of this happened, on the next day I turned my computer on and the screen was flickering on the system loading and I thought it was just changing to portuguese, but I waited hours and nothing moved, so I just forced it to turn off and booted again, and here the problem started showing:

At first it was really laggy and I couldn't start any game and they would crash almost instantly, I rebooted hoping it would help, then I couldn't do anything. After logging in, it would crash before I clicked anything and throw me back at the login screen. It was not getting better, but I found a possible solution eith recovery mode and updating graphic drivers, it kind of worked. I could use it, but while Minecraft was running at ~53 FPS with nice graphics, it barely reached 10 FPS with minimal graphics. I had to turn it off, and when I turned it on again, everything was happening the same way. But this time I can barely leave the login screen, and there is a kind of glitchy appearance to it, the icons get messy, my username sometimes disappear or gets glitchy at the login screen, some colors get distorted, and I can't even click the reboot button before the login screen crashes and "resets".

PS: When the login screen crashes, sometimes a screen that seems to mention internal processes shows up for a moment before the login screen comes back.

Sorry for long explanations and backstories, I want to provide as much info as possible hoping it is useful to tell you exactly how you can help me, any ideas of where this problem could be coming from/if it's my fault and how to not do it again and how do I fix it?

---

### Post by Impavidus on 2020-03-02
I've been using Ubuntu since 2006, but I've never used wine. I consider it a last resort.

If I get this straight, you hadn't used the computer in months, then you started it, installed some things, switched language, turned it off and the next time you tried to turn it on, it didn't work. While you computer was running, it may have installed some updates automatically. And given that it was months behind on those updates, it may have installed a lot of them at the same time. These updates may be the cause of your problem.

When you boot in recovery mode and then continue to a normal GUI login, the system tries to run with open source graphics drivers. This may explain the poor graphics quality, but at least it should allow you to fix some problems. Does that work? And can you tell us a bit more about your system? Like graphics hardware, which release of Ubuntu you run, which kernel. If in doubt, try these commands for some diagnostics:```
inxi -G
uname -a
lsb_release -a
```

---

### Post by cmcanulty on 2020-03-02
I would first try this command that fixes lots of issues and for sure won't cause any problem

```
 sudo dpkg --configure -a
```

Here is an explanation

[https://askubuntu.com/questions/163200/e-dpkg-was-interrupted-run-sudo-dpkg-configure-a]("https://askubuntu.com/questions/163200/e-dpkg-was-interrupted-run-sudo-dpkg-configure-a")

---

### Post by lucherd on 2020-03-02
Booted it in recovery mode to run the commands, here are the results, I hope they help you:

inxi -G: Graphics:  Card: Intel 4th Generation Core Integrated Graphics Controller           Display Server: x11 (X.Org 1.20.5 )
           drivers: vesa (unloaded: modesetting,fbdev)
           Resolution: 1440x900@0.00hz
           OpenGL: renderer: llvmpipe (LLVM 9.0, 256 bits)
           version: 3.3 Mesa 19.2.8

uname -a: Linux lucherd-Lenovo-63 5.3.0-40-generic #32~18.04.1-Ubuntu SMP Mon Feb 3 14:05:59 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

lsb_release -a: No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.4 LTS
Release:	18.04
Codename:	bionic

Thanks in advance.

---

### Post by Impavidus on 2020-03-03
Your system did automatically install a kernel upgrade, which may cause problems. Have you tried with an older kernel?

Integrated Intel graphics normally work without any tuning. I don't think that's the problem. Have all packages installed? You can try from the command line:```
sudo dpkg --configure -a
sudo apt install -f
```but there is actually an option for that when you boot in recovery mode.

---

