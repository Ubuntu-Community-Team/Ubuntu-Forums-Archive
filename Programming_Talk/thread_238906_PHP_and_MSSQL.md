---
title: "PHP and MSSQL"
date: 2006-08-18
forum: Programming Talk
---

### Post by brownrl on 2006-08-18
Best Ubuntuers

I am looking for a way to connect PHP to an MSSQL server without having to recompile PHP?

I know there is a way of doing it with recompiling --with-MSSQL however its only one customer of mine that needs it and I would like to be able to keep the machine up to date with apt-get update, apt-get upgrade. If I use the sources then PHP won't be upgraded with normal update?

I would be open to a solution that just could be 'include'd in code or maybe making a seperate stand alone php install just for that customer?

I posted this in a PHP forum as well but I figured since this was an ubuntu machine that I give a shot here as well.

Thanks in advance
Rob

---

### Post by ditikos on 2006-10-12
Actually there is an odbtp protocol that you use a winbox as an interface between mssql and php (with the use of a dynamic .so lib) but I can't find the ubuntu package. And I hate compiling.

You can also use it with conjunction of adodb php (that has the appropriate driver).

---

