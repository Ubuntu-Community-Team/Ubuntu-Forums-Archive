---
title: "Unmet dependencies while installing qt-sdk (libgl1-mesa-glx)"
date: 2013-04-28
forum: New to Ubuntu
---

### Post by Gart3nzw3rg on 2013-04-28
Hey everyone!

I am currently running Ubuntu 13.04 and I tried to install the qt sdk today.

I used apt-get install qt-sdk and got an error that some packages have unmet dependencies. After digging a little deeper I found the responsible package:

```
libgl1-mesa-glx (= 9.1.1-0ubuntu3) but 9.2.0~git20130216.dd599188-0ubuntu0sarvatt~quantal is to be installed
```

I searched for it with the synaptic package manager and pressed control+e to downgrade it but it says that when I downgrade the package then many other packages will be removed. Is it safe to downgrade? If not, what else can I do to fix it?

---

### Post by gordintoronto on 2013-04-28
Nothing good has ever happened when I let the system remove packages.

I have 32-bit Ubuntu 13.04 installed in VirtualBox. I just used Synaptic Package Manager to install qt-sdk. There was a warning message about phonon, but otherwise it went very smoothly. I'm pretty sure libgl1-mesa-glx was present before I installed qt-sdk.

Did you upgrade to 13.04 or do a fresh install?

---

### Post by Gart3nzw3rg on 2013-04-29
I upgraded to 13.04 but I had the same problem while I was still running 12.10. I can do a fresh install but I would prefer not to because then I would have to set up everthing again.

---

### Post by Yellow Pasque on 2013-04-29
You have the xorg-edgers PPA installed (and you still have old quantal packages from it that are messing apt up). You should remove the PPA unless you still need it.
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:xorg-edgers/ppa
```

---

### Post by Gart3nzw3rg on 2013-04-29
Thanks for the response.

When I try to remove it it says: "Warning:  Could not find package list for PPA: xorg-edgers ppa"

When I search for xorg in sources.list and sources.list.d/* I get:

/etc/apt/sources.list.d/xorg-edgers-ppa-quantal.list.save:deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) quantal main

Is that the PPA that needs to be removed?

---

### Post by Yellow Pasque on 2013-04-29
Yeah, that's the one.

---

### Post by Gart3nzw3rg on 2013-04-29
Sorry I just can't get to remove it. Whats the exact command that I need? 

No matter what I try, I get: Warning:  Could not find package list for PPA: ...

---

### Post by Yellow Pasque on 2013-04-29
That's probably because the deb line points to quantal when you're now on raring. You've got a mess on your hands. Personally, I would just go ahead and remove anything installed from that PPA and add back the Ubuntu repo version when done.

---

### Post by Gart3nzw3rg on 2013-04-29
I think I solved it.

I first added the xorg-edgers/ppa and then I run update/upgrade. After that I tried to install the qt-sdk again and it worked this time. Not sure if this is the proper way but it seems to be fine now.

---

