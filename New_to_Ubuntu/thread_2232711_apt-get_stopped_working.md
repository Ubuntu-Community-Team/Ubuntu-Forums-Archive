---
title: "apt-get stopped working"
date: 2014-07-03
forum: New to Ubuntu
---

### Post by David_Craig on 2014-07-03
Hi,

I've encountered a problem with apt-get, my system information is

```
uname -a
Linux david-Lenovo-G570 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:31:42 UTC 2014 i686 i686 i686 GNU/Linux

```

The problem is that if I try to use ```
apt-get install package
``` I get the following error,

```
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/repository.spotify.com_dists_stable_non-free_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
```


after some searching I came across a [solution]("http://ubuntuforums.org/showthread.php?t=863742") to a bug giving a similar error,

```
sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get update
```

but this did not work for me. Anyone know what causes this and how to solve??

---

### Post by ubudog on 2014-07-03
Try using [this]("http://ubuntuforums.org/showthread.php?t=2230860&p=13055620#post13055620") solution.

---

### Post by David_Craig on 2014-07-03
still get the same error.

---

### Post by ubudog on 2014-07-03
Looks like Spotify's repository is broken:
[http://community.spotify.com/t5/Help-Desktop-Linux-Mac-and/Spotify-0-9-11-for-GNU-Linux/m-p/844713](http://community.spotify.com/t5/Help-Desktop-Linux-Mac-and/Spotify-0-9-11-for-GNU-Linux/m-p/844713)

Another post has also been made recently:
[http://ubuntuforums.org/showthread.php?t=2232710](http://ubuntuforums.org/showthread.php?t=2232710)

As a workaround, try [this]("http://community.spotify.com/t5/Help-Desktop-Linux-Mac-and/Spotify-0-9-11-for-GNU-Linux/m-p/845061/highlight/true#M91512"), which seems to be working.

---

### Post by David_Craig on 2014-07-03
> **ubudog said:**
> Looks like Spotify's repository is broken:
[http://community.spotify.com/t5/Help-Desktop-Linux-Mac-and/Spotify-0-9-11-for-GNU-Linux/m-p/844713](http://community.spotify.com/t5/Help-Desktop-Linux-Mac-and/Spotify-0-9-11-for-GNU-Linux/m-p/844713)

Another post has also been made recently:
[http://ubuntuforums.org/showthread.php?t=2232710](http://ubuntuforums.org/showthread.php?t=2232710)

As a workaround, try [this]("http://community.spotify.com/t5/Help-Desktop-Linux-Mac-and/Spotify-0-9-11-for-GNU-Linux/m-p/845061/highlight/true#M91512"), which seems to be working.

that worked, thanks

---

### Post by ubudog on 2014-07-03
> **David_Craig said:**
> that worked, thanks

Great!

---

