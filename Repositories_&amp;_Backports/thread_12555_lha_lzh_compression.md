---
title: "lha lzh compression"
date: 2005-01-25
forum: Repositories &amp; Backports
---

### Post by dwanders on 2005-01-25
I am trying to uncompress a file that is in lzh format (extension) *.lha. File roller tries to open the file then fails as LZH is not installed. So an attemtp to install lzh or lha with:

apt-get update
apt-get install lha
or 
apt-get install lhz 

returns:
root@PC201:/home/danderso # apt-get install lha
Reading Package Lists... Done
Building Dependency Tree... Done
Package lha is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package lha has no installation candidate
root@PC201:/home/danderso #

If it has been replaced, by what? if so, is there a way to configure file roller to use the replacement? 

If it has not been replaced, is there a different way to install it (I know I could use 
synaptic, but searches in it for lha or lzh also show nothing. 

Thanks in advance for the help.

---

### Post by mendicant on 2005-01-25
You might need a multiverse source in your sources.list.

---

### Post by dwanders on 2005-01-25
I currently have 
CDROM unstable
warty
warty-security
stable from marillat
jedit
java blackdown unstable

how can I add multiverse?

---

### Post by dwanders on 2005-01-25
and it worked, just so others dont need to search through the lists again:

sudo gedit /etc/apt/sources.list

add the following line:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse

if you dont have it. Save the file, then do
apt-get update
apt-get install lha

and you should be gravy.

---

### Post by hogzilla on 2008-10-02
This was returned when I did an apt-get update

```
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/warty/multiverse/binary-i386/Packages.gz  404 Not Found
```

Anything I can do to get lhz?

---

### Post by SimbaSpirit on 2008-10-19
hogzilla you do realize you posted in a 2 year old thread right? We're using hardy now, almost intrepid

---

