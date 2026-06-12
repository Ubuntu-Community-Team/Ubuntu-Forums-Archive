---
title: "adding 2nd hard drive"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by northwestuntu on 2008-04-27
i just installed a 2nd hard drive that i am using for more storage only.  i might make it my home folder.  

what's the easiest way to install this?

does this need to be extended or primary?

its only going to have files on it, no other operating systems.

thanks

---

### Post by Tatty on 2008-04-27
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)  This tells you how to make a separate /home partition on an installed system.

I just followed this guide myself, though i had to do three things differently:

1. add sudo before the find command
2. recursively chown the new home folder to my user and group
3. find all the files in the oldhome which are owned by root and chown them back to root in the new home folder.

---

### Post by northwestuntu on 2008-04-28
little harder then i thought it would be.

---

### Post by northwestuntu on 2008-04-28
ok i think i got it.  except when i click on the extra hard drive it asks for a password?  do i have to enter a pass everytime i access the 2nd drive?

---

### Post by logos34 on 2008-04-28
> **northwestuntu said:**
> ok i think i got it.  except when i click on the extra hard drive it asks for a password?  do i have to enter a pass everytime i access the 2nd drive?

sudo chown -R yourusername:yourusername /path/to/2nddrive
sudo chmod -R 755 /path/to/2nddrive

---

### Post by northwestuntu on 2008-04-28
thanks

---

### Post by northwestuntu on 2008-05-01
if i do a fresh install of hardy would it mount and give me permission of my 2nd internal drive after install?  without having to jump through all these hoops?

what a pain of adding a hard drive for a newbie like me :mad:

---

### Post by northwestuntu on 2008-05-01
would it set up everything for me is what i am trying to say.

---

### Post by drsox1899 on 2008-05-01
Yes.

Just be sure to select the second drive as the location for /home and the first drive as the location for /.  
During setup it will ask you how to partition.  Just select Manual and remember that each drive will be listed.  Make the right selections about which directories to put where.

This way all your "data" files are on the second drive and can be preserved when/if you reinstall or upgrade the Ubuntu version.

---

### Post by northwestuntu on 2008-05-01
> **drsox1899 said:**
> Yes.

Just be sure to select the second drive as the location for /home and the first drive as the location for /.  
During setup it will ask you how to partition.  Just select Manual and remember that each drive will be listed.  Make the right selections about which directories to put where.

This way all your "data" files are on the second drive and can be preserved when/if you reinstall or upgrade the Ubuntu version.

that's exactly how i want it to work, thanks :guitar:

---

### Post by drsox1899 on 2008-05-01
> **northwestuntu said:**
> that's exactly how i want it to work, thanks :guitar:

PS  If you already have /home on your second drive (or for future installs) and want to preserve what's there - don't select formatting for this partition.  This way the existing data will be preserved.

The install sequence will insist on formatting the / partition !!

Also you need to create a swap partition (2xRAM space typically).  Do this on the first drive.

---

