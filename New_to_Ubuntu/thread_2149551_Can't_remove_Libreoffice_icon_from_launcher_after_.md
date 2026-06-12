---
title: "Can't remove Libreoffice icon from launcher after PPA upgrade to LO4."
date: 2013-05-29
forum: New to Ubuntu
---

### Post by kramer65 on 2013-05-29
Hello people,

Since I wanted to use the latest version of Libreoffice on my Ubuntu 12.04 install I used the following to add the new PPA and upgrade to the latest version:

```
sudo add-apt-repository ppa:libreoffice/ppa
sudo apt-get update
sudo apt-get dist-upgrade
```

I already had Libreoffice in my launcher. But after the upgrade when I click it, it simply opens a second item on the launcher and I can't remove the present icon anymore. When I right-click the icon it shows three lines: New Document, An empty line (I've never seen that), and Keep in launcher (even though it is already set to stay there). It doesn't show an option to take it away from the launcher.

Does anybody know how I can fix this? All tips are welcome!

---

### Post by gifford on 2013-05-29
Try to reinstall, but first remove the icon from the launcher, run "sudo apt-get purge libreoffice*". This will remove libreoffice, then install from the repository you have added.
Sorry, I misread your post. I would try to remove libreoffice, then see if you can't remove the launcher. Might also reboot after purging, then see if the icon is gone or try to remove it then.

---

### Post by kramer65 on 2013-05-31
Thanks! That worked indeed. After reinstalling and rebooting it was gone. Also, I now just installed LO writer and calc, since those are the only parts I need from Libreoffice.. :)

Cheers!

---

