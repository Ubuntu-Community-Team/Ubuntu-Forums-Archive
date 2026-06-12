---
title: "gcc stdio.h compilation error?"
date: 2008-03-10
forum: Programming Talk
---

### Post by Thesuperchang on 2008-03-10
Hello, I'm a new programming to the C world. All the programming computers at uni seem to be running Ubuntu Edgy, so I decided that I'd set my crap-top up with Gutsy. Well not really a crap-top, Ubuntu is the only thing that doesn't make my Compaq Presario V3021AU overheat.

Anyways, I made a simple C programme but when I compile it gives me an error about stdio.h not found and printf being an ambiguous command. Well obviously the compiler complains about printf because its from the not found sdtio so that not the problem. However why can't the gcc compiler find the stdio library. Its pretty much a fresh install of Gutsy with a few additions such as broadcom drivers, compiz manager and WINE.

Thanks in advance,
C. Anderson.

---

### Post by Thesuperchang on 2008-03-10
Ok so I do a bit of forum scanning and I find a thread saying I need the build-essential package. So I open up a terminal and type,
sudo apt-get install build-essential
I type my password and it finds all the crap and goes to install. But just I think everything is going smoothly, it demands I pop in my Ubuntu install CD. Unfortunately I lent this to my lab partner and haven't got it back yet. Is there anyway I can download the build-essential package from the net or something?

---

### Post by Cenotaph on 2008-03-10
You need build-essential. Just go to Software Sources in System -> Administration, unselect the CD and use repositories from the net.

---

### Post by Jessehk on 2008-03-10
To just expand what Ceotahph said...

apt, Ubuntu's (and its parent, Debian) package manager, knows where to find and download software from *repositories*. These repositories are stored in the file /etc/apt/sources.list . 

You can edit this file with either a text editor (such as gedit, or nano) or with a GUI such as Synaptic Package Manager (as mentioned previously).

By default, Ubuntu adds its installation CD as a repository, but it can be removed. Doing so will make apt search for software online rather than on physical media.

Makes sense? :)

---

### Post by Mevsthevoices on 2008-03-11
> **Cenotaph said:**
> You need build-essential. Just go to Software Sources in System -> Administration, unselect the CD and use repositories from the net.

Yea, this will come with gcc and g++ (for c++), plus stdio.h library which is located in /usr/include/stdio.h if installed. So #include /usr/include/stdio.h fixing this should also remove any winging about ambiguous functions

---

### Post by the_unforgiven on 2008-03-11
> **Thesuperchang said:**
> Ok so I do a bit of forum scanning and I find a thread saying I need the build-essential package. So I open up a terminal and type,
sudo apt-get install build-essential
I type my password and it finds all the crap and goes to install. But just I think everything is going smoothly, it demands I pop in my Ubuntu install CD. Unfortunately I lent this to my lab partner and haven't got it back yet. Is there anyway I can download the build-essential package from the net or something?
Another trick (apart from the normal "disabling of cdrom in sources.list" which others have told you) is to keep an ISO of the CD onto your hard disk and loop-mount it on /cdrom. This comes handy when you don't have access to your CD rightaway, but it might be required for apt to find out dependencies.

The command to loop-mount is:
```
$ sudo mount -o loop /path/to/iso/file /cdrom
```

This way, you won't have to keep messing up with sources.list.

After you're done, you can just unmount it using:
```
$ sudo umount /cdrom
```
HTH ;)

---

### Post by Thesuperchang on 2008-03-11
Awesome, thanks guys. My Ubuntu set up is pretty much done now.

Regards,
C. Anderson

---

