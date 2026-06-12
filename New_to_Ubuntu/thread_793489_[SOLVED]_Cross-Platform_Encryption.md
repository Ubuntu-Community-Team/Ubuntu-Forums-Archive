---
title: "[SOLVED] Cross-Platform Encryption"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by SurrealWraith on 2008-05-13
Firstly, I would like to point out that I have no experience with encryption whatsoever, other than the knowledge of what makes a "Strong Password" and how to use crackers and brute-forcers.  This means I will likely require much clarification.

I need a way to password protect a folder from Linux on a FAT32 flashdrive.  Is there any way to do this so Windows will recognize the protection?  I don't know if I am explaining this too clearly, nor am I certain as to whether this constitutes as encryption or not.  

It doesn't need to be password protected I guess; I just need it to be secure, and accessible from Linux and Windows without needing to install a program on every computer I wish to open the folder from.

Thanks

---

### Post by macaholic on 2008-05-13
Take a look at [TrueCrypt]("http://www.truecrypt.org/"), I'm pretty sure it provides what you are looking more.

---

### Post by SurrealWraith on 2008-05-13
Thanks for the suggestion.  I'm actually installing it right now.

---

### Post by SurrealWraith on 2008-05-13
I'm having some trouble with Truecrypt.  Does it require me to make a new partition?

---

### Post by macaholic on 2008-05-13
Unfortuantely I haven't any personal experience with truecrypt, you shouldn't need another partition. [This guide]("http://howtoforge.com/truecrypt-with-gui-on-ubuntu-7.10") was written for gutsy, however it still could be useful.

---

### Post by Inxsible on 2008-05-13
From Wikipedia:> **TrueCrypt** is a [software application]("http://en.wikipedia.org/wiki/Software_application") used for [on-the-fly encryption]("http://en.wikipedia.org/wiki/On-the-fly_encryption"). It can create a virtual encrypted disk in a file (container), which can be mounted as if it were a real disk. TrueCrypt also supports device-hosted volumes, which can be created on either an individual [partition]("http://en.wikipedia.org/wiki/Partition_%28computing%29") or an entire disk. 

So yes, i think it will create a new partition to put the files on.

---

### Post by bodhi.zazen on 2008-05-13
Truecrypt is the way to go. You can use either an ecnrypted file or encrypt an entire partition or flash drive.

See here  [http://www.howtoforge.com/truecrypt_data_encryption](http://www.howtoforge.com/truecrypt_data_encryption)

[http://www.truecrypt.org/docs/?s=tutorial](http://www.truecrypt.org/docs/?s=tutorial)

The only "problem" with truecrypt is you need administrative rights on both boxes to run it.

The best cross platform solution I know of, that does not require administrative rights, is bcrypt :

[http://bcrypt.sourceforge.net/](http://bcrypt.sourceforge.net/)

This is a command line tool though and only encrypts single files.

There is a gui front end, Best Crypt : [http://www.jetico.com/download.htm](http://www.jetico.com/download.htm)

It is not free, but works under wine.

See also : [http://www.linuxjournal.com/article/5938](http://www.linuxjournal.com/article/5938)

---

### Post by crossedout on 2008-05-13
Go with Truecrypt.  Use the container encryption for a single file or group of files, it works perfectly with both Windows and Ubuntu across a FAT32 drive/partition.  As bodhi.zazen stated, you can encrypt an entire partition if you want to, but it sounds as though you don't really need all that.

-Xout

---

### Post by SurrealWraith on 2008-05-13
> **bodhi.zazen said:**
> Truecrypt is the way to go. You can use either an ecnrypted file or encrypt an entire partition or flash drive.

See here  [http://www.howtoforge.com/truecrypt_data_encryption](http://www.howtoforge.com/truecrypt_data_encryption)

[http://www.truecrypt.org/docs/?s=tutorial](http://www.truecrypt.org/docs/?s=tutorial)

The only "problem" with truecrypt is you need administrative rights on both boxes to run it.

The best cross platform solution I know of, that does not require administrative rights, is bcrypt :

[http://bcrypt.sourceforge.net/](http://bcrypt.sourceforge.net/)

This is a command line tool though and only encrypts single files.

There is a gui front end, Best Crypt : [http://www.jetico.com/download.htm](http://www.jetico.com/download.htm)

It is not free, but works under wine.

See also : [http://www.linuxjournal.com/article/5938](http://www.linuxjournal.com/article/5938)


Seeing as I lack administrative priveledges on the Windows boxes at my school (unless I want to risk making myself an admin again and getting caught), I guess Truecrypt won't work.  Also, I *really* don't want to take the time to individually encrypt 500+ files with bcrypt, nor do I wish to pay for Best Crypt unless I truly have to. (Sorry for being so picky)  I guess if I really wanted to take the time I could potentially tweak bcrypt (or get my friend to do it) so it can encrypt whole folders.

---

### Post by SurrealWraith on 2008-05-14
I wasn't getting anywhere with Truecrypt, then I realized I might as well just put the folder in a .rar file with a unique and "strong" password.  This will suffice for my purposes.  Thanks for your help everyone!

---

