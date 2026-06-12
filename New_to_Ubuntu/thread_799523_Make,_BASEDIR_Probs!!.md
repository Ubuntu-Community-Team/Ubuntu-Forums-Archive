---
title: "Make, BASEDIR Probs!!"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by leo83 on 2008-05-19
Hello all,

Thanks for making ubuntu install so simple. No Fear now.My first task is successfully complete.

I am first time Linux user,My 2nd task is to issue a Make command using terminal, however i am not successful

Tried googling with Make and BASEDIR keywords with very less useful results.


leo@leo-desktop:/srv/krone/Mini-Controller/Codebase 2.5.0.0/PoE$ make
. ./checkpath.sh

PATH WARNING!  Your BASEDIR is not set!
Press any key to continue

make -C tools all
make[1]: Entering directory `/srv/krone/Mini-Controller/Codebase 2.5.0.0/PoE/tools'
cd mfg; make install
make[2]: Entering directory `/srv/krone/Mini-Controller/Codebase 2.5.0.0/PoE/tools/mfg'
cp mfgChecksum /toolbin
cp: cannot create regular file `/toolbin': Permission denied
make[2]: *** [install] Error 1
make[2]: Leaving directory `/srv/krone/Mini-Controller/Codebase 2.5.0.0/PoE/tools/mfg'
make[1]: *** [mfg] Error 2
make[1]: Leaving directory `/srv/krone/Mini-Controller/Codebase 2.5.0.0/PoE/tools'
make: *** [tools] Error 2


I need some guidance about BASEDIR, how and where do i find it..
Any Tutorials etc,please post links.

cheers,
Abhi

---

### Post by Cypher on 2008-05-19
Dump the contents of the Makefile (or makefile) to [http://pastebin.com/](http://pastebin.com/) and we can take a look..

---

### Post by leo83 on 2008-05-19
> **Cypher said:**
> Dump the contents of the Makefile (or makefile) to [http://pastebin.com/](http://pastebin.com/) and we can take a look..

I have posted it, with name Abhishek, please look in and inform

Thanks

---

### Post by Cypher on 2008-05-19
You need to provde the URL for us to see it..we can't search based on your name..

---

### Post by leo83 on 2008-05-20
> **Cypher said:**
> You need to provde the URL for us to see it..we can't search based on your name..

Here it is,

[http://pastebin.com/m41b1b316](http://pastebin.com/m41b1b316)

---

