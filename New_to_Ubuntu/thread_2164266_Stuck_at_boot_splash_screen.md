---
title: "Stuck at boot splash screen"
date: 2013-07-30
forum: New to Ubuntu
---

### Post by devongarber1 on 2013-07-30
Hello,
I seem to be having a problem when I boot up my computer. I use Kubuntu 13.04 but I thought I would try XFCE since my computer has had graphics issues in the past (which is actually the reason I use Kubuntu). But now when I boot up my computer it just endlessly pulses blue around the Kubuntu logo. I got the Xorg.0.log log and this is what the last few lines say: ```
[    33.393] (EE) NOUVEAU(0): [drm] failed to set drm interface version.[    33.394] (EE) NOUVEAU(0): [drm] error opening the drm
[    33.394] (EE) NOUVEAU(0): 820: 
[    33.394] (II) UnloadModule: "nouveau"
[    33.394] (EE) Screen(s) found, but none have a usable configuration.
[    33.394] 
Fatal server error:
[    33.394] no screens found
[    33.394] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    33.394] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    33.394] (EE) 
[    33.437] Server terminated with error (1). Closing log file.



``` I have a Compaq Presario 5430US with 1GB of RAM

---

### Post by mojo706 on 2013-07-31
Hello, has this problem occured during the first boot after installing XFCE or it is a subsequent boot? Do you see a recovery option during boot?

---

### Post by VMC on 2013-07-31
I'm a tad confused with your title. So does Xubuntu work OK, and you want to fix Kubuntu?

I don't know about the older "[COLOR=#000000][FONT=HPSimplified]64MB SDR nVidia™ GeForce2 MX ", but have you tried adding "nomodeset" to the kernel string?

When grub comes up, type 'e' then do to line that has "linix" in the beginning, then add *nomodeset* to the end of the line and push F10 to boot.
See if that at least boots past the Kubuntu logo.[/FONT][/COLOR]

---

### Post by devongarber1 on 2013-07-31
> [COLOR=#000000][FONT=HPSimplified]When grub comes up, type 'e' then do to line that has "linix" in the beginning, then add *nomodeset* to the end of the line and push F10 to boot.
See if that at least boots past the Kubuntu logo.[/FONT][/COLOR] That got me past the boot screen and when I got to the login I figured out what happened. I had accidentally installed XDM which apparently does not like either my monitor or my graphics :oops: . I just uninstalled it through the tty and everything started working again.

---

