---
title: "How to create Launchpad PPA from Ubuntu binary"
date: 2018-05-20
forum: Packaging and Compiling Programs
---

### Post by nasa8x on 2018-05-20
I have package geekcash-1.0.1-x86_64-linux-gnu.tar.gz download at [https://github.com/GeekCash/geekcash/releases](https://github.com/GeekCash/geekcash/releases)
How to create Launchpad PPA from this binary (geekcash-1.0.1-x86_64-linux-gnu.tar.gz). 
&#8232;I used the command:&#8232;
> cd geekcash-1.0.1&#8232;
dh_make --indep --createorig
&#8232;debuild -S -sa -kF11623B6


> 
cd ..
dput ppa:geekcash/ppa geekcash_1.0.1-1_source.changes
Uploaded success but not see anything at Launchpad


—
My purpose to use the repository is as follows:
> sudo add-apt-ppo repository: geekcash/ppa -y
sudo apt-get install geekcash


Then I can call the library everywhere:
> geekcashd
—


Someone wrote an article or tutorial video to me or someone else based on that to do. A 30k Geek (GeekCash) reward is given to you after the job is complete.


Thanks and appreciate the help!

---

