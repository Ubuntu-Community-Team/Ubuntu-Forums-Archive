---
title: "Update downloads failing."
date: 2013-11-26
forum: New to Ubuntu
---

### Post by dougcumiskey123 on 2013-11-26
Since making an attempt at getting the integrated finger scanner to work (and failing) I have has a update downloading problem. the software update program says its 17 days out of date despite having seen the downloads come down. In addition when I do a available download check I get the following error report

W:GPG error: [http://ubuntu.univ-nantes.fr](http://ubuntu.univ-nantes.fr) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>, W:Failed to fetch [http://ppa.launchpad.net/madman2k/ubuntu/dists/hardy/main/binary-i386/Packages](http://ppa.launchpad.net/madman2k/ubuntu/dists/hardy/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/madman2k/ubuntu/dists/hardy/restricted/binary-i386/Packages](http://ppa.launchpad.net/madman2k/ubuntu/dists/hardy/restricted/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/madman2k/ubuntu/dists/hardy/universe/binary-i386/Packages](http://ppa.launchpad.net/madman2k/ubuntu/dists/hardy/universe/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/madman2k/ubuntu/dists/hardy/multiverse/binary-i386/Packages](http://ppa.launchpad.net/madman2k/ubuntu/dists/hardy/multiverse/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Can anyone please help as I am really lost on this one.

---

### Post by fantab on 2013-11-26
Those 404 errors on my side as well. Remove them useing 'Software Center' ->Edit -> Software Sources -> Other software and remove those or uncheck them.

Then from Terminal:
```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get clean
sudo apt-get update
```

---

### Post by Bucky Ball on 2013-11-26
Open Software Sources>Other Software and untick all third-party repos related to or mentioning 'madman2k'. That repo is your problem. Update.

---

### Post by dougcumiskey123 on 2013-11-26
Many thanks, at least now I can get the updates still need to get rid of the mistakes I made on the finger scan or was that not part of it?

---

### Post by Bucky Ball on 2013-11-26
Did that get updates running smoothly again? No errors? If so, run these two in a terminal, one after the other:

```
sudo apt-get update
sudo apt-get upgrade
```

That will get your system up to date and we can see where you are.

As for the finger scanner issue, if it is not working after that, post a new thread about it as the update problem outlined in the title of this one will be solved. ;)

---

### Post by dougcumiskey123 on 2013-11-26
Yes every thing came down and confirmed using ( sudo apt-get update/sudo apt-get upgrade) I still have other issues but I can research them. once again many thanks, I had visions of having to re-install the system, Pheee!

---

### Post by Bucky Ball on 2013-11-26
> **dougcumiskey123 said:**
> I had visions of having to re-install the system, Pheee!

Always a last resort. ;)

As I say, post new threads for any other issues. Good luck. Please mark this thread a solved by following the instructions in my signature.

---

