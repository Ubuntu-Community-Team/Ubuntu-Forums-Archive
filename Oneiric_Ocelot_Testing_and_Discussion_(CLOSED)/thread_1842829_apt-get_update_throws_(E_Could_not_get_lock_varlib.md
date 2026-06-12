---
title: "apt-get update throws (E: Could not get lock /var/lib/apt/lists/lock)"
date: 2011-09-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by lobo_tuerto on 2011-09-12
Hello guys,


(BTW, I wasn't running another instance of apt-get, nor upgrading).

This morning I ran a **sudo apt-get update**, no problem it showed that there were some changes pending. After a few mins I tried running it again to see if more changes were on its way, only to receive this error:

```
$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Recurso no disponible temporalmente)
E: Unable to lock directory /var/lib/apt/lists/
```

Then went into _top_ to see if something was going on, and it showed a couple of bzip2 process running on top of the list, so I did a: ps aux | grep bzip and found this:

```
$ ps aux | grep bzip
root     31731  3.2  0.0  28504  1856 ?        SN   07:59   0:03 /usr/lib/apt/methods/bzip2
victor   32165  0.0  0.0  13472   900 pts/2    S+   08:01   0:00 grep --color=auto bzip
```

Is this a normal behaviour? it never happened to me that apt-get would lock after a simple apt-get update. Don't know what does /usr/lib/apt/methods/bzip2 do running in the background holding a lock to my repositories list?


This event, paired with this one: [http://ubuntuforums.org/showthread.php?t=1842402](http://ubuntuforums.org/showthread.php?t=1842402) is already making me paranoid! :(

---

### Post by seeker5528 on 2011-09-14
> **lobo_tuerto said:**
> This morning I ran a **sudo apt-get update**, no problem it showed that there were some changes pending. After a few mins I tried running it again to see if more changes were on its way, only to receive this error:

```
$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Recurso no disponible temporalmente)
E: Unable to lock directory /var/lib/apt/lists/
```

Never had an issue like that unless something else was running the grabbed the lock, which could be update-manager.

Could also be that something grabbed the lock, then died before the lock was unset/released.

Normally in those situations, my first thing is to reboot, then immediately after logging in I try whatever I was trying before that complained about the lock file, if it still complains, then I delete the lock file, it should be created again automatically the next time something runs the uses it.

Later, Seeker

---

