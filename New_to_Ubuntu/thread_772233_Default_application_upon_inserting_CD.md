---
title: "Default application upon inserting CD"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by GabrielWolff on 2008-04-28
I'd like to change the default application that opens upon inserting a CD. I guess the answer is out there, as this is a really basic question, but I couldn't find a thread to this issue.

Anyone?

---

### Post by martrn on 2008-04-28
for gnome desktop see :-

At a terminal type :-
```
sudo gedit /usr/share/applications/defaults.list 
```

and look for x-content/blank-cd
for blank stuff etc....

Threds relateing to this type of thing :-----

[http://ubuntuforums.org/showthread.php?t=585430](http://ubuntuforums.org/showthread.php?t=585430)
[http://ubuntuforums.org/showthread.php?t=654320](http://ubuntuforums.org/showthread.php?t=654320)

++ more 

> I couldn't find a thread to this issue.
try google to search for threds on this site, its better than the search go at the top of this forum......

---

### Post by mlentink on 2008-04-28
Open up Nautilus (the file-explorer)
Then select Edit > Preferences and choose the media-tab.

---

### Post by GabrielWolff on 2008-04-28
Great, thanks to both of you, it worked perfectly :)

---

