---
title: "i recently installed linux xfce on a chromebook, but i can't seem to install steam"
date: 2015-09-11
forum: New to Ubuntu
---

### Post by saffron2 on 2015-09-11
i recently installed linux onto my chromebook as there's some applications i've been wanting to use. these all seem to work fine so i thought i'd try to see if i can get steam to work.
it installed fine but unfortunately when i try to install a game it informs me that well:

steam needs to install these additional packages:
libgl1-mesa-dri:i386, libg-mesa-glx:i386, libc6:i386

so i enter my password and then it says:

```
w: failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/trusty/main/binary-i386/packages](http://ports.ubuntu.com/ubuntu-ports/dists/trusty/main/binary-i386/packages) 404 not found [ip: 91.189.88.151 80]

w: failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/trusty/restricted/binary-i386/packages](http://ports.ubuntu.com/ubuntu-ports/dists/trusty/restricted/binary-i386/packages) 404 not found [ip: 91.189.88.151 80]

w: failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/trusty/universe/binary-i386/packages](http://ports.ubuntu.com/ubuntu-ports/dists/trusty/universe/binary-i386/packages) 404 not found [ip: 91.189.88.151 80]

w: failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/trusty/multiverse/binary-i386/packages](http://ports.ubuntu.com/ubuntu-ports/dists/trusty/multiverse/binary-i386/packages) 404 not found [ip: 91.189.88.151 80]

w: failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/trusty-updates/main/binary-i386/packages](http://ports.ubuntu.com/ubuntu-ports/dists/trusty-updates/main/binary-i386/packages) 404 not found [ip: 91.189.88.151 80]

w: failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/trusty-updates/restricted/binary-i386/packages](http://ports.ubuntu.com/ubuntu-ports/dists/trusty-updates/restricted/binary-i386/packages) 404 not found [ip: 91.189.88.151 80]

w: failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/trusty-updates/universe/binary-i386/packages](http://ports.ubuntu.com/ubuntu-ports/dists/trusty-updates/universe/binary-i386/packages) 404 not found [ip: 91.189.88.151 80]

w: failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/trusty-updates/multiverse/binary-i386/packages](http://ports.ubuntu.com/ubuntu-ports/dists/trusty-updates/multiverse/binary-i386/packages) 404 not found [ip: 91.189.88.151 80]

w: failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/trusty-security/main/binary-i386/packages](http://ports.ubuntu.com/ubuntu-ports/dists/trusty-security/main/binary-i386/packages) 404 not found [ip: 91.189.88.151 80]

w: failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/trusty-security/restricted/binary-i386/packages](http://ports.ubuntu.com/ubuntu-ports/dists/trusty-security/restricted/binary-i386/packages) 404 not found [ip: 91.189.88.151 80]

w: failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/trusty-security/universe/binary-i386/packages](http://ports.ubuntu.com/ubuntu-ports/dists/trusty-security/universe/binary-i386/packages) 404 not found [ip: 91.189.88.151 80]

w: failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/trusty-security/multiverse/binary-i386/packages](http://ports.ubuntu.com/ubuntu-ports/dists/trusty-security/multiverse/binary-i386/packages) 404 not found [ip: 91.189.88.151 80]

e: some index files failed to download. they have been ignored, or old ones used instead.

reading package lists... done.
building dependency tree
reading state information... done
package libc6:i386 is not available but is referred to by another package.
this may mean that the package is missing, has been obsoleted or is only available from another source
however the following packages replace it:
libg-mesa-glx-lts-vivid libgl1-mesa-glx-lts-utopic

package libgl1-mesa-dri:i386 is not available, but is referred to by another package.
this may mean that the package is missing, has been obsoleted, or is only available from another source
however the following packages replace it:
libg-mesa-glx-lts-vivid libgl1-mesa-glx-lts-utopic

package libgl1-mesa-dri:i386 is not available, but is referred to by another package.
this may mean that the package is missing, has been obsoleted, or is only available from another source
however the following packages replace it:
libg-mesa-glx-lts-vivid libgl1-mesa-glx-lts-utopic

e: package 'libgl1-mesa-dri:i386' has no installation candidate
e: package 'libgl1-mesa-dri:i386' has no installation candidate
e: package 'libc6:i386' has no installation candidate
press return to continue:
```

so i press return and:

you are missing the following 32 bit libraries and steam may not run:
libc.so.6

so basically it doesn't work and i've tried multiple commands and it seems to imply i'm missing a core file or something that you need to work so i don't know what that would be but i've gone to alot of posts like this:[http://steamcommunity.com/app/221410/discussions/0/617330227198738356/?insideModal=1](http://steamcommunity.com/app/221410/discussions/0/617330227198738356/?insideModal=1)
but none of them seem to have worked.

so maybe a chromebook is incapable of this, or maybe this version of linux can't do this but it'd be nice to have some confirmation.

also if it wasn't obvious i am really new to this, and my technical skills only go so far, so if the solution is complicated, i need a simple explanation. :)[/FONT][/COLOR]

---

### Post by cariboo on 2015-09-11
I'd suggest you try a different mirror, if you have synaptic package manager installed got to Settings->Repositories and change to the Main server.

---

### Post by sandyd on 2015-09-11
What chromebook is this?

Steam will not work on a ARM based chromebook.

---

### Post by saffron2 on 2015-09-11
it's an hp chromebook but the system app says the model's a NVIDIA Tegra Soc (Flattened Device Tree) it says the architecture is a arm7lv though so i think it might be an arm device, oh well that's a little dissapointing.

---

### Post by sargetech on 2015-10-12
That is what is is, an arm processor. Sorry about that.....

---

