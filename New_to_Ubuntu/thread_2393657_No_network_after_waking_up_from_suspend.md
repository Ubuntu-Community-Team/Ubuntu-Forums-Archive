---
title: "No network after waking up from suspend"
date: 2018-06-06
forum: New to Ubuntu
---

### Post by Habibie on 2018-06-06
I just installed LUbuntu 18.04 on my old AMD Phenom II X3 with a 4 GB RAM. Upon waking up from a suspend, my computer can no longer connect to my LAN and *ifconfig* shows no IP Address. Has anyone encountered such an issue and can offer a solution?

---

### Post by Habibie on 2018-06-08
Finally, I found this [solution]("https://ubuntuforums.org/showthread.php?t=2355314&page=2&p=13622400#post13622400") to resolve this issue. Basically, I did the following:


[LIST=1]
[*]Run this *lshw -C network* as root to find out the kernel driver name for my Ethernet card. This will be needed in the script below.
[*]Then, create [COLOR=#000000][FONT=&amp]/lib/systemd/system-sleep/wakeon_suspend[/FONT][/COLOR] file and make it executable (chmod 755 [COLOR=#000000][FONT=&amp]/lib/systemd/system-sleep/wakeon_suspend[/FONT][/COLOR])
[/LIST]

The content of [COLOR=#000000][FONT=&amp]/lib/systemd/system-sleep/wakeon_suspend[/FONT][/COLOR] file is shown below. I hope this will help others.#!/bin/sh

```
#!/bin/sh
ModName="r8169"

case $1/$2 in
  pre/*)
    echo "activate $2..."
    /bin/systemctl stop network-manager.service
    /sbin/modprobe -rf $ModName
    ;;
  post/*)
    echo "wakeup from $2..."
    /sbin/modprobe $ModName
    /bin/systemctl start network-manager.service
    ;;
esac
```

---

### Post by danthonyd on 2018-06-08
Install dconf-editor
then under org/gnome/desktop/screensaver/picture-uri change the path.

---

