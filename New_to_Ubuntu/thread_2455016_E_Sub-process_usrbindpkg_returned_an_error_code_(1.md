---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2020-12-10
forum: New to Ubuntu
---

### Post by praneetarora on 2020-12-10
Hi, all. I am unable to install new applications. I am getting the following output. Kindly guide me.

[https://paste.ubuntu.com/p/zkwcgmqF2Q/](https://paste.ubuntu.com/p/zkwcgmqF2Q/)

---

### Post by #&amp;thj^% on 2020-12-10
That's one big mess, roughly over 2000 dpkg:errors, 
The best I can offer with a short amount of time I can spend in the forums.
Please try this:**(One line at a time)**
```
sudo apt autoclean
sudo dpkg --configure -a
```
Along with this 
```
 sudo apt install --fix-broken
```
Post back anything relevant.

---

### Post by praneetarora on 2020-12-10
@1fallen.  I followed your instructions, but I am getting the same error.

---

### Post by deadflowr on 2020-12-11
This is something I had not since before, but luckily (or unfortunately) it's happen to others.
See: [https://askubuntu.com/a/950616]("https://askubuntu.com/a/950616")
For a possible solution.
But basically, this solution would mean nothing short of reinstalling all those packages.
(With over 2000 packages affected this means essentially a complete reinstall of the OS)

The link also provides other possible solutions, or at least reasons.
Perhaps it might be a matter of a single package being off, which if found and fixed will fix the rest, outright.

---

### Post by ActionParsnip on 2020-12-11
could try:
```

sudo apt-get clean
sudo apt-get --reinstall install `dpkg -l | grep ^ii | awk {'print $2'}`
sudo apt-get -f install

```

---

### Post by praneetarora on 2020-12-11
Nope. This also didn't work. Same error.

---

### Post by praneetarora on 2020-12-11
> **deadflowr said:**
> This is something I had not since before, but luckily (or unfortunately) it's happen to others.
See: [https://askubuntu.com/a/950616](https://askubuntu.com/a/950616)
For a possible solution.
But basically, this solution would mean nothing short of reinstalling all those packages.
(With over 2000 packages affected this means essentially a complete reinstall of the OS)

The link also provides other possible solutions, or at least reasons.
Perhaps it might be a matter of a single package being off, which if found and fixed will fix the rest, outright.


This will take a long time :( I am looking for a more optimal solution. Otherwise I will have  to reinstall the OS.

---

### Post by Impavidus on 2020-12-11
It appears there are two separate problems here, although they could be related. First, many files list files are missing. They're supposed to be in /var/lib/dpkg/info. Each installed package must have a files list file with a list of all files installed as part of that package. Apparently someone or something deleted a huge number of files there, although not all; 58061 files are still listed in the remaining lists. This causes all your warnings, but not the error.

The error is caused by a corrupted /etc/default/grub file. It tried to execute the word If in the first line of the file as if it were a command, but it's supposed to be in a comment. Have a look at your /etc/default/grub. Does it look corrupted? Someone or something must have damaged it.

These two things combined look like random file corruption, which is a strong indicator (but no guarantee) for hard drive failure. Have you recently checked the health of your hard drive?

---

### Post by praneetarora on 2020-12-11
Yes, my hard drive(It is an ssd) is fine. I ran some tests also. I did check the grub file and it looks fine to me. Have a look at it-   [ https://pastebin.ubuntu.com/p/ftV2PpyrTr/]("https://pastebin.ubuntu.com/p/ftV2PpyrTr/")

Also, I think I am seeing this error since my system didn't shutdown properly as it lost power and all that while installation of updates were happening. What do you think?

---

### Post by #&amp;thj^% on 2020-12-11
> **Impavidus said:**
> It appears there are two separate problems here, although they could be related. 
These two things combined look like random file corruption, which is a strong indicator (but no guarantee) for hard drive failure. Have you recently checked the health of your hard drive?

+1 I'm leaning on this thought also.

---

### Post by #&amp;thj^% on 2020-12-11
> **praneetarora said:**
> Yes, my hard drive(It is an ssd) is fine. 
Also, I think I am seeing this error since my system didn't shutdown properly as it lost power and all that while installation of updates were happening. What do you think?

All this points to file corruption, and the time it would take to try and fix it well a re-install would result in a better experience I would think. Power failures can damage drives even SSD's and it tears up the OS as it was not out to bed properly.
Sorry to hear though.:(

---

### Post by Impavidus on 2020-12-12
Your /etc/default/grub looks fine, except that you have to add a # at the start of the first line. If you do so, your system may be salvageable, but you still have to rebuild the missing files list files by reinstalling those packages.

One (or two, as I think there used to be a space between the # and the If) missing byte at the start of a file isn't really what one would expect from file corruption resulting from a broken ssd, but you never know. /etc/default/grub isn't modified during upgrades, so I don't think this is a likely error resulting from power loss during an upgrade. The files list files get replaced during an upgrade (not all at the same time). When files are added to or deleted from the directory, or when their names or inodes change, the directory gets written to. If a power failure happens during that operation, this can delete files that weren't modified.

At this point it looks like either a user doing something really unexpected or truly random filesystem damage, which could have affected other files as well.

---

