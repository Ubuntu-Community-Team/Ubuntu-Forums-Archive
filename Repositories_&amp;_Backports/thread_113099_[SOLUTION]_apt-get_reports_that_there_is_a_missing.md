---
title: "[SOLUTION] apt-get reports that there is a missing public key"
date: 2006-01-05
forum: Repositories &amp; Backports
---

### Post by ironblade on 2006-01-05
Hi all,

As I just had this problem, and didn't find the solution written up anywhere, I thought I'd share how I solved it.
This particular PC is running Debian testing, but the approach is identical for Ubuntu.

I was getting this error  when running apt-get update:
```
W: GPG error: ftp://mirror.myISP.net testing Release:
The following signatures couldn't be verified
because the public key is not available: NO_PUBKEY [key_id]
W: You may want to run apt-get update to correct these problems
```
[key_id] is the id string of the missing public key.

The solution is to run:
```
gpg --recv-keys [key_id]
gpg --export [key_id] | apt-key add -
apt-get update
```

Make sure you have a valid keyserver entry in your gpg config file.

Cheers!

---

### Post by Treviño on 2006-01-08
Thanks man.
It has worked to me ;)

You only forgot the "sudo" before than apt-key add ;)

---

### Post by astrobob.tk on 2010-03-06
Hi there,

It didn't owrk for me :(

here's what i get:

sudo apt-get upadte

```
W: GPG error: http://www.fbreader.org stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY [key id]
W: You may want to run apt-get update to correct these problems

```gpg --export [key id] | apt-key add -

```

gpg: no writable keyring found: eof
gpg: error reading `-': general error
gpg: import from `-' failed: general error
```gpg --export [key id]

produces random characters

please help

---

### Post by mrhhug on 2010-12-11
you could roll the dice and try this```
wget -q "http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x[key_id]" -O- | sudo apt-key add -
```

astrobob.tk, 
 i had the same problem, I used another method that worked for me, heres the walkthrough i used : 
[http://www.rebelzero.com/fixes/apt-get-gpg-error-public-key-not-available/88](http://www.rebelzero.com/fixes/apt-get-gpg-error-public-key-not-available/88)

but in case that site ever dies, heres what i did (lucid): 


```
Sudo aptitude update
```
gave me the error
```
W: GPG error: SOMEWEBSITE ./ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY [key_id]
```
Next  i tried ironblade's method but for some reason this key didn't take - i got hung on the export
hit Ubuntu's keyserver at [http://keyserver.ubuntu.com:11371/](http://keyserver.ubuntu.com:11371/)
in the serach string make sure you dont forget your 0x <-- thats a zero; so your gonna search for 0x[key_id]
now if it finds something your doing well. click on the link on the same line as "**pub**"
now hopefully your looking at the public key. All you need to do is to tell your ubuntu to look at that public key.
Copy the exact web address. and insert it into this line in between the " marks
```
wget -q "exactwebaddress" -O- | sudo apt-key add -
```
sample = wget -q "http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xBCCF7AF0B6571FCA" -O- | sudo apt-key add -

my ubuntu replied "OK" and i knew all was well

that worked for me hope it can help someone

---

