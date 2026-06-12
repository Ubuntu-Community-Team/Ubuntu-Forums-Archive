---
title: "password"
date: 2012-05-21
forum: New to Ubuntu
---

### Post by potypotumus on 2012-05-21
hi i have been useing ubuntu and have forgoton my password i have seen the youtube vids on how to change it but it dont work even when it says password changed it has not so i cant upgrade or do anything it seems to me the only way is to reinstall windows then reinstall ubuntu as i have downloaded the new 1 and put it on the kea but it dont boot from the kea what can i do anyone ??? help lol

---

### Post by Revolutionary101 on 2012-05-21
Can you not get into your account at all?

---

### Post by potypotumus on 2012-05-21
> **Revolutionary101 said:**
> Can you not get into your account at all?
yeah can it works fine the only thing i cant do is upgrade or install updates as it keeps asking me for my password and i have forgoton it ?

---

### Post by papibe on 2012-05-21
Hi potypotumus.

Follow this [tutorial]("http://www.psychocats.net/ubuntu/resetpassword") to change your password under 'recovery mode'.

Regards.

---

### Post by Revolutionary101 on 2012-05-21
> **potypotumus said:**
> yeah can it works fine the only thing i cant do is upgrade or install updates as it keeps asking me for my password and i have forgoton it ?

You should just be able to change the password by opening terminal and typing in:

```
passwd
```

---

### Post by Lynceus on 2012-05-21
a good tutorial. 
But now that i know that, isn't it easy to break into someone's computer if you're sitting behind it

---

### Post by Lynceus on 2012-05-21
> **Revolutionary101 said:**
> You should just be able to change the password by opening terminal and typing in:

```
passwd
```
Just tried it,  you have to put in the current password first

---

### Post by Revolutionary101 on 2012-05-21
> **Lynceus said:**
> a good tutorial. 
But now that i know that, isn't it easy to break into someone's computer if you're sitting behind it

They could have other safe guards like a BIOS boot up password. I personally use one of these so my computer is absolutely useless to anyone who wants to gain unauthorized access to my computer.

> **Lynceus said:**
> Just tried it,  you have to put in the current password first
Yeah I just realized that. Oh well, good for future reference.

---

### Post by potypotumus on 2012-05-21
> **papibe said:**
> Hi potypotumus.

Follow this [tutorial]("http://www.psychocats.net/ubuntu/resetpassword") to change your password under 'recovery mode'.

Regards.
yeah thats the one i tryed lol it even said password changed but when i tryed it had not

---

### Post by Lynceus on 2012-05-21
Strange... srry for asking, but are you sure you typed the same password when you logged in?

---

### Post by Lynceus on 2012-05-21
> **Revolutionary101 said:**
> They could have other safe guards like a BIOS boot up password. I personally use one of these so my computer is absolutely useless to anyone who wants to gain unauthorized access to my computer.

I did some quick research...
Quote => if you have several people using your computer, you can put small  obstacles in their way by setting a root password, setting a Grub  password, or setting a BIOS password. Still, anyone who has physical  access to your computer and a little know-how practically has root  access anyway. She can boot a live CD and mount your partition or even  just physically remove the hard drive from your computer and put it in  another computer. There's a certain amount of trust you automatically  give anyone by allowing her to sit at your computer.

---

### Post by papibe on 2012-05-21
Try this:

Open a terminal and run:
```
gksu-properties
```
Then make sure that the settings are:
```

Authentication mode: sudo
Grab mode          : enable
```
Tell us how it goes.
Regards.

---

### Post by potypotumus on 2012-05-21
> **Lynceus said:**
> Strange... srry for asking, but are you sure you typed the same password when you logged in?
?? what

---

### Post by Lynceus on 2012-05-21
i said srry. i made the mistake of editing my password, and then typing it in wrong, when i logged in,  in the past...:)
I thought i had a serious problem too

---

### Post by potypotumus on 2012-05-21
> **Lynceus said:**
> i said srry. i made the mistake of editing my password, and then typing it in wrong, when i logged in,  in the past...:)
I thought i had a serious problem too
no i just typed a 2 letter password and it said it was changed but when it booted up it said wrong password

---

### Post by Cheesemill on 2012-05-21
> **potypotumus said:**
> no i just typed a 2 letter password and it said it was changed but when it booted up it said wrong password
Try a longer password. Ubuntu has policies in place that won't let you use a weak password.

> But now that i know that, isn't it easy to break into someone's computer if you're sitting behind it
Yes it is. It's even trivial to get round a BIOS password as well, it only takes a couple of minutes. That's aside from the fact that you can boot with a Live CD or remove the drive to a different machine if you want to access someone elses data. There is a well known saying, physical access = root access. The only way to be safe is to use encryption to protect your data.

---

### Post by Revolutionary101 on 2012-05-21
> **Cheesemill said:**
> 
Yes it is. It's even trivial to get round a BIOS password as well, it only takes a couple of minutes. That's aside from the fact that you can boot with a Live CD or remove the drive to a different machine if you want to access someone elses data. There is a well known saying, physical access = root access. The only way to be safe is to use encryption to protect your data.

True, however my Dell XPS won't let you boot to any medium without entering the BIOS password first. I am also thinking about encrypting my HDD file-system to get around the "take out HDD" vulnerability.

Regardless, I think this is kinda off track from where the original thread started.

---

