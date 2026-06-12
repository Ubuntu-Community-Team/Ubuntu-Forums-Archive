---
title: "Can someone tell me if this is an unofficial repo"
date: 2006-05-03
forum: Repositories &amp; Backports
---

### Post by Campitor on 2006-05-03
Hi all.

  I'm currently located in Costa Rica.  I downloaded UBUNTU from my university's ftp site.  Browsing through the ftp I found what I believe is an unofficial repository or mirror.  Is there a way to find out if these are repositories, a mirror, or just copies of all the files in some other repository.  These addresses are the ones that I checked:

[HTML]ftp://ftp.ucr.ac.cr/pub/ubuntu/[/HTML]
[HTML]ftp://ftp.ucr.ac.cr/pub/ubuntu/pool/[/HTML]
[HTML]ftp://ftp.ucr.ac.cr/pub/ubuntu/dists/breezy/[/HTML]

If they are repositories (up to date), how can I use those to install/update packages? This would be a lot faster download, than getting packages from some other repo in the US.  Thanks in advance for your help

Camp

---

### Post by o_fortuna on 2006-05-03
[QUOTE=Campitor]Hi all.

  I'm currently located in Costa Rica.  I downloaded UBUNTU from my university's ftp site.  Browsing through the ftp I found what I believe is an unofficial repository or mirror.  Is there a way to find out if these are repositories, a mirror, or just copies of all the files in some other repository.  These addresses are the ones that I checked:

[HTML]ftp://ftp.ucr.ac.cr/pub/ubuntu/[/HTML]
[HTML]ftp://ftp.ucr.ac.cr/pub/ubuntu/pool/[/HTML]
[HTML]ftp://ftp.ucr.ac.cr/pub/ubuntu/dists/breezy/[/HTML]

If they are repositories (up to date), how can I use those to install/update packages? This would be a lot faster download, than getting packages from some other repo in the US.  Thanks in advance for your help

Camp[/QUOTE]
These are the official Ubuntu mirrors for Costa Rica:
```
Costa Rica
    * http://ftp.ucr.ac.cr/ubuntu/
    * ftp://ftp.ucr.ac.cr/pub/ubuntu/

```
So, yes, those will work. Just edit the sources.list. Open the terminal (Applications, Accessories, Terminal) and copy this in:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
sudo gedit /etc/apt/sources.list
```
Replace the mirrors in that file with the ones above. If it doesn't work for some reason, you can always go back to the old ones:
```
sudo cp /etc/apt/sources.list.old /etc/apt/sources.list
```

---

