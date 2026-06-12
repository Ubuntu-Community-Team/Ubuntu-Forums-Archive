---
title: "What Level of Berkely DB is in the Ubuntu 14.04 Repo?"
date: 2014-10-05
forum: Programming Talk
---

### Post by james-armstrong on 2014-10-05
Hi all!

It says here [http://docs.oracle.com/cd/E17076_04/html/programmer_reference/intro_products.html ]("http://docs.oracle.com/cd/E17076_04/html/programmer_reference/intro_products.html")that there are four levels of Berkely DB:

         
[LIST]
[*]             Berkeley DB Data Store 
[*]             Berkeley DB Concurrent Data Store 
[*]             Berkeley DB Transactional Data Store 
[*]              Berkeley DB High Availability 
[/LIST]

but that the open source distribution includes and builds all four.

But when I say dpkg -L libdb5.3:amd64

I see a single 
/usr/lib/x86_64-linux-gnu/libdb-5.3.so

And don't really have a clue what "Level" I'm looking at.

Can anyone tell me?

Thanks.

---

### Post by gordintoronto on 2014-10-05
I suggest you install Synaptic Package Manager, and search it for "Berkeley". It appears to have a mish-mash of 5.1, 5.2, 5.3 and 6.0.

---

