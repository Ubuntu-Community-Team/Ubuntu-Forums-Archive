---
title: "[SOLVED] Thunderbirds says unable to write data to hdd"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by stinger30au on 2008-10-03
I have installed 8.04 on this pc a few days ago and everything has been running fine.

the hdd that the email is saved on is from memory a ntfs drive

(used to be XP Pro but wiped it)

this morning i turn on pc and get thunderbird to recieve email and it gives me this exact error



Unable to write email to mailbox. Make sure the file system allows you write privileges and you have enough disk space



i have over 40 gig free of space on the drive and i have added or deleted nothing to the system.


any ideas????


i just did a quick test i can navigate to the directory where the data is stored and create new files and directorys.


seems strange it has been working for the past few days and now today it decided it is going to have a dummy spit

---

### Post by stinger30au on 2008-10-03
found the answer

i did a

chmod -R 777 PortableApps


and restart pc and its all good!!!


YAY FOR ME!

---

### Post by stinger30au on 2008-10-03
damn... got too excited too early


i recieved one email and now its doing the same thing again

restarted pc and still no go


weird stuff

---

### Post by stinger30au on 2008-10-03
i got it working again


this time i did 

file -> compact folders


and now its working again.... for the time being

---

