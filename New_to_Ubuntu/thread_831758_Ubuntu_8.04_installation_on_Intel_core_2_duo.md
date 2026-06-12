---
title: "Ubuntu 8.04 installation on Intel core 2 duo"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by theemperor on 2008-06-17
Hi,

Following error message happened to me when i tried installing ubuntu 8.04 on my core 2 duo machine

Error Message
================================================== =============
[53.218125] CRC Error
[53.218889] Kernel panic - not syncing: VFS: unable to mount root fs on unknown-block(104,1)
================================================== =============
I realize that CRC error is CD Reading error. I am writing a new CD and installing it today. Will post the result soon

Thanks

Bijoy

---

### Post by pedro_orange on 2008-06-17
CRC is just a cyclic redundancy check and just an error checking algorithm (like parity etc)

I would imagine it's a parition error. So reformat your hdd and have another go.

---

### Post by theemperor on 2008-06-17
Thanks a lot...

How do I format hdd. Currently my hdd has got a crashed Solaris. Pls help..

Thanks

Bijoy

---

### Post by theemperor on 2008-06-17
I will neither be able to login solaris nor ubuntu

Thanks

Bijoy

---

### Post by pedro_orange on 2008-06-17
If you're gonna format you're going to lose all the data on the hdd at the moment.

You can do it using the Ubuntu LiveCD. Simply put it in, boot up into the LiveCD. Double click the install icon, following the instructions and when the partition manager opens choose guided use entire disk. (Or however you want it setup) the installer will format the partition before copying files to it.

---

### Post by MasterSander on 2008-06-17
I'm not so certain it's a HDD error. It could indeed also mean your cd is corrupt. Can you login to ubuntu using the live cd and did you check for defects?

---

### Post by theemperor on 2008-06-17
Thanks a lot....

This error occured when I tried using without installing and when i tried installing it to my hdd as well.

Both times error occured after I selected the language option and the next screen.

Hence I will not be able to format.

I will do try checking the CD for any defects

Thanks

Bijoy

---

### Post by MasterSander on 2008-06-17
Now I'm pretty sure it's your cd. 'Cause the setup is running from the cd and not from your hard drive, so normally you have a bad CD.

---

### Post by theemperor on 2008-06-17
Okie....

I will do write a new CD and then try.

Will post the result day after tomorrow

Thanks

Bijoy

---

### Post by pedro_orange on 2008-06-17
> **MasterSander said:**
> Now I'm pretty sure it's your cd. 'Cause the setup is running from the cd and not from your hard drive, so normally you have a bad CD.

Good call.
I should actually read the posts properly before posting.

---

