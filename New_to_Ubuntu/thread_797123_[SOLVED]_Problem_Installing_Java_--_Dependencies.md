---
title: "[SOLVED] Problem Installing Java -- Dependencies"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by jethin on 2008-05-17
I'm trying to install Java on my Xubuntu machine so I can run applets in Firefox. I've tried this as per another forum entry:

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

But I just get this error:

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-java6-jre: Depends: java-common (>= 0.24) but it is not installable
                 Depends: sun-java6-bin (= 6-06-0ubuntu1) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-06-0ubuntu1) but it is not installable
  sun-java6-plugin: Depends: sun-java6-bin (= 6-06-0ubuntu1) but it is not going to be installed
E: Broken packages
```

Can anyone help? I gotta tell you that I'm committed to this Linux thing, but it's been a *nightmare* trying to get my computer to do anything mcuh more than play solitaire thus far. Thanks, Jeremy

---

### Post by overdrank on 2008-05-17
> **jethin said:**
> I'm trying to install Java on my Xubuntu machine so I can run applets in Firefox. I've tried this as per another forum entry:

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

But I just get this error:

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-java6-jre: Depends: java-common (>= 0.24) but it is not installable
                 Depends: sun-java6-bin (= 6-06-0ubuntu1) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-06-0ubuntu1) but it is not installable
  sun-java6-plugin: Depends: sun-java6-bin (= 6-06-0ubuntu1) but it is not going to be installed
E: Broken packages
```

Can anyone help? I gotta tell you that I'm committed to this Linux thing, but it's been a *nightmare* trying to get my computer to do anything mcuh more than play solitaire thus far. Thanks, Jeremy

HI and it has been awhile since I have used XFCE but you may check to see if your repos have been enabled under software sources.

---

### Post by mikewhatever on 2008-05-17
Start Synaptic, go to Edit, and select Fix broken packages.

---

### Post by zvacet on 2008-05-17
Follow **overdrank** advice and check in system>admin>software sources that you have checked all under Ubuntu software and updates tab.Reload.You can try fix it like **mikewhatever** said but easier way to install it is to type in terminal

```
sudo apt-get install xubuntu-restricted-extras
```

> I gotta tell you that I'm committed to this Linux thing, but it's been a *nightmare* trying to get my computer to do anything mcuh more than play solitaire thus far.

[This]("https://help.ubuntu.com/community/HowToGetHelp") will be very useful for begining.

---

### Post by jethin on 2008-05-17
Thanks zvacet! I followed your (simple) instructions and, after a long download/install process, was able to re-run my original command and install Java. Problem resolved in under 12 hours.

And thanks for the documentation link as well. I have (and will continue to) spend a lot of time learning the ropes there. But one of the main reasons I want to stick with (X)ubuntu is because of the excellent community (see all posts above.) Now, on to the next issue... Thanks guys.

---

