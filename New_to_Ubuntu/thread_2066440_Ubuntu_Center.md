---
title: "Ubuntu Center?"
date: 2012-10-04
forum: New to Ubuntu
---

### Post by Yezinki on 2012-10-04
Installed various apps like Pidgin, VLC player, Skype, Kopete & Shutter using Ubuntu center is that the correct way or they should be installed via terminal or synaptics?

Shutter when clicked takes a bit to load, showing updating plugin load info........is that normal?

Thanks.

---

### Post by Frogs Hair on 2012-10-04
Using the software center is fine although the synaptic package manager is a nice tool should you choose to install it. I know gimp checks plugins while opening but I have not tried Shutter for quite a while because the default application serves my purposes. Shutter is a nice application though.

---

### Post by Yezinki on 2012-10-04
Thanks Frogs Hair for your reply.

Since am new to Ubuntu after a while how does one check updates of apps installed either from software center or synaptics?

Thanks again for clarifying about shutter.

---

### Post by alphacrucis2 on 2012-10-04
> **Yezinki said:**
> Thanks Frogs Hair for your reply.

Since am new to Ubuntu after a while how does one check updates of apps installed either from software center or synaptics?

Thanks again for clarifying about shutter.

If updated versions land in the repos then your system will offer to install them when it periodically checks the repos for updates. However except for bug and security fixes, many (most) apps don't get updated until the next Ubuntu release. There are some exceptions such as Mozilla T'bird and Firefox. Also some new versions on rare occasions get backported so enable the backports repo. Often new versions of popular software will be packaged up by enthusiasts on the launchpad ppa facility. However ppa versions are not supported by Ubuntu so use at your own risk. On the other hand I have rarely had issues with ppa versions. A couple of good web sites to follow are:

Webupd8   [http://www.webupd8.org/](http://www.webupd8.org/)

omgubuntu  [http://www.omgubuntu.co.uk/](http://www.omgubuntu.co.uk/)


Those sites are blogs which have news about new ppa's and lots of other ubuntu related stuff.

---

### Post by Yezinki on 2012-10-04
Thanks alphacrucis2 for sharing your expert advice.

If updated versions land in the repos then my machine will offer to install them even if they have been installed from Ubuntu software center?

---

### Post by alphacrucis2 on 2012-10-04
> **Yezinki said:**
> Thanks alphacrucis2 for sharing your expert advice.

If updated versions land in the repos then my machine will offer to install them even if they have been installed from Ubuntu software center?

Yes. Software Centre is just a front end for the dpkg (Debian package management) system that Ubuntu uses. There are a few front ends such as synaptic and software centre (graphical ones), apt-get (command line). All of them are using the same underlying package management system and database. You can also install Debian packages directly by downloading the corresponding deb file and installing by either double clicking on the file (by default that will cause software centre to install it or you can also install deb packages from the command line using the dpkg command. It is also possible to install software for which no deb package is available. However you should only do that as a last resort.

---

### Post by Yezinki on 2012-10-04
Thanks alphacrucis2 appreciate your expert assistance big time.

---

