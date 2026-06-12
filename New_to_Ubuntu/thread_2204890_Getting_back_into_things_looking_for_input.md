---
title: "Getting back into things looking for input"
date: 2014-02-10
forum: New to Ubuntu
---

### Post by ghostcoredevelopme on 2014-02-10
Greetings everybody.

I would like to introduce myself to the forums being as i am sure ill be making full use of them.

I would classify myself as more of a computer hobbyist...not particularly skilled but not inept either. All that being said id like to bounce a few things off of all of you.

I'm setting up my office/learning environment to which my goal is to really start diving into the nuts and bolts of things. I really want to get into programming and network engineering. I decided to go with ubuntu due to it's ease of use to start out. To that effect I have 4 systems which are as follows

1. Desktop Dual Boot win7/13.10 64bit (if it were not for the adobe suite and games I would go pure linux)
2. Laptop Dual Boot win7/13.10 64bit(again the adobe suite)
3-4 two old dusty nc8230 notebooks pure 13.10 32bit HOWEVER one only has 40gb space the other 150gb
*I also have a 1TB ext usb drive for additional storage

So now to the meat of it here is my initial thinking I want a LAMP service running on my home network. I've found plenty of documents on the subject....ALOT in these forums alone...rather overwhelming but encouraging. Anyhow this is more of a solicitation of your thoughts on my..well thoughts. I was debating using 13.10 server on the old notebooks but not sure I need to for what I want.

I want to have the mysql server independent of the apache server with the sql server on the laptop with the larger drive and apache sites and assets being served from the lesser of the two supplemented with the external drive.
 so again am i better served going with a server version for the old notebooks (gives me exposure to that version and other avenues for Study)

these two dusty systems gotta be useful!

---

### Post by Impavidus on 2014-02-11
Welcome. If you want to get into the nuts and bolts of things, Linux is the place to be.

First of all, remove the dust from the dusty notebooks. It could cause overheating.

If I'm correct, these notebooks have a Pentium M 730 CPU. I think these should be OK for any Ubuntu version (without a heavy desktop environment, of course). Some other Pentium Ms have a problem with pae, have a look [here]("https://help.ubuntu.com/community/PAE") if you encounter strange problems during installation. They should happily run the server edition, which is command line only. The question is more how comfortable you will be with command line only. I don't know how much RAM you need for your servers. Disk space seems plenty, for Ubuntu at least. It easely fits in 20GB and, if careful, can be squeezed in less than 7GB.

If the other machines have no problem with Win7, they should have no problem with any Ubuntu version. The only catch is that many pre-installed Win7 systems use MBR partitioning and have all four primary partitions already in use. You may have to remove one of the partitions before proceding. All resizing of Windows partitions can best be done from within Windows, creating Linux partitions is done by the live disk.

---

