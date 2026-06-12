---
title: "Paranoic security questions"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by personal-data-removed on 2008-08-14
Hi

I found a windows virus attached to a linux program that i downloaded.
I got paranoic. :D

Installed clam, avast and avg, but i didnt liked those av performances.

Avast needs a 12 months key.
AVG have problems updating.

Perhaps Clam is the best, because it is the default av in ubuntu.
I have clam av database updated, but i cant install the new clam version, i am not sure how to make volatile repositories work. 
I gives an error, says that i dont have the key.

But i am running clam old version with updated database, and all seams to be ok.

I have a paranoic question, by typing this commands:

sudo chmod 775 /opt/grisoft/avg7/bin/avgupdate
cd /opt/grisoft/avg7/var/
sudo chmod 777 run
sudo chmod 777 update/log

What i am doing is giving AVG permission to download any update, right ?

How to cancel the commands above, and remove the AVG permission to update itself ? (Already uninstalled AVG)


Thanks

---

### Post by lisati on 2008-08-14
The way to give AVG permission to do the updates is to add your username to the avg user group, then log off and log on again. It's in the AVG documentation.

---

### Post by personal-data-removed on 2008-08-14
@lisati
Thanks for the reply, but i already uninstalled AVG.
I think i will go with the clam av.

What is puzzling my mind is how to remove the AVG permission to update itself ?

---

### Post by billgoldberg on 2008-08-14
A window virus cant do any damage on linux.

---

### Post by personal-data-removed on 2008-08-14
"A window virus cant do any damage on linux"
But i can pass it without intention to other computers with windows.

---

### Post by brian_p on 2008-08-14
> **jocampeao said:**
> Hi

I found a windows virus attached to a linux program that i downloaded.


So we might learn from your experience:

What was the program? Where did you download it from? How did you discover there was a virus attached to it?

---

### Post by nonmainstreamer on 2008-08-20
hi, can you help me dlete this account, please?! please reply out of this post if you want. thanx

---

### Post by nonmainstreamer on 2008-08-20
hi, can you help me delete this account, please?! please reply out of this post if you want. thanx

---

### Post by meindian523 on 2008-08-20
> **jocampeao said:**
> Hi

I found a windows virus attached to a linux program that i downloaded.
I got paranoic. :D

Installed clam, avast and avg, but i didnt liked those av performances.

Avast needs a 12 months key.
AVG have problems updating.

Perhaps Clam is the best, because it is the default av in ubuntu.
I have clam av database updated, but i cant install the new clam version, i am not sure how to make volatile repositories work. 
I gives an error, says that i dont have the key.

But i am running clam old version with updated database, and all seams to be ok.

I have a paranoic question, by typing this commands:

sudo chmod 775 /opt/grisoft/avg7/bin/avgupdate
cd /opt/grisoft/avg7/var/
sudo chmod 777 run
sudo chmod 777 update/log

What i am doing is giving AVG permission to download any update, right ?

How to cancel the commands above, and remove the AVG permission to update itself ? (Already uninstalled AVG)


Thanks
Nopes,by typing those commands,you are giving anybody who has an a/c on your box permission to RUN AVG,NOT giving AVG permissions to do anything.

---

### Post by linuxguymarshall on 2008-08-20
> **jocampeao said:**
> "A window virus cant do any damage on linux"
But i can pass it without intention to other computers with windows.

Which is why we should all use UNIX or UNIX-like systems

---

