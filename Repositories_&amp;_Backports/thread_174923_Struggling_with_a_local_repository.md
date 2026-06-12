---
title: "Struggling with a local repository"
date: 2006-05-12
forum: Repositories &amp; Backports
---

### Post by rpm13 on 2006-05-12
I am running ubuntu (breezy upgraded to dapper but perhaps not properly) at home.  I do not want to expend my bandwidth on large downloads.  So I got a copy of a (fairly complete but not sure) repo from a friend who has a mirror in his office.

When I tried to install emacs from there synaptic complained.  I found that the actual version in the pool was higher than the version in the Packages.gz in dists.  So I removed the Packages.gz and remade them with dpkg-scanpackages.

Now it started giving me errors with some md5 in the release file.  So I removed the release file.  Now synaptic works but shouts about authentication.

Any suggestions??

---

### Post by jtibau on 2006-05-13
Don't worry much about the authentication issue. The problem is that ubuntu repositories use gnu pg to authenticate the provider of the packages, that way it somehow knows that you aren't getting/installing stuff that might be dangerous to your sytem.
You, however, know the person that gave you the packages, so you are pretty much sure that he didn't replace some program with some malicious code that he wrote...
At least I think that is the idea of identifying the owner of the repository.
Since you erased the Release file, you erased the identifier.
I think that's the way it works anyway.
I'm working on building my own repo to help some friends, same as you I think. I'm working around the issue of building the release file appropiately. Getting a valid GPG key seems kinda troublesome though, so I think I will make my friends suffer through the authentication question.... :D 
Hope that helps

---

### Post by tsmets on 2006-05-27
I did a *server* install on a machine whihc is supposed to run all the time !
I woul dlike not to leave in the Ubuntu DVD permanently in the DVD reader to be able to install all the new package. I therefore did a copy of the DVD on the hard disk.

I would like to modify the first line of ```
 /etc/apt/sources.list
``` to something to indicate that there is a copy of the DVD under /data/ubuntu-5.1 from```
# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
deb file:///data/ubuntu-5.1[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
```

Would this work .... ?
Otherwize, what do I need to do ... ?

\T,

---

### Post by Mustard on 2006-05-27
[QUOTE=tsmets]I did a *server* install on a machine whihc is supposed to run all the time !
I woul dlike not to leave in the Ubuntu DVD permanently in the DVD reader to be able to install all the new package. I therefore did a copy of the DVD on the hard disk.

I would like to modify the first line of ```
 /etc/apt/sources.list
``` to something to indicate that there is a copy of the DVD under /data/ubuntu-5.1 from```
# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
deb file:///data/ubuntu-5.1[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
```

Would this work .... ?
Otherwize, what do I need to do ... ?

\T,[/QUOTE]

I assume this server is online?

---

### Post by tsmets on 2006-05-27
> I assume this server is online?

Nha,
There is just a lot of disk space on the "Server", so instead of downloading the packages, I would like to keep simply a copy on the server directly. Nothin', like NFS where it would be located .... just directly on the server ... ?


\T,

---

