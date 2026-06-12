---
title: "making repository from DVD/CD Image"
date: 2006-01-02
forum: Repositories &amp; Backports
---

### Post by rupert on 2006-01-02
Hi,
on the debian blog someone postet a shellscript that creates a local repository from an iso image.
[http://blog.daniel-baumann.ch/2006/01/01#20060101_repository-from-images](http://blog.daniel-baumann.ch/2006/01/01#20060101_repository-from-images)

since I have a really slow internet connection and somtimes play arround with my installation, i would love to see this converted to ubuntu to build a full featured local repo.

thx

---

### Post by tkjacobsen on 2006-01-16
I just bulid my own repository today containint all my an my roommates kubuntu and ubuntu packages. Not the ones from the installation but the ones downloaded with apt. 
I followed this howto:
[http://www.debian.org/doc/manuals/repository-howto/repository-howto](http://www.debian.org/doc/manuals/repository-howto/repository-howto)

I mountet an external harddisk at /home/anta/repo

I added the packages downloaded with apt. These are in /var/cache/apt/archives. Those i put in:
/home/anta/repo/dists/breezy/main/
Then (so apt can read the repo): 
```
mkdir /home/anta/repo/breezy/main/binary-i386
```

I also added the packages from the ubuntu install cd locate in /media/cdrom0/pool. Those are in
/home/anta/repo/dists/breezy/cd/
```
mkdir /home/anta/repo/breezy/cd/binary-i386
```

and finally build the repository:
```
dpkg-scanpackages dists/breezy/main/ /dev/null | gzip -9c > dists/breezy/main/binary-i386/Packages.gz

dpkg-scanpackages dists/breezy/cd/ /dev/null | gzip -9c > dists/breezy/cd/binary-i386/Packages.gz
```

Then the repository can be added:
```
deb file:/home/anta/repo/ breezy main cd 
```

---

