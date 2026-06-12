---
title: "Newbie-ext hd and 2nd internal HD no access"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by jjanolo on 2008-10-28
I have an external WD 160 Gb hd and internal 40 gb HD, have reformatted to ext3. I am able to mount and unmount but I can do anything else such as create folder or anything. I checked on properties-permission, it say "You are not the owner...." Ovner and Group is set to root.

I tried doing sudo chmod 777 /media/sdb1....no luck same with /media/sdg1...still no luck. 

Any help would be appreciated.

---

### Post by pofigster on 2008-10-28
As far as the internal HD goes - have you tried setting up an entry in your fstab to correspond?  You can then set the owner to yourself so you ought to have read/write access.

For the external HD - I'm honestly not sure.  Every external drive I've ever plugged in via USB has granted me r/w access.

---

### Post by didac on 2008-10-29
Sorry for sounding offensive, but did you reboot? If so, post your /etc/fstab and the results of 

    sudo fdisk -l

---

