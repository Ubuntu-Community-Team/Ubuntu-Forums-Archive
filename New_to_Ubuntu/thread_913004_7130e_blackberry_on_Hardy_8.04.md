---
title: "7130e blackberry on Hardy 8.04"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by rubing on 2008-09-07
Hey All,

I am running fluxbox on Hardy 8.04.  I just purchased a sprint 7130e blackberry with phone as modem option in my sprint contract.

I bought this phone, since I read this post  [http://ubuntuforums.org/showthread.php?p=4550979]("http://ubuntuforums.org/showthread.php?p=4550979") where someone got this phone working.

I am trying to follow what he did, but his setup was on a ubuntu 7.10.   Just looking at the first 4 steps he did I have the following problems:



1. ***No problem here!***
cd /usr/include/

2.  ***I Do not have this file freetype****
sudo mv freetype freetype-back

3. ***my freetype2 directory is empty*****
sudo mv freetype2/freetype/ .

4. ***there is no lib directory under /usr/X11R6/*****
sudo ln -s /usr/X11R6/lib/libXm.so.4 /usr/X11R6/lib/libXm.so.3

If anybody has some advice or an alternative tutorial I should try, I would be ever-grateful!!!  thanx.

---

