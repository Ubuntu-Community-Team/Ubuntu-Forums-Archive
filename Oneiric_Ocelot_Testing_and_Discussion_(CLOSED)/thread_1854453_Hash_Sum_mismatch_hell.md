---
title: "Hash Sum mismatch hell"
date: 2011-10-04
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ubiquitin.jf on 2011-10-04
I come to you all this afternoon with a frustrating problem.

Since moving house last week, I've had the following problems when trying to update:

```
Get:22 http://archive.ubuntu.com oneiric/main i386 Packages [1,227 kB]         
94% [20 Packages bzip2 0 B] [22 Packages 570 kB/1,227 kB 46%]       208 kB/s 3s
bzip2: Data integrity error when decompressing.
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

```and

```
W: Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric_main_source_Sources  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric_universe_source_Sources  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric_universe_binary-amd64_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.

```It is always these specific packages which cause the problem and the same problem pops up regardless of server (I've tried 10 different ones now!). I have tried every single possible fix Google has thrown up and I even reinstalled Ubuntu to see if that would help.

At first I thought the problem was the wifi dongle I was using, so I connected my netbook (also 11.10) to the wifi in this house using it and tried to update. No troubles there. It also can't be the ISP or router chewing up the files as the problem isn't present on my netbook. What on earth is going on here?!

---

### Post by MacUntu on 2011-10-04
Try this: Go to '/var/lib/apt/lists' and remove everything in there (including the 'partial' folder). Then try 'sudo apt-get update' again (that should recreate all that content).

---

### Post by ubiquitin.jf on 2011-10-04
> **MacUntu said:**
> Try this: Go to '/var/lib/apt/lists' and remove everything in there (including the 'partial' folder). Then try 'sudo apt-get update' again (that should recreate all that content).

Tried that fix and many variations on that fix, still no joy. The first time I ran apt on my fresh install the bug was thrown up again.

---

