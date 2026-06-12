---
title: "why arent xpadneo and xboxdrv working?"
date: 2022-05-02
forum: New to Ubuntu
---

### Post by gangweedstudios on 2022-05-02
when trying to install xpadneo, it just gives me this response "sed: can't read lib/../VERSION: No such file or directory"
and when trying to start xboxdrv it tells me "Job for xboxdrv.service failed because of unavailable resources or another system error. See "systemctl status xboxdrv.service" and "journalctl -xeu xboxdrv.service" for details."

running systemctl status xboxdrv.service shows 
× xboxdrv.service - Xbox controller driver daemon
     Loaded: loaded (/etc/systemd/system/xboxdrv.service; enabled; vendor preset: enabled)
     Active: failed (Result: resources)
        CPU: 0

May 02 17:33:59 my pc systemd[1]: xboxdrv.service: Failed to load environment files: No such file or directory
May 02 17:33:59 my pc systemd[1]: xboxdrv.service: Failed to run 'start-pre' task: No such file or directory
May 02 17:33:59 my pc  systemd[1]: xboxdrv.service: Failed with result 'resources'.
May 02 17:33:59 my pc systemd[1]: Failed to start Xbox controller driver daemon.
May 02 17:55:22 my pc systemd[1]: xboxdrv.service: Failed to load environment files: No such file or directory
May 02 17:55:22 my pc systemd[1]: xboxdrv.service: Failed to run 'start-pre' task: No such file or directory
May 02 17:55:22 my pc systemd[1]: xboxdrv.service: Failed with result 'resources'.
May 02 17:55:22 my pc systemd[1]: Failed to start Xbox controller driver daemon.

---

