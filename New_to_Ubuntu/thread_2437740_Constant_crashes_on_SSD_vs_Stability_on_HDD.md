---
title: "Constant crashes on SSD vs Stability on HDD"
date: 2020-02-28
forum: New to Ubuntu
---

### Post by heqro on 2020-02-28
Hello everyone,

after having fiddled a bit with ubuntu, I found out I had an SSD available to install Ubuntu in. I am not too certain about why is this happening, but on my SATA drive I basically have never encountered an unrecoverable crash, whereas on SSD it just takes to open a file for the whole system to crash.

The SSD contents are as follows:
[LIST]
[*]7.45Gb swap 
[*]4.65Gb home folder 
[*]23.23Gb root, 
[/LIST]
whereas the HDD contents were automatically handed out to me by the installer.

I'm not too certain about how I should proceed.

Further information: Both drives feature Kubuntu 18.04 LTS.

Edit: I've wiped out the entirety of the SSD and placed Kubuntu instead, letting it do its own thing. It still crashes.

Edit2: I'm running the following
Intel(R) Core(TM) i7-4770 CPU @ 3.40GHz
HDD: ST2000DM001-1CH164 (2TB)
SSD: M4-CT128M4SSD2     (120GB)
16GB RAM
GPU: NVIDIA GeForce GTX 660

BIOS:
BIOS Information
        Vendor: American Megatrends Inc.
        Version: 0605
        Release Date: 08/07/2013
        Address: 0xF0000
        Runtime Size: 64 kB
        ROM Size: 8192 kB
        Characteristics:
                PCI is supported
                APM is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                Boot from CD is supported
                Selectable boot is supported
                BIOS ROM is socketed
                EDD is supported
                5.25"/1.2 MB floppy services are supported (int 13h)
                3.5"/720 kB floppy services are supported (int 13h)
                3.5"/2.88 MB floppy services are supported (int 13h)
                Print screen service is supported (int 5h)
                8042 keyboard services are supported (int 9h)

---

### Post by CelticWarrior on 2020-02-28
The SSD can be defective.

---

### Post by heqro on 2020-02-28
I'm currently enjoying a session on Windows 10 after wiping out the SSD again and installing Windows over it. Needless to say, I have not been experiencing any problems with it at all. Could it be a matter of drivers?

---

### Post by oldfred on 2020-02-28
Also your /home was way too small.
You typically can allocate 25 or 30GB to / (root) if using separate /home or data partition(s) for all your data.
But if you have little data, or want a smaller install then better to keep /home inside / so unallocated space can be shared.
Also new installs use a swap file, so separate swap partition not required. But a swap partition will be used if found.

Have you updated SSD firmware & UEFI firmware?

---

### Post by heqro on 2020-02-28
> **oldfred said:**
> Also your /home was way too small.

I didn't plan on saving anything there, though

> **oldfred said:**
> Have you updated SSD firmware & UEFI firmware?

I have not updated anything SSD-related besides installing Kubuntu, then Manjaro, then Kubuntu, and then Windows again.

However, I have also been experiencing random crashes on live USB sessions by doing the exact same things (moving the mouse and just generally opening windows; it's all I can do without crashing).

---

### Post by Autodave on 2020-02-28
Perhaps giving some info on your hardware would help us.

---

### Post by heqro on 2020-02-28
Thanks for pointing it out. I edited the original post.

---

### Post by heqro on 2020-02-29
I solved this issue by just downloading Pop!_OS.

Either the drivers for my GPU were the thing I needed or Gnome is just what I'll stick to, as it's the only thing stable on my desktop.

---

