---
title: "Linux unistalled needed packages"
date: 2021-05-05
forum: New to Ubuntu
---

### Post by merken667 on 2021-05-05
Hi,

I uninstalled *pcmanfm* as it froze while looking through files. During uninstalling it told me:

```
The following packages were automatically **installed and are no longer required**:
  fonts-crosextra-caladea fonts-crosextra-carlito fonts-linuxlibertine fonts-sil-gentium fonts-sil-gentium-basic gstreamer1.0-gtk3 libabw-0.1-1 libapache-pom-java libbsh-java libcommons-logging-java
  libcommons-parent-java libe-book-0.1-1 libel-api-java libepubgen-0.1-1 libetonyek-0.1-1 libhsqldb1.8.0-java libjsp-api-java libllvm6.0 libllvm7 libllvm8 libllvm8:i386 libllvm9 libllvm9:i386
  **libreoffice**-avmedia-backend-gstreamer **libreoffice**-base **libreoffice**-base-core
```

I used *apt autoremove* command and it uninstalled my libreoffce suite. So looks like *autoremove* command is inconsistent and also removes important **needed** parts of the system and your applications? Isn't *autoremove* command dangerous for your applicaions? I needed libreoffice and it actually has nothing to do to pcmanfm.

I use Lubuntu.

---

### Post by Dennis N on 2021-05-05
You are not alone. You have to be careful with that. The man page for apt (which documents the command) contains a warning:

> You should check that the list does not include applications you have grown to like even though they were once installed just as a dependency of another package. You can mark such a package as manually installed by using apt-mark(8). Packages which you have installed explicitly via install are also never proposed for automatic removal.

So, if you see something that you want to keep show up in the autoremove list, use **apt-mark manual <package>** to prevent removal with autoremove:
```
sudo apt-mark manual libreoffice*
```
should protect all package names beginning with libreoffice from autoremoval.

You can check what a package depends on with **apt depends <package>**

---

### Post by ActionParsnip on 2021-05-05
What is the output of
```

apt-cache policy libreoffice

```
Thanks

---

### Post by Impavidus on 2021-05-05
You had a package (I think it was lubuntu-desktop) that's there to automatically install a full Lubuntu desktop environment. It triggers automatic installation of both pcmanfm and libreoffice. Then you removed pcmanfc (BTW, a bit drastic to remove it because it freezes. Why not investigate first? Chances are there's something wrong with your system that will disrupt file management no matter what file manager or command line tools you use). This tells the package manager that you don't want the full Lubuntu desktop environment and lubuntu-desktop is removed too. And all packages automatically installed to satisfy dependencies of lubuntu-desktop become autoremovable. The package manager isn't very good at guessing what software you need.

You can simply reinstall libreoffice. All settings and documents should still be there.

---

