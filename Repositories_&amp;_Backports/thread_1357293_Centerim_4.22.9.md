---
title: "Centerim 4.22.9"
date: 2009-12-17
forum: Repositories &amp; Backports
---

### Post by rickbear on 2009-12-17
Hi, I am new to this forum and not sure this is the right forum.
 
But I would like to hear when the new Centerim is available in the repositories?
For now there is 4.22.7 and it doesn't work anymore because some days ago the msn part stopped working. Centerim worked on an update and it should now work in 4.22.9, but there are still no updates when I make a apt-get update/upgrade.
 
Who desides what and when will be available in the repositories?
Is there a way to force install it? (besides from downloading source and compile).
 
- rick -

---

### Post by noorbeast on 2009-12-19
I have no idea where you can obtain a deb for centerim 4.22.9, or when it will be available, but it is pretty easy to make and install your own, even if it does mean compiling centerim from source, and it did fix the msn issue for me.

You do need to install some packages. On Karmic install the following via a terminal: sudo apt-get install build-essential checkinstall libcurl4-openssl-dev libncurses5-dev 

Then get the centerim source: wget http://www.centerim.org/download/releases/centerim-4.22.9.tar.gz

Unpack the source: tar xvfz centerim-4.22.9.tar.gz

Go to the unpacked centerim source by doing the following: cd centerim-4.22.9

Compile centerim by doing the following:

./configure
make

Now create and install your own deb by doing the following, just hit enter at the prompts for checkinstall to accept the defaults:

sudo checkinstall -D make install 

Centerim is installed to /usr/local/bin, so make a symlink to /usr/bin by doing the following:

sudo ln -s /usr/local/bin/centerim /usr/bin/centerim

You should then be good to go, so fire up centerim and msn should work fine.

---

### Post by rickbear on 2009-12-22
Thanks. Works like a charm :-)
Would have been nice, if I could just have made an apt-get upgrade though.

---

### Post by noorbeast on 2009-12-22
Good stuff, I hope it was easy enough to follow!

Ubuntu is pretty good, but sometimes we have to help ourselves, and knowing how is a handy skill that many share on these forums.

---

