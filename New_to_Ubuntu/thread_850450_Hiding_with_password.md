---
title: "Hiding with password"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by NikS on 2008-07-05
Hi all,

I am using ubuntu desktop 8.04 and do share my user account with my family members.
Is there a way i can password-protect or hide with a password my important files??
And files on removabe drives??

"Like an application or something that hides files till I provide it with a password?"

---

### Post by sydbat on 2008-07-05
Would your family members mind having their own accounts? If they are willing, I think this would be the best solution.

---

### Post by Madman6510 on 2008-07-05
Giving them seperate accounts would be the way to go, but if it's really sensitive, you might want to encrypt them with TrueCrypt.

---

### Post by grim4593 on 2008-07-05
Well you can use winrar to encrypt files. The issue is that in order to make a rar file with a password you have to do it from the command line since I haven't seen any frontends that let you encrypt. But when you open the rar with Archive Manager a password prompt will come up before you can see the files.

---

### Post by bodhi.zazen on 2008-07-05
You can archive the files with zip ( -P)

Depending on security :

1. You should make separate accounts as suggested earlier.

2. You might want to look at encryption (LUKS or Truecrypt)

---

### Post by unutbu on 2008-07-05
If you choose to make a separate accounts,
the default setting in Ubuntu will allow all files in /home to be readable by everyone. To change that,
open a terminal and type

```
chmod 700 $HOME
```
The 7 means you get read,write and execute permission and the 0's means members of your group and everyone else can not read, write or execute files or directories in your home. 

There are ways to make things less restrictive; for example, you could allow others to read files, but not to modify them. You could also make your $HOME readable, but a subdirectory only readable by you. In other words, the permissions can be set on a file-by-file, directory-by-directory basis.

---

### Post by Dr Small on 2008-07-05
If you wanted to only encrypt a file, you could use GnuPG with either a password or a public key / private key combination.

---

### Post by hyper_ch on 2008-07-05
or you could create a truecrypt container

---

### Post by bodhi.zazen on 2008-07-05
> **unutbu said:**
> If you choose to make a separate accounts,
the default setting in Ubuntu will allow all files in /home to be readable by everyone. To change that,
open a terminal and type

```
chmod 700 $HOME
```The 7 means you get read,write and execute permission and the 0's means members of your group and everyone else can not read, write or execute files or directories in your home. 

There are ways to make things less restrictive; for example, you could allow others to read files, but not to modify them. You could also make your $HOME readable, but a subdirectory only readable by you. In other words, the permissions can be set on a file-by-file, directory-by-directory basis.

Umm, nice thought but that will not work as they are sharing a common user to log in ...

:lolflag:

---

### Post by NikS on 2008-07-06
Seems it is best to creat different accounts then!!
It'l take long time to uncompress those files every time need them on my computer, its quite slow..

Then I can block the access by setting chmod as well!! Right??
Thanks all!!

Any suggestions about the removabe drives???

---

### Post by bodhi.zazen on 2008-07-06
Once you have a separate user name you can set ownership and permissions on the removable drive as well, assuming it is a linux native file system (ext3, reiserfs, xfs, jfs).

---

### Post by tramir on 2008-07-06
[Truecrypt]("http://www.truecrypt.org") is a good way to go. You can get a deb package from their website. It can also create "hidden" volumes (never tried it yet, so I have no idea how that works). And it has a nice GUI, so you don't really need to do anything from the command line except from starting it - it doesn't put an icon in the menus. So just press ALT+F2 and then type "truecrypt". From there eon it should be pretty self-explanatory, I think.

---

### Post by NikS on 2008-07-06
> **tramir said:**
> [Truecrypt]("http://www.truecrypt.org") is a good way to go. You can get a deb package from their website. It can also create "hidden" volumes (never tried it yet, so I have no idea how that works). And it has a nice GUI, so you don't really need to do anything from the command line except from starting it - it doesn't put an icon in the menus. So just press ALT+F2 and then type "truecrypt". From there eon it should be pretty self-explanatory, I think.

Wow!!
Thanks Tramir!!
Just checked that site out, It seems I will try Truecrypt put before i create different accounts..
But From screenshots, it seems difficult to operate since i am completely unaware of those encryption algorithms n hash algorithms!!! but will surely try!!!

---

### Post by NikS on 2008-07-06
Thanks Tramir!!
It worked pretty fine, though I dont understand most of the technical description of the most technical words like Keyfiles, XTS, serpent etc etc, i could use it!!

Thanks once again!!

---

### Post by bodhi.zazen on 2008-07-06
One nice feature about truecrypt, it is cross platform (as long as you have admin access).

If you are so inclined, I found the truecrypt documentation to be quite good, a lot if information in 1 place :

[http://www.truecrypt.org/docs/](http://www.truecrypt.org/docs/)

---

### Post by NikS on 2008-07-07
True, But I experienced certain problems with Truecrypt on windows..
My antivirus software halted on reboot n got damaged, I had to re-install it after i removed truecrypt!!
So,
Using it with linux alone!!

Anyways I have a different software on windows that serves the purpose!!
:)

I tried it under wine on ubuntu as well- obviously it dint work!!

---

