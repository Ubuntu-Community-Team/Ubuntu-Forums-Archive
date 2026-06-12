---
title: "Chrome is not working in Ubuntu 16.04"
date: 2018-02-27
forum: New to Ubuntu
---

### Post by imgagan on 2018-02-27
I haven't remember that what I did on my system that cause the chrome browser not working. All the things were going fine but now when I click the chrome browser icon then it is not opening. I have re-installed it but still have the same problem. I also have open it through terminal using command: google-chrome it returns me an error:
[B]
ATTENTION: default value of option force_s3tc_enable overridden by environment.
[8831:8831:0228/065113.899190:ERROR:sync_control_vsync_provider.cc(62)] glXGetSyncValuesOML should not return TRUE with a media stream counter of 0.
[/B]
Can anybody please help me.

Thanks

---

### Post by kerry_s on 2018-02-27
in terminal:

rm -rf ~/.config/google-chrome

this will reset chrome back to fresh install

---

### Post by imgagan on 2018-02-27
> **kerry_s said:**
> in terminal:

rm -rf ~/.config/google-chrome

this will reset chrome back to fresh install

I have done it but not working. I want to tell you that when I check the mirror option under the Display settings then chrome is working but after unchecked it then chrome again not working.

---

### Post by vasa1 on 2018-02-27
Have you tried```
google-chrome --disable-gpu
```from a terminal?

---

### Post by imgagan on 2018-02-27
> **vasa1 said:**
> Have you tried```
google-chrome --disable-gpu
```from a terminal?

I just have tried it and returns me this error:

[4093:4093:0228/074409.603596:ERROR:gpu_process_transport_factory.cc(1009)] Lost UI shared context.
[4093:4093:0228/074414.920941:ERROR:navigation_entry_screenshot_manager.cc(135)] Invalid entry with unique id: 1

---

### Post by vasa1 on 2018-02-27
And the browser still doesn't launch?

---

### Post by imgagan on 2018-02-27
Yes Vasa1, it still not working!

---

### Post by vasa1 on 2018-02-27
Could you please install *inxi* and then post the output of *inxi -Fxz* so we know a little about your system?

---

### Post by imgagan on 2018-02-27
> **vasa1 said:**
> Could you please install *inxi* and then post the output of *inxi -Fxz* so we know a little about your system?

Here what I received after installing inxi run command as you have suggested:

```
System:    Host: enlightened Kernel: 3.11.0-12-generic x86_64 (64 bit) Desktop: KDE 4.11.2 Distro: Ubuntu 13.10Machine:   Mobo: Intel model: DG35EC version: AAE29266-210
           Bios: Intel version: ECG3510M.86A.0112.2009.0203.1136 date: 02/03/2009
CPU:       Quad core Intel Core2 Quad CPU Q8400 (-MCP-) clocked at 1998.00 MHz 
Graphics:  Card: Intel 82G35 Express Integrated Graphics Controller 
           X.Org: 1.14.3 drivers: intel (unloaded: fbdev,vesa) Resolution: 1360x768@60.0hz 
           GLX Renderer: Mesa DRI Intel 965G GLX Version: 2.1 Mesa 9.2.1
Network:   Card: Intel 82566DC Gigabit Network Connection driver: e1000e 
Drives:    HDD Total Size: 500.1GB (38.8% used)
Info:      Processes: 304 Uptime: 1:50 Memory: 4983.3/7975.7MB Client: Shell (bash) inxi: 1.9.12

```

---

### Post by imgagan on 2018-03-02
Hi @Vasa1 I just have revert the settings under the Software & Updates then Updated system software to go through Software Updater. I also restore the settings to use this command: ```
dconf reset -f / 
```

But after all that Chrome is still not working. Now I feel that I'm really in trouble.

Please help!

---

### Post by imgagan on 2018-03-02
[COLOR=#111111][FONT=Ubuntu]Hayee everyone, its working now![/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I just made some settings under the Setting >> Display. First I checked the mirror option and applied and then again uncheck the mirror option and select the Built-in-Display next to the Launcher Placement.

Finally, it fixed, thanks to all of you especially Vasa1 to show your interest in my problem![/FONT][/COLOR]

---

### Post by mörgæs on 2018-03-02
Good, then please mark the thread solved.

---

### Post by biarkivior on 2018-03-04
I have also had the same problem. my chrome browser just quit working and i did all the steps i have followed on here to try to reinstall and have searched the internet over and it is still not working also running ubuntu 16.04 lts

---

### Post by biarkivior on 2018-03-04
i have fixed my problem by restarting my desktop after in stalling the command lines and updating the computer

---

