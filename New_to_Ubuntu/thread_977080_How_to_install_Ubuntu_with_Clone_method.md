---
title: "How to install Ubuntu with Clone method?"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by asaren on 2008-11-09
How to install Ubuntu with Clone method?

Does this method spend less time to install?

And Can i the clone to install in different specification PC?

Thank you

---

### Post by kuttifunk on 2008-11-20
Same to me.
For an application working offline, i wish to develop and test an ubuntu image as xen guest and then clone it to install it offline on a small pc configuration. Best with usb-stick. Partimage or dd is probably not what i want, though.
Any clues? 

Greetings

---

### Post by Dedoimedo on 2008-11-20
Hello,

Try Remastersys, Clonezilla, PartImage, in that order.
Remastersys allows you to create bootable, redistributable versions of your own distro.

Got tutorials for all three mentioned, check if you're interested.

Dedoimedo

---

### Post by kuttifunk on 2008-11-20
remastersys seems to be it. Thanks indeed.

:)

---

### Post by Keen101 on 2008-11-20
i've heard good things about clonezilla.

---

### Post by Sarmacid on 2008-11-20
I've been able to clone my ubuntu installs just using dd and it worked fine, but were PCs with the same specs. Not sure if it would work otherwise, but it could be an option.

---

### Post by The Cog on 2008-11-20
Why not just use tar to make an archive of the whole drive? If you do it from a live CD, there's no issue with getting a copy of /sys and the other non-physical directories included. Then also using a live CD, extract the tar onto the new (freshly formatted) disk.

---

### Post by asaren on 2008-11-21
> **Dedoimedo said:**
> Hello,

Try Remastersys, Clonezilla, PartImage, in that order.
Remastersys allows you to create bootable, redistributable versions of your own distro.

Got tutorials for all three mentioned, check if you're interested.

Dedoimedo

Thank you everyone and thank Dedoimedo so much.

Remastersys seems to be what i was looking for, but How much RAM it require for run Live CD? Is 256MB going to be fine?

---

### Post by Dedoimedo on 2008-11-21
The same as your normal Ubuntu ... 256MB should work, but could be a little tight...
Dedoimedo

---

