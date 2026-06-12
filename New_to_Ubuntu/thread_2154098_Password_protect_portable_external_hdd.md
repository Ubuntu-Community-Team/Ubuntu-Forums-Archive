---
title: "Password protect portable external hdd"
date: 2013-06-13
forum: New to Ubuntu
---

### Post by htanmsa on 2013-06-13
I recently brought a seagate backup plusexternal portable hdd 1tb.so it doesnt have any password protect feature so i got this idea.I decided to install ubuntu like a portable os on it and then copy files from windows and make it as back up hdd.In this way i can protect files from others and also there wont be much virus.since i am beginner does this work practically and will it keep safe from others.also can I connect it to othet computer and boot it from usb and use as regulard hdd like minilaptop carrying on.I will make entire 1 tb in ubuntu file format instead of nfts.since ubuntu file.format works both ways.I do know about trucrypt but i fell like this is more secure and advantegous And would be prone to virus.so are they any disadvantages

---

### Post by newb85 on 2013-06-13
Well, ubuntu has to be installed in an ext filesystem, which Windows can't read.

---

### Post by Mark Phelps on 2013-06-13
"ubuntu file format" does not "work both ways".  Ubuntu can read/write it; Windows can not.  If you want a data partition to be shareable between Linux and Windows, you would do better to use NTFS.

As to encryption, if I had a dollar for every post I've seen over the years from folks who encrypted their stuff only to have something unexpected occur -- and then lose access to all their stuff -- I would be RICH now.

The BEST protection against data compromise is what you're already proposing -- keep the data in a physical location that is external to the PCs in use.  Once someone gains physical access to the encrypted drive, it's only a matter of time until they get access to the data.  In  my personal opinion, encrypting the external drive is only going to cause you problems in the long run.

---

### Post by htanmsa on 2013-06-13
what I mean by both ways is that it can read nfts and copy it to or  from nfts.and why i said that is because if windows cant Read it and also you need a password to access data in it.so in this way atleast everybody doesnt steal it.So when ever i need that data i would simply login to ubuntu using my username and password and then copy it to windows.So does this work or should i give up in protecting and use as simple external which anyone can acEss

---

### Post by newb85 on 2013-06-13
I misunderstood what you're proposing the first time. You're suggesting that you boot the ubuntu system in the external HDD every time you're backing up.  The ubuntu system reads and copies from the NTFS.  Encrypted file systems are less recoverable if something goes wrong, but what you're suggesting should work for backing up documents, etc. There may be snags if you try using it with different machines, because the hardware would be different, so consider that before jumping in.

---

### Post by Impavidus on 2013-06-13
Also, writing to the Windows C partition from an Ubuntu system isn't very safe. It can break Windows, so you need to make sure the Windows system has a separate data partition (usually labeled D). Apart from that and the comment by newb85, it sounds unconventional but probably OK.

---

### Post by newb85 on 2013-06-13
One last thought:  If I were setting up an Ubuntu system on an external HDD to back up files from an internal Windows system, I would set the Ubuntu system up unencrypted with an extra ext4 partition on the external HDD that is encrypted that only contains the backed up files.  That way, as long as you have an Ubuntu system and the password for the encrypted partition, you have access to the files.  (It just seems the most robust approach to me.)

---

