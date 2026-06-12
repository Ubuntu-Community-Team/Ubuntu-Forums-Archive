---
title: "Naming conventions for original packages in PPA"
date: 2010-08-31
forum: Packaging and Compiling Programs
---

### Post by SwedishWings on 2010-08-31
I have my own original package in my personal PPA and want to name it correctly.

Reading through the documentation on Ubuntu naming conventions leave me somewhat confused. There is very little on how to name **original** packages. It describes mostly repackaging of upstream packages from Debian, or modified packages.

Can someone explain the correct naming for an **original** package as it should be written in Debian/changelog?

What i need to know, is the correct format of the version number and how to distinguish between Karmic, Lucid etc.

Thanks in advance,
Mike

---

### Post by Bachstelze on 2010-08-31
If the version is for example 3.21, name it 3.21-1~foo1. You can replace foo with karmic, lucid, etc. to differentiate them.

---

### Post by KdotJ on 2010-08-31
Can't you just have ubuntu there instead of the defined release 

Eg.
package-1.0ubuntu1

---

### Post by Bachstelze on 2010-08-31
Technically you can but it's generally a bad idea to have the same version on different packages (packages on different releases must be different, because you have the release name in debian/changelog).

---

### Post by SwedishWings on 2010-09-01
Thanks for the replies!

The next issue i face is to upload this to another ppa than my personal. I had no problems upload to my personal ppa with:

```
$ dput -f ppa:mikael-sesamiq/ppa macfanctld_0.2~karmic_source.changes 
```

I have registered a ppa ([https://launchpad.net/macfanctld](https://launchpad.net/macfanctld)) but can't find out how to use dput to upload to that ppa. I have tried all ways i can think of but always get rejections.

What would be the correct dput command to do this? Or, perhaps i have configured it wrong? 

Thanks in advance,
Mike

---

### Post by Bachstelze on 2010-09-01
Maybe the GPG key you use to sign your packages is not registered for this PPA?

---

