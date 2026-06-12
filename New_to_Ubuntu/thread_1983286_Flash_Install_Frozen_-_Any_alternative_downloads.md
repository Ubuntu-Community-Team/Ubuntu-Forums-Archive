---
title: "Flash Install Frozen - Any alternative downloads?"
date: 2012-05-20
forum: New to Ubuntu
---

### Post by mr_luksom on 2012-05-20
Hi, 

I've done a clean install of Lubuntu 12.04, and I'm having problems installing flash.

The original install hung, and I had to restart it (10 hours). It appeared to hang at the end of the process (where flash/mp3 plugins are installed). I managed to install with no issues without the non-free plugins, however now I cannot install flash.

It appears to hang on the flash download - I get this far below:

```
Setting up xul-ext-ubufox (2.0.3-0ubuntu1) ...
Setting up libdbusmenu-gtk4 (0.6.1-0ubuntu3) ...
Setting up firefox (12.0+build1-0ubuntu0.12.04.1) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up update-notifier-common (0.119ubuntu8.1) ...
flashplugin-installer: downloading http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.235.orig.tar.gz
```

Are there any alternative downloads? I couldn't make sense of anything from the adobe site.

---

### Post by sikander3786 on 2012-05-20
First of all, make sure there aren't any half-configured packages by running this command:

```
sudo dpkg --configure -a
sudo apt-get install -f
```

If 'flashplugin-installer' is still causing problems, remove it and try the above mentioned commands again:

```
sudo apt-get purge flashplugin-installer
```

For installing Flash, you can use Flash-aid Firefox add-on:

[http://www.tuxgarage.com/2011/05/manage-your-flash-plug-ins-by-using.html](http://www.tuxgarage.com/2011/05/manage-your-flash-plug-ins-by-using.html)

Or, though none of these might work as smooth as Adobe Flash Player, you can try your luck with any of the alternatives mentioned here:

[http://www.tuxgarage.com/2012/02/adobe-drops-support-of-flash-for.html](http://www.tuxgarage.com/2012/02/adobe-drops-support-of-flash-for.html)

---

### Post by Cheesemill on 2012-05-20
If it's anything like my machine then it hasn't actually hung, you just don't get any feedback on the download progress of the flash .tar.gz file.

Just leave it a while to complete the download in the background then it will continue installing.

---

### Post by Gone fishing on 2012-05-20
Do you connect through a proxy?

In the past I've had a similar problem and but installed flash from the commandline without a problem.


```
sudo -i
``` **then** ```
apt-get install flashplugin-installer
```

---

