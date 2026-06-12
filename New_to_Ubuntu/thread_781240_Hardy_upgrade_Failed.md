---
title: "Hardy upgrade Failed"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by deaster2 on 2008-05-04
I am trying to upgrade from gutsy to hardy via update manager but
get this error: "http://archive.canonical.com/ubuntu/dists/hardy/Release Unable to find expected entry  commercial/binary-i386/Packages in Meta-index file (malformed Release file?)"

Can anyone tell me what I need to do...This is an HP dual-core AMD64 laptop. Gutsy works fine....
Thanks in advance

---

### Post by alienexplorers on 2008-05-04
You would have been better off doing a completely new install of 8.04.

---

### Post by Shampyon on 2008-05-04
Go to your terminal and enter
```
gksu gedit /etc/apt/sources.list
```
Search for the word "web". It shouldn't appear in any of your sources, but a few people have noticed it mysteriously added to theirs. This error occured on my system a day or two ago. I was lucky enough to have finished my upgrade before then.

So if you see "web" added in your source lines just delete all instances, save and restart your update manager.

---

### Post by deaster2 on 2008-05-04
> **Shampyon said:**
> Go to your terminal and enter
```
gksu gedit /etc/apt/sources.list
```
Search for the word "web". It shouldn't appear in any of your sources, but a few people have noticed it mysteriously added to theirs. This error occured on my system a day or two ago. I was lucky enough to have finished my upgrade before then.

So if you see "web" added in your source lines just delete all instances, save and restart your update manager.

Thanks for the response...the word "web" wasn't in the sources.list file...it couldn't have been that simple. Strange that my desktop upgraded without a hitch, but this laptop has failed numerous times.

---

