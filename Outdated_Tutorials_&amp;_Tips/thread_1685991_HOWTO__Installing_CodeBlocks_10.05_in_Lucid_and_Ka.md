---
title: "HOWTO:  Installing Code::Blocks 10.05 in Lucid and Karmic."
date: 2011-02-11
forum: Outdated Tutorials &amp; Tips
---

### Post by stchman on 2011-02-11
Hello all.

I was trying to install Code::Blocks on my Lucid install.  The version in the repos is old and I wanted to get the latest version  I did some Googling with no success.

After messing around I was able to get the 10.05 version of Code::Blocks installed.

Apparently you need at least 2.8.10 of libwxgtk2.8-0.  Lucid and Karmic have these packages.

First install the package:

```

sudo apt-get install libwxgtk2.8-0

```Then grab the binary of Code::Blocks from the website.  These are pre-compiled .deb packages for Code::Blocks.

32bit
[http://sourceforge.net/projects/codeblocks/files/Binaries/10.05/Linux%20%2832%20bit%29/codeblocks-10.05-1-debian-i386.tar.bz2]("http://sourceforge.net/projects/codeblocks/files/Binaries/10.05/Linux%20%2832%20bit%29/codeblocks-10.05-1-debian-i386.tar.bz2")

64bit
[http://sourceforge.net/projects/codeblocks/files/Binaries/10.05/Linux%20%2864%20bit%29/codeblocks-10.05-1-debian-amd64.tar.bz2](http://sourceforge.net/projects/codeblocks/files/Binaries/10.05/Linux%20%2864%20bit%29/codeblocks-10.05-1-debian-amd64.tar.bz2)

Unpack the archive, navigate to the folder where the .deb packages reside, and then from the terminal do the following:
```

sudo dpkg -i *.deb

```You now have the latest version of Code::Blocks for Lucid or Karmic.

Hope this helps.

---

### Post by parth.s on 2011-07-12
Worked for me. Cheers!!=D>

---

