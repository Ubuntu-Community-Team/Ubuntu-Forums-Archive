---
title: "Howto: Gaim 2.0 beta 5"
date: 2006-12-16
forum: Outdated Tutorials &amp; Tips
---

### Post by cborga1985 on 2006-12-16
***[SIZE="6"][COLOR="Red"]Old thread but this still works for those who can't use beta 6.[/COLOR][/SIZE]***

**[SIZE="3"]Instructions for i386(Dapper,Edgy)[/SIZE]**

**Add Debuntu to your sources**
```
sudo gedit /etc/apt/sources.list

```
Add this to the bottom of the file

**For Dapper:**
```
#Debuntu Repo
deb  http://repository.debuntu.org/ dapper multiverse
deb-src http://repository.debuntu.org/ dapper multiverse
```

**For Edgy:**
```
#Debuntu Repo
deb  http://repository.debuntu.org/ edgy multiverse
deb-src http://repository.debuntu.org/ edgy multiverse
```
Now save the file

**Add Debuntu as a trusted source**
```
cd ~
wget http://repository.debuntu.org/GPG-Key-chantra.txt
sudo apt-key add GPG-Key-chantra.txt
rm GPG-Key-chantra.txt
```

**Update Apt**
```
sudo apt-get update
```

**Install Gaim**
```
sudo apt-get install gaim gaim-data
```
Type **Y** when it asks you to install the dependencies.

**[COLOR="Red"]Instructions to revert back to older version.[/COLOR]**

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

### Post by magomago on 2007-01-05
Thanks for the repo :)

---

### Post by supertux on 2007-01-05
thx, its working fine here!

---

### Post by dysfunctional on 2007-01-07
works like a charm! thank you very much, was looking for this.

---

### Post by Sammi on 2007-01-13
Thanks! It worked like a charm :D

---

### Post by cajunaggie on 2007-01-14
Oooh! Look at the pretties! :D

---

### Post by voidmain on 2007-01-15
Looks like the debuntu repositories only have beta3. Is that correct or is beta5 somewhere?

---

### Post by th3gh05t on 2007-01-31
Hi,

I followed these instructions, and everything is working, but I need to downgrade back to v1.5. File transfers don't work with this new version..

How do I downgrade back to the original version?

Thanks for your help!

---

### Post by Sammi on 2007-01-31
1.5 is in the Dapper repositories. Just uninstall Gaim in Synptic. Do this command in a terminal:```
sudo apt-get clean

```and you should find version 1.5 in Synaptic again.

If not then I found the packages on [packages.ubuntu.com]("http://packages.ubuntu.com/"): [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gaim&searchon=names&subword=1&version=dapper&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gaim&searchon=names&subword=1&version=dapper&release=all)

---

### Post by Zer0Nin3r on 2007-02-01
This is great and all, but who is hosting these repositories?  How can one tell if the source is trustworthy?

**update**
The site looks legit, and I don't doubt it, but I remember reading some posts in the Easy Ubuntu Forum about being careful using repositories from 3rd parties or not well known sources.

---

### Post by jake3988 on 2007-02-01
> **th3gh05t said:**
> Hi,

I followed these instructions, and everything is working, but I need to downgrade back to v1.5. File transfers don't work with this new version..


Yeah, beta 5, while awesome, does break a few things.  For instance, I saw the great tutorial on how to change your gaim message using autoprofile.  It breaks autoprofile pretty badly too. (its a known bug because of an API change)

Not to be a sorry bum on a great thread, but uh, just want to bring that up as well.

Also to note: I have beta3 and file-transfers work on that.  So, just remove the newly added repository and if you have all the normal repositories beta3 should be available.

---

### Post by cborga1985 on 2007-02-17
> **jake3988 said:**
> Yeah, beta 5, while awesome, does break a few things.  For instance, I saw the great tutorial on how to change your gaim message using autoprofile.  It breaks autoprofile pretty badly too. (its a known bug because of an API change)

Not to be a sorry bum on a great thread, but uh, just want to bring that up as well.

Also to note: I have beta3 and file-transfers work on that.  So, just remove the newly added repository and if you have all the normal repositories beta3 should be available.

just wanted to add instructions to remove this version

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

