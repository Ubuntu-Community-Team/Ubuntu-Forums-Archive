---
title: "Information request: How &quot;easy&quot; is it to add Debian package (experimental) to PPA?"
date: 2021-08-11
forum: Packaging and Compiling Programs
---

### Post by ameinild on 2021-08-11
Hello

I'm new to this aspect, and is seeking overall advice.

I would like to do the following:

[LIST=1]
[*]Take a newer version of a Debian package than is found in Ubuntu repos 
[*]Test it on my system 
[*]Put it in a PPA, for easier distribution for myself and friends 
[/LIST]
Let's take Nano as an example, where this is the [experimental version]("https://packages.debian.org/experimental/nano") I would like to publish in my PPA.

I understand that I have to upload a source package to the PPA, and I can also see that source packages are available from Debian in the link above.

So my question is: *How "difficult" is it for me to take an existing source package as above, and make it ready to upload to PPA? And which additional steps will I have to take besides grabbing the sources directly from Debian for the package to be ready for upload to PPA?*

I understand I might have to sign some files myself, including the [FONT=courier new]P_V_source.changes[/FONT] file, which is not present from Debian.

I would really appreciate an overall estimate of how much of the source packages I can "reuse" from Debian, and how much I have to do myself for this to be possible.

Many thanks in advance. 

Regards, Artur

---

### Post by TheFu on 2021-08-11
You'll probably need to compile it for Ubuntu library versions, since Ubuntu and Debian often have different base libraries.

As for creating a package or setting up a PPA, that is beyond my skill.  There is a Debian guide for doing both, however.  At that level, Ubuntu and Debian are the same.
[https://wiki.debian.org/HowToPackageForDebian](https://wiki.debian.org/HowToPackageForDebian)
[https://wiki.debian.org/DebianRepository/Setup](https://wiki.debian.org/DebianRepository/Setup)

---

### Post by ameinild on 2021-08-12
I should probably add, that the programs I'm referring to will run out of the box, i.e. programs I've verified work when I just install the newer binary from Debian - such as the case is with Nano for instance.

---

### Post by TheFu on 2021-08-12
> **ameinild said:**
> I should probably add, that the programs I'm referring to will run out of the box, i.e. programs I've verified work when I just install the newer binary from Debian - such as the case is with Nano for instance.

Then don't be a middle-man and point your friends at the debian PPA for those packages. That's the easiest and it removes all the security stuff from your mandate.  If people are on the same LAN as you, you could setup a APT-cache so only the first person to load a package causes it to be downloaded, then everyone else gets it from the local cache.  I run **apt-cacher-ng** for that purpose. After setup, it is mostly self-managing. It auto-expires old packages, for example.  

Installing a new system with the same release as another system on the LAN is really fast, since almost every package will be cached locally.

---

### Post by ameinild on 2021-08-13
It seems this was more difficult than I first thought, since some of the build dependencies for Debian are not available for Ubuntu. So I probably need to setup a Debian VM for this to work, since you have to rebuild and sign the packages before they can be uploaded to the PPA.

---

