---
title: "Bulid-essentials"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by limkopi on 2008-07-27
can anyone tell me where to download bulid-essentials without having the disc?

Thank In Advance

---

### Post by nbayiha on 2008-07-27
From synaptic . But i guess u have CRrom selected in synaptic.
Ok try this 

System ->Administration ->synaptic package manager->settings->repositories-> and deselect the CDROM on the box down. reload and everything should be fine now. 

To install build essential just 
 ```
sudo apt-get install build-essential
```

---

### Post by Sef on 2008-07-27
```
sudo apt-get update && sudo apt-get install build-essential
```

No s on essential.  A disk hasn't been needed for the last couple of releases.

---

### Post by northern lights on 2008-07-27
> **nbayiha said:**
> To install build essential just 
 ```
sudo apt-get install build essential
```
add a hyphen, it's 'build-essential'

---

### Post by limkopi on 2008-07-27
can someone tell me where to get bulid-essentials my com cant read cds or dvds.. so ya i have a wired connection..

---

### Post by northern lights on 2008-07-27
Run ```
sudo apt-get update
sudo apt-get install build-essential
```

But how would that be related to CDs and DVDs?

As for watching DVD movies, follow [RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

---

### Post by overdrank on 2008-07-27
Please limkopi do not create multiple threads on the same subject. I have merged your threads. :)

---

