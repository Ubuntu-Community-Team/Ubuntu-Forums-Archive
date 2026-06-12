---
title: "Apt Repository error?"
date: 2005-02-27
forum: Repositories &amp; Backports
---

### Post by refused777 on 2005-02-27
Hey again,
I managed to get my net connection up and running, and thank you to everyone who helped out with that! 'm glad to say I'm typing this message in Ubuntu right now. At the moment, I'm apt-getting some updates and new software for Ubuntu, but after running sudo apt-get update, I keep getting these errors:

```
W: Couldn't stat source package list http://archive.ubuntu.com warty/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com warty/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com warty/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com warty/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com warty/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

```

When I run update again, I get:

```
Err http://archive.ubuntu.com warty/universe Sources
  Bad header line
Err http://archive.ubuntu.com warty/universe Release
  Bad header line
Err http://archive.ubuntu.com warty/multiverse Packages
  Bad header line
Err http://archive.ubuntu.com warty/multiverse Release
  Bad header line

``` 

My apt-gets work, but this error is kind of annoying. Any ideas?

Thanks again.

---

