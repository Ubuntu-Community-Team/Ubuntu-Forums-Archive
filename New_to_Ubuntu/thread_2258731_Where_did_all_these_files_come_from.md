---
title: "Where did all these files come from?"
date: 2014-12-30
forum: New to Ubuntu
---

### Post by renbri on 2014-12-30
I was downloading some videos using the command line and the "youtube-dl..." function and, despite numerous pauses and restarts, succeeded in getting the MIT lecture videos I wanted into my Home folder, thence to a flash drive.
But now, when I look in my Home folder, it contains all kinds of stuff that wasn't there before: a series of folders called .cache, .compiz, .config, .dbus, etx -even one called None (which contained a movie folder, in which was a movie.iso)!??
My inclination is to send everything that wasn't there before to the rubbish bin but, since I've no idea how it all happened, I am alarmed and I don't know what to do .

---

### Post by deadflowr on 2014-12-30
The folders and files starting with a dot are always there, so **do not** trash them.
The dot means they're normally hidden. They are YOUR configuration folders and files and without them you'll bork your user's setup.
Meaning if you delete them you will not be able to start your desktop session correctly.
Typically those files are hidden by default, but can be set to view, usually by clicking  ctrl + H.

As for the folder marked None, that's not normal, so you probably can go ahead and trash it, if you want.

---

### Post by renbri on 2014-12-30
Phew! I'm glad I asked. I note that ctrl + H also hides them again. Thanks df.

---

### Post by renbri on 2014-12-30
Oops, I'm not out of the woods yet. I now have the situation whereby, when I leave the Files environment and return, the hidden files have reappeared. This happens even if, instead of using Ctrl + H, I go to the View menu at the top and untick the "Show hidden files" option. In other words, I can only hide the files during this session; the next time I select Files they will all show again. He-e-e-e-elp!

---

### Post by plucky on 2014-12-30
> **renbri said:**
> Oops, I'm not out of the woods yet. I now have the situation whereby, when I leave the Files environment and return, the hidden files have reappeared. This happens even if, instead of using Ctrl + H, I go to the View menu at the top and untick the "Show hidden files" option. In other words, I can only hide the files during this session; the next time I select Files they will all show again. He-e-e-e-elp!

Open **Edit > Preferences** and un-tick "Show Hidden Files".

Good Luck

---

### Post by renbri on 2014-12-30
Thanks, plucky, that did it. ( So many options. So many mysteries.)
This forum is such a bonus for me.
Happy new year.

---

### Post by raja.genupula on 2015-01-01
Glad you have solved your issue. Please mark the thread as solved. So it can save our little time.

---

