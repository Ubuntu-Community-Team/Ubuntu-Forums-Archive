---
title: "install .rpm files on old kubuntu"
date: 2011-12-08
forum: New to Ubuntu
---

### Post by Gweld on 2011-12-08
I am newbie and using old version of kubuntu. I want to install .rpm files but  some of commands including 'apt-get' and is not working. please help.

---

### Post by Lars Noodén on 2011-12-08
The [RPM](http://rpm.org/) package manager is for Red Hat and related distros.  You can try using [alien](http://manpages.ubuntu.com/manpages/precise/en/man1/alien.1p.html) to install RPMs, but you are better off looking in [Ubuntu's own repostority](http://packages.ubuntu.com/) for the same package and install it from there.

---

### Post by editheraven on 2011-12-08
Look here : [http://kitenet.net/~joey/code/alien/]("http://kitenet.net/%7Ejoey/code/alien/") .

```
$sudo apt-get update
$sudo apt-get install alien
$man alien
```Theoretically you can install any other format (slackware, rpm etc) on a deb distro. However, i do not recommend using it. What RPM package do you want to install?

le : i see that someone else posted while i was typing.

---

### Post by BBQdave on 2011-12-08
> **Gweld said:**
> I am newbie and using old version of kubuntu. I want to install .rpm files but  some of commands including 'apt-get' and is not working. please help.

Hi Gweld, you are mixing two different GNU/Linux distro's.  Kubuntu (based on Debian) uses **.deb** files.  Fedora (based on Red Hat Linux Enterprise) uses **.rpm** files :)

You could update Kubuntu to the latest release, which may help with some of your software concerns.  Or if you have older hardware, you could use Kubuntu 10.4 LTS.  Either way, you can use **Software Center** or **Synaptic Package Manager** to install software (**.deb** files).

Most software comes both in **.deb** and **.rpm**, so you just need to track down the **.deb** file of the software you want to install.

Or if you prefer **.rpm** files, you can install Fedora Linux.

---

