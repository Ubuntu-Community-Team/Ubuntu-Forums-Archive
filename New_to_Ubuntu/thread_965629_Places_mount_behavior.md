---
title: "Places mount behavior"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by airencracken on 2008-10-31
In 8.10 when I click on my other drives in places it starts totem for some reason in an attempt to play any files that may be on that drive. This is in opposition of how it behaved in 8.04 where it would simply mount the drive.

Any way to change this behavior?

---

### Post by plucky on 2008-10-31
> **airencracken said:**
> In 8.10 when I click on my other drives in places it starts totem for some reason in an attempt to play any files that may be on that drive. This is in opposition of how it behaved in 8.04 where it would simply mount the drive.

Any way to change this behavior?

See this [bug report](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/260492)

Open nautilus in a terminal and right click on a folder and select "open with Application" and select **File Browser**.

---

### Post by airencracken on 2008-10-31
Thanks for the reply. That seemed to work. 

Also nautilus keeps telling me that the drive has photos and prompts me to open f-spot (with a light blue bar). Can I disable that for this drive?

---

### Post by plucky on 2008-11-01
> **airencracken said:**
> Thanks for the reply. That seemed to work. 

Also nautilus keeps telling me that the drive has photos and prompts me to open f-spot (with a light blue bar). Can I disable that for this drive?

Open **System > Preferences > Removable Drives and Media** and untick "Import Digital Photographs when connected"


Good Luck

---

### Post by airencracken on 2008-11-01
> **plucky said:**
> Open **System > Preferences > Removable Drives and Media** and untick "Import Digital Photographs when connected"


Good Luck

No dice. It was already unchecked. It doesn't prompt me to open f-spot with a pop-up, but just with a little notification area above the icons.

---

### Post by an93l on 2008-11-02
I have this very same issue, the drive is auto mounted in my home folder but whenever I access it the f-spot manager has that stupid bar at the top. it is very anoying.

---

### Post by benerivo on 2008-11-02
It is a bug in nautilus. See [here]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/258936"). This causes normal mounts to behave as if they are cd's rather than drives.

---

### Post by an93l on 2008-11-03
wow that was a bit of a simple oversite on the devs part i think. renaming the pictures folder to something else so the drive doesn't geet seen as a picture CD is just too simple, so here goes.

---

