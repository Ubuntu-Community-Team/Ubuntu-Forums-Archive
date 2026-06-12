---
title: "dpkg Error processing"
date: 2005-03-10
forum: Repositories &amp; Backports
---

### Post by sanman_nor on 2005-03-10
so I loaded up sinaptic and it said I had a broken pakage 
so I went to fix broken package and it said 
"
dpkg Error processing /var/cache/apt/archives/libavcodec2_1%3a0.4.9-prelsarge0.2_i386.deb (_ _ unpack):
trying to overwrite ' /usr/lib/libavcodec.so.0.4.9-prel'   , which is also package libavcodec0
dpkg- deb: subprocess pastdo I fix ite killed by signale  (broken pipe)
" 
fallowed by the failed to apply all changes scroll up... bla bla blaa
 
what the heck is it saying and how do I fix it
thankyou

---

### Post by sanman_nor on 2005-03-15
I can't do anything with syinaptic, it stops downloading and goes strait to loading and  fails

---

### Post by sanman_nor on 2005-03-19
I can't remove or add anything with sanapteic

---

### Post by cdhotfire on 2005-03-20
try to delete /var/cache/apt/archives/libavcodec2_1%3a0.4.9-prelsarge0.2_i386.deb that would be my suggestion.  But if it doesnt work, then put it back just in case it makes things worse.

---

### Post by sanman_nor on 2005-03-20
and to do that what should I do

---

### Post by cdhotfire on 2005-03-20
```
sudo mv /var/cache/apt/archives/libavcodec2_1%3a0.4.9-prelsarge0.2_i386.deb /home/USERNAME/
```

put you username in USERNAME, and like i said if it doenst work, do

```
sudo mv /home/USERNAME/libavcodec2_1%3a0.4.9-prelsarge0.2_i386.deb /var/cache/apt/archives/
```

if it doesnt work tell me, and i will try and help you out. ;-)

---

