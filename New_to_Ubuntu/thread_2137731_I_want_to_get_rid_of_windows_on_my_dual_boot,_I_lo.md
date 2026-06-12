---
title: "I want to get rid of windows on my dual boot, I love linux!"
date: 2013-04-21
forum: New to Ubuntu
---

### Post by SukuC23101993 on 2013-04-21
After messing with linux on and off for years, I want to finally get rid of my dual boot. Windows presence just gets me annoyed, how can I stop dual booting and just boot normally into linux?

---

### Post by Frogs Hair on 2013-04-21
If it is a traditional dual boot and not a Wubi installation see deleting partitions at the link.[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)


Edit: You could also just backup your files and format the entire hard-drive and do a fresh installation.

---

### Post by BigZ1981 on 2013-04-21
> **Frogs Hair said:**
> You could also just backup your files and format the entire hard-drive and do a fresh installation.

I second that motion.  Then you won't have to deal with the whole mess of reverting to a single boot.  Plus it's like having a brand new system again! :D

---

### Post by AndyOpie150 on 2013-04-22
What files would need to be backed up? Just the home file, or more?

---

### Post by deadflowr on 2013-04-22
> **AndyOpie150 said:**
> What files would need to be backed up? Just the home file, or more?

Any and every file you feel that you want to keep.
If that means only files in the home folder, then so be it.
If you have scripts or configuration files you would like to keep, so as to not have to re-edit them later, that is fine as well.

My take on it is that if you did any editing to any file, then back it up. Unless of course you borked up that file.

---

### Post by ArminasAnarchy on 2013-04-22
I find Dropbox is really handy for this kind of thing. :D Using a couple of sym-links to automatically back things up also means you can forget (more or less) about backing up manually:

```
ln -s /thing/you/want /where/you/want/it
```, 

...so if you want everything in your Documents folder backed up, you'd do:

```
ln -s /home/username/Documents /home/username/Dropbox
```

There's a .deb you can download from the website, run it and then start the program. Make sure you have the 'gpg-me' package installed - it doesn't seem to pick it up as a dependancy, and only notifies you about it when you're installing the daemon.

---

### Post by Frogs Hair on 2013-04-22
Drop box or Ubuntu One work for moving files from one installation to another. I install the latest releases so my home folder is synced on Ubuntu One. I still need a dual boot so what happens in Windows stays in Windows :o though Ubuntu One has a Win installer.

---

