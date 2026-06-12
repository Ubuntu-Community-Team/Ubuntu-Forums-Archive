---
title: "Are there no updates to nvidia drivers despite the huge vulnerability?"
date: 2024-12-06
forum: New to Ubuntu
---

### Post by blueleafy on 2024-12-06
A few weeks back, nvidia revealed that there was a vulnerability in all of their graphics drivers that allowed others almost complete control over the computer. This flaw was found in the version I am using, 550-120. I was told by several other linux users not to update the drivers by downloading them from nvidia's website, and to wait on my distro to roll out the updates. It's been a few weeks, at least, but from what I can see on my end, both ```
sudo apt list --installed | grep nvidia-driver
``` and Nvidia X Server Settings are reporting that I am still on 550-120. The updated version that fixed the issue was 127. The nvidia website is now offering 135. I've gotten away with not using the nvidia drivers thus far, but in order to play video games I need to be on nvidia's drivers and not the x org one. 

My system specs: 
> Operating System: Kubuntu 24.04
KDE Plasma Version: 5.27.11
KDE Frameworks Version: 5.115.0
Qt Version: 5.15.13
Kernel Version: 6.8.0-49-generic (64-bit)
Graphics Platform: X11
Processors: 12 × AMD Ryzen 5 5600X 6-Core Processor
Memory: 15.5 GiB of RAM
Graphics Processor: NVIDIA GeForce RTX 2060/PCIe/SSE2
Manufacturer: ASUS

And the output for the nvidia command I posted earlier:
> [FONT=monospace][COLOR=#000000]WARNING: apt does not have a stable CLI interface. Use with caution in scripts. [/COLOR]

[COLOR=#ff5454]**nvidia-driver**[/COLOR][COLOR=#000000]-550-open/noble-updates,noble-security,now 550.120-0ubuntu0.24.04.1 amd64 [installed][/COLOR]
[/FONT]

Not sure on what to do. I don't want to stay on vulnerable graphics drivers :(

---

### Post by 1fallen on 2024-12-06
Arch took care of this before nVidia did,  I can't seem to get a straight answer from any of  our Developers yet.

So I took the driver from nvidia.com
```
nvidia-smi
Fri Dec  6 11:15:57 2024       
+-----------------------------------------------------------------------------------------+
| NVIDIA-SMI 565.57.01              Driver Version: 565.57.01      CUDA Version: 12.7     |
|-----------------------------------------+------------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id          Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |           Memory-Usage | GPU-Util  Compute M. |
|                                         |                        |               MIG M. |
|=========================================+========================+======================|
|   0  NVIDIA GeForce RTX 3050 ...    Off |   00000000:01:00.0 Off |                  N/A |
| N/A   30C    P0              8W /   60W |      15MiB /   4096MiB |      0%      Default |
|                                         |                        |                  N/A |
+-----------------------------------------+------------------------+----------------------+
                                                                                         
+-----------------------------------------------------------------------------------------+
| Processes:                                                                              |
|  GPU   GI   CI        PID   Type   Process name                              GPU Memory |
|        ID   ID                                                               Usage      |
|=========================================================================================|
|    0   N/A  N/A      2222      G   /usr/lib/xorg/Xorg                              4MiB |
+-----------------------------------------------------------------------------------------+

```

This is something I normally don't recommend.....BUT

I'm now at this very moment grabbing this one "565.77"[h=1][/h]"

---

### Post by 1fallen on 2024-12-06
Also you can check against the cve with:
```
sudo pro fix CVE-2024-0126
```
Mine is not affected:
```
CVE-2024-0126: 
NVIDIA GPU Display Driver for Windows and Linux contains a vulnerability
which could allow a privileged attacker to escalate permissions. A
successful exploit of this vulnerability might lead to code execution,
denial of service, escalation of privileges, information disclosure, and
data tampering.
 - https://ubuntu.com/security/CVE-2024-0126

No affected source packages are installed.

&#10004; CVE-2024-0126 does not affect your system.

```

---

