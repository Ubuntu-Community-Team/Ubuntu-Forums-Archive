---
title: "Installing Eclipse 3.1M4 using apt-get"
date: 2005-01-30
forum: Repositories &amp; Backports
---

### Post by behrangsa on 2005-01-30
Hi

How can I install Eclipse 3.1M4 using apt-get?

Thanks in advance.

---

### Post by mendicant on 2005-01-30
I don't think anybody has a .deb package for it.  It's fairly self contained, so I usually just install it somewhere handy, and put a link or shell script it ~/bin.

---

### Post by mendicant on 2005-01-30
Oh, and of course, you'll need to install java.  Debian has some packages for doing that from a downloaded .bin file, so I imagine Ubuntu has it somewhere (maybe in multiverse or hoary).  You can also just install it somewhere handy, and use symbolic links and JAVA_HOME environment variables.

---

### Post by behrangsa on 2005-01-31
Thanks alot. I installed Java 1.5 update 1 using apt-get. Then I installed Eclipse the plain way you recommended.

Thanks anyways.

---

### Post by xbaez on 2005-06-01
[http://packages.debian.org/unstable/devel/eclipse-platform](http://packages.debian.org/unstable/devel/eclipse-platform)

Why doesn't anybody builds a .deb version for Ubuntu?
what if I download the one from Debian?

It will be really cool if all major development applications for Linux will be available for Ubuntu

---

### Post by xbaez on 2005-06-01
The package is really old though
I did found an eclipse package at the repositories (Ubuntu), but I got this message:

eclipse-nls-sdk:
 Depends: eclipse-platform (>=2.1.2) but it is not installable

Any suggestions?

I just love to install all the applications with Synaptic

---

### Post by mendicant on 2005-06-01
I don't think anybody has packaged it.  You can do it yourself, of course, but I find it just as easy to put it into some subdirectory of /usr/local/stow/, then put a script at /usr/local/bin/eclipse that will run it for me.  Then when I don't want it (because I've upgraded to the latest milestone or RC), I can just remove the directory.

---

### Post by xbaez on 2005-08-02
Have you tried the php extensions of Eclipse?

Eclipse is AMAZING for programming in Java and in PHP, it even has a local browser incorportaed ;)

However I still think it should be in a repository, you tell me that why should anybody place it at a repository?

Well, I ask a similar question, why not?

apt-get install eclipse

it NEVER gets any easier than that.

I think it should be a supported application by the Backports guys

---

