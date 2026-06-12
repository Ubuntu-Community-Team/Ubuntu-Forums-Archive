---
title: "Installing emacs 25.1 on Ubuntu 16.04 error: You must put some 'source' URIs in your"
date: 2016-10-03
forum: New to Ubuntu
---

### Post by caffeinated2 on 2016-10-03
Hi ubuntu forums, this is my first time on this forum. I'm very new to linux and would like to expand my knowledge. I'm attempting to install emacs 25.1 on my ubuntu 16.04 system. I'm following a guide that instructs me to use the following PPA

[https://launchpad.net/~ubuntu-elisp/+archive/ubuntu/ppa](https://launchpad.net/~ubuntu-elisp/+archive/ubuntu/ppa)

I've added the Ubuntu Emacs Daily Snapshot PPA to my system, and I attempted to install the build dependencies. (Dumb question, what's the difference between 'downloading' and 'installing' in terms of the build dependencies?)

I ran 

    >sudo apt install build-essential checkinstall

and then

    >sudo apt-get build-dep emacs24

But I get the following output

    Reading package lists... Done
    E: You must put some 'source' URIs in your sources.list

I take this to mean apt-get can't find the build dependencies, isn't this what adding the PPA to my system with

    >sudo add-apt-repository ppa:ubuntu-elisp/ppa
    >sudo apt-get update

should have corrected? I've edited the sources.list file in /etc/apt by individually uncommenting all the pairs of deb and deb-src lines, and uncommenting everything, but that didn't solve the problem.

---

### Post by him610 on 2016-10-03
> I'm attempting to install emacs 25.1 on my ubuntu 16.04 system.

Are there any major differences between the emacs 25.1 and the emacs packages listed in the Ubuntu repository?
If not, then why not download and install from the repository?

---

