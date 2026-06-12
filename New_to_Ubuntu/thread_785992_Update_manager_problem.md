---
title: "Update manager problem"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by eberndl on 2008-05-07
I'm re-posting this from the general help forum, because this one seems to be more active.   [Original thread]("http://ubuntuforums.org/showthread.php?p=4906128#post4906128").

I'm trying to complete an update that Ubuntu says I need (orange yield sign on task bar).  I open the update manager, and it says it has been 9 days since my last update.  I tell it to check for updates, and get this error message:
```
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.
```

My Hardy Heron CD is in the computer, and is on my desktop (so I assume it's properly mounted).  Any idea of what I should do?

Thanks in advance.

---

### Post by angry_johnnie on 2008-05-08
Open a terminal and type

```
gksu gedit /etc/apt/sources.list
```

and then comment out (add a # sign at the beginning) the first line, so it looks like this:

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release Candidate i386 (20080417)]/ hardy main restricted

Save the changes and exit the text editor.
Then, in terminal do

```
sudo apt-get update
```

And it won't be looking for the cdrom any more.

---

### Post by eberndl on 2008-05-08
Worked like a charm!!! THANK YOU!!!

---

