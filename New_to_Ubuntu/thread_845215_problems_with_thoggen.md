---
title: "problems with thoggen"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by Zelix on 2008-06-30
im a big fan with thoggen i used it on fiesty and gutsy but now that i have a new install of hardy i cant get it to work at all. ive installed all the dvd codecs best i can but yet i cant get thoggen to read the disc.

"An error occured:

  Could not read from resource."

i used this tutorial to get my codecs working... 
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1) 
 &  
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

the tutorial got it about half right. i can play dvds in vlc now but not in movie player.  my problem is i wanna be able to backup my movies.  

any help would be appreciated, thanks for your time.

---

### Post by someonestolemyname on 2008-07-18
Try this:

sudo /usr/share/doc/libdvdread3/install-css.sh

It's changed since Gutsy, so it might not have been done on your computer.

---

### Post by matthewcraig on 2008-07-18
There is a problem with Region 1 DVDs and Thoggen.  There is a patch on it's way out to resolve the issue.  Are you getting a blue-screen instead of the title video display?

---

### Post by unckybob on 2010-12-09
On one of my machines Thoggen will work with region 1 DVDs. On the other machine I get the blue screen.

I don't think the bug has anything to do with region 1 DVDs.

---

### Post by KrayziiKat on 2011-06-18
> **matthewcraig said:**
> There is a problem with Region 1 DVDs and Thoggen.  There is a patch on it's way out to resolve the issue.  Are you getting a blue-screen instead of the title video display?

I'm also experiencing this problem, complete with the blue screen. Is that patch out yet, and if so, how can I find it? I'm trying to back up a ton of DVDs, and having less success than I'd like.

---

