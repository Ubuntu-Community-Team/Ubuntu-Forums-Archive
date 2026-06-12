---
title: "Uninstalling Google Chrome"
date: 2016-01-23
forum: New to Ubuntu
---

### Post by n2te on 2016-01-23
I'm a new user to Linux & Ubuntu (14.04 LTS) and getting comfortable with navigating about the GUI. (enjoying it immensely. Wish I had switched to Linux a long time ago.)  I realized after installing the Google Chrome browser and launching it that it will not run on the older 32 bit machine which I installed it on.  I want to remove/uninstall it but the Software Center does not show it as being installed in any of the listed categories and thus I can't uninstall it.  What might I be doing wrong?
Thanks.
Eddie

---

### Post by sandyd on 2016-01-23
Hi,

Please post the output of
```

dpkg -l | grep google
```

This will list all of your packages that start with "google", one of them should be google chrome.

---

### Post by monkeybrain20122 on 2016-01-23
Open the terminal (fastest way is to press ctrl+alt+t), then type
```
sudo apt-get remove google-chrome-stable
```

Only applications from Ubuntu's repositories show up in the Software Centre apparently. I suggest installing synaptic as a  much better gui package manager, it shows you all the packages installed and third party repositories (and a lot more info) and it is much faster than the Software Centre. The only things that are in the Software Centre but not synaptic are paid apps.

You can install it either from the Software Centre (synaptic-package-manager) or from the terminal 
```
sudo apt-get install synaptic
```

---

### Post by sammiev on 2016-01-23
Hi,

When you remove the wrong version of Google Chrome, no use to install the [32bit version]("http://www.omgubuntu.co.uk/2016/01/google-chrome-linux-32-bit-discontinued") as it's almost at it EOL. (End Of Life)

---

### Post by $yl9pAR%t on 2016-01-23
It is easy to overlook in Software Center because it has not got well known Google Chrome icon there. Look for google-chrome-stable, it has description "The web browser from Google".

---

### Post by n2te on 2016-01-24
Great & helpful information. Thank you. Both commands executed  successfully. The Synaptic app looks really neat and very helpful.  I haven't read  through the corresponding user manual yet but with a quick glance at the  beginning of the manual it describes the "Package List" shown on the  left of the screen as "Lists known packages".  What is meant by "*known*"?  Packages that are globally registered somewhere? (My apologies if this  is a dumb question.) Is this essentially like a one stop shopping  resource to find a package of interest? (I guess I need to read up more  on the world of packages.) The first listed category, "Amateur radio  (universe)" got me excited. Need to explore that one.
Thanks.
Eddie (N2TE)

---

