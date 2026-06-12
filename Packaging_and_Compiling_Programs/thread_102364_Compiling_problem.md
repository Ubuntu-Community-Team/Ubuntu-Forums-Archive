---
title: "Compiling problem"
date: 2005-12-11
forum: Packaging and Compiling Programs
---

### Post by NitrOuS on 2005-12-11
I hope I made thread in the right place...I have a problem compiling my c programmes. I have installed gcc compiler in console with the command 
apt-get install gcc 
and everything worked fine.But when I try to compile a c file it returns me that it doesn't recognises the *.h files even though I searched them and I found them in my system for example stdio.h library is located in /usr/lib/perl/5.8.7/CORE/nostdio.h
 (this is the result returned by 'locate' command). So there must be a problem with the linker. What can I do to fix it?Thanx!

---

### Post by yentingchen on 2005-12-12
Do u install libc6-dev package?

---

### Post by NitrOuS on 2005-12-12
[QUOTE=yentingchen]Do u install libc6-dev package?[/QUOTE]
I don't thing so but how can I do it?I'm new in linux and I will need some more help...

---

### Post by yentingchen on 2005-12-12
[QUOTE=NitrOuS]I don't thing so but how can I do it?I'm new in linux and I will need some more help...[/QUOTE]

apt-get update
apt-get install libc6-dev

---

### Post by NitrOuS on 2005-12-13
Thanks a lot!That helped!I search for this in net generally and I also installed a builter and now eveything works just fine!Thanks for your time!
:D :p

---

