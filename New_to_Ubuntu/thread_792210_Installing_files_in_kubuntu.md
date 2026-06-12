---
title: "Installing files in kubuntu"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by duganator on 2008-05-12
Ok so I am having a little bit of trouble installing some tar.gz files on my computer.  It has certainly been a while for me using this so I am a little rusty, but I do remember that I have to extract the file.  I did extract the file to my desktop, and then in the terminal, I ran cd Desktop, and then tried sudo apt-get install (package name) and it always says it couldn't find the package.  I'm kind of at a loss for words.  I have searched all over the net, but the information isn't very helpful.  All the tutorials assume knowledge of ubuntu/kubuntu and that is something I dont have.

---

### Post by tzulberti on 2008-05-12
If you could find the packages maybe you don't have activated the backports, universe or multiuniverse. Fot this, you should open synaptic, and go to Settings -> Repositories.

Nevertheless, if oyu still want to use the tar.gz, you should use:
tar -xvvzf foo.tar.gz
cd foo
./configure
./make install

---

### Post by SunnyRabbiera on 2008-05-12
> **tzulberti said:**
> If you could find the packages maybe you don't have activated the backports, universe or multiuniverse. Fot this, you should open synaptic, and go to Settings -> Repositories.

Nevertheless, if oyu still want to use the tar.gz, you should use:
tar -xvvzf foo.tar.gz
cd foo
./configure
./make install

hes using kubuntu, so instead of synaptic it will be adept... yuck...

---

