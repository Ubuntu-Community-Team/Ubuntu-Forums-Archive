---
title: "Update Issue"
date: 2010-04-20
forum: Philippine Team
---

### Post by dmzamora on 2010-04-20
Magandang Araw po!

Patulong naman. 

I updated my ubuntu karmic when online.  But lately, nagkaka-error po.

ito po yung error message:

```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://ae.archive.ubuntu.com karmic-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.bz2  Hash Sum mismatch

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.bz2  Hash Sum mismatch

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.bz2  Hash Sum mismatch

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.bz2  Hash Sum mismatch

W: Failed to fetch http://ae.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
```

What should I do?  

Thanks for the help!

---

### Post by Script Warlock on 2010-04-20
try to switch server.

---

### Post by loell on 2010-04-20
yung cached key nya biglang nag iba,


try to acquire an updated one


```
sudo apt-get update -o Acquire::http::No-Cache=True
```

---

### Post by dmzamora on 2010-04-22
@script warlock- how do i do that? hehe.

@loell- will try that tonight... this happened to me before-- dili maka update.  Sa house lain among isp, lahi pud na company sa work.  Gidala nako one time sa office akong laptop, nag update siya... could it be the internet connection too?

Salamat daan!

---

### Post by neehs on 2010-04-22
@dmzamora Sir, sa inyoha bang office your using proxy server? ingon ka ning update sya? please check.

---

### Post by dmzamora on 2010-04-23
Wala po ko'y gibuhat, but I think nag-update siya. Pero naa napud lahi na error nigawas:

```
W: GPG error: http://security.ubuntu.com karmic-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

```

Libog na ko. hehehe.

@neehs wala daw mi naka proxy sa office.

---

### Post by dmzamora on 2010-04-26
Hi again!  I am back.
Nag-update ko, it says man na updated akong sytem but after it has downloaded (or na-download gyud ba?), mao ni ang error:

```
W: GPG error: http://security.ubuntu.com karmic-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

```

Ano dapat kong gawin? thanks!

---

### Post by loell on 2010-04-26
try,

```
sudo apt-get -o Acquire::http::No-Cache=True -o Acquire::BrokenProxy=true update
```

---

### Post by dmzamora on 2010-04-26
@loell  Thanks!  I think nasolve siya.  Wala na tong error.  	=D>

Salamat!

---

### Post by loell on 2010-04-26
no probs.. ;)

---

### Post by dmzamora on 2010-04-26
@loell

Unsa ang dahilan ngano naga error ug ing-ato?

---

### Post by dodo_ur on 2012-01-29
thank you alot 
it works :)

---

### Post by pinoyskull on 2012-01-30
> **dmzamora said:**
> @loell

Unsa ang dahilan ngano naga error ug ing-ato?
could be cache problem

---

