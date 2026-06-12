---
title: "[Ubuntu 16.04.4 LTS] Most of my basic command suddenly not working (apt,etc)"
date: 2018-07-18
forum: New to Ubuntu
---

### Post by cimani on 2018-07-18
Hello

i don't know what happening ,but my server acting really weird in the last 3 days 

maybe friend of mine doing something to the server or maybe got hacked

2 days ago there's additional open port which i didn't recognize (port 9090)

sudo apt-get
web server (port 80)

when i run this command 
```
sudo apt-get *
```

the cli return this
```
sudo: apt-get: command not found
```

i have no idea why this happen (im a windows user)

but in bash history i saw this line is executed
```
sudo apt-get --purge remove libstdc++6
```


This is my server detail
```
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.4 LTS
Release:        16.04
Codename:       xenial
```

---

### Post by wyliecoyoteuk on 2018-07-18
libstdc++6 is a c++ runtime library, which is needed for your commands.
Can you run dpkg?
If so you can reinstall the lost package
[https://askubuntu.com/questions/818752/how-to-fix-broken-libstdc6-which-also-breaks-apt](https://askubuntu.com/questions/818752/how-to-fix-broken-libstdc6-which-also-breaks-apt)
If there is an additional port, I would close it and investigate, you may well have been hacked.
[https://www.speedguide.net/port.php?port=9090](https://www.speedguide.net/port.php?port=9090)

---

### Post by Impavidus on 2018-07-18
Just checking on 18.04, there's a huge load of packages (including apt) depending on libstdc++6. I'm not sure it's the same on 16.04 (some may still depend on an older version, like libstdc++5), but I'm surprised the computer still works, more or less. But the fact that the command appears in the bash history doesn't guarantee that libstdc++6 and everything depending on it were actually removed. The person running the command may have aborted.

To see what was actually removed, read your logs:```
grep "purge\|remove" /var/log/dpkg.log
```You may have to check older log files too, in the same directory. You can do this from a live disk, if necessary. In that case, mount the partition with your log files and change the path in the command accordingly.

If you consider being hacked a serious possibility, wipe your hard drive, reinstall and restore your files from backups made before these strange things happened.

---

