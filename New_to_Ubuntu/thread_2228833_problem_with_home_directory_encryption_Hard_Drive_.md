---
title: "problem with home directory encryption: Hard Drive Not Big Enough!"
date: 2014-06-09
forum: New to Ubuntu
---

### Post by Old Jimma on 2014-06-09
Hi Community: ):P

I tried to encrypt my home directory this evening using the directions at: [http://www.howtogeek.com/116032/how-to-encrypt-your-home-folder-after-installing-ubuntu/]("http://www.howtogeek.com/116032/how-to-encrypt-your-home-folder-after-installing-ubuntu/").

The directions seemed easy.   ;)

When I got to the step of encrypting my home directory from a superuser account I used:

**sudo ecryptfs-migrate-home -u homedirectoryname**

... and I got the error message that my hard drive wasn't big enough!   ](*,)

And, of course my home director wasn't encrypted because of this!

My home director is a separate hard drive from the SSD that has the Ubuntu Opperating System on it.

What do I have to do to have an encrypted hard drive? Do I need to buy a larger drive, and do a copy from the old one to the new one, then try to encrypt?

If I need a drive, how large should it be?? :-k

I'll be grateful for your advice! [-o<

Sincerely,
Old Jimma from the Old Country

---

### Post by Vladlenin5000 on 2014-06-09
*First of all I must make clear that I've never done this therefore the following thoughts are just speculation.*

I suspect the method you linked works for the simple partitioning - /home is a folder inside / - but not for a separated /home partition. Why? Please note that > *The migration command will create a backup on your computer* therefore it needs as much free space as the total occupied by /home. It should work nice and easy for a fresh installation within a big enough drive. The command will use the remaining free space in / for the backup.
I have absolutely NO CLUE how it would play with a separated /home. I suppose it'll try to backup the whole /home _including its free space_...
Also waiting for other inputs.

---

