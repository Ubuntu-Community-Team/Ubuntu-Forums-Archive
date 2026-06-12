---
title: "Forgotten password"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by swill on 2008-07-19
:(:confused:OK, I put unbuntu on my laptop to begin to learn the system some time agao.  It has been a while since I've login.  I forgot my username and/or passord.  Can anyone tell me how I can retrieve or change them?

Thanx in advance
Steve:(

---

### Post by ercferret18 on 2008-07-19
boot computer in recovery mode, select "drop to root shell" and then type passwd -a [your account] then select a new password

---

### Post by init1 on 2008-07-19
> **swill said:**
> :(:confused:OK, I put unbuntu on my laptop to begin to learn the system some time agao.  It has been a while since I've login.  I forgot my username and/or passord.  Can anyone tell me how I can retrieve or change them?

Thanx in advance
Steve:(
Another way to do this is to use a Linux Live CD (such as Ubuntu) and then 'chroot' into your system. 
What partition is Ubuntu on? The first one?

---

### Post by swill on 2008-07-19
Thanx friend...

Steve

---

### Post by kamitsukai on 2008-07-19
> boot computer in recovery mode, select "drop to root shell" and then type passwd -a [your account] then select a new password 

erm... OK this is worrying does that mean that anyone could potentially gain access to my Ubuntu account like this if they were actually using my pc?

---

### Post by JillSwift on 2008-07-19
> **kamitsukai said:**
> erm... OK this is worrying does that mean that anyone could potentially gain access to my Ubuntu account like this if they were actually using my pc?Yup. Fortunately you can password protect that option. Easiest way to set that up is to get "startupmanager".

---

### Post by init1 on 2008-07-19
> **kamitsukai said:**
> erm... OK this is worrying does that mean that anyone could potentially gain access to my Ubuntu account like this if they were actually using my pc?
Yes, anyone using your computer could log in with single user mode, or use a live CD. You can prevent this however by 
Setting your BIOS password- If you change your boot order so that the hard drive is first, and make sure that it can't be changed without a password, they can't use a live CD. 
Setting a Grub password- you can remove single user mode from the grub menu, and put a password on grub so they can't circumvent that

---

### Post by drubin on 2008-07-19
> Yes, anyone using your computer could log in with single user mode, or use a live CD. You can prevent this however by
Setting your BIOS password- If you change your boot order so that the hard drive is first, and make sure that it can't be changed without a password, they can't use a live CD.
Setting a Grub password- you can remove single user mode from the grub menu, and put a password on grub so they can't circumvent that

Isn't this a bit over kill? I mean I some one has physical access to your computer. and they want to go through that effort they could just as easily take the hard drive and mount it on to another system and have access to all the data that way?? Right?

---

### Post by bodhi.zazen on 2008-07-19
> **kamitsukai said:**
> erm... OK this is worrying does that mean that anyone could potentially gain access to my Ubuntu account like this if they were actually using my pc?

Physical access = bad news this way. If someone has physical access the only protection you have is encryption. Encryption will protect your system files and personal data (as long as the encrypted file system is not mounted). You can install into an encrypted partition using the Alternate CD.

Of course someone can always install another OS or boot a live CD and use your hardware if they wish to ignore or forgo your personal data.

All the other suggestions on this thread will deter only the most casual intruder and can be easily defeated, most in a matter of seconds. Do not consider those suggestions as security measures.

---

### Post by bodhi.zazen on 2008-07-19
> **rubinboy said:**
> Isn't this a bit over kill? I mean I some one has physical access to your computer. and they want to go through that effort they could just as easily take the hard drive and mount it on to another system and have access to all the data that way?? Right?

You are correct, all those suggestions can be defeated in a matter of seconds.

---

### Post by drubin on 2008-07-19
Is encryption of the whole drive an option for day to day use speed/performance wise?

---

### Post by stinger30au on 2008-07-19
> **kamitsukai said:**
> erm... OK this is worrying does that mean that anyone could potentially gain access to my Ubuntu account like this if they were actually using my pc?

dont panic, ubuntu is not the first os you can do this too.

you can do it to windows as well

[http://home.eunet.no/pnordahl/ntpasswd/](http://home.eunet.no/pnordahl/ntpasswd/)

a backdoor does come in handy when passwords have been forgotten

---

### Post by bodhi.zazen on 2008-07-20
> **rubinboy said:**
> Is encryption of the whole drive an option for day to day use speed/performance wise?

Once the file system is decrypted there is not much of a performance hit.

---

