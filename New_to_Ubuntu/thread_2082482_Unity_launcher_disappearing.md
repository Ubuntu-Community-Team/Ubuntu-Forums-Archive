---
title: "Unity launcher disappearing"
date: 2012-11-09
forum: New to Ubuntu
---

### Post by Thee on 2012-11-09
Hi there, first time posting!

Let me first explain what is cause of the problem, so you guys can maybe  better help me out.

I have my monitor attached to my DVI port and my TV attached to my HDMI port on ATI graphics card. When my computer is turned on before the TV, and the TV after (few mins, hours, no matter), for some reason (this is regardless of the OS, happens on Windows too) in the moment that the TV is about to show the picture, my monitor goes blank for a 2-3 sec. And thats ok, I guess its an ATI thing, it doesn't bother me. But, after my monitor turns on again, the Unity launcher disappears. The global menu is still there, and I can bring up the HUD using the shortcut key on my keyboard, but the icons and the launcher itself is invisible.

Note: This happens no matter if I currently have Clone Screen on or Single Display. Also When ever this happens, I get an error message, how resolution cant be set or something, cant remember exactly, but I can reproduce the error if its needed.

So, my question is, can I prevent this from happening (launcher disappearing), or if not, can I at least bring it back again without needing to logout and log back in?

Thanks

---

### Post by grahammechanical on 2012-11-09
We have to make some assumptions because you do not provide the information. You are using 12.04? You have Launcher Auto-hide set to Off?

You should also realise that Ubuntu sets the correct video settings by probing the Monitor during boot to get the optimum resolutions and not from reading a script.

What happens if you switch on both monitor and TV before booting the computer? You may need to create a display profile that can be used by the OS. 

Regards.

---

### Post by Thee on 2012-11-09
Sorry, totally forgot to mention. I'm running 12.10 (but was the same on 12.04), and yes, Auto-hide is off.

Monitor is always on, I'm not switching it off at any point (ofc it goes into sleep mode when computer is off), but its only the computer and the TV that I switch off.

If I was to turn the TV on first and then the computer, then such thing wouldn't happen, all would be fine. Like I said, its not the problem for me, I dual boot Win 7 and the same thing happens there - monitor turns off for few secs when I turn on the TV, only difference is there is no error message nor does anything disappear over there.

---

### Post by Thee on 2012-11-10
Here is the error message I get when I turn on the TV:

[b][i]Could not switch the monitor configuration

required virtual size does not fit available size: requested=(3840, 1080), minimum=(320, 200), maximum=(1920, 1920)[/i][/b]

---

### Post by newb85 on 2012-11-10
Could be a graphics card/driver issue.  Please give the output of
```
sudo lshw -C video
```

---

### Post by Thee on 2012-11-10
Here's the output:

```
  *-display               
       description: VGA compatible controller
       product: Barts PRO [Radeon HD 6800 Series]
       vendor: Advanced Micro Devices [AMD] nee ATI
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:51 memory:d0000000-dfffffff memory:fdec0000-fdedffff ioport:ee00(size=256) memory:fde00000-fde1ffff

```

---

