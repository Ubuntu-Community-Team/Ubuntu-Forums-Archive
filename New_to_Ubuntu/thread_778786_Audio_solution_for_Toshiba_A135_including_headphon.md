---
title: "Audio solution for Toshiba A135 including headphones Gutsy and earlier"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by stchman on 2008-05-02
Hello all, I just wanted to pass along a bit of information.  I have a Toshiba Satellite A135 series laptop.

I have finally gotten the headphones and everything else to work.  Mind you this is for Gutsy and earlier.  Hardy Heron solves the problem, but I did not want to upgrade.

The solution was to use the alsa-base from Hardy and install Alsa 1.0.15 and all works.

Here is an install script for Also 1.0.15.

[http://www.stchman.com/tools/alsa/alsa_setup_15.sh](http://www.stchman.com/tools/alsa/alsa_setup_15.sh)

Script must be run as root with 755 permissions.

Here is the alsa-base that I used from the Hardy installation.  Just replace your old alsa-base with this one.  Here is how you do it.

I hope this helps.

---

