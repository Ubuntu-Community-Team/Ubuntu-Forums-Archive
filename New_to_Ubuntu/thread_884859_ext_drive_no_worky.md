---
title: "ext drive no worky"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by intimatewipe on 2008-08-09
Hello Peeps,
Trying to connect an external 111gb usb drive to 8.04,it shows an error saying to either force mount or remove safely option using windows which I've done,downloaded gparted to see if it would read the drive(no),I have the app to read ntfs installed,any imput would be greatly appreciated

---

### Post by PmDematagoda on 2008-08-09
Use ntfsfix to try and fix the drive, install ntfsfix with:-
```
sudo apt-get install ntfsprogs
```
and run ntfsfix on the drive with:-
```
sudo ntfsfix /dev/path-to-drive
```
after ntfsfix is finished you should be able to mount the drive again.

---

### Post by bpowell2005 on 2008-08-09
> **PmDematagoda said:**
> Use ntfsfix to try and fix the drive, install ntfsfix with:-
```
sudo apt-get install ntfsprogs
```
and run ntfsfix on the drive with:-
```
sudo ntfsfix /dev/path-to-drive
```
after ntfsfix is finished you should be able to mount the drive again.

I've had to do this before; it works like a champ...I don't know why my Windows keeps dorking up my external drive...I've followed the "remove safely" method, but still have problems mounting without "force" in linux. NTFSFIX saved the day!

---

### Post by intimatewipe on 2008-08-09
thanks for the help guys will try asap,had a large gremlin turn up and give me several hours of nightmare to deal with,will let you know how I get on:)

---

