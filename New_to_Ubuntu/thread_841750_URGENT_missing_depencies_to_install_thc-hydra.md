---
title: "URGENT: missing depencies to install thc-hydra"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by Sc4Rzz on 2008-06-26
Hello Ubuntu users,

I need some pro help..
I tried to install thc-hydra recently, and without succes.

I was missing 4 dependencies, and already installed 2 of them.
I still need ssh2 en SAP (sapr3) but they aren't in synaptic! (or not under the names ssh2 and sapr3...)

It's really urgent,, hope you can help.

the error I got:

```

sc4rzz@desktopsc4rzz:~/Desktop/hydra$ ./configure

Starting hydra auto configuration ...

Checking for openssl (libssl/ssl.h) ...
                                    ... found
Checking for Postgres (libpq) ...
                              ... found
Checking for SVN (ibsvn_client-1 libapr-0.so libaprutil-0.so) ...
                              ... found
Checking for SAP/R3 (librfc/saprfc.h) ...
                                      ... NOT found, module sapr3 disabled
Get it from http://www.sap.com/solutions/netweaver/linux/eval/index.asp
Checking for libssh (libssh/libssh.h) ...
                                      ... NOT found, module ssh2 disabled
Get it from http://0xbadc0de.be/ - use v0.11!

Hydra will be installed into .../bin of: /usr/local
  (change this by running ./configure --prefix=path)

Writing Makefile.in ...

NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES
=======================================================================
ARM/PalmPilot users: please run ./configure-arm or ./configure-palm respectivly

now type "make"
sc4rzz@desktopsc4rzz:~/Desktop/hydra$ 


```

---

### Post by ibutho on 2008-06-26
In the output shown above, there are links to where you can download the packages you need.

---

### Post by Sc4Rzz on 2008-06-26
> **ibutho said:**
> In the output shown above, there are links to where you can download the packages you need.

I know this, but the link is outdated, and leads me back to a page where I can order some CD's... 

There is no download for the package..

---

### Post by ex.hav0k on 2008-07-29
you can download the stuff, they're big downloads:  7x650mb.  it says minimum hdd space is like 15gigs... i dont really want that either.  i just want the few small lib files and dependencies... im trying to find somewhere to download the librfc and saprfc.h files from.

edit: this was for SAP R/3.  for the ssh... did you follow that link?  i followed it and you can install a file called libssh-0.2.  try going to [http://0xbadc0de.be/wiki/libssh:libssh](http://0xbadc0de.be/wiki/libssh:libssh)

---

### Post by Sc4Rzz on 2008-08-13
> **ex.hav0k said:**
> you can download the stuff, they're big downloads:  7x650mb.  it says minimum hdd space is like 15gigs... i dont really want that either.  i just want the few small lib files and dependencies... im trying to find somewhere to download the librfc and saprfc.h files from.

edit: this was for SAP R/3.  for the ssh... did you follow that link?  i followed it and you can install a file called libssh-0.2.  try going to [http://0xbadc0de.be/wiki/libssh:libssh](http://0xbadc0de.be/wiki/libssh:libssh)

sorry for the late response.
I already have ssh now.. only the sap/r3 is so annoying..
found it yet? and do you have a download link for the big downloads?

---

### Post by decadude on 2008-11-20
having the same exact problem

bump

surely someone knows this

---

### Post by Locutus_of_Borg on 2008-11-20
thc-hydra is not worth the trouble.

it will not make you a 1337 HAXOR, but will instead make you ask many many more questions on how it works before you scrap the whole concept and brute force your own myspace accounts or whatever..


I did eventually get it to compile, but never once got it to work right, and half of the internet will agree i think, **** sux

---

### Post by txwooley on 2009-01-20
I have the same problem with missing dependencies.  Synaptic says openssl and libssh are installed, but terminal says, "NOT found" for both.  These and SAP/R3 are the only missing dependencies.  Do I need an older version?  Is ./configure pointing to the wrong place to find these files?

---

### Post by p0cky84 on 2009-07-23
> **Locutus_of_Borg said:**
> thc-hydra is not worth the trouble.

it will not make you a 1337 HAXOR, but will instead make you ask many many more questions on how it works before you scrap the whole concept and brute force your own myspace accounts or whatever..


I did eventually get it to compile, but never once got it to work right, and half of the internet will agree i think, **** sux


Man you **really** do suck, now don't you? THC Hydra is the best of its kind, and as for;
> **Locutus_of_Borg said:**
> I did eventually get it to compile, **but never once got it to work right**, and half of the internet will agree i think, **** sux
That doesn't sound like it was Hydra's fault... Don't blame the apps for your failure.

---

### Post by linuxethylamide on 2009-10-13
> **p0cky84 said:**
> Man you **really** do suck, now don't you? THC Hydra is the best of its kind, and as for;

That doesn't sound like it was Hydra's fault... Don't blame the apps for your failure.

Hydra does seem quite usefull, I really wish it had a brute-force option. 
I just switched to ubuntu, Hydra works fine, but I am also having trouble compiling a gui for it.

---

