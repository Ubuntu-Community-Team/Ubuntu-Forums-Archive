---
title: "Cowbuilder --create in Ubuntu 11.04"
date: 2011-05-05
forum: Packaging and Compiling Programs
---

### Post by jaromil on 2011-05-05
I've tried to create a cowbuilder environment for ubuntu "testing" (or oneiric? is that how we have to call it? wishing there would be a number there...) and it failed.

This is the command i've used

```

sudo DIST=oneiric sudo cowbuilder --create --distribution oneiric --components "main universe"  --debootstrapopts --exclude="udev,pcmciautils,initramfs-tools" --debootstrapopts --arch --debootstrapopts i386

```this the resulting error, after correctly retrieving and extracting all packages, as it starts installing:

```

I: Installing core packages...
W: Failure trying to run: chroot /var/cache/pbuilder/base.cow/. dpkg --force-depends --install /var/cache/apt/archives/base-files_6.3ubuntu1_i386.deb /var/cache/apt/archives/base-passwd_3.5.22_i386.deb
E: debootstrap failed
W: Aborting with an error
pbuilder create failed

```anyone using it here? i need it to test compilation for i386 target on a 64bit machine (oh yea, it feels so lucky to have one)

I'm grateful for any hints you'll spare. ciao

---

### Post by MadCow108 on 2011-05-05
you have a couple of odd values in your command.
DIST is not used by cowbuilder, it uses DISTRIBUTION
(DISTRIBUTION and --distribution is redundant)
there is an extra sudo in the command
instead of the debootstrapopt you can use --architecture or ARCH environment variable

e.g.
```
sudo ARCH="i386" DISTRIBUTION="oneiric"  cowbuilder --create  --components "main universe"  --debootstrapopts --exclude="udev,pcmciautils,initramfs-tools"
```

but I don't think this explains why it failed. maybe you the version that got downloaded was broken. Try again.

make sure your filesystem supports hardlinks, else cowbuilder will not work.

---

### Post by jaromil on 2011-05-06
I've tried your line, but it failed at the same point:

```
I: Extracting zlib1g...
I: Installing core packages...
W: Failure trying to run: chroot /var/cache/pbuilder/base.cow/. dpkg --force-depends --install /var/cache/apt/archives/base-files_6.3ubuntu1_i386.deb /var/cache/apt/archives/base-passwd_3.5.22_i386.deb
E: debootstrap failed
W: Aborting with an error
pbuilder create failed
```i'm using a fresh install on ext4 fs

also tried removing debootstrapopts, but problem stays

FWIW the same commandline on debian 6.0 works

---

### Post by MadCow108 on 2011-05-07
can you run it with --debug. maybe that helps finding the problem.
and clear your apt-caches, apt-get clean and rm -f /var/cache/pbuilder/aptcache/*

---

### Post by jaromil on 2011-05-22
seems to be this:

```

E: Release signed by unknown key (key id AED4B06F473041FA)
+ log 'E: debootstrap failed'
+ case "$*" in
+ echo 'E: debootstrap failed'
E: debootstrap failed
+ exit 1
pbuilder create failed

```2 weeks passed and now this error pops up into the normal log when running even without --debug

the problem seems to be about a key missing (!?)
any ideas about this little weird issue? it makes me shiver a bit...

thanks,
ciao

---

### Post by MadCow108 on 2011-05-22
you seem to be building a debian chroot, AED4B06F473041FA is the debian main archive key

in that case you need to pass the debian keyring:
```
--debootstrapopts "--keyring=/usr/share/keyrings/debian-archive-keyring.gpg"
```

its in the debian-archive-keyring package

---

### Post by jaromil on 2011-05-23
ACK

i had leftovers in my pbuilderrc indicating debian sid as the target for the cowbuild, commenting them out made the cowbuilder --create work.

thanks for all your patience! i'm learning this thing little by little...

FYI built results will be available here [http://apt.dyne.org](http://apt.dyne.org)
not so much software packaged yet, but then here we go, i've got ubuntu cows now! :^D

ciao

---

