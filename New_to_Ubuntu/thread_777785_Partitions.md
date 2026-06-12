---
title: "Partitions"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by UnWarierMage224 on 2008-05-01
Hi folks, 

So I took a look at my partitioning setup with GParted and it's a little bit more messed up than I thought. 

There is 1 primary NTFS partition for Windows. 
Then there is 1 logical partition. In this logical partition there is 1 NTFS partition for My Documents, the linux EXT3 partition, and the linux swapfile partition. 

Would it be a better idea to move linux/swap to their own dedicated partitions (and if so, how would I go about doing that without hosing anything)? Or is the way its currently setup still OK? 

-'Mage

---

### Post by phoenix_abhi on 2008-05-01
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

I think this will explain u what to do

---

### Post by dtrot55 on 2008-05-01
I would reccomend it on a seperate partition..that way you wont ruin your other installation of Windows if something should go wrong.

---

### Post by UnWarierMage224 on 2008-05-01
OK, so is there any way I can safely move it out of the logical partition using gParted? Or do I have to wipe linux completely and reinstall it outside the logical partition? 

If I do have to wipe it, how can I backup my settings? 

-'Mage

---

### Post by spindizzy on 2008-05-01
installed latest ubuntu on it's own partition. works good. afraid i made the partition too small (8 gigs as suggested). how do i expand partition?
[email]tor@mobwords.ca[/email] please; i'm not a great forum attendee.

---

### Post by dtrot55 on 2008-05-01
I would just reformat Ubuntu on its own partition..as in wipe out completely and reinstall....only thing is I have no idea on your backup settings question...normally i just reformat and mess with settings later.

---

