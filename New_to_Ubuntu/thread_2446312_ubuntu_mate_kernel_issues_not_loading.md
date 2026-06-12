---
title: "ubuntu mate kernel issues not loading"
date: 2020-06-28
forum: New to Ubuntu
---

### Post by lolojr1 on 2020-06-28
i recently got a raspberry pi 4 4 gig model 

i wanted to use berryboot so i can run retropie and a regular desktop oriented ubuntu OS 

when i reboot or when i loaded the fresh install of 18.04.4 server

i get a red error in the load screen 
> failed to start load kernel modules

this install gives me all kinds of issues besides that and im not sure if its related 

ive tested the checksum before i installed 
reformatted the sd card 
everything goes smoothly like on a normal pc 
i get the os running and run in terminal to install ubuntu mate with tasksel
apt-get update gives me issues
upgrade too
i cant change my time on the clock even if i change the time zone...im sure there is more 

> systemd-modules-load.service - Load Kernel Modules

>    Loaded: loaded (/lib/systemd/system/systemd-modules-load.service; static; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sun 2018-01-28 15:58:19 UTC; 2 years 4 months ago
     Docs: man:systemd-modules-load.service(8)
           man:modules-load.d(5)
  Process: 248 ExecStart=/lib/systemd/systemd-modules-load (code=exited, status=1/FAILURE)
 Main PID: 248 (code=exited, status=1/FAILURE)

Jan 28 15:58:19 ubuntu systemd-modules-load[248]: Failed to find module 'lp'
Jan 28 15:58:19 ubuntu systemd-modules-load[248]: Failed to find module 'ppdev'
Jan 28 15:58:19 ubuntu systemd-modules-load[248]: Failed to find module 'parport_pc'
Jan 28 15:58:19 ubuntu systemd-modules-load[248]: Module 'iscsi_tcp' is builtin
Jan 28 15:58:19 ubuntu systemd-modules-load[248]: Failed to find module 'ib_iser'
Jan 28 15:58:19 ubuntu systemd[1]: systemd-modules-load.service: Main process exited, code=exited, status=1/FAILURE
Jan 28 15:58:19 ubuntu systemd[1]: systemd-modules-load.service: Failed with result 'exit-code'.
Jan 28 15:58:19 ubuntu systemd[1]: Failed to start Load Kernel Modules.
Warning: Journal has been rotated since unit was started. Log output is incomplete or unavailable.

---

