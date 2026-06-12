---
title: "Linux Question User ID"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by Julian Lewis on 2008-05-14
Hi 
   I have just mounted my home directory at work using NFS after installing nfs client and portmapper. My problem is now that my user ID assigned by Ubuntu is 1000 and I need to change it to get write access. 
Can anyone tell me how can I change my user ID from 1000 to say 515 ?

Thanks

---

### Post by mandrill on 2008-05-14
> **Julian Lewis said:**
> Hi 
   I have just mounted my home directory at work using NFS after installing nfs client and portmapper. My problem is now that my user ID assigned by Ubuntu is 1000 and I need to change it to get write access. 
Can anyone tell me how can I change my user ID from 1000 to say 515 ?

Thanks

1000 is the default owner/single-user id. Probably better off keeping that id and changing permissions. See this....Aysiu knows his stuff.....

[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by coolen on 2008-05-14
As I understand it UIDs under 1000 are for processes and stuff (0 is root). Changing your UID could also mess up your access rights on your own machine.

Can you not change the UID requirements for write access?

---

### Post by coolen on 2008-05-14
Oh, if you need permissions on your own machine (as in, this is a directory on your machine, shared on the network) you could just work as root for a bit...

---

### Post by Julian Lewis on 2008-05-14
Aghh !!

  I didn't explain properly, the remote system I want to mount my home directory from, is running Linux SLC4 (Scientific Linux 4, a derivative of Redhat). I don't manage that system, I am just a user. So at work I come with my Ubuntu (7.10 I scared to update it) laptop, and plug it in to my work network. I want to run a local Eclipse but I can't save my work because of the UserID mismatch. 
I created another Ubuntu User and forced UID to be 515, and if I SU as that user I do have read/write access. Unfortunately I screwed up because the new user I created I forced to use the same home directory as my new user. (Bad idea as I can't log in as that user only SU it, and I can't seem to suppress it as its not listed under the GUI System->Administration->Users and Groups). When I launched Eclipse under 515 it promptly crashes (not a big surprise).
So now I have a mess to clean up, and only know how to use the GUI. So how do I clean up the mess I made.
Cheers

---

### Post by coolen on 2008-05-14
Could you delete the user, then recreate it, specifying a home directory?

---

### Post by t0p on 2008-05-14
> **coolen said:**
> Oh, if you need permissions on your own machine (as in, this is a directory on your machine, shared on the network) you could just work as root for a bit...

I hate to criticize someone's suggestion without making one of my own, but...

Working as root comes with dangers, and I think it's inadvisable to work as root except when necessary (ie for administration, when you need to edit system files etc).

---

### Post by mandrill on 2008-05-14
Perhaps you could tap one of your IT system admin guys on the shoulder and ask?

---

### Post by coolen on 2008-05-14
> **t0p said:**
> I hate to criticize someone's suggestion without making one of my own, but...

Working as root comes with dangers, and I think it's inadvisable to work as root except when necessary (ie for administration, when you need to edit system files etc).

My apologies. That suggestion was meant as a last resort, for when it is necessary. Fixing the problem to work as an underprivileged user is, of course, the better (and more attractive) option.

---

