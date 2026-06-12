---
title: "Wine and skype 64-bit issues."
date: 2012-10-31
forum: New to Ubuntu
---

### Post by Athquiz on 2012-10-31
I'm fairly new to ubuntu. I'm on 12.10 64-bit (I think?), and I've been trying to install wine. I run ```
sudo apt-get update && sudo apt-get install wine
``` and get the result: 

The following packages have unmet dependencies:
 wine : Depends: wine1.4 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

I get a similar message trying to install skype.

The following packages have unmet dependencies:
 skype : Depends: skype-bin but it is not installable
E: Unable to correct problems, you have held broken packages.

I think this is a multiarch problem, but I don't yet know how to diagnose it.

---

### Post by MikeCyber on 2012-10-31
could be as I installed wine with software center on 12.10 64bit without problems but I had previously installed ia32 libs (or alike)

---

### Post by Athquiz on 2012-10-31
> **MikeCyber said:**
> could be as I installed wine with software center on 12.10 64bit without problems but I had previously installed ia32 libs (or alike)

I tried that originally. I got and error like this:

wine1.4: PreDepends: dpkg (>= 1.15.7.2~) but 1.16.7ubuntu6 is to be installed
         Depends: libc6 (>= 2.14) but 2.15-0ubuntu20 is to be installed
         Depends: wine1.4-amd64 (= 1.4.1-0ubuntu1) but 1.4.1-0ubuntu1 is to be installed
         Depends: wine1.4-i386 (= 1.4.1-0ubuntu1) but it is not going to be installed

---

### Post by COMECON on 2012-10-31
Try running this command:
```
sudo apt-get -f install
```And then run again:
```
sudo apt-get update && sudo apt-get install wine
```

---

### Post by Athquiz on 2012-10-31
> **COMECON said:**
> Try running this command:
```
sudo apt-get -f install
```And then run again:
```
sudo apt-get update && sudo apt-get install wine
```

I tried this. Doesn't appear to change anything.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by squakie on 2012-10-31
Try:

sudo apt-get build-dep wine

---

### Post by squakie on 2012-10-31
Now I want to ask about the 2nd part of the title of this thread:  are you installing wine to run Skype?  If so, you don't need to.  Just install the native Skype package from the software center or using synaptic package manager.

---

### Post by Athquiz on 2012-11-01
> **squakie said:**
> Now I want to ask about the 2nd part of the title of this thread:  are you installing wine to run Skype?  If so, you don't need to.  Just install the native Skype package from the software center or using synaptic package manager.

I tried both of those.

```
Package dependencies cannot be resolved

The following packages have unmet dependencies:

skype: Depends: skype-bin but it is not going to be installed

```

Synaptic gives me "Could not apply changes! Fix broken packages first."

Also,

```
athquiz@ubuntu:~$ sudo apt-get build-dep wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Picking 'wine1.4' as source package instead of 'wine'
E: Unable to find a source package for wine1.4

```

---

### Post by squakie on 2012-11-01
In synaptic, did you try clicking on "edit" up on the top bar and then "fix broken packages" in the drop down?  What does it say?

Somehow I also wonder if there isn't somehow a mismatch with something 64-bit versus something 32-bit.  So, you are running 64-bit Ubuntu, correct?  Have you tried manually installing something that perhaps you used the 32-bit name instead of the 64-bit name?

---

### Post by Athquiz on 2012-11-01
> **squakie said:**
> In synaptic, did you try clicking on "edit" up on the top bar and then "fix broken packages" in the drop down?  What does it say?

Somehow I also wonder if there isn't somehow a mismatch with something 64-bit versus something 32-bit.  So, you are running 64-bit Ubuntu, correct?  Have you tried manually installing something that perhaps you used the 32-bit name instead of the 64-bit name?

I just "fixed broken packages" in synaptic. Not sure if it did anything. I also tried:
```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

I've tried both the 32 bit and 64 bit versions of both of these, but it seems that the 64 bit has a dependency for the 32 bit version. Results for wine:

```
athquiz@ubuntu:~$ sudo apt-get install wine1.4-amd64
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.4-amd64 : Depends: wine1.4-common (= 1.4.1-0ubuntu1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
athquiz@ubuntu:~$ sudo apt-get install wine1.4-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.4-common : Depends: wine1.4 (= 1.4.1-0ubuntu1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
athquiz@ubuntu:~$ sudo apt-get install wine1.4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.4 : Depends: wine1.4-i386 (= 1.4.1-0ubuntu1) but it is not installable
           Recommends: gnome-exe-thumbnailer but it is not going to be installed or
                       kde-runtime but it is not going to be installed
           Recommends: ttf-droid
           Recommends: ttf-mscorefonts-installer but it is not going to be installed
           Recommends: ttf-umefont but it is not going to be installed
           Recommends: ttf-unfonts-core but it is not going to be installed
           Recommends: winbind but it is not going to be installed
           Recommends: winetricks but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

---

### Post by MikeCyber on 2012-11-01
In my freshly installed 12.10 it worked right out of the box. Did you update a previous installation? You must have done some weird things...

---

### Post by squakie on 2012-11-01
+1 That's what I was thinking in my last post - it seems some of the libs are out of date for what is installed.  It really reminds me of the one time I did an update instead of a fresh install of an updated release.  Particulary when going from something like 10.04 to 11.04, perhaps 11.04 to 12.04 or 12.10 is the same.  The libs just aren't matching up.

---

### Post by AlexDudko on 2012-11-01
It could be caused by this bug [https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/1016294]("https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/1016294") and until it's not resolved there's no way to install skype from repositories for you.
Though you can always download skype's official packages from here [http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/]("http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/") and install them manually.

---

