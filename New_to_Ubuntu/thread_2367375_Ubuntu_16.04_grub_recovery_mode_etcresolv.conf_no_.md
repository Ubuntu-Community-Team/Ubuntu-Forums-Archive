---
title: "Ubuntu 16.04 grub recovery mode: /etc/resolv.conf no such file or directory"
date: 2017-07-29
forum: New to Ubuntu
---

### Post by linengmiao on 2017-07-29
Hello everyone

Ive installed ubuntu 16.04 on my laptop (lenovo thinkpad x200) a few months ago and suddenly I can t get past the splash screen. 


Where I m stuck: [https://i.stack.imgur.com/mJv7v.jpg](https://i.stack.imgur.com/mJv7v.jpg)


(i see the red dots gradually becoming white and vice-verca, so something is happening, but I can t get past this screen)


I thus decided to boot in recovery mode (I chose ubuntu with linux 4.10.0-28-generic (recovery mode)) to update and upgrade all my packages. But once I get there I have no internet access (with or without ethernet cable). This is what I get when trying to enable networking:


[https://imgur.com/gallery/enOea](https://imgur.com/gallery/enOea) 


Could someone explain me how to have internet access so I can hopefully be able to solve my other issue in order to be able to log in again on my machine?



More info about what I have tried can be found here: [https://www.reddit.com/r/techsupport/comments/6qa9bk/ubuntu_1604_grub_recovery_mode_etcresolvconf_no/](https://www.reddit.com/r/techsupport/comments/6qa9bk/ubuntu_1604_grub_recovery_mode_etcresolvconf_no/)
and [https://www.reddit.com/r/linuxquestions/comments/6qa7fg/ubuntu_1604_grub_recovery_mode_etcresolvconf_no/](https://www.reddit.com/r/linuxquestions/comments/6qa7fg/ubuntu_1604_grub_recovery_mode_etcresolvconf_no/)

So far nobody managed to solve the issue...

Thanks!

---

### Post by Bashing-om on 2017-07-29
linengmiao; Hello;

More than one way to get to a terminal and activate networking. For now let's follow your thought process and access the system via the recovery console.
In the recovery menu is the option to "enable networking" choose this and then " resume normal boot".

Trying to work with what you have here .
Update and upgrade; see then if you can boot up normally.

If no, we then take action to find the fault .


[INDENT][INDENT]what to do when the process breaks
[/INDENT][/INDENT]

---

### Post by nyck66 on 2018-03-24
I'm having a similar problem in Ubuntu 16.04 LTS, when I run 'journalctl | grep modules' I get:

`Mar 24 10:56:02 nobu-ThinkPad-T420 systemd[1]: systemd-modules-load.service: Main process exited, code=exited, status=1/FAILURE
Mar 24 10:56:02 nobu-ThinkPad-T420 systemd[1]: systemd-modules-load.service: Unit entered failed state.
Mar 24 10:56:02 nobu-ThinkPad-T420 systemd[1]: systemd-modules-load.service: Failed with result 'exit-code'.
Mar 24 10:56:02 nobu-ThinkPad-T420 systemd-modules-load[231]: Inserted module 'lp'
Mar 24 10:56:02 nobu-ThinkPad-T420 systemd-modules-load[231]: Inserted module 'ppdev'
Mar 24 10:56:02 nobu-ThinkPad-T420 systemd-modules-load[231]: Inserted module 'parport_pc'
Mar 24 10:56:02 nobu-ThinkPad-T420 systemd-modules-load[231]: Inserted module 'coretemp'
Mar 24 10:56:02 nobu-ThinkPad-T420 systemd-modules-load[231]: could not find module by name='off'
Mar 24 10:56:02 nobu-ThinkPad-T420 systemd-modules-load[231]: Failed to insert 'off': No such file or directory
Mar 24 10:56:02 nobu-ThinkPad-T420 systemd-modules-load[231]: could not find module by name='off'
Mar 24 10:56:02 nobu-ThinkPad-T420 systemd-modules-load[231]: Failed to insert 'off': No such file or directory
Mar 24 10:56:02 nobu-ThinkPad-T420 systemd-modules-load[231]: could not find module by name='off'
Mar 24 10:56:02 nobu-ThinkPad-T420 systemd-modules-load[231]: Failed to insert 'off': No such file or directory
Mar 24 10:56:02 nobu-ThinkPad-T420 systemd-modules-load[382]: could not find module by name='off'
Mar 24 10:56:02 nobu-ThinkPad-T420 systemd-modules-load[382]: Failed to insert 'off': No such file or directory
Mar 24 10:56:02 nobu-ThinkPad-T420 systemd-modules-load[382]: could not find module by name='off'
Mar 24 10:56:02 nobu-ThinkPad-T420 systemd-modules-load[382]: Failed to insert 'off': No such file or directory
Mar 24 10:56:02 nobu-ThinkPad-T420 systemd-modules-load[382]: could not find module by name='off'
Mar 24 10:56:02 nobu-ThinkPad-T420 systemd-modules-load[382]: Failed to insert 'off': No such file or directory
Mar 24 10:56:02 nobu-ThinkPad-T420 systemd[1]: systemd-modules-load.service: Main process exited, code=exited, status=1/FAILURE
Mar 24 10:56:02 nobu-ThinkPad-T420 systemd[1]: systemd-modules-load.service: Unit entered failed state.
Mar 24 10:56:02 nobu-ThinkPad-T420 systemd[1]: systemd-modules-load.service: Failed with result 'exit-code'.
Mar 24 10:56:03 nobu-ThinkPad-T420 systemd-modules-load[836]: could not find module by name='off'
Mar 24 10:56:03 nobu-ThinkPad-T420 systemd-modules-load[836]: Failed to insert 'off': No such file or directory
Mar 24 10:56:03 nobu-ThinkPad-T420 systemd-modules-load[836]: could not find module by name='off'
Mar 24 10:56:03 nobu-ThinkPad-T420 systemd-modules-load[836]: Failed to insert 'off': No such file or directory
Mar 24 10:56:03 nobu-ThinkPad-T420 systemd-modules-load[836]: could not find module by name='off'
Mar 24 10:56:03 nobu-ThinkPad-T420 systemd-modules-load[836]: Failed to insert 'off': No such file or directory
Mar 24 10:56:03 nobu-ThinkPad-T420 systemd[1]: systemd-modules-load.service: Main process exited, code=exited, status=1/FAILURE
Mar 24 10:56:03 nobu-ThinkPad-T420 systemd[1]: systemd-modules-load.service: Unit entered failed state.
Mar 24 10:56:03 nobu-ThinkPad-T420 systemd[1]: systemd-modules-load.service: Failed with result 'exit-code'.
Mar 24 10:57:49 nobu-ThinkPad-T420 sudo[2910]:     nobu : TTY=pts/18 ; PWD=/home/nobu ; USER=root ; COMMAND=/bin/systemctl status systemd-modules-load.service`

but I can boot and it seems like everything is operating normally on my Lenovo T420.  I think I started getting the "failed to start load kernel modules" after installing Nvidia 390.25 driver and CUDA Toolkit (using my machine for deep learning).  

I read somewhere else that it is a red herring.  I'm a linux newbie so hesitant to start editing system files while my computer seems to be operating fine.  Is this something that gets worse with time and eventually will be catastrophic?

---

