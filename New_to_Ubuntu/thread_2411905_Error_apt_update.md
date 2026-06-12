---
title: "Error apt update"
date: 2019-02-05
forum: New to Ubuntu
---

### Post by richoandika on 2019-02-05
after uninstall docky i got this, What should i do?

```
richoandika@hp:~$ sudo apt update
Hit:1 http://archive.ubuntu.com/ubuntu bionic InRelease
Hit:2 http://ppa.launchpad.net/bluetooth/bluez/ubuntu bionic InRelease
Hit:3 http://ppa.launchpad.net/bovender/bovender/ubuntu bionic InRelease 
Hit:4 http://archive.ubuntu.com/ubuntu bionic-updates InRelease          
Ign:5 http://ppa.launchpad.net/docky-core/stable/ubuntu bionic InRelease 
Get:6 http://archive.ubuntu.com/ubuntu bionic-backports InRelease [74,6 kB]
Hit:7 http://ppa.launchpad.net/linuxuprising/java/ubuntu bionic InRelease
Hit:8 http://archive.ubuntu.com/ubuntu bionic-security InRelease         
Hit:9 http://ppa.launchpad.net/webupd8team/java/ubuntu bionic InRelease  
Err:10 http://ppa.launchpad.net/docky-core/stable/ubuntu bionic Release
  404  Not Found [IP: 91.189.95.83 80]
Reading package lists... Done
E: The repository 'http://ppa.launchpad.net/docky-core/stable/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

---

### Post by oldos2er on 2019-02-05
Remove it. There's no bionic repo there, which is why you're getting a 404.

---

### Post by deadflowr on 2019-02-05
Remove the docky-core ppa.
```
sudo add-apt-repository --remove ppa:docky-core/stable
sudo apt update
```

They never built it for 18.04, only up to 17.10.

^ninja'd

---

### Post by richoandika on 2019-02-05
> **deadflowr said:**
> Remove the docky-core ppa.
```
sudo add-apt-repository --remove ppa:docky-core/stable
sudo apt update
```

They never built it for 18.04, only up to 17.10.

^ninja'd

Thanks broo

---

