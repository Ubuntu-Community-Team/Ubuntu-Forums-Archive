---
title: "Problem with libgtk2.0-dev"
date: 2006-10-01
forum: Programming Talk
---

### Post by bayger on 2006-10-01
Hello! I have a strange problem installing libgtk2.0-dev from repositories. It seems that binary version is newer than the dev version and synaptic throws some dependency error. Does anyone know how to solve this problem? I am complete beginner in linux programming. I'd like to learn gtk+ programming, but I can't install required packages. Thanks in advance for any help.

---

### Post by bayger on 2006-10-01
How to resolve the following problem (sudo apt-get install libgtk2.0-dev):

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libgtk2.0-0 (= 2.8.17-1ubuntu5) but 2.8.20-0ubuntu1 is to be installed
                 Depends: libpango1.0-dev (>= 1.10.0-2) but it is not going to be installed
E: Broken packages

Anybody? Please... :)

---

### Post by Perfect Storm on 2006-10-01
Do you by any chance have any un-official source in your sourcelist?

---

### Post by bayger on 2006-10-01
I figured out what was the problem. Indeed, I had some unofficial repositories added to the apt. Thank you for your reply. And sorry for confusion. Btw: it was probably easyubuntu that caused the problem. So be careful with this package.

Regards,
Bayger

---

### Post by Godzig on 2006-10-21
I'd love to see the sources.list that worked on this; as far as I can tell (admittedly newbie) I'm using the original sources.list (pre-easyubuntu which was probably the culprit for me as well) and I've tried update et al, but it still won't let me install libgtk2.0-dev with the exact same errors you were getting.

---

### Post by dizm on 2006-12-06
This worked for me:
<<<___
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
___
don't forget:
$ sudo apt-get update
$ sudo apt-get -f install
before
$ sudo apt-get install libgtk2.0-dev

right after this the gnome update manager went ahead and updated everything again, but it still looks ok.

[dapper,gnome,686]

---

