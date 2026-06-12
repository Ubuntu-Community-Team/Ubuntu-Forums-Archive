---
title: "can not shutdown or restart or even hibernate again after hibernate (ubuntu 18.04 LTS"
date: 2018-07-04
forum: New to Ubuntu
---

### Post by mohsenhasani5731 on 2018-07-04
I have a almost the problem match to this link ([https://askubuntu.com/questions/936442/ubuntu-hibernate-works-just-one-time#](https://askubuntu.com/questions/936442/ubuntu-hibernate-works-just-one-time#))
but In addition to the hibernate again i dont able shutdown or restart my laptop.


i have a ram with 8GB size and my swap partition is 11.2 GB  


help me please !


i think that is about swap . because at the first i don't have swap partition ( i have a swap file ) and i set it . after that i configure grub for mount swap partition at boot . 
any thing else need ? 



Result of 'journalctl -f' 
     
     nouveau 0000:01:00.0: DRM: failed to idle channel 0 [DRM]
     kernel: pci_pm_freeze(): nouveau_pmops_freeze+0x0/0x20 [nouveau] 
     returns -16
     dpm_run_callback(): pci_pm_freeze+0x0/0xe0 returns -16
     kernel: PM: Device 0000:01:00.0 failed to freeze async: error -16




`systemctl hibernate` or `pm-hibernate` have same problem 
but `s2disk` show saving progress and it be 100% and then hibernate but when resume . doesn't resume current state !

---

### Post by ajgreeny on 2018-07-04
You say you can not shutdown but what does command **shutdown now** (or reboot now) show in terminal?

---

### Post by rickdiaz on 2018-07-10
[COLOR=#000000][FONT=Ubuntu]Your system will shutdown, suspend, or hibernate when the following conditions are met:[/FONT][/COLOR]

[LIST]
[*]Any hosts that the computer is dependant on is not answering ping anymore.
[*]No keyboard or mouse activity has been detected on the computer for a while.
[*]And of course, the user has not disabled Autopoweroff.
[/LIST]

---

