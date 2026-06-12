---
title: "Crashes after upgrading to Ubuntu 22.04.4 LTS"
date: 2024-07-12
forum: New to Ubuntu
---

### Post by m-carrasco on 2024-07-12
Hi all,

I'm experiencing crashes after upgrading to Ubuntu 22.04.4 LTS. The crashes happen when my laptop is idle for awhile and the screen blanks. When I resume the system, the session has crashed and I need to log in again. 

When I upgraded Ubuntu, I faced some incompatibilities between the new kernel version and the packages related to my wifi adapter. I had to downgrade the kernel to version 5.15.0-46-generic to have wifi connectivity again. I'm uncertain whether this could be linked to the crashes. My laptop is a Lenovo Carbon X1 Gen 9.

I'd like to ask for some help regarding this. Also, I'd like to know what sort of information I could provide to help debugging this issue.

Best,
Manuel

---

### Post by currentshaft on 2024-07-13
journalctl --since "10 minutes ago"

Have you run "fwupdmgr install" to check for driver updates for your Lenovo?

---

### Post by vanadium on 2024-07-14
The issue is probably related with the sleep state. It could indeed that it is due to your wifi adaptor. Do you need to install a driver for it? Awaiting fixes at the level of the kernel or the driver, you may need to disable sleep state. You also could try the latest Ubuntu 24.04, which also is a long term release. As a more recent version, it may have better support for your wifi.

---

### Post by m-carrasco on 2024-07-15
Thank you both. 

I'll check the log as soon as a new crash occurs. I'll also consider the possibility of upgrading to 24.04. However, I'd like to confirm the cause of the crashes first.

I haven't tried running "fwupdmgr install", although I will do. As I said, I want to gather the crash logs first. 

I recall that I had to install a package for the wifi adaptor, although I cannot recall which one. The package was uninstalled during the upgrade due to incompatibilities with the new kernel version (6.x~).

---

### Post by m-carrasco on 2024-07-15
The system has just crashed, this is the [output]("https://gist.githubusercontent.com/m-carrasco/73120c81c1e4b378886582d55fc11857/raw/8c4098ceb9b34152eb458d31ff932f086e1a9dfd/gistfile1.txt") of "journalctl --since "10 minutes ago".

---

