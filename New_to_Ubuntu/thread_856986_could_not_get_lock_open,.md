---
title: "could not get lock open,"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by shredfitz on 2008-07-12
I have  a newly installed 8.04. When I try to install a program from add/remove applications, 
i get the following:

from add remove :"dpkg: parse error, in file '/var/lib/dpkg/available' newar line 4127: field name ' riorityx' must be followed by colon.

If I try to add a program with the terminal, I get: Could not get /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory.

any clue on this?

---

### Post by iaculallad on 2008-07-12
Try to close/exit all installation processes. Either an existing ap-get is or Synaptics is running:

To view any active apt-get processes using your terminal:

```
ps aux | grep apt-get
```

---

### Post by shredfitz on 2008-07-12
I get this:

brian     6277  0.0  0.0   3004   760 pts/0    S+   02:11   0:00 grep apt-get

---

### Post by iaculallad on 2008-07-12
Kill the process number of apt w/c is 6277 using your terminal:

```
kill -9 6277
```

or

```
sudo kill -9 6277
```

Then try opening your Synaptics or Add/Remove option.

---

### Post by shredfitz on 2008-07-12
that did nothing. same results.

---

### Post by iaculallad on 2008-07-12
Again, on your terminal:

```
sudo pkill apt
sudo apt-get update && sudo apt-get upgrade
```

Does it display any message/error?

---

### Post by hezuo on 2008-07-24
thx a lot it really worked for me.:)

---

