---
title: "Problems Using Ubuntu Software Center"
date: 2015-05-19
forum: New to Ubuntu
---

### Post by Stephan_H_Smith on 2015-05-19
Today I decided to install the Ubuntu Restricted Extras package. It started to install, got 3/4 of the way done, and I got an error. t said that my installed packages have unmet dependencies. It said to start the package manager from the right click menu, which I did (after closing the copy that was running). It gave me the option to repair the broken programs. I clicked ok. Now, the repair is waiting for the stalled install to finish, which it can't do because of the error. How do I stop the stalled install and get the repair install to run? I don't see an option for stopping or starting installs in the menus and I need to fix this. Thanks!

---

### Post by Vladlenin5000 on 2015-05-19
I think I know where it stalled and why... Ubuntu Restricted Extras include Microsot TTF fonts. It should have appeared a dialogue window for you to accept the license. If I remember correctly there was a bug in 14.04 where that window never came.

You can try to finish that installation in the terminal
```
sudo apt-get install --reinstall ttf-mscorefonts-installer
```
Then, in the same terminal window the EULA will appear. Use TAB, the directional keys and enter to navigate and select the options. That done, you can use the following command to finish other pending installations: ```
sudo apt-get install -f
```

---

### Post by Stephan_H_Smith on 2015-05-19
Thanks, Vladlenin5000! I tried that after closing the Software Center. This is what I got: 

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

EDIT: Ok, the box for the microsoft EULA popped up. I accepted it and clicked ok, then the install errored out and asked me to report the bug. I did, and it said it was already reported. Software center then closed itself. When I reopened it, both jobs were gone from the progress tab. I don't know if the repair actually ran or not, because it never told me what software needed to be repaired, so I can't check it.

---

### Post by Vladlenin5000 on 2015-05-19
Try the common update/upgrade in terminal:
```
sudo apt-get update
sudo apt-get upgrade
```

Please report back any errors. If none then it won't hurt to check whether or not the remaining restricted extras were installed (by trying to install again). Also in terminal so you can see the errors:
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Stephan_H_Smith on 2015-05-19
Ok, here is the result of apt-get upgrade

The following packages were automatically installed and are no longer required:
  account-plugin-windows-live cabextract kde-l10n-engb libupstart1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


apt-get install ubuntu-restricted-extras said the same thing. I guess that means it installed ok? And I still have no idea about what needed to be repaired

---

### Post by Vladlenin5000 on 2015-05-19
Yes, everything is fine regarding the installation, apt-get is happy now :p
The suggestion to use 'autoremove' is optional. The listed packages are now orphan, no longer needed... In a nutshell, they're doing nothing therefore can be safely removed. However, there's no problem in keeping them and by removing you'll get back a few MB of free space at most.

---

### Post by Stephan_H_Smith on 2015-05-19
Sweet! Thank you much for your help!

---

### Post by Vladlenin5000 on 2015-05-19
You're welcome :p

If you consider the issue solved please use the thread tools in your first post to mark the thread as solved so other can benefit.

Happy Ubuntuing.

---

