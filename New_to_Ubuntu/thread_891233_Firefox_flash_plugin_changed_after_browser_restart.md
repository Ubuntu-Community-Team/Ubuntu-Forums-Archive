---
title: "Firefox flash plugin changed after browser restarts"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by steve.klebanoff on 2008-08-15
I'm experiencing something strange...right after I install the debugger version of flash 9 it works with the next instance of firefox that is opened.  

Unfortunately, when I close that firefox window and open a new one, its back to the non-debugger version of flash - in that window and from then on.  

Any idea of why this could happen?

Thanks,
Steve

---

### Post by picpak on 2008-08-15
Could you go to Tools > Add-Ons > Plugins and enable and disable your plugins from there?

---

### Post by steve.klebanoff on 2008-08-15
When I open add-ons, there is
Shockwave Flash 9.0 r124 ... and
Shockwave Flash 9.0 r115.

Both were enabled.   When I only disable r124 i can't view any flash files in the browser. When I only disable r115 flash files run but still not with the Debugging version.

---

### Post by steve.klebanoff on 2008-08-15
Okay, this is strange.  I reinstalled the Flash debugging version plugin.  I opened firefox right after, so I was using the one instance of firefox that will actually use the flash debugger version.    

In *this* instance of firefox...I went to manage the plug-ins and the opposite is true of the other instances...Both r124 and r115 are listed and both enabled. When I disable r115 I can't view any flash files...when I disable r124 I can still view flash files with the debugger.

---

### Post by picpak on 2008-08-15
I had a problem with two conflicting Flash plugins (although neither of them were debuggers); I fixed it by running

```
sudo apt-get remove flashplugin-nonfree
```

try that and see what happens.

---

### Post by steve.klebanoff on 2008-08-15
> **picpak said:**
> I had a problem with two conflicting Flash plugins (although neither of them were debuggers); I fixed it by running

```
sudo apt-get remove flashplugin-nonfree
```

try that and see what happens.
Worked like a charm. Thank you!

---

### Post by picpak on 2008-08-15
No problem. :)

---

