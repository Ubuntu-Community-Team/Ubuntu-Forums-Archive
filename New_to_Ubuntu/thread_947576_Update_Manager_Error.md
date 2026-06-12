---
title: "Update Manager Error"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by CoCoKnots on 2008-10-14
I am using Ubuntu 7.10 & received an update notice. When I clicked on the icon to begin the Medibuntu Package update it hangs up on Kaffeine, the first file at 5% downloaded. There are additional files in the package (libavcodec1d,libavformat1d, libavutil1d & libpostproc1d. Of course the download doesn't get that far.  What do I need to do now ?

---

### Post by shredder12 on 2008-10-14
try selecting files other than "kaffeine" for download..and tell me whether they get downloaded or not..
you can select a file for download by clicking on the check box before the package name..

---

### Post by CoCoKnots on 2008-10-14
I looks like libutil1d is the only file which was able to install.

---

### Post by shredder12 on 2008-10-14
well what are the errors it give while downloading other files..
like the one you specified "kaffeine"...

---

### Post by CoCoKnots on 2008-10-14
No error message... It just hangs without any progress. Download speed shows 'Unknown'.

---

### Post by CoCoKnots on 2008-10-14
Would it be better to take this opportunity to upgrade to Hardy ?

---

### Post by dhtseany on 2008-10-14
Honestly, with Intrepid's release coming here in the near future I'd just upgrade to Hardy.

Just my 2 cents

Peace
Sean

---

### Post by CoCoKnots on 2008-10-14
Hi Sean, Do you mean Wait for Intrepid ?

---

### Post by dhtseany on 2008-10-14
Nah, I meant to play it safe and upgrade to Hardy. Then, after Intrepid has been out awhile and has a good chunk of the bugs fixed, I'd upgrade to Intrepid.

Peace
Sean

---

### Post by freeediver on 2008-10-14
I got this message
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
This all relates to my frustration in trying to get google earth to work again But that is a different post.
What Should I do now?
I cant update?

---

### Post by JoshuaRL on 2008-10-14
Do this from the terminal:
```

sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade

```
That should clean everything up, and get you ready to install what you want.

---

