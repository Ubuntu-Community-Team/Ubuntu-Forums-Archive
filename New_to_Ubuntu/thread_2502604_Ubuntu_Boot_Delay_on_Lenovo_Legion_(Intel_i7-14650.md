---
title: "Ubuntu Boot Delay on Lenovo Legion (Intel i7-14650HX, NVIDIA RTX 4060)"
date: 2024-11-21
forum: New to Ubuntu
---

### Post by gance on 2024-11-21
[COLOR=#0C0D0E][FONT=-apple-system]I recently installed Ubuntu on my Lenovo Legion laptop with the following specs:[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]CPU: Intel Core i7-14650HX (16 cores, 24 threads, 2.2–5.2 GHz) GPU: NVIDIA GeForce RTX 4060 (8GB GDDR6) When I power on the laptop, I see the Lenovo Legion logo followed by the Ubuntu logo, but the screen freezes for 1–2 minutes before reaching the welcome/login page. This delay is consistent every time I boot.[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]Things I've tried so far:[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]Updated all packages using sudo apt update && sudo apt upgrade. Installed the latest NVIDIA drivers (nvidia-driver-560). Disabled Secure Boot in the BIOS. Is this behavior normal on high-performance laptops like mine, or could it be related to the hybrid graphics (Intel + NVIDIA)? How can I optimize the boot time and get rid of this delay?[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]Any advice or debugging tips would be appreciated![/FONT][/COLOR]
[https://ibb.co/X32zhTp](https://ibb.co/X32zhTp)

---

### Post by him610 on 2024-11-21
You should see what is causing the delay with this from terminal,
```
systemd-analyze && systemd-analyze critical-chain

```
After start/restart, you can also press the *esc* key to view the progress of the boot up process.

---

