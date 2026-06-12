---
title: "apt-get update can't find repository"
date: 2014-08-06
forum: New to Ubuntu
---

### Post by wimpy2 on 2014-08-06
Lubuntu 14.04. When I run <sudo apt-get update> I get 2  errors, which seem to be related:
> Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
W: Failed to fetch [http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

If I untick > **[http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu](http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu) trusty** main in Software Updater,  <sudo apt-get update> runs through OK. Is there an alternative source to the repository or can I safely leave it unticked?
Any help would be appreciated.

---

### Post by ian-weisser on 2014-08-06
Yes, you can safely untick it. Or delete it.

404 means the same thing it does on a web page - that the page, if it used to exist, no longer does.
The PPA you were (or still are) using has been withdrawn, or perhaps you have upgraded to a version of Ubuntu that PPA does not support.
If you don't use that software anymore, time to uninstall it.

---

### Post by claracc on 2014-08-06
The message you receive is completely correct.

When I write in firefox the first url given, [http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu/dists/trusty/main/binary-i386/Packages) I also obtain a 404 not found error, since the software addressed is not there.

If you see with firefox the second url given: [http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu/dists/](http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu/dists/) , you can see there is not any Trusty directory, so the software cannot be found. See attached image.

What for is this ppa?

---

### Post by wimpy2 on 2014-08-06
Thank you both for your replies.
@**claracc** I have no idea what this repository contains. It must have existed at some time or even moved to a new address. From what you've said it seems that it just doesn't exist.
I'll follow **ian-weisser**'s advice and leave it unticked in Software Updater. I'll mark this as "Solved"

---

### Post by claracc on 2014-08-07
You are very welcome.

Glad you got fixed your problem.

---

### Post by wimpy2 on 2014-08-07
@**claracc** I had a look at another lubuntu 14.04 installation on one of my other PCs. This second one was using grub4dos as its bootloader and had not used grub2. I recall that I not only re-activated grub2 on the problem PC, but I also installed the grub2 customizer, which kept crashing. I uninstalled the customizer and have since reverted back to grub4dos on the problem PC. At the moment there are some other repositories, like the one I unticked which are not on the second PC. I presume the customizer put them in, when it was installed. Both lubuntus run OK, but I don't know how to completely remove these repositories from Software Updater. I guess I'll have to do some more reading. :)

---

### Post by claracc on 2014-08-07
One easy way to add or remove ppa repositories is through update manager.

You run update manager, and then click on settings tab, in the new window appearing, you select other software tab, there you have a list of ppa repositories that you can enable by click on its left square or disable if unticked. Also, trough add and remove tabs you can add or remove ppas.

I attached two images, one of update manager and one with the ppas I have, note the docky one is disabled.

---

### Post by wimpy2 on 2014-08-07
@**claracc** Thanks for the advice. I used the Remove (Quitar) button to get rid of those repositories, and it worked like a charm. I'm most grateful for your help.

---

