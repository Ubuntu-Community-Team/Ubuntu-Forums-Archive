---
title: "Software updater keeps installing network manager after I intentionally uninstall it."
date: 2018-02-16
forum: New to Ubuntu
---

### Post by almostamyth on 2018-02-16
On Lubuntu 17.10, I was having dropped wifi with the Gnome network manager and none of the solutions I tried on Ubuntu forums helped.  So I decided to install Wicd and remove the Gnome default network manager using the steps described here: [https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD).

Everything went fine.  Wicd installed and connected without a problem and Gnome uninstalled flawlessly.  The gnome icon disappeared and I now only see the Wicd icon in the task bar.

Great right?  Well every time I run software updater, it reinstalls the Gnome network manager.  I then see the Gnome icon next to the Wicd icon.  So I have to go through the Gnome uninstall process again.

Is there a way to stop the software updater from installing Gnome Network Manager?  Thank you.

P.S. Please don't address the wifi drop issue I was having with Gnome.  Not interested in trying to make Gnome work, just want it to be gone and not come back.  Thanks again.

---

### Post by ajgreeny on 2018-02-16
I am using 16.04 and in that version **network-manager-gnome** is a dependency of the **lubuntu-desktop** package and that is what keeps bringing back the network-manager-gnome.

**lubuntu-desktop** is just a meta-package so does nothing except pull in all the packages needed for the full Lubuntu OS, so it can be safely removed from your system and will not affect anything apart from updating your system to 18.04, if that is what you intend after April this year.

If you do want to update to 18.04 rather than clean install, you can simply install the lubuntu-desktop package to your 17.10 first, then do the system version upgrade.

---

### Post by vasa1 on 2018-02-16
> **almostamyth said:**
> ...
Great right?  Well every time I run software updater, it reinstalls the Gnome network manager.  I then see the Gnome icon next to the Wicd icon.  So I have to go through the Gnome uninstall process again.
...
Instead of using the software updater, please consider using the command-line: *sudo apt-get update* and *sudo apt-get dist-upgrade*. Then you can post the output of both commands so that people can see clearly what is going on.

---

### Post by tinylagarto on 2018-02-16
I also guess it depends on the meta package lubuntu-desktop.

See:

```
apt depends lubuntu-desktop

```
It will definitely show you that it depends on the package:

```
network-manager-gnome



```

Now if you were to use the terminal like already mentioned by others you would probably see that you can uninstall the meta package with an autoremove:

```
sudo apt autoremove 
```

---

### Post by wildmanne39 on 2018-02-16
*Thread moved to **New to Ubuntu**.*

---

