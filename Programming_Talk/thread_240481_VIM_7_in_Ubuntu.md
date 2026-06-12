---
title: "VIM 7 in Ubuntu ?"
date: 2006-08-20
forum: Programming Talk
---

### Post by krypto_wizard on 2006-08-20
When will VIM 7 hit the Ubuntu repos ?

---

### Post by Note360 on 2006-08-21
You have to compile it. Trust me though it is well worth it.

---

### Post by stoeptegel on 2006-08-21
Wasn't vim7 backported? I've got it installed by apt somehow, somewhere :-k

---

### Post by krypto_wizard on 2006-08-21
how does your /etc/apt/source.list looks like. I can't find vim 7 in backports either.

---

### Post by krypto_wizard on 2006-08-21
I got the answer. Add these lines to your /etc/apt/source.list


deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas all
deb-src [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas all

and upgrade to VIM 7 is cakewalk.

---

### Post by star477 on 2006-08-28
I added these lines to my sources .list but when I run aptitude update I get an error message:

W: GPG error: deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas Release: The foolowing signature couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135Da466

Further up I also got the message:

Ign: [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas Release

As you might notice I am not so familiar with the package management and installing from other than the usual sources. But I do like to get Vim7.

Can anyone help me?

---

### Post by skymt on 2006-08-28
> **star477 said:**
> I added these lines to my sources .list but when I run aptitude update I get an error message:

W: GPG error: deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas Release: The foolowing signature couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135Da466

Further up I also got the message:

Ign: [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas Release

As you might notice I am not so familiar with the package management and installing from other than the usual sources. But I do like to get Vim7.

Can anyone help me?


You should be fine. The error just means you don't have Seveas's public key on your GPG keyring. This means you aren't protected from man-in-the-middle attacks, but those are rare and extremely hard to pull off in the context of package management.

Or, you could fix it like so (from [http://mirror.ubuntulinux.nl/](http://mirror.ubuntulinux.nl/), not mine):
```
wget http://mirror.ubuntulinux.nl/1135D466.gpg -O- | sudo apt-key add -
```

EDIT: That code didn't work for me (infinite loop). It worked when I seperated the commands, like so:
```
wget http://mirror.ubuntulinux.nl/1135D466.gpg
sudo apt-key add 1135D466.gpg
rm 1135D466.gpg
```

ANOTHER EDIT: I just noticed Aptitude does parallel downloads! Sweet!

---

### Post by yigal.weinstein on 2006-08-29
Just download as debs by reading,
[http://blog.publicidadpixelada.com/2006/07/31/small-how-to-vim-70-running-on-ubuntu-dapper/](http://blog.publicidadpixelada.com/2006/07/31/small-how-to-vim-70-running-on-ubuntu-dapper/)
dpkg -i *

easy enough?
and it works.

---

