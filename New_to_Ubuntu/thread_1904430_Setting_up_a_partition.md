---
title: "Setting up a partition"
date: 2012-01-04
forum: New to Ubuntu
---

### Post by Chris_Nickel on 2012-01-04
Hello,
I juat started using Ubuntu at work today and I'm thinking about installing it on my home computer so I can play with it.
How big of a partition is reasonable to set up to install Ubuntu and have room for some apps?
 
Thanks
 
-Chris

---

### Post by JRV on 2012-01-04
It can install in as little as 4 gig, but that gives you very little room for added programs and data.  I would start with about 40 gig.
If you are dual booting Ubuntu will have access to your Window partition, and Windows will not be able to read the Ubuntu partition.

---

### Post by Chris_Nickel on 2012-01-04
Thanks,
I'm probably going to pick up a new laptop with a 600 gig drive, so setting aside 50 or so won't be a problem.
 
-Chris

---

### Post by oldfred on 2012-01-04
If sharing with Windows it is better to create another NTFS partition for shared data. Then you do not have to write into the NTFS system partition which can lead to issues. You can set c: drive to read only in Ubuntu if you manually mount it so you can avoid issues. Even some Windows users suggest a separate data partition (d drive), so when you have to reinstall Windows you do not have to reinstall all your data (backups still required).

I put Firefox & Thunderbird profiles in my shared when I first started dual booting as my wife wanted her email & web pages. Once I did that I was able to stay in Ubuntu most of the time, but there always seems to be one app that you have to boot back into Windows for.

---

