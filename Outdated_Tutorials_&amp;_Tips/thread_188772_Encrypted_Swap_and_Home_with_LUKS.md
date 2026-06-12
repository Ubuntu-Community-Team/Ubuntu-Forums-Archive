---
title: "Encrypted Swap and Home with LUKS"
date: 2006-06-04
forum: Outdated Tutorials &amp; Tips
---

### Post by virgo977virgo on 2006-06-04
I wrote the wiki page [https://wiki.ubuntu.com/EncryptedFilesystemHowto3](https://wiki.ubuntu.com/EncryptedFilesystemHowto3) to show how to encrypt swap and home with LUKS on Ubuntu 6.06 and 5.10

hope you will find it useful

bye

---

### Post by ways on 2006-06-06
nice how-to. didnt know encrypted swap was so easy to set up.

can you add how to do the same when home is a file, not a partition?
and if you know, how to integrate this with pam, so login pass will be accepted as mount-pass.

---

### Post by matthew on 2006-06-06
That looks great. I am going to have to try it out when I have some spare time.

---

### Post by delbene on 2006-06-06
Very nice!!!

Would be also wonderful to have a wiki including a fully encrypted ubuntu system...

---

### Post by virgo977virgo on 2006-06-09
[QUOTE=ways]nice how-to. didnt know encrypted swap was so easy to set up.

can you add how to do the same when home is a file, not a partition?
and if you know, how to integrate this with pam, so login pass will be accepted as mount-pass.[/QUOTE]
look here:
[LIST]
[*][Rene Mayrhofer's blog - Encrypted home directories]("http://www.mayrhofer.eu.org/Default.aspx?pageindex=7&pageid=26")
[*][Linux Journal - Implementing Encrypted Home Directories]("http://www.linuxjournal.com/article/6481")
[/LIST]

However, I won't use PAM, because I think that a good encryption password ([diceware.com]("http://www.diceware.com")) isn't a good login/root password; in fact, I prefer to have a long (around 40 chars) encryption password to be used one time, and a mildly long (around 15 chars) system password to be used every time I need.

---

### Post by ways on 2006-06-09
thanks. those links really helped. but does anyone else get problems with ownership? 

volume * crypt - /home/.&.img /home/& loop,user,exec - -
in pam_mount

after mount root owns my home. tried adding uid=&, but apparently ext3 (which i used) does not allow this option.

---

### Post by jgrantham on 2006-06-11
Will this destroy anything in the home folder? Should I start with a clean system before puting anything on it?

---

### Post by ways on 2006-06-11
[QUOTE=ways]thanks. those links really helped. but does anyone else get problems with ownership? 

volume * crypt - /home/.&.img /home/& loop,user,exec - -
in pam_mount

after mount root owns my home. tried adding uid=&, but apparently ext3 (which i used) does not allow this option.[/QUOTE]

works now. dont think i changed anything. :rolleyes: 


> 
Will this destroy anything in the home folder? Should I start with a clean system before puting anything on it?


it will, if you follow the guide and reformat a home partition. but if you choose to create a file to keep "home" in, you can do it without deleting anything.

---

### Post by virgo977virgo on 2006-06-12
> **ways]it will [destroy anything in the home folder], if you follow the guide and reformat a home partition. but if you choose to create a file to keep "home" in, you can do it without deleting anything.[/QUOTE]

I've updated the [guide]("https://wiki.ubuntu.com/EncryptedFilesystemHowto3") to better explain home data preservation.

From the guide, *warnings* section:
[QUOTE]encrypting a partition is a destructive operation said:**
> http://man.linuxquestions.org/index.php?query=shred&type=2&section=1[/url] 

 [http://www.cs.auckland.ac.nz/~pgut001/pubs/secure_del.html](http://www.cs.auckland.ac.nz/~pgut001/pubs/secure_del.html) 


---

### Post by ways on 2006-06-16
anyone else lost suspend & hibernate after doing this?

---

### Post by imagine on 2006-06-16
[QUOTE=ways]anyone else lost suspend & hibernate after doing this?[/QUOTE]
In the howto, the swap partition is encrypted using a random key. That means the swap partition is encrypted with a new key at every reboot and then reformatted, since the old content obviously cannot be read anymore. The helper application "cryptsetup" hides a bit what is actually done.

What you'll have to do in every case is encrypting the swap partition as a normal partition, ie with a password. I didn't try dm-crypt together with suspend to ram or suspend to disk yet though.

---

### Post by ways on 2006-06-16
[QUOTE=imagine]In the howto, the swap partition is encrypted using a random key. That means the swap partition is encrypted with a new key at every reboot and then reformatted, since the old content obviously cannot be read anymore. The helper application "cryptsetup" hides a bit what is actually done.

What you'll have to do in every case is encrypting the swap partition as a normal partition, ie with a password. I didn't try dm-crypt together with suspend to ram or suspend to disk yet though.[/QUOTE]

yeah. sorry bout that. i found that encryption was not the problem. don't want to keep other laptopusers from using this. suspend is just (and has always been) a bit unreliable. it work fine now. thanks again for your work.

---

### Post by virgo977virgo on 2006-06-17
[QUOTE=imagine]What you'll have to do in every case is encrypting the swap partition as a normal partition, ie with a password.[/QUOTE]

Why you suggest to *encrypt the swap partition as a normal partition **in every case*** ???

What's wrong with encrypting the swap with a random key ???

Maybe encrypting swap as a normal partition is needed by hibernate ???

Or it's only more speedy ???

---

### Post by imagine on 2006-06-17
[QUOTE=virgo977virgo]Why you suggest to *encrypt the swap partition as a normal partition **in every case*** ???[/QUOTE]
That was a misunderstanding. I meant in every case when you want to keep the data in the swap partition. If there's no need for that then a random key is just fine.

---

