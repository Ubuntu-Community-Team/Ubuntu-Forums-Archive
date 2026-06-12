---
title: "System check?"
date: 2012-10-03
forum: New to Ubuntu
---

### Post by Yezinki on 2012-10-03
Good Morning,

I have a question, after a fresh Ubuntu install & apps needed is there some way, commands etc to check the OS/file system/kernels etc.

Just to have a peace of mind that all done is correct.

Btw Ubuntu is running fine, just feel it a bit bloated not as crisp after I run BleachBit the previously?

Thanks.

---

### Post by jerrrys on 2012-10-03
update and upgrade

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=update+and+upgrade&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=update+and+upgrade&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by Yezinki on 2012-10-03
Thanks jerrrys for the reply & posted link.

What exactly is fsck?

---

### Post by Lars Noodén on 2012-10-03
[fsck](http://manpages.ubuntu.com/manpages/precise/en/man8/fsck.8.html) checks and repairs file systems.  

[https://help.ubuntu.com/community/SystemAdministration/Fsck](https://help.ubuntu.com/community/SystemAdministration/Fsck)

It should only be used on unmounted file systems.

---

### Post by Yezinki on 2012-10-03
Thanks Lars Noodén.

How does one unmount a system & remount a system?

---

### Post by Lars Noodén on 2012-10-03
You can mount and umount with the programs 'mount' and 'umount', but it is not safe to work on a live system.  Better to use the Live DVD (desktop) and work from that.  

What are you trying to do?

---

### Post by Yezinki on 2012-10-03
Thanks Lars Noodén for your reply. Was thinking of checking file system read about fsck.

Installed Pidgin 1st than Skype & Kopete.....at times Pidgin acts up & becomes non responsive from the side quick launcher.

---

### Post by Lars Noodén on 2012-10-04
If you want to see more about your EXT file system you can also look at [tune2fs](http://manpages.ubuntu.com/manpages/precise/en/man8/tune2fs.8.html) or dumpe2fs.  Just don't change anything: If it's not broken, don't fix it. ;)

---

### Post by mikewhatever on 2012-10-04
I think you should just relax and enjoy the fresh install. No offence, but you'll likely cause more harm checking the system (with fsck and mount), then checking. 
Leave it alone. No need to fix what's not broken.

---

### Post by Yezinki on 2012-10-04
Thanks Lars Noodén & mikewhatever for your experienced suggestions.

---

