---
title: "BURST PPA error and rejection email. Please Help"
date: 2018-11-08
forum: Packaging and Compiling Programs
---

### Post by the13thfloorelevators on 2018-11-08
So I'm trying to create a BURST ppa for the Proof of Capacity Consortium software stack. I've started with the wallet. I downloaded it and built it from source and used Debuild to make it the files needed for the PPA. When I use Dput to push the file into the ppa it says it was successful but then I get a rejection email with the output:
 
```
Rejected:
burstcoin-wallet_2.2.4-1.dsc: Unknown section 'unknown'
burstcoin-wallet_2.2.4.orig.tar.gz: Unknown section 'unknown'
burstcoin-wallet_2.2.4-1.debian.tar.xz: Unknown section 'unknown'
burstcoin-wallet_2.2.4-1_source.buildinfo: Unknown section 'unknown'
Further error processing not possible because of a critical previous error.

 burstcoin-wallet (2.2.4-1) cosmic; urgency=medium
```

it shows my changlog file I made which is. 

```
burstcoin-wallet (2.2.4-1) cosmic; urgency=medium 
 -- the13thfloorelevators <the13thfloorelevators@protonmail.com>  Wed, 07 Nov 2018 23:15:49 +0000
```
 
If you guys have any idea about what I am doing wrong let me know.[HR][/HR]I think I found the culprit.
The section field in my control file was set to unknown lol. Thx

---

