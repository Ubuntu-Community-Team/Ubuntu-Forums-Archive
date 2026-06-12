---
title: "chmod parse check"
date: 2011-09-24
forum: New to Ubuntu
---

### Post by Sidney232 on 2011-09-24
Can someone parse the following commands for me? I'm relatively new to command line and I don't want to screw the family photo collection. (This is an attempt to get around the nautilus recursive permissions 'bug' that seems to have been around for ages.)

```
sudo chmod -R o= /home/shared
sudo chmod -R g=rwx /home/shared 
```

o is aimed at the kids...
g is me and the wife.

Cheers.

---

### Post by Lisiano on 2011-09-24
Are you trying to set everything to be everyones?
```
sudo chmod -R 777 /home/shared
```
This will set everything to be rwx.
If you don't want your kids to be able to modify anything but see stuff, do this.
Create a group with you and your wife in it.
```
sudo addgroup adults
sudo addgroup husband adults
sudo addgroup wife adults
```
Husband -> You.
Wife -> Your wife.
Now do this
```
sudo chown husband:adults -R /home/shared
chmod 775 -R /home/shared
```
This will give anyone in the group adults rwx and rx to everyone else (x is needed for folders)
If you don't want your kids to see anything, then change 775 to 770. You can also make your wife own the files instead of yourself.

---

### Post by Sidney232 on 2011-09-24
Cheers, sorted.

---

