---
title: "how do I know the Software Updater is up to date?"
date: 2016-01-25
forum: New to Ubuntu
---

### Post by anotherChris on 2016-01-25
The website of the program Anki currently has Anki 2.0.33, but the Software Updater got me to 2.0.32.  How does information about software by non-Ubuntu-team developers get into the Software Updater, and does the Software Updater ever fail to keep us up to date?

Also:

What is the difference between using the Software Updater and

```
sudo apt-get update
```

And do these both check for updates for *all* my programs?

Thanks.  I'm... New to Ubuntu, as the forum says.

---

### Post by deadflowr on 2016-01-25
Part 1:
The [Masters of the Universe!!!]("https://wiki.ubuntu.com/MOTU")

Part 2: software updater and sudo apt-get update both run the same check for package updates.
The difference is the software updater will list any new updates that can be installed after it finishes the check.
to see new updates with apt-get you need to run another command
```
sudo apt-get upgrade
```
Also software updater has a builtin function called phased updates that is used to slowly release updates to users 
See: [https://wiki.ubuntu.com/PhasedUpdates](https://wiki.ubuntu.com/PhasedUpdates)

but basically both apt-get and the software center are looking and grabbing packages from the exact same place.
so their is no packages that one will see that the other won't.

---

### Post by grahammechanical on 2016-01-25
> How does information about software by non-Ubuntu-team developers get into the Software Updater,

Strictly speaking software does not get into Software Updater. They have to get into the Ubuntu archives or repositories. The developer has to submit his software for inclusion and a code audit has to be done before the software is included in the Ubuntu archives and then it appears in Ubuntu Software Centre & is also installable through apt-get.

Not only does this code audit take time but updated versions of applications go into the Ubuntu archives of new Ubuntu releases and are not backported into the archives of existing Ubuntu releases. I have also heard that due to a lack of volunteers there was or is a backlog of these code audits.

I think that Libreoffice & Firefox are two of the exceptions to this but generally speaking if we want a newer version of some utility or application we have to upgrade to a newer version of Ubuntu.

The Ubuntu developers are trying to change things. They developed Debian packaging into Click packaging and then evolved Click packaging in to Snappy packaging. This simplifies for developers both the packaging and the submission of applications for acceptance into the Ubuntu archives and at the same time greatly reduces the time that code audits take without compromising the need for security checks.

Should this new packaging concept become standard for Ubuntu desktop as it is on Ubuntu phones, then it will mean that as soon as a developer upgrades his application it can be submitted for inclusion in the app store and it will be accepted or rejected in minutes and not months as at present. It also means that there can be more than one version of an app in the app store at the same time. 

We wait and see if all this comes to pass.

P.S. Some reading about dpkg. That is also involved in the updating/upgrading of software packages.

[https://en.wikipedia.org/wiki/Dpkg](https://en.wikipedia.org/wiki/Dpkg)

---

### Post by anotherChris on 2016-01-25
Thank you both.  These answered my questions exactly.

---

