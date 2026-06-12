---
title: "Ubuntu restart when click on URL"
date: 2022-12-29
forum: New to Ubuntu
---

### Post by asubscriber on 2022-12-29
Given:

Ubuntu 22.04 LTS

Laptop: Lenovo Legion

I noticed that SOMETIMES when I click on a any URL then my laptop is **restart**!

Here details on my system:

```
System:
  Kernel: 5.15.0-56-generic x86_64 bits: 64 compiler: gcc v: 11.3.0
    Desktop: GNOME 42.5 tk: GTK 3.24.33 wm: gnome-shell dm: GDM3 42.0
    Distro: Ubuntu 22.04.1 LTS (Jammy Jellyfish)
Machine:
  Type: Laptop System: LENOVO product: 81T3 v: Legion Y540-17IRH-PG0
    serial: <filter> Chassis: type: 10 v: Legion Y540-17IRH-PG0
    serial: <filter>
  Mobo: LENOVO model: LNVNB161216 v: NO DPK serial: <filter>
    UEFI-[Legacy]: LENOVO v: BHCN45WW date: 05/24/2022
Battery:
  ID-1: BAT0 charge: 46.8 Wh (96.9%) condition: 48.3/52.5 Wh (91.9%)
    volts: 12.3 min: 11.3 model: LGC L17L3PG1 type: Li-poly serial: <filter>
    status: N/A cycles: 340
  Device-1: hidpp_battery_0 model: Logitech Wireless Mouse M545/M546
    serial: <filter> charge: 55% (should be ignored) rechargeable: yes
    status: Discharging
Memory:
  RAM: total: 15.54 GiB used: 3.78 GiB (24.3%)
  Array-1: capacity: 32 GiB slots: 2 EC: None max-module-size: 16 GiB
    note: est.
  Device-1: ChannelA-DIMM0 size: 8 GiB speed: 2667 MT/s type: DDR4
    detail: synchronous bus-width: 64 bits total: 64 bits
    manufacturer: SK Hynix part-no: HMA81GS6JJR8N-VK serial: <filter>
  Device-2: ChannelB-DIMM0 size: 8 GiB speed: 2667 MT/s type: DDR4
    detail: synchronous bus-width: 64 bits total: 64 bits
    manufacturer: SK Hynix part-no: HMA81GS6JJR8N-VK serial: <filter>
CPU:
  Info: 6-core model: Intel Core i7-9750H bits: 64 type: MT MCP smt: enabled
    arch: Coffee Lake rev: A cache: L1: 384 KiB L2: 1.5 MiB L3: 12 MiB
  Speed (MHz): avg: 1056 high: 2300 min/max: 800/4500 volts: 0.8 V
    ext-clock: 100 MHz cores: 1: 800 2: 800 3: 800 4: 800 5: 1961 6: 2300
    7: 1219 8: 800 9: 800 10: 800 11: 800 12: 800 bogomips: 62399
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: NVIDIA TU117M [GeForce GTX 1650 Mobile / Max-Q] vendor: Lenovo
    driver: nouveau v: kernel pcie: speed: 2.5 GT/s lanes: 16 ports:
    active: eDP-1 empty: DP-1,DP-2,HDMI-A-1 bus-ID: 01:00.0
    chip-ID: 10de:1f91 class-ID: 0300
  Device-2: Chicony Integrated Camera type: USB driver: uvcvideo
    bus-ID: 1-6:3 chip-ID: 04f2:b6d9 class-ID: 0e02 serial: <filter>
  Display: server: X.Org v: 1.22.1.1 compositor: gnome-shell driver:
    gpu: nouveau note:  X driver n/a display-ID: :0 screens: 1
  Screen-1: 0 s-res: 1920x1080 s-dpi: 96 s-size: 508x286mm (20.0x11.3")
    s-diag: 583mm (23")
  Monitor-1: XWAYLAND0 mapped: eDP-1 model: AU Optronics res: 1920x1080
    hz: 60 dpi: 128 size: 380x220mm (15.0x8.7") diag: 438mm (17.3") modes:
    max: 1920x1080 min: 800x600
  OpenGL: renderer: NV167 v: 4.3 Mesa 22.0.5 direct render: Yes
Audio:
  Device-1: Intel Cannon Lake PCH cAVS vendor: Lenovo driver: snd_hda_intel
    v: kernel bus-ID: 00:1f.3 chip-ID: 8086:a348 class-ID: 0403
  Device-2: NVIDIA vendor: Lenovo driver: snd_hda_intel v: kernel pcie:
    speed: 2.5 GT/s lanes: 16 bus-ID: 01:00.1 chip-ID: 10de:10fa class-ID: 0403
  Sound Server-1: ALSA v: k5.15.0-56-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Intel Cannon Lake PCH CNVi WiFi driver: iwlwifi v: kernel
    bus-ID: 00:14.3 chip-ID: 8086:a370 class-ID: 0280
  IF: wlp0s20f3 state: up mac: <filter>
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    vendor: Lenovo driver: r8169 v: kernel pcie: speed: 2.5 GT/s lanes: 1
    port: 3000 bus-ID: 07:00.0 chip-ID: 10ec:8168 class-ID: 0200
  IF: enp7s0 state: down mac: <filter>
Bluetooth:
  Device-1: Intel Bluetooth 9460/9560 Jefferson Peak (JfP) type: USB
    driver: btusb v: 0.8 bus-ID: 1-14:5 chip-ID: 8087:0aaa class-ID: e001
  Report: hciconfig ID: hci0 rfk-id: 2 state: up address: <filter>
    bt-v: 3.0 lmp-v: 5.1 sub-v: 100 hci-v: 5.1 rev: 100
Drives:
  Local Storage: total: 476.94 GiB used: 84 GiB (17.6%)
  ID-1: /dev/nvme0n1 vendor: Samsung model: MZVLB512HBJQ-000L2
    size: 476.94 GiB speed: 31.6 Gb/s lanes: 4 type: SSD serial: <filter>
    rev: 3L1QEXF7 temp: 36.9 C scheme: GPT
Partition:
  ID-1: / size: 467.89 GiB used: 83.99 GiB (18.0%) fs: ext4
    dev: /dev/nvme0n1p3
  ID-2: /boot/efi size: 512 MiB used: 5.2 MiB (1.0%) fs: vfat
    dev: /dev/nvme0n1p2
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 0 KiB (0.0%) priority: -2
    file: /swapfile
Sensors:
  System Temperatures: cpu: 45.0 C pch: 45.0 C mobo: N/A gpu: nouveau
    temp: 44.0 C
  Fan Speeds (RPM): N/A
Repos:
  Packages: 2006 apt: 1979 snap: 27
  Active apt repos in: /etc/apt/sources.list
    1: deb http://md.archive.ubuntu.com/ubuntu/ jammy main restricted
    2: deb http://md.archive.ubuntu.com/ubuntu/ jammy-updates main restricted
    3: deb http://md.archive.ubuntu.com/ubuntu/ jammy universe
    4: deb http://md.archive.ubuntu.com/ubuntu/ jammy-updates universe
    5: deb http://md.archive.ubuntu.com/ubuntu/ jammy multiverse
    6: deb http://md.archive.ubuntu.com/ubuntu/ jammy-updates multiverse
    7: deb http://md.archive.ubuntu.com/ubuntu/ jammy-backports main restricted universe multiverse
    8: deb http://security.ubuntu.com/ubuntu jammy-security main restricted
    9: deb http://security.ubuntu.com/ubuntu jammy-security universe
    10: deb http://security.ubuntu.com/ubuntu jammy-security multiverse
  No active apt repos in: /etc/apt/sources.list.d/google-chrome.list
  No active apt repos in: /etc/apt/sources.list.d/kelleyk-ubuntu-emacs-jammy.list
  No active apt repos in: /etc/apt/sources.list.d/pgadmin4.list
  No active apt repos in: /etc/apt/sources.list.d/postgresql-pgdg.list
  No active apt repos in: /etc/apt/sources.list.d/steam.list
  No active apt repos in: /etc/apt/sources.list.d/teams.list
  Active apt repos in: /etc/apt/sources.list.d/teamviewer.list
    1: deb [signed-by=/usr/share/keyrings/teamviewer-keyring.gpg] https://linux.teamviewer.com/deb stable main
  No active apt repos in: /etc/apt/sources.list.d/ubuntu-elisp-ubuntu-ppa-jammy.list
Info:
  Processes: 355 Uptime: 5m wakeups: 3 Init: systemd v: 249 runlevel: 5
  Compilers: gcc: 11.3.0 alt: 11/12 Shell: Sudo (sudo) v: 1.9.9 default: Bash
  v: 5.1.16 running-in: emacs inxi: 3.3.13



```

P.S. Before on my laptop I use Linux Mint 21 and this kind of problems not exist.

---

### Post by TheFu on 2022-12-29
Did you check the system log files for issues around that time?

Typically, it will be a hardware issue, like the PSU or a loose PSU connection/short inside, but occasionally, it might be a software bug that would be logged.  It could be a tiny crack someone on the motherboard that isn't seen, so you could lightly bump the computer to see if that causes the issue without the browser.

With a software bug, there's hope.
Try a different browser, try different websites.
Don't use javascript.
Does it ever happen when no browser is running?
If you boot from a USB flash drive into a "Try Ubuntu" environment, does it still happen?  That would mean it is probably hardware, not the OS or your userid's settings.
You can create another userid on the system and see if that user has the same issue.  Or not.  If not, that would say it is likely personal settings, not the OS and not the hardware.

Standard troubleshooting stuff.

But start by checking the logs.  Google "ubuntu logs" for more about where and how to view those.

With a hardware issue, it becomes a test, replace a part, test, replace a part, test, cycle. For laptops, if it is hardware, then usually the replacement part costs more than a newer, better, laptop.  

Personal experience: In 2011, I had a dell laptop (Core2 Duo with MS-Vista) that the external power connector had a cracked connection to the motherboard. It wouldn't boot at all. I couldn't see anything clearly broken and it was just over a year old.  Thankfully, the credit card I used to buy it doubled the warranty for all purchases, so the 1 yr warranty was expired, but the CC coverage was still there.  They wanted a certified repair shop to diagnose the problem and provide a report, which cost $150. The repair shop said a new motherboard was necessary for $600. Rather than fund that, the insurance paid me $650 for loss of use.  I started looking for a replacement laptop and found a Core i5 one w/ Win7 about 4 months later on an amazing deal. It was more than 2x faster and I was pleased with the result. I still have that replacement laptop, though it seldom is booted anymore.

---

### Post by asubscriber on 2022-12-30
When I sometimes click for image's link then laptop 'FREEZE". So I need to hard reset. 

If I reinstall Ubuntu 22.04... is it help?

---

### Post by TheFu on 2022-12-30
> **asubscriber said:**
> When I sometimes click for image's link then laptop 'FREEZE". So I need to hard reset. 

If I reinstall Ubuntu 22.04... is it help?

Did you look at the logs?

---

### Post by asubscriber on 2022-12-30
I attached logs

---

### Post by TheFu on 2022-12-30
> **TheFu said:**
> Did you look at the logs?

Did **YOU** look at the logs?  Maybe someone else will look. That isn't something I'm willing to do as a volunteer. Feels too much like work to me. Sorry.

---

### Post by asubscriber on 2022-12-30
I don't know what exact to search in the logs.

---

### Post by Doug S on 2022-12-30
> **TheFu said:**
> Maybe someone else will look. That isn't something I'm willing to do as a volunteer. Feels too much like work to me. Sorry.Agreed, but I did look, not sure why. There should be several crash logs in /var/crash as referenced by the supplied logs (see apport.log).
Excerpt:```
ERROR: apport (pid 4472) Fri Dec 30 16:00:28 2022: apport: report /var/crash/_opt_teamviewer_tv_bin_TeamViewer.1000.crash already exists and unseen, skipping to avoid disk usage DoS
ERROR: apport (pid 28999) Fri Dec 30 19:28:13 2022: host pid 2912 crashed in a separate mount namespace, ignoring
ERROR: apport (pid 28996) Fri Dec 30 19:28:13 2022: called for pid 27699, signal 6, core limit 0, dump mode 1
ERROR: apport (pid 28996) Fri Dec 30 19:28:13 2022: executable: /usr/bin/emacs-gtk (command line "/usr/bin/emacs")
ERROR: apport (pid 28996) Fri Dec 30 19:28:14 2022: gdbus call error: Error connecting: Error sending credentials: Error sending message: Broken pipe

ERROR: apport (pid 28996) Fri Dec 30 19:28:14 2022: debug: session gdbus call:
ERROR: apport (pid 28996) Fri Dec 30 19:28:14 2022: apport: report /var/crash/_usr_bin_emacs-gtk.1000.crash already exists and unseen, skipping to avoid disk usage DoS
ERROR: apport (pid 5109) Fri Dec 30 19:30:06 2022: called for pid 2353, signal 6, core limit 18446744073709551615, dump mode 1
ERROR: apport (pid 5109) Fri Dec 30 19:30:06 2022: ignoring implausibly big core limit, treating as unlimited
ERROR: apport (pid 5109) Fri Dec 30 19:30:06 2022: executable: /usr/bin/Xwayland (command line "/usr/bin/Xwayland :0 -rootless -noreset -accessx -core -auth /run/user/1000/.mutter-Xwaylandauth.IZRSX1 -listen 4 -listen 5 -displayfd 6 -initfd 7")
ERROR: apport (pid 5109) Fri Dec 30 19:30:07 2022: debug: session gdbus call: (true,)

ERROR: apport (pid 5109) Fri Dec 30 19:30:07 2022: writing core dump to core._usr_bin_Xwayland.1000.d77da1fc-7745-40ae-a007-b7a5462987bb.2353.1608 (limit: -1)
ERROR: apport (pid 5109) Fri Dec 30 19:30:08 2022: this executable already crashed 2 times, ignoring
ERROR: apport (pid 5122) Fri Dec 30 19:30:08 2022: called for pid 2483, signal 6, core limit 0, dump mode 1
ERROR: apport (pid 5122) Fri Dec 30 19:30:08 2022: executable: /usr/bin/emacs-gtk (command line "emacs")
ERROR: apport (pid 5122) Fri Dec 30 19:30:09 2022: debug: session gdbus call: (true,)

ERROR: apport (pid 5122) Fri Dec 30 19:30:09 2022: apport: report /var/crash/_usr_bin_emacs-gtk.1000.crash already exists and unseen, skipping to avoid disk usage DoS
ERROR: apport (pid 5143) Fri Dec 30 19:30:12 2022: called for pid 2258, signal 11, core limit 0, dump mode 1
ERROR: apport (pid 5143) Fri Dec 30 19:30:12 2022: executable: /opt/teamviewer/tv_bin/TeamViewer (command line "/opt/teamviewer/tv_bin/TeamViewer")
ERROR: apport (pid 5143) Fri Dec 30 19:30:12 2022: is_closing_session(): Could not determine DBUS socket.
ERROR: apport (pid 5143) Fri Dec 30 19:30:12 2022: apport: report /var/crash/_opt_teamviewer_tv_bin_TeamViewer.1000.crash already exists and unseen, skipping to avoid disk usage DoS
ERROR: apport (pid 9201) Fri Dec 30 19:36:22 2022: host pid 2457 crashed in a separate mount namespace, ignoring
ERROR: apport (pid 18224) Fri Dec 30 20:59:41 2022: host pid 10858 crashed in a separate mount namespace, ignoring
```

---

### Post by #&amp;thj^% on 2022-12-30
> **Doug S said:**
> Agreed, but I did look, not sure why. There should be several crash logs in /var/crash as referenced by the supplied logs (see apport.log).
Excerpt:```
ERROR: apport (pid 4472) Fri Dec 30 16:00:28 2022: apport: report /var/crash/_opt_teamviewer_tv_bin_TeamViewer.1000.crash already exists and unseen, skipping to avoid disk usage DoS
ERROR: apport (pid 28999) Fri Dec 30 19:28:13 2022: host pid 2912 crashed in a separate mount namespace, ignoring
ERROR: apport (pid 28996) Fri Dec 30 19:28:13 2022: called for pid 27699, signal 6, core limit 0, dump mode 1
ERROR: apport (pid 28996) Fri Dec 30 19:28:13 2022: executable: /usr/bin/emacs-gtk (command line "/usr/bin/emacs")
ERROR: apport (pid 28996) Fri Dec 30 19:28:14 2022: gdbus call error: Error connecting: Error sending credentials: Error sending message: Broken pipe

ERROR: apport (pid 28996) Fri Dec 30 19:28:14 2022: debug: session gdbus call:
ERROR: apport (pid 28996) Fri Dec 30 19:28:14 2022: apport: report /var/crash/_usr_bin_emacs-gtk.1000.crash already exists and unseen, skipping to avoid disk usage DoS
ERROR: apport (pid 5109) Fri Dec 30 19:30:06 2022: called for pid 2353, signal 6, core limit 18446744073709551615, dump mode 1
ERROR: apport (pid 5109) Fri Dec 30 19:30:06 2022: ignoring implausibly big core limit, treating as unlimited
ERROR: apport (pid 5109) Fri Dec 30 19:30:06 2022: executable: /usr/bin/Xwayland (command line "/usr/bin/Xwayland :0 -rootless -noreset -accessx -core -auth /run/user/1000/.mutter-Xwaylandauth.IZRSX1 -listen 4 -listen 5 -displayfd 6 -initfd 7")
ERROR: apport (pid 5109) Fri Dec 30 19:30:07 2022: debug: session gdbus call: (true,)

ERROR: apport (pid 5109) Fri Dec 30 19:30:07 2022: writing core dump to core._usr_bin_Xwayland.1000.d77da1fc-7745-40ae-a007-b7a5462987bb.2353.1608 (limit: -1)
ERROR: apport (pid 5109) Fri Dec 30 19:30:08 2022: this executable already crashed 2 times, ignoring
ERROR: apport (pid 5122) Fri Dec 30 19:30:08 2022: called for pid 2483, signal 6, core limit 0, dump mode 1
ERROR: apport (pid 5122) Fri Dec 30 19:30:08 2022: executable: /usr/bin/emacs-gtk (command line "emacs")
ERROR: apport (pid 5122) Fri Dec 30 19:30:09 2022: debug: session gdbus call: (true,)

ERROR: apport (pid 5122) Fri Dec 30 19:30:09 2022: apport: report /var/crash/_usr_bin_emacs-gtk.1000.crash already exists and unseen, skipping to avoid disk usage DoS
ERROR: apport (pid 5143) Fri Dec 30 19:30:12 2022: called for pid 2258, signal 11, core limit 0, dump mode 1
ERROR: apport (pid 5143) Fri Dec 30 19:30:12 2022: executable: /opt/teamviewer/tv_bin/TeamViewer (command line "/opt/teamviewer/tv_bin/TeamViewer")
ERROR: apport (pid 5143) Fri Dec 30 19:30:12 2022: is_closing_session(): Could not determine DBUS socket.
ERROR: apport (pid 5143) Fri Dec 30 19:30:12 2022: apport: report /var/crash/_opt_teamviewer_tv_bin_TeamViewer.1000.crash already exists and unseen, skipping to avoid disk usage DoS
ERROR: apport (pid 9201) Fri Dec 30 19:36:22 2022: host pid 2457 crashed in a separate mount namespace, ignoring
ERROR: apport (pid 18224) Fri Dec 30 20:59:41 2022: host pid 10858 crashed in a separate mount namespace, ignoring
```
+1
@op From your logs I'd start here:
```
[B]ERROR: apport (pid 5109) Fri Dec 30 19:30:07 2022: writing core dump to core._usr_bin_Xwayland.1000.d77da1fc-7745-40ae-a007-b7a5462987bb.2353.1608 (limit: -1)
ERROR: apport (pid 5109) Fri Dec 30 19:30:08 2022: this executable already crashed 2 times, ignoring[/B]
ERROR: apport (pid 5122) Fri Dec 30 19:30:08 2022: called for pid 2483, signal 6, core limit 0, dump mode 1
```

---

### Post by TheFu on 2022-12-30
Thanks for sifting the logs guys.

I'm not surprised.
* teamviewer
* xemacs
* Wayland

I am a reformed emacs user, BTW.  They've fully accepted me into the church of vim. ;)  Maybe the text emacs will work, since switching powerful editors isn't something done lightly.

Instead of teamviewer, use ssh and/or x2go. There are a few edge conditions where x2go isn't a good option, but most people wouldn't have those.  

Instead of Wayland, use X11, especially if you have an nvidia GPU.  Wayland doesn't seem to support the screen capture stuff that X11 has for 30+ yrs. OTOH, Wayland closes the security issues that X11 has abused to make those possible the last ... er ... 30+ yrs too.  ;)  Wayland doesn't support a few of my critical workflows yet, but I'm hopeful that in 2026, it will be ready.  Systemd and PulseAudio may be ready for production use by then too.  Almost weekly, I still have issues with both on some system here.

---

### Post by asubscriber on 2022-12-31
One log attached

---

### Post by asubscriber on 2022-12-31
I use TeamViewer because I need to remote support (with GUI) of another computer (Linux Mint 20). For me more convenient to use TeamViewer than AnyDesk.

---

### Post by asubscriber on 2022-12-31
Here logs just after ""FREEZE", because click on image's URL.

---

### Post by TheFu on 2022-12-31
> **asubscriber said:**
> I use TeamViewer because I need to remote support (with GUI) of another computer (Linux Mint 20). For me more convenient to use TeamViewer than AnyDesk.

Windows people seem to always use Windows tools for stuff like this.  Different OSes have different, usually better, native solutions.

Use x2go instead. No need to trust external middle-men to make connections, especially on the same LAN.  x2go runs in the background. No userid needs to be logged into the system to allow remote access.

Plus, your computer won't be crashing.

I've shown you (the horse) the water hole, but I can't make you drink from it.

---

### Post by asubscriber on 2022-12-31
You think that my laptop is restart because I use TeamViewer???

Is it a joke?
 Ubuntu is restart because I use TeamViewer?

The question is: Why I need to use Ubuntu 20.02 LTS if it restart because I use TeamViewer???

---

### Post by TheFu on 2022-12-31
Dude, google this: "teamviewer wayland crashing"

---

### Post by asubscriber on 2023-01-01
I remove TeamViwer. But after 3 hours, I click over image URL.... and again the laptop "freeze". Only hard reset help.
So the problem is not in TeamViwer.

---

### Post by TheFu on 2023-01-02
> **asubscriber said:**
> I remove TeamViwer. But after 3 hours, I click over image URL.... and again the laptop "freeze". Only hard reset help.
So the problem is not in TeamViwer.

If you are using TeamViewer and Wayland together, it could be.  Did you switch from Wayland to X11, as suggested in post #10?

Anything doing funny things with graphics is suspected.
1) GPU driver.
2) Display server. (Wayland or X11)
3) Program doing funny things, like TeamViewer does when it connects to the display server.

Any or all of those things are in the crash stack reported.  You need to check all of them out ... as suggested in post #10.

BTW, if the crash reported x2go, I'd look there first and at the Display server, then the GPU driver. Follow what the logs say. If you change something, you need to look at fresh logs.  Troubleshooting 101 stuff.

---

### Post by asubscriber on 2023-01-02
In file  */etc/gdm3/custom.conf* in daemon section
*WaylandEnable=false*

save file and reboot.

But after reboot whole colors are YELLOW. Very bad. I can't see anything.

---

