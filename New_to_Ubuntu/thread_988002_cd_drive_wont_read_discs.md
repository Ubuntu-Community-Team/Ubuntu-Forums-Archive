---
title: "cd drive wont read discs"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by muted1987 on 2008-11-20
should read dvd drive wont read discs

hey all ive just inserted a blank disc as i was using brasero and found that it wasnt finding the blank dvd, i then tried to open a data disc but even nautilus wasnt opening the drive with unable to mount location. 

would like to be able to run cd/dvds any help  appreciated

---

### Post by cozmicharlie on 2008-11-20
Can you manually mount it?
```
sudo mount /dev/scd0 /media/cdrom
```

Here is a list of things to check:
Check your Bios - reboot and press F2 to make sure the cdrmom shows up in your bios
Check group permissions - go to menu>system>administration>users and groups.  Unlock it and check fuse and make sure you are checked as user.
If nothing works paste the results of this command
```
lshw -C disk
```

and this command
```
cat /etc/fstab
```

---

