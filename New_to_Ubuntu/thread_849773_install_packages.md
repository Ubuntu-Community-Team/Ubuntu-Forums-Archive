---
title: "install packages"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by lio_013 on 2008-07-04
i reinstall ubuntu on my computer 
and i have more than 200 package on a cd "i burn them as data cd " 
is there a method to install them all together ?
not one by one
please help

---

### Post by scragar on 2008-07-04
if they are .deb then yes:
```
cd /media/cdrom0
for i in `ls`
do
sudo dpkg -if /media/cdrom0/
done
```
if that doesn't work there's a recursive option that may work:```

sudo dpkg -R -i /media/cdrom0
```


after that's done run```
sudo apt-get install -f
```
to make sure everything has the dependencies met.

---

### Post by lio_013 on 2008-07-04
i tryed to do the first code but i couldnot
i did the second one it cause me alot of problems on the synpatic and add/remove 
now im running on "sudo apt-get update to fix the problems"
any ideas????

---

### Post by lio_013 on 2008-07-04
i alsohad a packages that i cannot remove from my synaptic list 
the package is kio-umountwrapper

---

### Post by ChameleonDave on 2008-07-04
> **lio_013 said:**
> i alsohad a packages that i cannot remove from my synaptic list 
the package is kio-umountwrapper

That's one that comes up more than once.

Some people say it is because the package tries to remove a file that doesn't exist, and that creating the file will solve the problem by allowing it to be removed.  One of the following pairs of commands should fix that (depending on the exact version of kde):
```

mkdir -p /usr/share/apps/d**3**lphin/servicemenus/
touch /usr/share/apps/d**3**lphin/servicemenus/media_safelyremove.desktop.distrib
```
or
```
mkdir -p /usr/share/apps/d**o**lphin/servicemenus/
touch /usr/share/apps/d**o**lphin/servicemenus/media_safelyremove.desktop.distrib
```

When I had the problem, I fixed it in the following heavy-handed way:

```

sudo cd /var/lib/dpkg/
sudo mkdir info.backup
sudo mv info/kio-umountwrapper* info.backup/

```

or

```

sudo rm /var/lib/dpkg/info/kio-umount*
```


Once you have done any of those four solutions, do the following:

```

sudo dpkg --force-all --purge kio-umountwrapper
sudo apt-get install -f

```

...in order to clean up.

---

### Post by ChameleonDave on 2008-07-04
> **lio_013 said:**
> i reinstall ubuntu on my computer 
and i have more than 200 package on a cd "i burn them as data cd " 
is there a method to install them all together ?
not one by one
please help

I'd prefer not to install them all at once.  Linux dependencies are a tricky thing.  You'd also be installing old versions of a lot of software.

I'd just put them in /var/cache/apt/archives, open Synaptic, refresh, and mark all the software I wanted to install.  Synaptic would then intelligently use those packages that were available locally, and download those packages that it needed to.

---

### Post by lio_013 on 2008-07-05
great but i dont know how to copy all of them to the folder by using the terminal?

---

### Post by ChameleonDave on 2008-07-05
> **lio_013 said:**
> great but i dont know how to copy all of them to the folder by using the terminal?

Well, you don't have to use the terminal.

Let's say you're a GNOME and Nautilus user.  Open up Nautilus as root.  You can do that by typing "gksu nautilus" on the command line (I believe Ctrl + F2) opens one up in GNOME).

You can then navigate to your CD, copy, navigate to the archives directory, and paste.

######################

To do it entirely on the command line, you need to enter the exact path for both directories.  For example:

```
sudo cp   /media/cdrom/*.deb   /var/cache/apt/archives/
```

Notice that there is an asterisk in the first path but not the second.  The first path is to all of the files you want to move (the asterisk means "all").  The shell will expand that out to hundreds of entries.  The last path is the directory where all that should be dumped.

You can also use "mv" instead of "cp".

---

