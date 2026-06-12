---
title: "Backing up Ubuntu 11.04"
date: 2012-04-11
forum: New to Ubuntu
---

### Post by newport_j on 2012-04-11
We are going to be doing some very compilcated encrypting on my hardrive so I think it is a good idea to backup my hadrive.
 
I forgot the commands (and I cannot find the on the Ubuntu Forum) to back up using the tar command. 
 
Please give me the command to back up on DVD my Ubuntu 11.04 Linux system.
 
As I said I forgot the specifc tar command. I wil probably be requiring more than one DVD so I should save them on tar files able to completely fit ona DVD.
 
Thanks in advance.
 
Newport_j

---

### Post by newport_j on 2012-04-11
Okay I have got my system backed up. I need to just breakup the very large bz2 file and copy it on DVD's. I Know the command - I am assming it is the same as the one for cd's, but the 716000 is wrong because clearly DVD's hold more memory. But what do I replace 716000 with? These are basic DVD's no blu ray here. The command for cds is 
 
 
tar -cf cd-1 cd-1.tar -ML 716000 --remove-files bigbackup.tar.bz2
 
 
Now what goes in place of 716000 for a DVD backup?
 
Thanks in advance.
 
 
Newport_j

---

