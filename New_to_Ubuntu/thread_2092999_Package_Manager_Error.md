---
title: "Package Manager Error"
date: 2012-12-09
forum: New to Ubuntu
---

### Post by Cuencano on 2012-12-09
I tried to install Picasa on Ubuntu 12.10 (64 bit) but the installation did not complete, and now I have a Package Manager error: "Error BrokenCount>0. This usually means that your installed packages have unmet dependencies"

I ran:  sudo apt-get check

With this result:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 picasa : Depends: libc6-i386 (>= 2.2) but it is not installed
          Depends: lib32asound2 but it is not installed
          Depends: lib32z1 but it is not installed
E: Unmet dependencies. Try using -f.

This is probably a pretty simple problem but I don't know how to fix it, and I would be grateful for any help.

Thanks.

---

### Post by RossDoughty on 2012-12-09
Sorry if you have already done this, but have you run:

apt-get -f install

Thanks,
Ross.

---

### Post by Cuencano on 2012-12-09
> **RossDoughty said:**
>  Sorry if you have already done this, but have you run:

apt-get -f install

Thanks,
Ross.

If I try that command, I get:

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by oldos2er on 2012-12-09
> **Cuencano said:**
> If I try that command, I get:

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Use 'sudo': ```
sudo apt-get install -f
```

---

### Post by Cuencano on 2012-12-09
> **oldos2er said:**
> Use 'sudo': ```
sudo apt-get install -f
```


That seems to have solved it.

Thanks

(and the mome raths outgrabe)

---

