---
title: "HOW TO: Gaim 2.0 Beta 6 on Dapper"
date: 2007-02-17
forum: Outdated Tutorials &amp; Tips
---

### Post by cborga1985 on 2007-02-17
[SIZE="5"]***[COLOR="Red"]Notice: This seems to not work on Kubuntu but you can use beta 5. Here is my beta 5 [[COLOR="blue"][SIZE="5"][B][I]thread***[/SIZE][/COLOR]]("http://www.ubuntuforums.org/showthread.php?p=1893186#post1893186").[/COLOR][/B][/I][/SIZE]

**[SIZE="2"]For AMD64 Architecture:[/SIZE]**

**Step 1: Download the debs to your Desktop.**

*gaim_2.0.0+beta6-0ubuntu4_amd64.deb* (1.82 MB)
[http://www.megaupload.com/?d=S2Q0BA6K](http://www.megaupload.com/?d=S2Q0BA6K)

*gaim-data_2.0.0+beta6-0ubuntu4_all.deb* (5.04 MB)
[http://www.megaupload.com/?d=HH5GNP2J](http://www.megaupload.com/?d=HH5GNP2J)

*gaim-dbg_2.0.0+beta6-0ubuntu4_amd64.deb* (952 Bytes)
[http://www.megaupload.com/?d=SBDRAWHE](http://www.megaupload.com/?d=SBDRAWHE)

*gaim-dev_2.0.0+beta6-0ubuntu4_amd64.deb* (152.11 KB)
[http://www.megaupload.com/?d=Y76WSPHG](http://www.megaupload.com/?d=Y76WSPHG)

**Step 2: Install Gaim.**
```

cd ~/Desktop
sudo dpkg -i --force-all gaim_2.0.0+beta6-0ubuntu4_amd64.deb gaim-data_2.0.0+beta6-0ubuntu4_all.deb gaim-dbg_2.0.0+beta6-0ubuntu4_amd64.deb gaim-dev_2.0.0+beta6-0ubuntu4_amd64.deb
```

**Step 3: Fix Depends.**
```
sudo apt-get -f install
```

[SIZE="2"]**For I386 Architecture:**[/SIZE]

**Step 1: Add source repository.**
```
sudo gedit /etc/apt/sources.list

**Add this to the bottom and save file.**

#Debuntu Repository
deb-src http://repository.debuntu.org/ edgy multiverse

```
*Notice: Don't worry about the fact that we are using Edgy sources. It won't won't hurt anything for this purpose as long as you did what I said correctly.*

**Step 2: Update Apt.**
```

wget http://repository.debuntu.org/GPG-Key-chantra.txt
sudo apt-key add GPG-Key-chantra.txt
rm GPG-Key-chantra.txt
sudo apt-get upgrade (optional)
sudo apt-get dist-upgrade (optional)
sudo apt-get update

```

**Step 3: Get Gaim source files.**
```
mkdir ~/Desktop/gaim
cd ~/Desktop/gaim
apt-get source gaim-data gaim
cd gaim*
```
*Notice: You might get a message saying that something already has something or related. You can safely ignore this.*

**Step 4: Install fakeroot and essentials.**
```
sudo apt-get install build-essential dpkg-dev debhelper fakeroot cdbs libgadu-dev
```

**Step 5: Change repo to dapper source.**
```
sudo gedit /etc/apt/sources.list
```

Find **deb-src [http://repository.debuntu.org/](http://repository.debuntu.org/) edgy multiverse** and replace it with
deb [http://repository.debuntu.org/](http://repository.debuntu.org/) dapper multiverse and save. Now  run this command to update.
```
sudo apt-get update
```

**Step 6: Get depends.**
```
sudo apt-get build-dep gaim-data
```

**Step 7: Build Packages.**
```
fakeroot dpkg-buildpackage -d
```

**Step 8: Install Gaim.**
```
cd ..
sudo dpkg -i --force-all gaim*.deb
sudo apt-get -f install
```

**Step 9: Nothing** :lolflag: 
Gaim should be installed and working. Post any problems back to this post.

**[SIZE="2"][COLOR="Red"]Instructions to reverse to old version:[/COLOR][/SIZE]**

**Step 1: Remove Debuntu repository and Update Apt.**
```
sudo gedit /etc/apt/sources.list

**Remove debuntu line and save file.**

sudo apt-get update
```

**Step 2: Force Gaim to remove.**
```
sudo dpkg -P --force-all gaim gaim-data gaim-dbg gaim-dev
```

**Step 3: Reinstall Gaim which will also fix depends.**
```
sudo apt-get -f install
```

---

### Post by bioman85 on 2007-02-23
Thanks for the how-to. I just re-installed Dapper and set my /home to a whopping 100 MB, so once I fix that, I'll try out your methods.

---

### Post by subdee on 2007-03-02
at the part where i have to get the depends, i get the error as translated from Greek: Build dependencies for gaim-data are not satisfied.

?

---

### Post by cborga1985 on 2007-03-03
> **subdee said:**
> at the part where i have to get the depends, i get the error as translated from Greek: Build dependencies for gaim-data are not satisfied.

?

yeah it's fixed now

---

