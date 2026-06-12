---
title: "newbie encryption question"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by imT on 2008-06-08
Dose the password length compensate a less powerful algorithm ?
Let's say a 75 characters pass, would that make things as harder for the cracker than let's say a smaller pass with a better algorithm ?

---

### Post by tom66 on 2008-06-08
Well, a 75 character pass would be difficult to break, unless there turned out to be a 75 letter word in the English dictionary. 

In general, a longer pass is more secure, but introducing symbols, numbers and making it somewhat obscure would be better. A short six letter password like "$9Kn%L" is more secure than "nicetoast". (Don't use these passwords, they've been publicly documented now)

---

### Post by datajack on 2008-06-08
> **imT said:**
> Dose the password length compensate a less powerful algorithm ?
Let's say a 75 characters pass, would that make things as harder for the cracker than let's say a smaller pass with a better algorithm ?

As in almost all things, the answer is 'it depends on how it is being used'.

In practice, though, for most useful encryption schemes, the answer is no. In most non-trivial encryption systems, your password is not actually used to encrypt the data. Instead an encryption key is generated to protect the data and your password is used to scramble or create this key. (This is what it means when you see things like 1024 and 2048 bit length keys - longer keys are typically harder to crack but need much more cpu power to encrypt/decrypt) Depending on the system in use, an attacker may have access to this scrambled copy of the encryption key and sometimes not.

If they can access the scrambled key, then they can attempt to attack your password which will leave them with a large number of likely incorrect keys to try as (usually) there is no easy way of knowing if you have the right key until you try and decrypt the data. Their other option is to ignore your password and try and deduce the key directly. In cryptosystems that are known to be 'weak', it has been shown to be likely possible to do this within a reasonable time-scale and budget.

---

### Post by chewearn on 2008-06-08
> **imT said:**
> Dose the password length compensate a less powerful algorithm ?
Let's say a 75 characters pass, would that make things as harder for the cracker than let's say a smaller pass with a better algorithm ?

A longer password will be harder to crack, but up a point, limited by the encryption strength.

From my (rather limited) knowledge, most encryption algorithm does not actually use the supplied password to encrypt.  Instead, it generates a key (random number) for the encryption.

The strength of the key depends on the algorithm itself.  An 32-bit encryption will therefore have 2^32 keys, which in a modern computer is easily cracked.  64-bit will take longer, but not impossibly long.

The key is hashed to the password supplied by the user.  If you supply a weak password, the cracker will be able find the key from the hash by brute force.

However, if you supply a password which is longer than the key, the cracker will brute force the key itself.  The longer passwrod will be redundant, since you can get the same hash for more than one password.

Hope I'm not wrong with my explanation.

.

---

### Post by tom66 on 2008-06-08
> **AstalaVista said:**
> A longer password will be harder to crack, but up a point, limited by the encryption strength.

From my (rather limited) knowledge, most encryption algorithm does not actually use the supplied password to encrypt.  Instead, it generates a key (random number) for the encryption.

The strength of the key depends on the algorithm itself.  An 32-bit encryption will therefore have 2^32 keys, which in a modern computer is easily cracked.  64-bit will take longer, but not impossibly long.

distributed.net took 4 years to crack a 64-bit key. Not too much of a danger there, considering most keys are 128-bits.

---

### Post by Monicker on 2008-06-08
> **tom66 said:**
> distributed.net took 4 years to crack a 64-bit key. Not too much of a danger there, considering most keys are 128-bits.

The implementation and algorithm are still extremely important, regardless of key size. WEP is a good example of this.  You only need to gather a certain amount of wireless traffic encrypted via WEP in order to obtain the key.  With tools like aircrack-ng you can do this in under 5 minutes, even for a 128 bit WEP key.

---

### Post by imT on 2008-06-08
i see, thanks, 
so what about the encfs paranoia mode, is that good or i need to go expert and learn more about encryption ?

---

### Post by Monicker on 2008-06-09
> **imT said:**
> i see, thanks, 
so what about the encfs paranoia mode, is that good or i need to go expert and learn more about encryption ?

That I do not know.  I took a brief look at the encfs web site, but did not see many of what specific algorithms it supports.  I also did some brief searching but could not find any peer reviews of the encfs implementation.

---

### Post by petrocc on 2008-06-09
> **imT said:**
> i see, thanks, 
so what about the encfs paranoia mode, is that good or i need to go expert and learn more about encryption ?

[http://www.amazon.com/Applied-Cryptography-Protocols-Algorithms-Source/dp/0471117099/ref=pd_bbs_2?ie=UTF8&s=books&qid=1213021651&sr=8-2](http://www.amazon.com/Applied-Cryptography-Protocols-Algorithms-Source/dp/0471117099/ref=pd_bbs_2?ie=UTF8&s=books&qid=1213021651&sr=8-2)

---

### Post by the_doc on 2008-06-09
The algorithm is extremely important, a weak algorithm will undermine an encryption system regardless of the key length.  Attackers would use the weakness to compromise the system and thereby get access to traffic/data with the size of the actual key/pw making little difference.

---

### Post by ukripper on 2008-06-09
if this question is regarding Wireless lan then it is highly recommended you use WPA/WPA2 
WPA2 with AES encryption is very hard to crack.

WEP is useless to use and easily cracked using kismet

---

### Post by imT on 2008-06-09
according to man:
```
Paranoia mode uses the following settings:
           Cipher: AES
           Key Size: 256 bits
           Filesystem Block Size: 512 bytes
           Filename Encoding: Block encoding with IV chaining
           Unique initialization vector file headers
           Message Authentication Code block headers
           External IV Chaining
```
is it safe to be used with a 53 character pass, i use the app [ParolaPass]("http://ubuntuforums.org/showthread.php?t=299823") for the password generating ?

it's not about wireless encryption, it's about disk/file encryption mainly with ecfs.

---

### Post by the_doc on 2008-06-09
The AES cipher is a tried and tested one and a 53 character password is longer than most, I reckon it'll be more than enough.

---

### Post by ukripper on 2008-06-09
AES algorithm is quiet strong enough for disk encryption and would also require long password. I would use atleast 20 characters

---

