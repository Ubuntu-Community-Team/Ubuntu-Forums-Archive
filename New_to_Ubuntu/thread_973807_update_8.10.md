---
title: "update 8.10"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by scragar on 2008-11-07
If I'm not mistaken Xububntu uses the update-manager, same as ubuntu, so this should work:```
sudo apt-get update **## update listings**
sudo apt-get upgrade **## install current updates**
sudo update-manager -d **## launch the update manager looking for a distro update**

```if the last line complains about command not found/not installed, try doing the update from the command line, which should work:
```
sudo apt-get dist-upgrade
```

---

### Post by awlinux on 2008-11-07
8.04 wil not automatically offer an upgrade as it is an LTS version if you are trying to upgrade via Synaptic.

See [here]("http://www.ubuntu.com/getubuntu/upgrading") which is the same for Xubuntu.

---

### Post by REDace0 on 2008-11-07
I had the exact same problem going from ubuntu 8.04 to 8.10. For some reason my update manager wouldn't see the upgrade even though I had my settings right in System>Administration>Software Sources. The solution I found was to manually edit the file /etc/apt/sources.list which lists the URLs of the repositories and some parameters describing how they are to be processed. I changed all occurences of "hardy" to "intrepid". Now, if you have manually added some obscure software sources there, they may not have intrepid packages up yet, in which case those won't update (unless they put some up). Note that you're going to have to use 'sudo' in order to edit /etc/apt/sources.list as it's protected.

Does this help? :)

---

