---
title: "Mono: Unhandled Exception: System.NotSupportedException: CodePage 1252 not supported"
date: 2008-06-16
forum: Programming Talk
---

### Post by vcat on 2008-06-16
Hi!

I was playing with Ubuntu + Mono + Mysql and while testing a simple program that returns the result of a simple SELECT statement into the command line, ran into an error:

**Unhandled Exception: System.NotSupportedException: CodePage 1252 not supported**

Upon further investigation I found a very simple solution:

```
sudo apt-get install libmono-i18n2.0-cil
```

Since I did not find anything in these forums, I decide to sketch this post.

V.

---

### Post by tiger2004 on 2008-07-25
Thanks a lot for this tip. So far I had a painful experience with the mono project. Mono-server2 had a bug and it has been reported for a while but no one bothered to fix it. The bug is in the configuration of the mono server path it ends with exe  extension which it is  windows. I done a tutorial about it at [http://safwan.speakarabi.co.uk/](http://safwan.speakarabi.co.uk/). 

You have saved me lots of efforts. I tried everything to make the database connect but with no luck till I found this page.

---

### Post by choclatboy on 2008-08-03
Thank you very match:KS

---

### Post by LRT on 2008-09-05
thank you for this post!! this solved the same problem i was having.

[http://n2.nabble.com/error-CS0006:-cannot-find-metadata-file-`System.Data.dll`-td839742.html]("http://n2.nabble.com/error-CS0006:-cannot-find-metadata-file-`System.Data.dll`-td839742.html")

---

### Post by jake.conk on 2008-10-28
Thanks!!! This solved my issue on Unbuntu 8.04!!!

---

### Post by directhex on 2008-10-28
The root cause of this problem is a deviation between Ubuntu and Debian - on Debian, all package managers will installs "Recommends:" by default. On Ubuntu, SOME will install Recommends by default, some will not. libmono-i18n2.0-cil is a Recommends of limono-corlib2.0-cil, so if you aren't using the right package manager, you won't get the Recommends.

This divergence is fixed in Intrepid.

---

### Post by eugeniol on 2008-10-29
Now i'm new ubuntu user, this issue help me so much.

uke- Rosario, Argentina

---

### Post by itsols on 2010-03-06
Thank you vcat for your WONDERFUL thought! I've been struggling with this for a whole week but never could figure out this until I bumped into your superb post. It is indeed invaluable and I'm very thankful to you for this contribution.

@directhex, how are we (as users) supposed to know what libs go in where? After all, I use synaptic and install these things so it is supposed to work out the dependencies.

Anyway, I'm glad I was able to do this!

Cheers!
Khalid

---

