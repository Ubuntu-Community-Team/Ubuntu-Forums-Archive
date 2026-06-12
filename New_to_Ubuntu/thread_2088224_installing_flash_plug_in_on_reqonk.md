---
title: "installing flash plug in on reqonk"
date: 2012-11-25
forum: New to Ubuntu
---

### Post by jeebuz on 2012-11-25
Package not found - QApt Batch Installer

"The package "flashplugin-installer" has not been found among your software sources. Therefore, it cannot be installed. "


Can someone please break it down to me? First time on linux :) ty

Btw im trying to install google chrome, heres what happens when im trying to unpackage it: 
Package - google chrome installer
Status - Error: Cannot satisfy dependencies. 

What to do?

---

### Post by whatthefunk on 2012-11-25
If you install the restricted-extras package for your distro, it should come with the flash installer.

ubuntu-restricted-extras
kubuntu-restricted-extras
xubuntu-restricted-extras
lubuntu-restricted-extras

---

### Post by jeebuz on 2012-11-25
> **whatthefunk said:**
> If you install the restricted-extras package for your distro, it should come with the flash installer.

ubuntu-restricted-extras
kubuntu-restricted-extras
xubuntu-restricted-extras
lubuntu-restricted-extras

Just installed kubuntu's restricted extras pack and didn't fixed it mate. I'd also aprecciate a comment on the google chrome issue, if you please, ty.

---

### Post by whatthefunk on 2012-11-26
flashplugin-installer is in the repos and shows up in my software sources.  Check your software sources list by opening Muon Package Manager and going to **Settings** > **Configure Software Sources**.  On the first tab, Kubuntu Software, be sure that all boxes are checked.  Once they are all checked, close the Software Sources window and click **Check for Updates** on the Muon Package Manager toolbar.  Search for flashplugin-installer and you should find it.

About Google Chrome...Ive never installed it, but maybe I can help you out.  How are you trying to install it?  The best way would be to enable the Google Chrome PPA.  The PPA will include all dependencies your system needs.
[http://www.howopensource.com/2011/10/install-google-chrome-in-ubuntu-11-10-11-04-10-10-10-04/](http://www.howopensource.com/2011/10/install-google-chrome-in-ubuntu-11-10-11-04-10-10-10-04/)

---

### Post by newb85 on 2012-11-26
Specifically, the flashplugin-installer is in the multiverse repo.

If you go to the [Google Chrome Webpage]("http://www.google.com/aclk?sa=l&ai=CobyTc1CzUOzbD8aByQHCvYD4CNn3hbQCib7h5RuYtYDDRwgAEAEgwcLYF1CigbjN_v____8BYMnupoj0o_gPmAHT8gegAf31yPYDyAEBqgQZT9CxpDyTSUG-8032KI_z7GZXtruqTCQoLYAFkE4&sig=AOD64_3pqu3w-K2PYZySVi5KxS22umIZWw&ved=0CC8Q0Qw&adurl=http://www.google.com/chrome/intl/en/make/download.html%3F%26brand%3DCHMB%26utm_campaign%3Den%26utm_source%3Den-ha-na-us-sk%26utm_medium%3Dha&rct=j&q=google+chrome"), click "Download Chrome", select the proper version, and click "Accept and Install", it should add said PPA automatically.

---

