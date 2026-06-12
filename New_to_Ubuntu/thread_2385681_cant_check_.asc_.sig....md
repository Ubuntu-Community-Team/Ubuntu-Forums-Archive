---
title: "cant check .asc .sig..."
date: 2018-02-23
forum: New to Ubuntu
---

### Post by frank2222 on 2018-02-23
Hello all . I cant seem to be able to check any pgp... I run 

 sudo gpg --verify /try.asc /try.tar.xz

I'm in the directory with the files but I allways get...

gpg: Can't check signature: public key not found

Ive tried .sig file same result

Can someone please tell me what im missing.

Thanx in advance

---

### Post by Impavidus on 2018-02-23
I'm not very experienced with gpg, but you run it with sudo. That means you run gpg as the root user, but still with your normal user's environment. That may confuse gpg. If the files are readable for the ordinary user, there should be no need for sudo.

Your paths to the files start with a /. That means they are absolute paths, indicating the files are in the root directory, not in the current directory. The root directory would be a strange place for those files.

---

### Post by frank2222 on 2018-02-24
gpg --verify home/*****f/Downloads/setup.tar.bz2.sig home/*******/Downloads/setup.tar.bz2
gpg: can't open /*******f/Downloads/setup.tar.bz2.sig'
gpg: verify signatures failed: file open error

sudo gpg --verify home/darkelf/Downloads/-setup.tar.bz2.sig home/****f/Downloads/setup.tar.bz2
[sudo] password for *****: 
gpg: can't open `home/*****/Downloads/setup.tar.bz2.sig'
gpg: verify signatures failed: file open error


I tried the things you suggested...

What am i doing wrong?

EDIT:ADDED:  I noticed this in error...   ( ' )
here ...`home

---

### Post by frank2222 on 2018-02-24
gpg --veriify setup.tar.bz2.sig setup.tar.bz2
gpg: Signature made Sun 09 Jul 2017 01:20:57 AM AKDT using RSA key ID 54DDD393
gpg: Can't check signature: public key not found

I'm probably doing something wrong but i cant figure it out...

---

### Post by deadflowr on 2018-02-24
Same basic principal as this:
[https://help.ubuntu.com/community/VerifyIsoHowto#Find_out_what_key_was_used_to_issue_the_signature]("https://help.ubuntu.com/community/VerifyIsoHowto#Find_out_what_key_was_used_to_issue_the_signature")

---

### Post by frank2222 on 2018-02-25
[URL="https://ubuntuforums.org/member.php?u=1276577"] 						 							[B]Thank you for the reply deadflower

This is where I'm at now. I imported what I think is the key using
[/B][/URL][**[COLOR=#C61919][B]**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1276577")
gpg --keyserver hkp://keyserver.ubuntu.com --recv-keys 54DDD393
gpg: requesting key 54DDD393 from hkp server keyserver.ubuntu.com
gpg: key 54DDD393: public key "VeraCrypt Team <veracrypt@idrix.fr>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)


but now I get this...

sudo gpg --verify '/home/****8*/Downloads/veracrypt-1.21-setup.tar.bz2.sig' '/home/****/Downloads/veracrypt-1.21-setup.tar.bz2' 
gpg: Signature made Sun 09 Jul 2017 01:20:57 AM AKDT using RSA key ID 54DDD393
gpg: Good signature from "VeraCrypt Team <veracrypt@idrix.fr>"
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: 993B 7D7E 8E41 3809 828F  0F29 EB55 9C7C 54DD D393

Whats going on?

---

### Post by frank2222 on 2018-02-26
Can no one help?
I'm confused. I thought guys would have some advice...

---

### Post by frank2222 on 2018-02-28
Im giving this one more bump up in hopes someone can help....

---

