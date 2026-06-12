---
title: "compiz error: NO_PUBKEY 31A5F97FED8A569E"
date: 2006-07-16
forum: Repositories &amp; Backports
---

### Post by CheeseAndToast on 2006-07-16
When i reload in synaptic - i get the following errors:

W: GPG error: [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E

Any way to fix?

Thanks

---

### Post by reacocard on 2006-07-16
i get the same error. apparently we need a gpg key for the repo. no idea how to find it though.

---

### Post by tommcd on 2006-07-17
You need to get the gpg key. This link talks about a similar issue for debian multimedia repos that need a gpg key:

[http://www.debian-multimedia.org/faq.html](http://www.debian-multimedia.org/faq.html)

I am not sure exactly how to go about it for your situation though. There is a man page for gpg ('man gpg' in terminal). It is very long. Hope this helps.

---

### Post by eitch on 2006-07-23
Do this as a normal user guys:

gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 31A5F97FED8A569E

gpg --armor --export 1F41B907 > keyName.gpg

sudo apt-key add keyName.gpg

This way you've got a keyName.gpg file which you can keep somewhere safe and always add back to the apt gpg file.

Worked for me.

---

### Post by reacocard on 2006-07-24
nice eitch, that worked perfectly. for another repo also, although i had to change the numbers.

---

### Post by eitch on 2006-07-25
No problem... Glad I could help

P.S. The numbers are the ID of the public key. Every person who gpg signs a key will have his own number, so that's why you had to change em.

---

### Post by coldrick on 2006-08-09
For some reason this doesn't work for me. I did 
```
gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 31A5F97FED8A569E
gpg: requesting key ED8A569E from hkp server wwwkeys.eu.pgp.net
gpg: key ED8A569E: public key "Quinn Storm <livinglatexkali@gmail.com>" importedgpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1
gpg --armor --export 1F41B907 > beerorkid.gpg
sudo apt-key add beerorkid.gpg
OK

```

which looks OK, but when I ran apt-get update, I again got:
```
Reading package lists... Done
W: GPG error: http://www.beerorkid.com dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E
W: You may want to run apt-get update to correct these problems

```

Very strange. Any ideas?

Regards,
David

---

### Post by eitch on 2006-08-10
It does seem strange... On my machine I don't even need to install a signature for [www.beerorkid.com](www.beerorkid.com)...

See if you have these keys installed, otherwise search for them with the --recv-keys step

pub   1024D/DD4D5088 2001-10-09
uid                  Jonathan Riddell <jriddell@ubuntu.com>
uid                  Jonathan Riddell <jr@jriddell.org>
uid                  Jonathan Riddell (University Address) <jri@jriddell.org>
sub   1024g/D9F04547 2001-10-09

pub   1024D/1F41B907 1999-10-03
uid                  Christian Marillat <marillat@debian.org>
uid                  Christian Marillat <marillat@free.fr>
sub   1536g/C28DCC42 1999-10-03

pub   1024D/5B4420C4 2006-05-03 [expires: 2011-05-02]
uid                  DreamerC (For packages) <dreamerwolf2001@yahoo.com.tw>
sub   2048g/F769571F 2006-05-03 [expires: 2011-05-02]

pub   1024D/ED8A569E 2005-12-12
uid                  Quinn Storm <livinglatexkali@gmail.com>
sub   2048g/FBF299FF 2005-12-12


See ya....

---

### Post by coldrick on 2006-08-10
Ah geez, my bad. Notice in the above that I specified the wrong key on the --export step. Fixed that and all OK

Thanks,
David

---

### Post by eitch on 2006-08-10
As long as it works now =)) ggg

---

### Post by robyholmes on 2006-11-29
hi i am trying to install berly, i am stuck on installing the headers for the drivers. so i tryed to install them and it won't update says some thing about a key? so: this is what i did after looking at this forum>

shadowmodz@shadowmodz:~$ gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 31A5F97FED8A569E
gpg: requesting key ED8A569E from hkp server wwwkeys.eu.pgp.net
gpg --armor --export 1F41B907 > keyName.gpg
gpg: key ED8A569E: "Quinn Storm <livinglatexkali@gmail.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
shadowmodz@shadowmodz:~$ gpg --armor --export 1F41B907 > keyName.gpg
shadowmodz@shadowmodz:~$ sudo apt-key add keyName.gpg
gpg: no ultimately trusted keys found
OK
shadowmodz@shadowmodz:~$

and it didn't work, can anyone help? i am new to linux so i am not great at this? thanks a lot

---

