---
title: "installing mencoder"
date: 2014-12-15
forum: New to Ubuntu
---

### Post by evaristegalois on 2014-12-15
I use mencoder to edit video files on the command line. This has always worked well, but on my new computer (running Ubuntu 14.10) I type

which mencoder

in the terminal and get nothing. I tried to install it using

sudo apt-get install mencoder

as outlined at [https://help.ubuntu.com/community/MEncoder](https://help.ubuntu.com/community/MEncoder) but I get

Package mencoder is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However, the following packages replace it:
  mplayer

E: Package 'mencoder' has no installation candidate

I tried to google this problem, but no luck. I have mplayer installed.

---

### Post by mc4man on 2014-12-15
The mplayer source was removed in Debian & Ubuntu 14.10, it may return in 15.04 or later. So no source, no mencoder.
You could probably use 14.04's mencoder package or just build both yourself, that way you'd get a current version rather than the outdated one in the ubuntu repos
here - [http://ubuntuforums.org/showthread.php?t=2149564](http://ubuntuforums.org/showthread.php?t=2149564)
or updated here - 
[http://www.andrews-corner.org/ubuntu/mplayer.html](http://www.andrews-corner.org/ubuntu/mplayer.html)
(- the guide(s) are for trusty but should work ok in 14.10, or work ok with a little minor  help on the dependencies if need be.

---

### Post by andrew.46 on 2014-12-16
Certainly the website version is a little more up to date than the Forums thread as I debate if website or Forum is the better place...

---

### Post by evaristegalois on 2014-12-16
Thank you! I'll try to install mplayer from scratch without apt-get and see how it goes.

---

### Post by evaristegalois on 2014-12-17
This was a tricky install by hand. Just downloading mplayer-checkout-snapshot from [http://mplayerhq.hu/design7/dload.html](http://mplayerhq.hu/design7/dload.html) and running ./configure, make, and sudo make install didn't work because it got stuck on ./configure. I tried installing the freshest ffmpeg first, download from [http://ffmpeg.org/download.html](http://ffmpeg.org/download.html) and do ./configure, make, and sudo make install (the "make" part takes 45 minutes). Still stuck on ./configure trying to install mplayer. Restarted the computer and it worked! Phew! "which mencoder" now gives me /usr/local/bin/mencoder so I assume all is well.

Tags: install mencoder ubuntu 14.10 mencoder missing mencoder no longer comes with mplayer

---

