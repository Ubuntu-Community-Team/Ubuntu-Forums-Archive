---
title: "Any good disk cleaning program?"
date: 2011-10-25
forum: New to Ubuntu
---

### Post by hoangtu69 on 2011-10-25
Do you have a good free disk cleanning program that you recommend? I want to keep my machine clean by deleting unused programs and/or files. On windows, I use a program called CCleaner.
 
Is there a similiar one for Ubuntu that you recommend?
 
Thanks

---

### Post by _Ouroboros_ on 2011-10-25
bleachbit is a linux equivalent to ccleaner for removing temp files, history files, unused files related to localisations, etc.

install with:
```
sudo apt-get install bleachbit
```
or search for bleachbit using synaptic package manager.

As far as uninstalling sofware that you do not use, I don't know what software does that automatically for linux.  I would suggest uninstalling the packages manually one by one.

---

### Post by wolfen69 on 2011-10-25
I usually just do
```
sudo apt-get clean && sudo apt-get autoremove
```
will do the trick.

---

### Post by Mark Phelps on 2011-10-25
Just be very careful about using something called Computer Janitor.  I tried this a while back and it trashed my install so bad that I had to reinstall from scratch.

Also, don't get hungup on optimizing very small amounts of disk space usage.  Linux OSs are a lot less space demanding than Windows OSs.

You don't want to risk corrupting your install just to remove a small amount of disk space.

---

### Post by unknown user on 2011-10-25
I use bleachbit myself and find it ver good. I have never used (sudo apt-get clean) but will have a look at it tonight and see what it is like.

Removing the programs that I no longer use, I have found it easy enough to go into the software centre, click on installed software and then remove the ones that I no longer need from there.

I am currently looking for a good security delete program that has a good gui frontend. Something like this would help you are you could remove unwanted files and be sure that they are gone.

---

### Post by kemtnbkr on 2011-10-25
As far as 'disk cleaning' goes, 
```
sudo apt-get autoclean
```
just deletes package files that were downloaded, and are now installed and no longer needed.
```
sudo apt-get autoremove
```
removes any packages on your system that aren't required for another, cleaning up your install.

Both are useful, but they are more for keeping your installed programs under control than actual disk cleaning- they don't clear your cache or temp files or so on.  Just a FYI for those that didn't know :)

---

### Post by crjackson on 2011-10-25
> **wolfen69 said:**
> I usually just do
```
sudo apt-get clean && sudo apt-get autoremove
```
will do the trick.

+1

It's really is the best way to clean up, without risking anything.

---

### Post by wojox on 2011-10-26
> **hoangtu69 said:**
> On windows, I use a program called CCleaner.

Bleachbit is the Linux equivelent.

---

### Post by crjackson on 2011-10-26
> **kemtnbkr said:**
> As far as 'disk cleaning' goes, 
```
sudo apt-get autoclean
```
just deletes package files that were downloaded, and are now installed and no longer needed.
```
sudo apt-get autoremove
```
removes any packages on your system that aren't required for another, cleaning up your install.

Both are useful, but they are more for keeping your installed programs under control than actual disk cleaning- they don't clear your cache or temp files or so on.  Just a FYI for those that didn't know :)

```
sudo apt-get clean
```
will clear out your cache

most temp files are removed automatically each reboot...

---

### Post by beew on 2011-10-26
> **wolfen69 said:**
> I usually just do
```
sudo apt-get clean && sudo apt-get autoremove
```will do the trick.

That won't clean up things that are user specific such as your browser and media player caches. These are usually bigger than system junks like apt cache and so on. Bleachbit (not as root) would clean them all with one push of a button.

Also I find autoremove trying to remove stuffs which are actually useful like 3d-experimental driver in 11.10.

---

### Post by rojaasensei on 2011-10-26
> **_Ouroboros_ said:**
> bleachbit is a linux equivalent to ccleaner for removing temp files, history files, unused files related to localisations, etc.

install with:
```
sudo apt-get install bleachbit
```
or search for bleachbit using synaptic package manager.

As far as uninstalling sofware that you do not use, I don't know what software does that automatically for linux.  I would suggest uninstalling the packages manually one by one.


Or google Bleachbit's homepage.  They have the latest version there to download as a deb.  Actually the webpage address should be listed in its section in the software manager.

---

### Post by wolfen69 on 2011-10-26
imo, there's no need for bleachbit. Linux systems can run for years without any "cleaning" apps.

---

