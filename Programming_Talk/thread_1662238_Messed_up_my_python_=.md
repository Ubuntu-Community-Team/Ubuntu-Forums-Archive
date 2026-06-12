---
title: "Messed up my python =/"
date: 2011-01-07
forum: Programming Talk
---

### Post by 98174 on 2011-01-07
I've been developing Python apps on Ubuntu.

Recently, due to some patches the maintainers released in newer versions, I downloaded and installed Python 2.7 as well as Python 3.2b2.  I later solved the issue and successfully backported it to Python 2.6.5 (the default version on Ubuntu).

However, immediately after this whole incident, I began noticing _massive_ slowdowns in my python scripts.  Scripts that once took 30 seconds now took 500, 600 seconds.

Any input on this would be extremely helpful.

---

### Post by 98174 on 2011-01-07
<Cross-posting from General Help>

I've been developing Python apps on Ubuntu.

Recently, due to some patches the maintainers released in newer versions, I downloaded and installed Python 2.7 as well as Python 3.2b2. I later solved the issue and successfully backported it to Python 2.6.5 (the default version on Ubuntu).

However, immediately after this whole incident, I began noticing massive slowdowns in my python scripts. Scripts that once took 30 seconds now took 500, 600 seconds.

Any input on this would be extremely helpful.

---

### Post by Vox754 on 2011-01-07
> **98174 said:**
> <Cross-posting from General Help>

I've been developing Python apps on Ubuntu.

Recently, due to some patches the maintainers released in newer versions, I downloaded and installed Python 2.7 as well as Python 3.2b2. I later solved the issue and successfully backported it to Python 2.6.5 (the default version on Ubuntu).

However, immediately after this whole incident, I began noticing massive slowdowns in my python scripts. Scripts that once took 30 seconds now took 500, 600 seconds.

Any input on this would be extremely helpful.

1. First of all, LOL.
2. Next. I hope this teaches people not to randomly upgrade the Python installation without a very good reason.
3. Finally. If you want any help, why not give more details and explain what your programs do. Better yet, post the code. Can you demonstrate such slowdowns? Saying "my programs are slow, help" is rather vague.

---

### Post by Ejay010 on 2011-01-07
OK 
First, I would like to appologize for posting this here but i need urgent help.
I did something really stupid without researching, i unistalled the original pyhton.
Only because i thought if i had 3.1 i dnt need the old one but alot of programs run off of them, i now realize that.
Please help me i havent restarted my laptop since i ran symantic. i know i need to get something back. but please help me 
i am a like a super noob that ran straight to the forms for help. am in the terminal now using w3m. please tell me what to 
type so i can get my ubuntu running normally again PLEASE HELP ME.

---

### Post by cariboo on 2011-01-08
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by nvteighen on 2011-01-08
Ugh... this can be really hard to restore.

Look at Synaptic whether the ubuntu-desktop package is broken or not. If it is, reinstalling it should force reinstallation of the default stuff and, per dependencies, hopefully all python2.5 and python2.6. You may still have to reinstall some stuff manually.

Reinstalling Python wouldn't restore everything because you probably also deleted a lot of stuff that depended on it...

But this may fail. If it fails, the best would probably be reinstalling the OS.

---

### Post by MadCow108 on 2011-01-08
you could run *debsums* which compares checksums of files installed by packages.
Some files installed manually should have different checksums.
Then search for the package those files come from with apt-file and reinstall them.
But no idea if this will help

---

### Post by 98174 on 2011-01-08
...Did my thread just get hijacked?

---

### Post by Ejay010 on 2011-01-13
I had to do a fresh install of the OS.
Thats because after i logged out of ubuntu that day, it rejected my password even after i changed it in 
recovery mode.(i dont  knw if it had any thing to do with the fact that i was using the kubuntu desktop look.)
But thanks for replys and tips and once again sorry for postin this here, if this was the wrong thread.

for those who did the same thing DONT LOG OUT. DO what those guys said to do...or just delete your partition and reinstall ubuntu.

Oh and yea call it hijackin lol. i see it as a means to get ahead lol.:)

---

