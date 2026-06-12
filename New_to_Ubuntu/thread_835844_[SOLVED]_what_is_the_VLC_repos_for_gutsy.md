---
title: "[SOLVED] what is the VLC repos for gutsy?"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by sharks on 2008-06-20
what is the VLC repos for gutsy?

---

### Post by kerry_s on 2008-06-20
just open up synaptic and turn all the repo's on.
synaptic> settings> repositories

---

### Post by RomeReactor on 2008-06-20
A repo--or repository--tells the package managers in your Ubuntu system (Synaptic, Add/Remove, Aptitude, Apt-Get) where to look for programs to install; adding repositories increases the number of packages available for installation through those package managers, or lets you install a newer version of a certain program than what is found in the official repositories.

If you have your system up to date, you can install VLC from the official repositories. The version for Gutsy is 0.8.6--the same as the newest version from their site. You can find the program in Syanptic, or to install from the terminal:
```
sudo aptitude install vlc
```

EDIT: The version from the VideoLan site seems to be slightly more up to date (version 0.8.6 h) compared to the version in the official repositories for Gutsy (0.8.6 c). Don't know how significant is the difference between them, though. However, you shouldn't have any problem installing the version already available from the Ubuntu repositories.

---

### Post by jrusso2 on 2008-06-20
> **RomeReactor said:**
> A repo--or repository--tells the package managers in your Ubuntu system (Synaptic, Add/Remove, Aptitude, Apt-Get) where to look for programs to install; adding repositories increases the number of packages available for installation through those package managers, or lets you install a newer version of a certain program than what is found in the official repositories.

If you have your system up to date, you can install VLC from the official repositories. The version for Gutsy is 0.8.6--the same as the newest version from their site. You can find the program in Syanptic, or to install from the terminal:
```
sudo aptitude install vlc
```

EDIT: The version from the VideoLan site seems to be slightly more up to date (version 0.8.6 h) compared to the version in the official repositories for Gutsy (0.8.6 c). Don't know how significant is the difference between them, though. However, you shouldn't have any problem installing the version already available from the Ubuntu repositories.

The reason for all the 0.8.6 versions is security fixes, there was a number of security issues that affected VLC the last year.

---

### Post by RomeReactor on 2008-06-20
> **jrusso2 said:**
> The reason for all the 0.8.6 versions is security fixes, there was a number of security issues that affected VLC the last year.

I wasn't aware of that (haven't used VLC in a very long while); thanks.

---

