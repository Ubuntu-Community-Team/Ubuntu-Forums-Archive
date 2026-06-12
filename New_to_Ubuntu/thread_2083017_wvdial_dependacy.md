---
title: "wvdial dependacy"
date: 2012-11-11
forum: New to Ubuntu
---

### Post by maruf7 on 2012-11-11
Can anyone please tell me the dependancies of wvdial wvdial_1.61-4build1_i386.deb? I want to connect my ZTE wireless usb modem (cdma).

Note that I've already installed the following packages:
debconf_1.5.42ubuntu1_all.deb
libc6_2.15-0ubuntu10.3_i386.deb
libuniconf4.6_4.6.1-2build1_i386.deb
libwvstreams4.6-base_4.6.1-2build1_i386.deb
libwvstreams4.6-extras_4.6.1-2build1_i386.deb
ppp_2.4.5-5ubuntu1_i386.deb

But while installing wvdial 1.61, I encountered dependancy-related error.

Thanks.

---

### Post by newb85 on 2012-11-11
Sounds like you're making installation more difficult than it needs to be.  wvdial (the exact version you're trying to install, actually) is in the repositories.  That means you can install one of two ways and have dependencies handled for you.  (Actually, there are other ways, but these are the easiest.)

apt-get:
```
sudo apt-get install wvdial
```

Software Center:
Open the Software Center and type wvdial.  Notice the first listing is what you want.  Highlight it and click Install.

---

### Post by maruf7 on 2012-11-12
When I ran
```

sudo apt-get install wvdial

```

the result was
```

Reading package lists... Done
Building dependency tree
Reading state information... Done
wvdial is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
libc6-dev : Depends: libc6 (= 2.15-0ubuntu10) but 2.15-0ubuntu10.3 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

But I've already installed libc6_2.15-0ubuntu10.3 offline.
Can't work it out what is wrong.

---

### Post by coldcritter64 on 2012-11-12
OP have you tried running,

```
sudo apt-get -f install
``` as your results suggest ? That command can be very helpfull at times where dependency errors occur. Post any further output if it fails. Cheers.

---

### Post by newb85 on 2012-11-12
Indeed.  It requires a specific version of libc6, and you have manually installed a different version.  That's exactly why it's recommended to let apt-get handle dependencies automatically.

If the error message's suggestion doesn't work, I would try removing the manually installed libc6 and then running the suggestion again.

---

### Post by coldcritter64 on 2012-11-12
> **newb85 said:**
> ...
If the error message's suggestion doesn't work, I would try removing the manually installed libc6 and then running the suggestion again

+1, I agree OP, any needed dependencies for an application in the repos are taken care of automatically. It is best to stick to the repositories where possible OP, apart from dependency issues , it is far less risky than manual installations.

---

