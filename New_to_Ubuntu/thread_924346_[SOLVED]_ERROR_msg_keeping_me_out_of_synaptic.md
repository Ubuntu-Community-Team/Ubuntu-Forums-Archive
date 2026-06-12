---
title: "[SOLVED] ERROR msg keeping me out of synaptic"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by natedogg23 on 2008-09-19
it closes synaptic and add/remove if i close it. i must have messed up a word when adding a repository for miro and the terminal wont recognize sorce lists;        
        E: Malformed line 44 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
help!

---

### Post by northern lights on 2008-09-19
Please post the output of ```
cat /etc/apt/sources.list
```Thank you.

---

### Post by drs305 on 2008-09-19
Backup and open your sources.list for editing:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
gksu gedit +44 /etc/apt/sources.list
```

The editor will open on the line with the problem. If you can't figure out what the problem is, post it here by:
```
cat /etc/apt/sources.list
```

---

### Post by natedogg23 on 2008-09-19
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) edgy

---

### Post by drs305 on 2008-09-19
> **natedogg23 said:**
> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security multiverse
**deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) edgy**

Delete the last line that references "edgy" and save. That will solve your problem.

I note however that several of your commented lines (#) contain references to feisty (lines 35 & 36). If you try to uncomment them in the future they will also generate errors if you are running hardy. It would be best to either delete these references or change the version to "hardy" (and hope a hardy repository by that name exists). Again, these references only matter if you uncomment the line(s).

---

### Post by natedogg23 on 2008-09-19
delete it where? i cant get into synaptic and i knew that was the word that screwed it up! im very new to this so i also dont know what that means

---

### Post by northern lights on 2008-09-19
> **drs305 said:**
> Backup and open your sources.list for editing:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
gksu gedit +44 /etc/apt/sources.list
```
The editor will open on the line with the problem.
Now delete or comment (put a hash/pound sign #) the respective line.
Given that it's for Edgy and thus obsolete, deletion is in order.

---

### Post by drs305 on 2008-09-19
> **natedogg23 said:**
> delete it where? i cant get into synaptic and i knew that was the word that screwed it up! im very new to this so i also dont know what that means

Go back to my earlier post. Open a terminal (Applications, Accessories, Terminal). Then run these two commands in the terminal. It's best to cut/paste to avoid typos. 

```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
gksu gedit +44 /etc/apt/sources.list

```

Then delete the line and save.

---

### Post by issih on 2008-09-19
Just edit the file using a text editor..you will need root privileges though:

running this command in a terminal will open the file in a text browser with root privileges:

```
gksudo gedit /etc/apt/sources.list
```

just enter your login password when prompted and a text editor will pop up with the file open in it.

remove the offending line, or if you prefer comment it out by sticking a # sign at the start of the line, then save the file.

That should solve your problem

Hope that helps

---

### Post by natedogg23 on 2008-09-19
problem solved! i just r clicked on the error icon on the panel and found third party software from there and deleted it. thanks guys! how do u know all these terminal commands?

---

