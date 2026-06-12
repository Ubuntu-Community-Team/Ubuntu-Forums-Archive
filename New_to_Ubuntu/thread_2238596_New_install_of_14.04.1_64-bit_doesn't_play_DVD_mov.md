---
title: "New install of 14.04.1 64-bit doesn't play DVD movie"
date: 2014-08-08
forum: New to Ubuntu
---

### Post by hill0093 on 2014-08-08
New install of 14.04.1 64-bit doesn't play the 
DVD movie "My Fair Lady" even though it downloaded and
installed some updates after I inserted the DVD.
What do I do to make it work?

---

### Post by MrSteve on 2014-08-08
have you installed libdvdcss2 ?

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by hill0093 on 2014-08-08
When I click open with Videos, it says video could not be read.
And I cannot figure out how to install libdvdcss2.

---

### Post by Jonathan Precise on 2014-08-08
```
sudo apt-get install libdvdcss2
```

Hope it's of help :)

---

### Post by kc1di on 2014-08-08
Did you follow the link that MrSteve suggested. It will tell you how to install libdvdcss2.
also this link is a good one:
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by MrSteve on 2014-08-08
try this 

the 32 and 64 bit downloads are about half way down the page ...

[http://ubuntuhandbook.org/index.php/2014/04/enable-dvd-playback-ubuntu-14-04/](http://ubuntuhandbook.org/index.php/2014/04/enable-dvd-playback-ubuntu-14-04/)

then use the ubuntu software centre to install the deb file
right click the deb file and click USC to install ...

---

### Post by hill0093 on 2014-08-08
Sorry, I don't have time today.
Will try tomorrow.
Thanks for so many suggextions.
I see I have a lot to learn.
I do want to tell you that the computer 
plays .mp4's that I copied over from Windows 7.

---

### Post by Rob Sayer on 2014-08-09
Before doing apt-get install in terminal always do:

```
sudo apt-get update
```

or in Synaptic Package Manager hit the reload button.  I highly recommend synaptic ... haven't used Software Center for a long time not.  Always synaptic or the terminal.

You should also install ubuntu-restricted-extras, which isn't automatically installed.  It's one of the first things I put on a new install.

---

