---
title: "Newby Q: compiling firefox with apt-get source?"
date: 2007-06-20
forum: Packaging and Compiling Programs
---

### Post by [censored] on 2007-06-20
compiling firefox this way breaks my software index.

I would like to compile firefox, because I've experienced in the past that when you compile software specifically for your system, it seems to work a lot more smoothly. And lately, since about the last upgrade, I've noticed that firefox seems to hang and stall a lot on my humble Celeron 2800 1GB system.

On the command I basically did:
 
sudo apt-get source --compile mozilla-firefox

It took a while. Probably more than an hour. But I ended up with a whole heap of debs in my source directory. I mv them all into a special directory, cd into it, and went:

sudo dpkg -i *.deb

this worked well. Except that the package manager then complained that my software index was broken, and that the only way to fix it was to type "sudo apt-get install -f". However, if I do that, it just downloads and re installs the old generic binary. 

How can I get around this problem?

---

