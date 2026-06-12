---
title: "[SOLVED] BadRequest 3D acceleration"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by jon.mithe on 2008-11-13
Hi,

Struggling to find a solution to this problem. I recently upgraded from 8.04 to 8.10 and my 3D acceleration seems to of broke, not even the mesa drivers seem to work.

fglrxinfo, glxinfo, glxgears all throw this out:
 

```
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  159 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10
```


I've tried the basics, removing and reinstalling fglrx from synaptic but still the same problem.

I've removed fglrx and would of though it would drop back to the mesa drivers, but I still get the same error.  

I'm guessing this problem is something to do with x / gnome.

I have a fairly bog standard core duo with an ATI (unsure which one, pc is a dell, couple years old and was not exactly cutting edge...). With 8.04 I had fglrx installed and working perfectly (had some trouble I fixed here [http://ubuntuforums.org/showthread.php?t=846016](http://ubuntuforums.org/showthread.php?t=846016)), its just the upgrade has made things fail.

Any help to fix or understand this would be great cheers,
Jon.

---

### Post by eternalnewbee on 2008-11-13
Go to: **[B]Main Menu > System > Administration > Hardware Drivers**[/B], and see if you can activate your graphic card from there.
Hope this helps you.
Btw. You have a better chance of getting replies if you post issues that have to do with 3D acceleration in **Desktop Effects & Customization**.

---

### Post by jon.mithe on 2008-11-14
Cheers. I've posted the thread in Desktop Effects & Customization

[http://ubuntuforums.org/showthread.php?t=981857](http://ubuntuforums.org/showthread.php?t=981857)

edit: manage to solve the problem myself, some details are in that thread

---

