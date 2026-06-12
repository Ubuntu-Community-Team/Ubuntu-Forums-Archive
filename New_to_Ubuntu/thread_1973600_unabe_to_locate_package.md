---
title: "unabe to locate package"
date: 2012-05-05
forum: New to Ubuntu
---

### Post by mooshi222 on 2012-05-05
hi, i've just installd ubuntu 12.04 and i want to istall startup manager using synaptic package manager or software center but it is not listed when i search for it's name.I also tried terminal,but i recieve the error(unable to locate package) :( ;i thought that the problem is of repositories so i checked that universe software reposotory is enabled in synaptic and software center!:confused::confused:

---

### Post by codemaniac on 2012-05-05
Dear mooshi222 ,
Welcome to the world of UbuntuForums .

I can find it in the repos .
```
sudo apt-cache search startupmanager
```
go ahead and install it .

```
sudo apt-get install startupmanager
```

---

### Post by mooshi222 on 2012-05-05
thank you but again i receive the same error :unable to locate package startupmanager:(

---

### Post by oldos2er on 2012-05-05
Startupmanager's been removed from the repositories since it's no longer being developed. It's recommended to use Grub Customizer instead.

[https://launchpad.net/startup-manager/+announcement/8300](https://launchpad.net/startup-manager/+announcement/8300)

---

### Post by codemaniac on 2012-05-06
> **oldos2er said:**
> Startupmanager's been removed from the repositories since it's no longer being developed. It's recommended to use Grub Customizer instead.

[https://launchpad.net/startup-manager/+announcement/8300](https://launchpad.net/startup-manager/+announcement/8300)

I am on a Ubuntu Server 11.10 , and it is still in the repos .
```
root@codemaniac:/home/codemaniac# apt-cache search startupmanager
startupmanager - Grub, Usplash and Splash screen configuration
```

---

### Post by oldos2er on 2012-05-06
It's not in the 12.04 repos though.

---

### Post by philinux on 2012-05-06
> **oldos2er said:**
> Startupmanager's been removed from the repositories since it's no longer being developed. It's recommended to use Grub Customizer instead.

[https://launchpad.net/startup-manager/+announcement/8300](https://launchpad.net/startup-manager/+announcement/8300)

For the OP >  Grub Customiser link.

[https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

This is not in 12.04 repo. It's via a ppa.

---

### Post by codemaniac on 2012-05-06
> **oldos2er said:**
> It's not in the 12.04 repos though.

Thanks oldos2er for the enlightenment .

---

