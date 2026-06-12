---
title: "Ubuntu 20.04 has no video signals with gdm3"
date: 2020-10-02
forum: New to Ubuntu
---

### Post by uhsa2 on 2020-10-02
Hello - I did a fresh install of Ubuntu 20.04 on Zotac Ion frontend.

When I booted up - I was unable to get any GUI on. I tried troubleshooting reading various forums with the following:
[LIST]
[*]sudo apt install xserver-xorg-video-nvidia-390
[*]sudo bash -c "echo blacklist nouveau > /etc/modprobe.d/blacklist-nvidia-nouveau.conf"
[*]sudo bash -c "echo options nouveau modeset=0 >> /etc/modprobe.d/blacklist-nvidia-nouveau.conf"
[*]sudo apt-get --reinstall install gdm3
[*]sudo apt-get --reinstall install gnome
[*]sudo apt -get --reinstall install gnome-shell
[*]sudo apt install ubuntu-gnome-desktop
[*]sudo apt remove chrome-remote-desktop
[*]sudo nano /usr/share/X11/xorg.conf.d/10-nvidia.conf
[/LIST]
```

Section "Monitor"
  Identifier "Monitor0"
  Modeline "3840x2160_60.00"  712.75  3840 4160 4576 5312  2160 2163 2168 2237 -HSync +VSync
EndSection
Section "Screen"
  Identifier "Screen0"
  Device "DP-0"
  Monitor "Monitor0"
  DefaultDepth 24
  SubSection "Display"
    Depth 24
    Modes "3840x2160" "1920x1080"
  EndSubSection
EndSection

```

Nothing seems to work - I get "no video signal" on my monitor. This is very frustrating - hoping someone can point me in the right direction. 

Thank you!

---

### Post by CelticWarrior on 2020-10-02
Welcome.

I don't know where you got those instructions from. All is quite confusing and feels like coming from someone trying a lot of things to see what sticks and using unconventional commands like the parameter (--reinstall) before the actual command (apt install).

On top of that the Nvidia's website only mentions 340, not 390, for ION.

And lastly, with the correct option selected, Ubuntu 20.04 should install Nvidia drivers automatically. Then, if the machine is UEFI and being installed in UEFI mode (as it should) you also need to disable Secure Boot.

---

### Post by uhsa2 on 2020-10-02
Thank you for the reply - so the commands I listed were not in particular order. Just jotted down as I remembered those so I can show here what I did.

I checked under /sys/firmware and did not find EFI folder. I guess that I have booted as BIOS (not UEFI)?

I did install my Ubuntu via Rufus USB. 

Can you point me to steps I need to take in order to get this working the right now? I am new to the Ubuntu scene and not a pro here by any means. I just read and try to see if what is given 

I got this working in GUI but the only resolution I get is 640x480. I got this by installing nvidia-390

---

