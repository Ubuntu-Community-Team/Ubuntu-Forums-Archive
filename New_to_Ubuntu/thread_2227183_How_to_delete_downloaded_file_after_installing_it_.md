---
title: "How to delete downloaded file after installing it on Lubuntu? (Chrome &quot;Package&quot;) ?"
date: 2014-05-31
forum: New to Ubuntu
---

### Post by fran_3 on 2014-05-31
I installed Chrome on a new install of lubuntu. I used Firefox to navigate to the Chrome download on the web. When Firefox asked me "Do what... Download or Install?" I chose Install. Seems like somewhere along the line I got asked something again but whatever Chrome got installed.

The Questions:

- Is there a 'compressed' chrome download file somewhere on the system that can be deleted after install?
- In Linux speak is a compressed application download called a 'package' ? (I saw that word popup along the way it seems)

(I replaced XP on an old system that has a small 40GB hard disk and just want to learn how to delete compressed downloaded programs after they are installed.)

Thanks for any help.

---

### Post by vasa1 on 2014-05-31
The package should be in */var/cache/apt/archives*; use *sudo apt-get clean* to remove all of those files.

---

### Post by bapoumba on 2014-06-01
If the file was downloaded from Firefox, it should be in the default folder for downloading files, so I guess /home/<your_user>/Downloads ?

---

### Post by Impavidus on 2014-06-01
The thing you downloaded was probably a .deb file, also known as a package. It consists of compressed software (not necessarily an application), together with a list of other packages it depends on and scripts for proper installation and deinstallation.

If you ask Firefox to download a file, it is stored by default in your Downloads directory. You can configure Firefox to do otherwise. If you ask Firefox to directly open the file, or in case of a package install it, Firefox will save the file in /tmp and call the application that can open the file, in this case one of the package installers, directing it to the downloaded file. All files stored in /tmp get automatically deleted on reboot, so it is probably deleted already.

Packages you install from the repositories are cached in /var/cache/apt/archives and can be removed as vasa1 indicated.

---

