---
title: "Versioning issue after successful debian package creation"
date: 2010-06-04
forum: Packaging and Compiling Programs
---

### Post by megamaced on 2010-06-04
Hi,

I have created debian packages for nautilus elementary from the BZR branch but I have an issue with version numbers... This is my process:

1. Download the latest nautilus elementary from BZR (currently 2.31.1 in the about screen)
2. Rename the folder to nautilus-2.31.1
3. In the terminal, cd to the folder and enter dh_make -n -s -e [email]email@address.com[/email]
4. This creates the debian structure for me.
5. I then apt-get source the official ubuntu nautilus..
6. I copy most of the files from the debian folder in the source of the official nautilus (excluding patches) and move them to the debian folder in the target nautilus elementary folder
7. I then run fakeroot debian/rules clean followed by fakeroot debian/rules binary
8. The package builds complete successfully and I end up with a nautilus_2.31.1.deb and a nautilus-data_2.31.1.deb and libnautilusextension1_2.31.1.deb etc etc

Now the problem!

When I dpkg -i and install the packages, I get a warning to say that I am DOWNGRADING nautilus!! I thought this strange as my version is 2.31.1 vs the 2.30.1 installed. However on closer inspection I noticed that actually the version installed is 1:2.30.1. I cannot for the life of me understand how to append the "1:" before the version number. 

Can anyone help?

Cheers 8)

---

### Post by ammonkey on 2010-06-05
i can't help you with packaging but debian packages for nautilus-elementary already exist. You should try hadret ppa:
[http://hadret.rootnode.net/](http://hadret.rootnode.net/)

---

### Post by mc4man on 2010-06-06
Check your changelog..

---

### Post by SevenMachines on 2010-06-08
> **mc4man said:**
> Check your changelog..
ditto!
as always, i'm a bit unclear on the actual versioning policy your changes should have but as far as your question goes :)

current nautilus version (in lucid)
nautilus (1:2.30.1-0ubuntu1) lucid-proposed; urgency=low

i'm guessing you have something like
nautilus (2.31.1) lucid; urgency=low

whereas you were probably aiming for,
nautilus (1:2.31.1) lucid; urgency=low

---

### Post by megamaced on 2010-06-10
Thanks, actually the nautilus elementary ppa finally updated so I now have the packages I want...

But I am curious about the changelog. I did not copy across that file from the original source and basically left it untouched. So are you saying that if I prepend the 1: to the version in the changelog file that will make the package read 1:2.31.1 to dpkg?

Ta

---

### Post by SevenMachines on 2010-06-10
yes, dpkg recognises versions in the form 
 [ _epoch_:] _upstream_version_ [-_debian_revision_ ]

so 1:2.31.1
means epoch=1
upstream version =2.31.1

when no epoch is included then a zero epoch is implicit, ie
2.31.1 is actually 0:2.31.1

so 2.31.1 == 0:2.31.1 < 1:2.31.1

theres an explanation in 'man deb-version', which tends to make my head spin to be honest :)

---

### Post by mc4man on 2010-06-10
> I did not copy across that file from the original source

Many times when doing what your doing or variations of, you'll find the orig. source's changelog (if avail.) worth looking at or even sometimes  reusing - just add a new entry to top. (plus note changes/ patches, ect.


It shows you the current naming and how updates were/will be versioned which is handy depending on how you wish future updates to repo version to be handled.


( if I'm doing something that's a bit sketchy I may version it the same on a test build - on install it's seen as a re-install,  after that the repo version is an update which makes recovering from a 'bad' idea a snap.

---

### Post by megamaced on 2010-06-13
Cool thanks

---

