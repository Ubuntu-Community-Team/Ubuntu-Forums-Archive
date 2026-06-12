---
title: "Problem on booting Ubuntu Cinnamon 24.04 LTS"
date: 2024-08-11
forum: New to Ubuntu
---

### Post by mightbehappy on 2024-08-11
Im switching from Windows to Linux and I’m going to use Ubuntu Cinnamon as only operational system. Installation went as expected, no errors whatsoever. After completely installing it asked to restart and I did it, and I used it for about half an hour and I had to restart my computer again because it has some hardware problems with the notepad. The boot problem began there, it simply does not boot at all, as I saw no other option I tried reinstalling it, I used the same option I used before “erase everything and install ubuntu”. Everything went as expected and after the installation restart I tested shutting down the system and booting again to see if it would boot, and it did. Then I used it for a while and ended up not shutting it down. After i woke up opened my computer and the login screen was there and i logged in, after a few minutes using it the battery went out and it shut down, I placed my charger and now It doesn’t boot again. I did some searching and used Boot-repair, the report should be here: [https://paste.ubuntu.com/p/wjYFr85t5t/](https://paste.ubuntu.com/p/wjYFr85t5t/)

Some notes: I tried pressing esc to see the possible boot options and it flashed very quickly the Ubuntu boot option on the GNU GRUB and went to the GNU GRUB 2.12 console. 

My computer specs:
Kernel: 6.8.0-31-generic arch: ×86 64 bits: 64 compiler: gccv: 13.2.0 clocksource: tsc
Desktop: Cinnamon v: 6.0.4 tk: GTK v: 3.24.41 wm: Muffin v: 6.0.1 vt: 7 dm: LightDM v: 1.30.0 Distro: Cinnamon 24.04 LTS (Noble Numbat) base: Ubuntu
Machine:
Type: Laptop System: LENOVO product: 82MD v: IdeaPad 3 15ITL6
serial: «superuser required> Chassis: type: 10 v: IdeaPad 3 15ITL6 serial: <superuser required>
Mobo: LENOVO model: LNVNB161216 v: NO DPK serial: «superuser required> part-nu: LENOVO_MT_82MD_BU idea FM IdeaPad 3 15ITL6
uuid: «superuser required> UEFI. LENOVO V: GGCN51ww date: 11/16/2022
| v: 0.8 type: USB rev: 2.0 speed: 12 Mb/s lanes: 1 bUs- ID: 3-10:4
chip-ID: 8087:0aaa class-ID: e001
Report: hciconfig ID: hcio rfk-id: 2 state: down bt-service: enabled, running rfk-block: hardware: no software: yes address: <filter> Drives:
Local Storage: total: 245.93 GiB used: 4.87 GiB (2.0%)
|D-1:
model: NVMe IM2P33F4 256GB size: 238.47 GiB
speed: 31.6 Gb/5 lanes: 4 tech: SSD serial: «filter> fw-rev: 1B114215 temp: 29.9 C scheme: GPT |D-2:
vendor: Kingston model: Data Traveler 108 size: 7.46 GiB
type: USB rev: 2.0 spd: 480 Mb/s lanes: 1 tech: N/A serial: «filters Fw-rev: PMAP scheme: MBR
Partition:
ID-1: / size: 3.77 GiB used: 393.9 MiB (10.2%) Fs: overlay source: ERR-102
Swap:
Alert: No swap data was found.
Sensors:
System Temperatures: cpU: 36.0 C mobo: N/A
Fan Speeds (rpm): N/A
Repos:
Packages: 2120 pm: dpkg pkgs: 2111 pm: snap pkgs: 9
Active apt repos in:
1: deb cdrom:[Ubuntu-Cinnamon 24.04 LTS Noble Numbat - Release amd64 (20240425)1/ noble main multiverse restricted universe
Active apt repos in:
1: deb
2: deb
Active apt repos in:
1: deb
noble noble-updates noble-backports main universe restricted multiverse noble-security main universe restricted multiverse
noble main
Info:
Memory: total: 8 GiB note: est. available: 7.54 GiB used: 2.77 GiB (36.8%)
Processes: 302 Power: Uptime: 50m states: freeze,mem,disk suspend: s2idle wakeups: o hibernate: platform Init: systemd v: 255 target: graphical (5)
default: graphical
Compilers: gcc: 13.2.0 Shell: Bash v: 5.2.21 running-in: gnome-terminal inxi: 3.3.34

---

### Post by tea for one on 2024-08-11
In your Lenovo UEFI settings, do you have other security options?

Disable the following (if present):-
TPM (Trusted Platform Module)
PTT (Platform Trust Technology)
FTPM (Firmware Trusted Platform Module)
TPT (Trust Platform Technology)
Device Guard (some Lenovo devices)
OS Optimised Defaults (some Lenovo devices)
Lock UEFI BIOS Settings
Boot Order Lock

Enable Microsoft 3rd Party UEFI CA

Make sure that your laptop has sufficient charge and try to boot again.

---

### Post by currentshaft on 2024-08-11
.

---

### Post by oldfred on 2024-08-11
If tea for one's suggestions do not work.

With only one install, grub automatically boots that install.
So we do not know if grub boot issue, or later loading some driver.
Boot-Repair report is not showing anything that I can see, so probably not grub.
Right after UEFI/BIOS screen, but before grub appears can you press escape key & get grub menu?
If UEFI fast boot is on, you may not have time to press any key & full "cold" boot required. Full power down, not "warm" reboot.
If you get grub menu then can you boot recovery mode?

---

### Post by mightbehappy on 2024-08-11
Unfortunately the only options available from those you have listed were “Intel Plataform Trust Technology” and “Device Guard” which i disabled. I restarted my laptop and nothing happened. Heres a list of options I have on my Bios and their respective current values, just to make sure I didn’t miss anything. 

E - Enabled
D - Disabled

Boot:
    USB Boot (E)
    PXE Boot to LAN(E)
    IPV4 PXE First(E)
    EFI
    ubuntu(<filter>-NVMe <filter> 256GB)

Security:
    Intel Plataform Trust Technology(D)
    Device Guard(D)
    Secure Boot(D)
    Secure Boot Status(D)
    Plataform Mode(User mode)
    Secure Boot Mode(Standard)
    Reset to Setup Mode [Enter]
    Restore Factory Keys [Enter]

Configuration:
    Wireless LAN (E)
    Sata Controller Mode (AHCI)
    Intel VMD Controller(D)
    Intel (R) Virtualization Technology(E)
    Intel (R) VT-d Feature(E)
    Intel (R) Hyper - Threading Technology(E)
    BIOS Back Flash (D)
    HotKey Mode (E)
    Fool Proof Fn Ctrl (E)
    Flip to Boot (E)
    Always on USB (E)
    Charge in Battery Mode (E)

---

### Post by mightbehappy on 2024-08-11
Nothing is shown on the screen, not even lenovo logo, but the display turns on.

---

### Post by mightbehappy on 2024-08-11
I tried that and it actually worked, i pressed Esc and Enter at the same time and it opened the GNU boot menu and selected the Ubuntu option and loaded the system right away. Should i open another thread to try to fix the issue of not loading the system automatically?

---

### Post by tea for one on 2024-08-12
> **mightbehappy said:**
> i pressed Esc and Enter at the same time and it opened the GNU boot menu and selected the Ubuntu option and loaded the system right away.
It may be worthwhile editing Grub.
When you've next booted successfully, open a terminal and try this:-
```
sudo nano /etc/default/grub
```
```
GRUB_DEFAULT=0
[s]GRUB_TIMEOUT_STYLE=hidden[/s]
GRUB_TIMEOUT_STYLE=menu
[s]GRUB_TIMEOUT=0[/s]
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`( . /etc/os-release; echo ${NAME:-Ubuntu} ) 2>/dev/null || echo Ubuntu`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```
Ctrl O to save and Ctrl X to exit
```
sudo update-grub
```
Close terminal and power off
Power on and complete success ;)

---

### Post by mightbehappy on 2024-08-12
> **tea for one said:**
> It may be worthwhile editing Grub. When you've next booted successfully, open a terminal and try this:- ```
sudo nano /etc/default/grub
``` ```
GRUB_DEFAULT=0 [s]GRUB_TIMEOUT_STYLE=hidden[/s] GRUB_TIMEOUT_STYLE=menu [s]GRUB_TIMEOUT=0[/s] GRUB_TIMEOUT=10 GRUB_DISTRIBUTOR=`( . /etc/os-release; echo ${NAME:-Ubuntu} ) 2>/dev/null || echo Ubuntu` GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" GRUB_CMDLINE_LINUX=""
``` Ctrl O to save and Ctrl X to exit ```
sudo update-grub
``` Close terminal and power off Power on and complete success ;)  Thank you! I'll mark this thread as solved

---

