---
title: "[HOWTO] Sun Java Firefox Plugin for 32 bit and 64 bit (Useful for Runescapers)"
date: 2008-09-09
forum: Outdated Tutorials &amp; Tips
---

### Post by doorknob60 on 2008-09-09
Well, this is  my guide to set up Sun Java (needed for Runescape) in Ubuntu, both in 64 bit (AMD64) and 32 bit (i386). If you don't know whether you have 32 bit or 64 bit, go to a terminal (Applications > Accessories > Terminal) and type this:
```
uname -m
```
If it says x86_64, you have 64 bit, if it says i686 or x86 then you have 32 bit.

**32 Bit (i386):**

In terminal (Applications > Accessories > Terminal):
```
sudo apt-get install sun-java6-plugin ; sudo update-java-alternatives -s java-6-sun
```
And you should be good to go :)

**64 Bit (AMD64):**
Thanks to Sun, it's slightly more complicated...although when the final Java 7 is released it should be as easy as it is in 32 bit :) EDIT: 64 Bit Java beta is released. You can install it if you want, but right now I'm too lazy to update the guide. Once it's final I will though, and soon after that it should hit the Ubuntu repositories, rendering this guide almost useless :P EDIT: Hmm, the beta 64 bit PLuygin seems to white screen RS, at least now. It worked before the christmas event, now it still doesn't work. I'll leave this up.

Run each line one at a time in a terminal (Applications > Accessories > Terminal):
```
sudo apt-get install ia32-libs
wget http://jp-nii02.mozilla.org/pub/mozilla.org/firefox/releases/3.6/linux-i686/en-US/firefox-3.6.tar.bz2
tar -xf firefox-3.6.tar.bz2
sudo mv firefox /opt/firefox32
sudo apt-get install ia32-sun-java6-bin
sudo ln -s /usr/lib/jvm/ia32-java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /opt/firefox32/plugins/
sudo ln -s /opt/firefox32/firefox /usr/local/bin/firefox32
```

Now run the command 'firefox32' to start the 32 bit Firefox, complete with a Runescape compatible Java :) **Make sure you close *all* instances of Firefox before you do this or it won't work!**

---

