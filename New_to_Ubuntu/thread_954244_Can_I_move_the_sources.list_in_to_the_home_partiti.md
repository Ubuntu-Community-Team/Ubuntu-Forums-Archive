---
title: "Can I move the sources.list in to the home partition?"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by pluckypigeon on 2008-10-21
I know it sounds stupid but when I do a fresh install I always forget to back it up. 

Is there a way I could move it in to my home directory and have it read from there by apt-get and everthing?

Home is on a separate partition. 

Thanks!

---

### Post by Sef on 2008-10-21
> I know it sounds stupid but when I do a fresh install I always forget to back it up. 

Is there a way I could move it in to my home directory and have it read from there by apt-get and everthing?

Home is on a separate partition. 

Thanks!

Do you mean reinstalling the same version or the newer version.  If it is a newer version, then it would change the sources list and make the request invalid.

---

### Post by niteshifter on 2008-10-21
Hi,

You can use AptonCD to make an .iso in your home folder. Note that this won't help you on an upgrade, just a reinstall of the same version.

---

### Post by pluckypigeon on 2008-10-21
> **Sef said:**
> Do you mean reinstalling the same version or the newer version.  If it is a newer version, then it would change the sources list and make the request invalid.

No, sorry, I should have been more specific.

When I decide to do a fresh install I don't want to have to remember to back up stuff.

I usually forget the Apache settings and Repo list, those are the things that make me scared to do a fresh install.

I want to move the sources.list to my home folder so that it can be used from there instead of /etc/apt/ so I won't need to back it up if I decide to do a new install.

---

### Post by pluckypigeon on 2008-10-21
> **niteshifter said:**
> Hi,

You can use AptonCD to make an .iso in your home folder. Note that this won't help you on an upgrade, just a reinstall of the same version.

Thanks :), not exactly what I'm looking for but I'll check it out!

---

### Post by pluckypigeon on 2008-10-21
> **pluckypigeon said:**
> Thanks :), not exactly what I'm looking for but I'll check it out!

It's not really what I am looking for :(

---

### Post by hyper_ch on 2008-10-21
you could symlink them.. have the actual files in your home and symlink them to their location. But backing up /etc isn't a big thing either to do.

---

### Post by pluckypigeon on 2008-10-21
> **hyper_ch said:**
> you could symlink them.. have the actual files in your home and symlink them to their location. But backing up /etc isn't a big thing either to do.

Thanks! That sounds like what I need to do. How would I do that?

---

### Post by hyper_ch on 2008-10-21
first, you could read up what a symlink is ;)

---

### Post by pluckypigeon on 2008-10-21
> **hyper_ch said:**
> first, you could read up what a symlink is ;)

I'm reading this as we speak :)[http://en.wikipedia.org/wiki/Symbolic_link](http://en.wikipedia.org/wiki/Symbolic_link)

---

### Post by hyper_ch on 2008-10-21
:) wiki entry looks good :)

---

### Post by rakris on 2008-10-21
something like this :P. be sure to do some permission thingy

```
ln -s  $HOME/sources.list /etc/apt/sources.list
```

---

### Post by prshah on 2008-10-21
> **hyper_ch said:**
> you could symlink them.. have the actual files in your home and symlink them to their location. But backing up /etc isn't a big thing either to do.

> **hyper_ch said:**
> first, you could read up what a symlink is ;)

> **rakris said:**
> something like this :P. be sure to do some permission thingy

```
ln -s  $HOME/sources.list /etc/apt/sources.list
```

[spoonfeed]```

sudo cp -p /etc/apt/sources.list /home/sources.list
sudo ln -s /home/sources.list /etc/apt/sources.list

```

Notes:
a) ln needs absolute paths.
b) permissions on actual file apply to target file (symlinked file)

Note it is in "/home" _not_ /home/username (this will avoid confusion if the username ever changes)
[/spoonfeed]

---

### Post by pluckypigeon on 2008-10-21
thanks but i've fu**ed something up. i have to do a fresh install anyway.

---

### Post by kellemes on 2008-10-21
> **pluckypigeon said:**
> thanks but i've fu**ed something up. i have to do a fresh install anyway.

This is why moving or symlinking sources.list isn't going to protect you from trouble..
You better make regular backups of /etc
Tarring and compressing /etc give me a file of 1,74 Mb, so hardly any reason to pick individual files from /etc to backup.

---

### Post by pluckypigeon on 2008-10-21
> **kellemes said:**
> This is why moving or symlinking sources.list isn't going to protect you from trouble..
You better make regular backups of /etc
Tarring and compressing /etc give me a file of 1,74 Mb, so hardly any reason to pick individual files from /etc to backup.

Lol.:) I've reinstalled any way. I cut the apt directory and placed it in home and then it said there was no more space in root:confused:

I tried to put it back and it wouldn't let me, it also wouldn't let me open anything with root privileges. 

I don't know for sure if the problem came from moving the folder or something else though.

Anyway everything is fine now! I'm going to give up that idea!:)

I'm not going to mark this as solved unless someone complains because in all truth it's still unsolved

---

### Post by prshah on 2008-10-21
> **pluckypigeon said:**
> 
I'm not going to mark this as solved unless someone complains because in all truth it's still unsolved

Ok, since you're reinstalling anyway, you can create a separate partition with the mount point /etc/apt; just like you have a separate partition for /home.

Then, when reinstalling, all you have to do is take care not to overwrite /etc/apt; reinstalling /etc in another partition will not disturb the partition that carries /etc/apt.

---

### Post by hyper_ch on 2008-10-21
or just a mount point /etc

---

### Post by Archmage on 2008-10-21
How about copying every file into a folder of your home-partion. After an install you can than work on the files one by one.

BTW: If I'm modifing the sources.list I would do this (over ther terminal of Gnome):

cat ~/NewInstall/sources.list
(copy the whole thing)
sudo gedit /etc/apt/sources.list
(delete everything and than paste all in)

---

