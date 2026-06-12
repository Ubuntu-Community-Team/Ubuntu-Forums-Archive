---
title: "Chromium no longer runs"
date: 2011-09-14
forum: New to Ubuntu
---

### Post by gredawarha on 2011-09-14
Hello all.

I have Ubuntu 11.04 installed on my laptop.  Been running fine with no problems however recently Chromium (my preferred browser) will not load.  When clicking it on the unity icon it appears to load but then instantly vanish.

I am unsure as to why this is (I presume a recent update has done something?) and I don't know how to rectify the issue?

Any thoughts?

Thanks

---

### Post by ron999 on 2011-09-14
> **gredawarha said:**
> 
Any thoughts?

Thanks
Try using Chromium from one of the PPAs here:- [https://launchpad.net/chromium-project]("https://launchpad.net/chromium-project")

---

### Post by gandaran on 2011-09-14
find out the problem running chromium from terminal, type
```
chromium-browser
```
paste the output errors here

---

### Post by gredawarha on 2011-09-14
Thanks for the replies I got this:

darren@darren-Q330:~$ chromium-browser
Moonlight: 3.99.0.3
Moonlight: Attempting to load libmoonloaderxpi 
Segmentation fault

---

### Post by gandaran on 2011-09-14
> **gredawarha said:**
> Thanks for the replies I got this:

darren@darren-Q330:~$ chromium-browser
Moonlight: 3.99.0.3
Moonlight: Attempting to load libmoonloaderxpi 
Segmentation fault
backup the chromium user settings (home/"user"/.config/chromium) rename the chromium folder to something else then start chromium, if all goes well you'll have a new user profile and working chromium.
also you could remove the chromium moonlight plugin if that didn't work.

---

### Post by gredawarha on 2011-09-15
Okay I did that and Chromium now works but as a fresh install without my bookmarks etc.  How do I get them back without the original problem?

---

### Post by gandaran on 2011-09-15
> **gredawarha said:**
> Okay I did that and Chromium now works but as a fresh install without my bookmarks etc.  How do I get them back without the original problem?
try copying the /chromium/Default/Bookmarks file from the backup to the new profile.
also you could use the built in synchronization to store the bookmarks and restore them on every new install of chromium or google chrome.

---

### Post by gredawarha on 2011-09-15
That worked just need to install my extensions.

Many thanks for all your help.

---

### Post by BruceCM on 2011-09-20
Assuming you'd know about Chromium/ Chrome being able to sync with a Google account? Seems highly likely you do but just in case!

---

### Post by sadaruwan12 on 2011-09-20
My friend it seems like you have been answered please mark the thread as solved

---

