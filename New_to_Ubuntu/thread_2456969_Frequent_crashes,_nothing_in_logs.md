---
title: "Frequent crashes, nothing in logs"
date: 2021-01-22
forum: New to Ubuntu
---

### Post by distancy on 2021-01-22
I'm experiencing fairly frequent crashes running Ubuntu on my laptop. This has actually been an issue on-and-off for a few years. There will be a few weeks or months where it happens often (up to multiple times per day) and then doesn't happen for long stretches.

What typically happens is that:
* the display continues to respond to input (mouse or keyboard)
* the icons in the tray (both top right and applications on the left) either disappear or turn into grey boxes
* audio sometimes cuts out if playing
* sometimes one of the open applications will pop up "this application is not responding, force quit or wait"
* if I try running (eg) htop in the termal I get "Input/output error"
* this state may last for a few minutes -- I've stayed on video calls for several minutes from this point before a full crash rebooting.
* I need to reboot. 
* I don't see errors in the logs (journalctl or /var/log/syslog) from the time of the crash.

It's happening often this week and is extremely frustrating. Any help in getting to the bottom of this would be much appreciated!


Some basic system info (from neofetch):
> OS: Ubuntu 20.04.1 LTS x86_64 
Host: XPS 15 9560 
Kernel: 5.4.3-050403-generic 
Uptime: 17 mins 
Packages: 3305 (dpkg), 1 (flatpak), 14 (snap) 
Shell: bash 5.0.17 
Resolution: 1920x1080 
DE: GNOME 3.36.4 
WM: Mutter 
WM Theme: Adwaita 
Theme: Yaru [GTK2/3] 
Icons: Yaru [GTK2/3] 
Terminal: gnome-terminal 
CPU: Intel i7-7700HQ (8) @ 3.800GHz 
GPU: NVIDIA GeForce GTX 1050 Mobile 
GPU: Intel HD Graphics 630 
Memory: 3612MiB / 23782MiB 

---

### Post by VMC on 2021-01-22
I see you have multiple graphics. Did you install any drivers?

---

### Post by TheFu on 2021-01-22
I'd think it was some sort of hardware or data corruption issue. SSDs that are failing have causes this issue that I've seen.
> Input/output error
can be a bad cable, failing storage, bad PCI seating, power supply spike, cooling problem.

Have you setup journalctl.conf to retain logs between reboots?  If not, it is hard to troubleshoot HW issues.

---

### Post by distancy on 2021-01-22
> **VMC said:**
> I see you have multiple graphics. Did you install any drivers?

Thanks for the reply! Here's the driver info that I know how to find, is there anything else that would be helpful to show?

[ATTACH=CONFIG]287791[/ATTACH]

---

### Post by distancy on 2021-01-22
> **TheFu said:**
> I'd think it was some sort of hardware or data corruption issue. SSDs that are failing have causes this issue that I've seen.

can be a bad cable, failing storage, bad PCI seating, power supply spike, cooling problem.

Have you setup journalctl.conf to retain logs between reboots?  If not, it is hard to troubleshoot HW issues.

Thanks! I don't think I have enabled it explicitly but `journalctl --boot=-1` does show logs from the previous boot (and no errors just before the crash) so I think it is enabled. Any other ideas for how I could investigate this?

---

### Post by distancy on 2021-01-23
> **TheFu said:**
> I'd think it was some sort of hardware or data corruption issue. SSDs that are failing have causes this issue that I've seen.

can be a bad cable, failing storage, bad PCI seating, power supply spike, cooling problem.

Have you setup journalctl.conf to retain logs between reboots?  If not, it is hard to troubleshoot HW issues.

The most recent time this happened my command gave "command not found" rather than input/output error, if that's helpful.

---

### Post by TheFu on 2021-01-23
> **distancy said:**
> The most recent time this happened my command gave "command not found" rather than input/output error, if that's helpful.

That just confirms a storage subsystem issue ... or you were mistyping the command.  New people who don't use tab-completion often mistype commands.  Heck, even with tab-completion, people sometimes mistype commands.

---

### Post by ActionParsnip on 2021-01-23
Test RAM health. Make sure that's OK
Make sure you have the latest BIOS

---

### Post by distancy on 2021-01-24
> **TheFu said:**
> That just confirms a storage subsystem issue ... or you were mistyping the command.  New people who don't use tab-completion often mistype commands.  Heck, even with tab-completion, people sometimes mistype commands.

Yep tried `ls` as well, which I think less likely to have mistyped and also got `command not found`.

Do you have any suggestions on how to proceed? Any diagnostics that would help narrow it down?

---

### Post by distancy on 2021-01-24
> **ActionParsnip said:**
> Test RAM health. Make sure that's OK
Make sure you have the latest BIOS

Thanks for the suggestions!

I think I have the latest BIOS. [This page]("https://www.dell.com/support/home/en-us/product-support/product/xps-15-9560-laptop/drivers") shows that the latest version is 1.21.0, and running ```
sudo dmidecode -s bios-version
``` shows me 1.21.0 as well. 

Will test RAM and report back.

---

### Post by TheFu on 2021-01-24
> **distancy said:**
> Yep tried `ls` as well, which I think less likely to have mistyped and also got `command not found`.

Do you have any suggestions on how to proceed? Any diagnostics that would help narrow it down?

When ls doesn't work, that's a huge failure.  Reseat the cables, run fsck, run SMART tests and reports (2 separate commands).  SMART should show a bad cable or slowly failing storage, but not always.

Ensure you have excellent backups for anything you don't want to loose.

I've never, ever, seen RAM fail in over 3 decades unless it is in terrible environment - too hot, lots of vibration, stuff like that. That's way all RAM comes with a lifetime guarantee. It doesn't fail.  Now, on some Ryzens systems, RAM can be picky about tuning numbers.  I've had that issue where RAM rates at 3200 Mhz refuses to run more than 2 days at that speed, but if I drop it back to 2800 Mhz, it is perfectly stable.  This is more an issue with 2-pairs, not fully matched sets. I didn't have any issues with 1 pair of DDR4 running at 3200 Mhz ... well ... except running out of RAM for the processes to use.  My 2-pair refused to boot at 2900 Mhz. The BIOS failed and reset the speeds back to something like 1800 Mhz in failsafe mode.

My best guess now is a dying disk.

---

