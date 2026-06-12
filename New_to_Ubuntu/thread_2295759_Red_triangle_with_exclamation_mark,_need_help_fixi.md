---
title: "Red triangle with exclamation mark, need help fixing updates"
date: 2015-09-21
forum: New to Ubuntu
---

### Post by LoLaccount.01 on 2015-09-21
This is what shows when i try to do update and upgrade, i still don't know how to fix it. I also get the red exclamation mark and when i try to click "Show Updates" it returns that my software and systems are up to date. 

```
Err http://ppa.launchpad.net trusty/main amd64 Packages                        
  404  Not Found
Err http://ppa.launchpad.net trusty/main i386 Packages                         
  404  Not Found
Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
Ign http://ppa.launchpad.net trusty/main Translation-en                        
W: Failed to fetch http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.



```

---

### Post by slickymaster on 2015-09-21
Just remove the offending PPA from your system. Here's a thorough how-to: [http://askubuntu.com/questions/65911/how-can-i-fix-a-404-error-when-using-a-ppa-or-updating-my-package-lists](http://askubuntu.com/questions/65911/how-can-i-fix-a-404-error-when-using-a-ppa-or-updating-my-package-lists)

---

### Post by LoLaccount.01 on 2015-09-21
Thank you slickmaster, that helped me soo much, i had it fixed. Now i know more :) 

Thanks again

---

### Post by slickymaster on 2015-09-21
I'm glad you've got it fixed.

Please don't forget to [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") so other people searching the forums know that it provides a working solution for their problem.

---

