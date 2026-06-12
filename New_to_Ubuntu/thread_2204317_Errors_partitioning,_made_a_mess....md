---
title: "Errors partitioning, made a mess..."
date: 2014-02-07
forum: New to Ubuntu
---

### Post by bc.haynes on 2014-02-07
Please take a look at this:
[ATTACH=CONFIG]250174[/ATTACH]
If you will notice, the extended partition goees into the unallocated area (blue outline, if you can see it). Is that a gparted error (Ha) or have I messed up, again. Do I need to install the distros again? (I don't mind) Or can the unallocated area be used for another distro? Wish I could remember how I did this. Not much help, there.

---

### Post by sammiev on 2014-02-07
Mine look s like that as I test 3 or 4 OS at a time. When I'm only testing 3 my partitioning looks much like yours.

---

### Post by bc.haynes on 2014-02-07
Is it okay to use the unallocated area for another OS?

---

### Post by sammiev on 2014-02-07
As you can see in my blue out lined box, I have 3 OS installed. So yes, you can use the unallocated area for another OS.

---

### Post by Bucky Ball on 2014-02-07
If you're talking about the unallocated area between sda6 and sda5, put what you like in there! Create logical partitions and install what you like. There is no limits that are going to effect you on how many logical partitions you can put inside an extended.

Your setup is absolutely normal. Nothing amiss there. See my attached Gparted screenshot for my mess. Note the contents of the extended partition. A regular disk, not set to EFI, with the four partition limitation (logicals inside the extended overcome this piffling detail). ;)

Only Win must be on a primary partition. Ubuntu doesn't care ...

---

### Post by Bashing-om on 2014-02-07
bc.haynes;

^^ +1 , I see nothing wrong with your partitioning( I have looked at it 3 times ) - the "yellow" bands that you are concerned about I think are but the used space indicator.

Install way !

[INDENT][INDENT]It's ubuntu, 1st rule
[INDENT][INDENT][INDENT]have fun
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bc.haynes on 2014-02-07
Thank all of you. That relieves pressure I felt, Going-By-The-Book.

---

