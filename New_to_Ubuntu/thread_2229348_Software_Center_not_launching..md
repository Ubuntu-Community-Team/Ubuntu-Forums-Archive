---
title: "Software Center not launching."
date: 2014-06-12
forum: New to Ubuntu
---

### Post by neale3456 on 2014-06-12
When I go to launch the Software Center, it will not launch. I have tried some of the suggestions for those who have had this problem solved but to no avail have those worked. Thanks for the help.

---

### Post by jinglongtang on 2014-06-26
The same for me over here.
I already removed it and reinstalled it. Still not working.
If I start it in the Terminal with sudo I get this message:

2014-06-26 18:18:43,794 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
Traceback (most recent call last):
  File "/usr/bin/software-center", line 130, in <module>
    app = SoftwareCenterAppGtk3(options, args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 397, in __init__
    self.icons)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/installedpane.py", line 95, in __init__
    CategoriesParser.__init__(self, db)
  File "/usr/share/software-center/softwarecenter/db/categories.py", line 251, in __init__
    self._build_string_template_dict()
  File "/usr/share/software-center/softwarecenter/db/categories.py", line 303, in _build_string_template_dict
    region = "%s" % get_region_cached()["countrycode"]
KeyError: 'countrycode'

---

### Post by whitesmith on 2014-06-26
Some hardware information would help those of us who are not psychic. And what's the Ubuntu version?

---

### Post by ibjsb4 on 2014-06-26
Try to open it in terminal

```
gksudo software-center
```

[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

---

### Post by collisionystm on 2014-06-26
Try this.

Use ALT+ F2 to open the Run Command dialog. (or do it in terminal)

type

software-properties-gtk

and hit enter.

Go to the 'Other Software' tab and uncheck any extra PPA's you may have added. One of these may be causing your issue.

After closing run at the terminal

sudo apt-get clean
sudo apt-get update

Now try to open software center.

---

### Post by UT_Libertarian on 2014-07-01
having the same problem.  Tried "[COLOR=#000000]software-properties-gtk" in Terminal, and got "[/COLOR]/usr/bin/python: error while loading shared libraries: /lib/i386-linux-gnu/libssl.so.1.0.0: invalid ELF header"

---

### Post by collisionystm on 2014-07-01
> **UT_Libertarian said:**
> having the same problem.  Tried "[COLOR=#000000]software-properties-gtk" in Terminal, and got "[/COLOR]/usr/bin/python: error while loading shared libraries: /lib/i386-linux-gnu/libssl.so.1.0.0: invalid ELF header"


Do this

sudo bash

apt-get clean

apt-get update

apt-get dist-upgrade

Run the upgrade. Then see if you can open software center.

---

### Post by UT_Libertarian on 2014-07-01
During the execution of "apt-get update", it spits out a bunch of lines, the last of which are as follows:

Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                         
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en_US                    
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise Release.gpg                                              
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise Release
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free i386 Packages/DiffIndex
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free i386 Packages/DiffIndex
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free TranslationIndex
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free TranslationIndex
100% [Connecting to packages.medibuntu.org]

Before a number of the last lines appear, the "100% [Connecting to packages.medibuntu.org]" appears, but the last one seems to hang.  No change after several minutes.  Still waiting just in case I wasn't patient enough.

---

### Post by UT_Libertarian on 2014-07-01
During the execution of "apt-get update", it spits out a bunch of lines, the last of which are as follows:

Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                         
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en_US                    
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise Release.gpg                                              
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise Release
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free i386 Packages/DiffIndex
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free i386 Packages/DiffIndex
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free TranslationIndex
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free TranslationIndex
100% [Connecting to packages.medibuntu.org]

Before a number of the last lines appear, the "100% [Connecting to packages.medibuntu.org]" appears, but the last one seems to hang.  No change after several minutes.  Still waiting just in case I wasn't patient enough.

---

### Post by UT_Libertarian on 2014-07-01
Okay, so I waited.  It finished, with the following:

Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free TranslationIndex
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free i386 Packages
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free i386 Packages
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en_US
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en_US
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Fetched 1,773 kB in 9min 38s (3,066 B/s)   
W: Failed to fetch [http://packages.medibuntu.org/dists/precise/Release.gpg](http://packages.medibuntu.org/dists/precise/Release.gpg)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)


W: Failed to fetch [http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages](http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)


W: Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/binary-i386/Packages](http://packages.medibuntu.org/dists/precise/non-free/binary-i386/Packages)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)


W: Failed to fetch [http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en_US](http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en_US)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)


W: Failed to fetch [http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en](http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)


W: Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en_US](http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en_US)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)


W: Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en](http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)


E: Some index files failed to download. They have been ignored, or old ones used instead.



Then, when running the upgrade (in Terminal), I get the following:

/usr/bin/python: error while loading shared libraries: /lib/i386-linux-gnu/libssl.so.1.0.0: invalid ELF header
Processing ufw triggers failed. Ignoring.
Errors were encountered while processing:
 /var/cache/apt/archives/python-uno_1%3a3.5.7-0ubuntu6.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Software Center still fails to launch.

---

### Post by UT_Libertarian on 2014-07-03
Just realized a newer LTS version is available.  Will update, and go from there.

---

### Post by UT_Libertarian on 2014-07-03
Okay, so the Update Manager won't launch either.

---

### Post by UT_Libertarian on 2014-07-03
Found the corrupted file, restored valid copy.  Celebrations throughout the land.

---

