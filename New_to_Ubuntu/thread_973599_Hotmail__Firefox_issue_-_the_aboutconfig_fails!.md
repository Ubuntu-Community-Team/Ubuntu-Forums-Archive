---
title: "Hotmail / Firefox issue - the about:config fails!"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by kuriooo on 2008-11-06
Hello, 

I'm relatively new to Ubuntu & Firefox, and also having the same problem with the Hotmail upgrade (can't reply or compose text in a new mail). 

I see the about:config fix suggested in multiple searches, but my about:config settings already appear to be correct, they state Firefox/3.03 in both the 'general.useragent.vendor' and 'general.useragent.extra' values. 

Any other suggestions about what to do with this? I've got Ubuntu 8.04. 

Also, on another thread someone suggested an addon called 'UserAgentSwitcher' and creating a default profile, but I didn't see any values to fill in when configuring the options on this add on. A plain default profile with blank boxes doesn't do anything for me. 

Thanks in advance, 
c

---

### Post by kerry_s on 2008-11-06
what does your useragent say:
[http://www.useragent.org/](http://www.useragent.org/)

try clearing cookies and cache?

---

### Post by kuriooo on 2008-11-06
After clearing private data & restarting browser, useragent is 

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.3) Gecko/2008092510 Ubuntu/8.04 (hardy) Firefox/3.0.3

I tried Tools-ClearPrivateData and then restarted the browser, but still same issue...

---

### Post by Gregvk3kv on 2008-11-06
Hi am also new to Ubunto and also have the same problem with new installation on clean hard drive can anyone assist.

Thanks Greg

> **kuriooo said:**
> Hello, 

I'm relatively new to Ubuntu & Firefox, and also having the same problem with the Hotmail upgrade (can't reply or compose text in a new mail). 

I see the about:config fix suggested in multiple searches, but my about:config settings already appear to be correct, they state Firefox/3.03 in both the 'general.useragent.vendor' and 'general.useragent.extra' values. 

Any other suggestions about what to do with this? I've got Ubuntu 8.04. 

Also, on another thread someone suggested an addon called 'UserAgentSwitcher' and creating a default profile, but I didn't see any values to fill in when configuring the options on this add on. A plain default profile with blank boxes doesn't do anything for me. 

Thanks in advance, 
c

---

### Post by kuriooo on 2008-11-07
Just want to say that entering the specific info contained in this thread [http://ubuntuforums.org/showthread.php?t=963252](http://ubuntuforums.org/showthread.php?t=963252)   about UserAgentSwitcher and then selecting that profile prior to opening Hotmail fixed the problem.

---

### Post by GarfIIeld on 2008-11-18
This solution worked for me:
```
sudo gedit /usr/lib/firefox-3.0.4/defaults/preferences/ubuntu-useragent.js
```

and change:

```
pref ("general.useragent.vendor", "Ubuntu");
pref ("general.useragent.vendorSub", "8.10");
pref ("general.useragent.vendorComment", "intrepid");
```

to:

```
pref ("general.useragent.vendor", "Firefox");
pref ("general.useragent.vendorSub", "8.10");
pref ("general.useragent.vendorComment", "intrepid");
```

---

