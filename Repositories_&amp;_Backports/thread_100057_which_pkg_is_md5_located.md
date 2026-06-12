---
title: "which pkg is md5 located"
date: 2005-12-06
forum: Repositories &amp; Backports
---

### Post by Darren Crotchett on 2005-12-06
I am looking for the command line utility, "md5".   For example, I just want to be able to create an md5 string like:

md5 keyword

In which package would it be located?

TIA,
Darren

---

### Post by 5-HT on 2005-12-06
Are you looking specifically for 'md5', or just a utility to generate/check md5 sums?

If you specifically want 'md5', unfortunately, I'm neither familiar with 'md5' nor could find it on the main, restricted, universe, or multiverse repositories.

**There is**, however, an excellent command line md5 utility called 'md5sum' that is part of the coreutils package.

It should be already installed as the coreutils package contains just that...core system utilities (like ls, mv, etc...).

To learn what it can do, and how to use it check out the manual page:
```
 man md5sum 
```


Hope this helps.

---

### Post by Darren Crotchett on 2005-12-06
[QUOTE=5-HT]Are you looking specifically for 'md5', or just a utility to generate/check md5 sums?

If you specifically want 'md5', unfortunately, I'm neither familiar with 'md5' nor could find it on the main, restricted, universe, or multiverse repositories.

**There is**, however, an excellent command line md5 utility called 'md5sum' that is part of the coreutils package.

It should be already installed as the coreutils package contains just that...core system utilities (like ls, mv, etc...).

To learn what it can do, and how to use it check out the manual page:
```
 man md5sum 
```


Hope this helps.[/QUOTE]


Thanks.  But, as far as I can see, that only generates an md5sum on a file.  I use/used a program called md5 on FreeBSD to generate an encrypted key based on a string.  

I'm trying to encrypt my password and put it in a database.  So, for example, I want to do this from the command line (I think the option is "-c"):

$md5 -c secret_password

Thanks,
Darren

---

### Post by vampire_janus on 2005-12-07
look for the package openssh and/or openssl

---

### Post by Darren Crotchett on 2005-12-07
[QUOTE=vampire_janus]look for the package openssh and/or openssl[/QUOTE]

Thanks.  I have both installed already.

Darren

---

### Post by 5-HT on 2005-12-07
[QUOTE=Darren Crotchett]Thanks.  But, as far as I can see, that only generates an md5sum on a file.  I use/used a program called md5 on FreeBSD to generate an encrypted key based on a string.  

I'm trying to encrypt my password and put it in a database...

Thanks,
Darren[/QUOTE]

Yeah, sorry didn't realize you wanted it for that purpose, and md5sum AFAIK just generates and checks a hash.

Just bumping this in the hope that someone more knowledgeable may be able to help you out.

---

### Post by knattlhuber on 2008-02-04
Some two years too late but still...
There's the 'sleuthkit' package that has the md5 command.

Also, PHP can generate an MD5 hash key from a string:

[FONT="Courier New"]string md5  ( string $str  [, bool $raw_output  ] )[/FONT]

---

