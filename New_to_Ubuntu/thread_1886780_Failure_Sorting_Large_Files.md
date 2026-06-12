---
title: "Failure Sorting Large Files"
date: 2011-11-25
forum: New to Ubuntu
---

### Post by CompBio on 2011-11-25
I've been trying to sort some large files, on the order of 15GB in size.  These have all unique records, so the files should not shrink once sorted.

Running the sort command on an 80GB disk with 60GB free, I got the following error:

sort: write failed: /tmp/sortZ8yS8X: No space left on device
sed: couldn't write 121 items to stdout: Connection reset by peer

I could try splitting the file into smaller pieces, sort them and then write code to collate the files, but it seems to me a sort program should be a hell of a lot more robust than this.

Any suggestions?

---

### Post by CompBio on 2011-11-25
Argh!  RTFM.  My /tmp drive has only 8GB.  I'm rerunning the sort now using -T to point to the 80GB drive.  :rolleyes:

---

### Post by Lars Noodén on 2011-11-25
/tmp is too small on your system to do the sort.  You could use the [-T](http://manpages.ubuntu.com/manpages/precise/en/man1/sort.1.html) (--temporary-directory=DIR) option to specify a different directory for temporary files on a partition with more space.  Use **df -h** to see how much space is left.  You might also try **apt-get clean** to clean out the cache and free up more space.

---

