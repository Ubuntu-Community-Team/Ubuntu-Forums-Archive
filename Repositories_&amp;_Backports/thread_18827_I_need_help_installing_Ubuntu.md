---
title: "I need help installing Ubuntu"
date: 2005-03-08
forum: Repositories &amp; Backports
---

### Post by wolves on 2005-03-08
I cant seem to install Ubuntu. I always get to about 8 percent of installing the base system and it stops at a red screen. It says there was a problem with something like "console-tools" and will not finish the setup. Im am running this on an amd 64 and really need help!!! I downloaded the iso and burned it to a cd at a low speed.
Please help me!!!

---

### Post by bored2k on 2005-03-08
[QUOTE=wolves]I cant seem to install Ubuntu. I always get to about 8 percent of installing the base system and it stops at a red screen. It says there was a problem with something like "console-tools" and will not finish the setup. Im am running this on an amd 64 and really need help!!! I downloaded the iso and burned it to a cd at a low speed.
Please help me!!![/QUOTE]
 Did you check if the .iso was not corrupt ? [with the md5sum on the dl website] ?

---

### Post by wolves on 2005-03-08
umm.... i dont know what that is. so can u discribe that last part a little more?

---

### Post by bored2k on 2005-03-08
MD5SUMs are file verifiers. Every file has one, and it will tell you if you're download is correct . [If the warty.iso md5sum is 200 , and you're .iso says 201, you're download is incorrect].

Here are the sums:
> 7159290f68dff2a93f1a07d2c2b6ce35  warty-release-install-amd64.iso
a491903a2d2197651864dec3836d85e0  warty-release-install-i386.iso
6ef6fe1a63831c0c92db9a89869a33ea  warty-release-install-powerpc.iso
dac84a3abf5a1a104d768d569a62579e  warty-release-live-i386.iso

[http://www.brandonstaggs.com/filecheckmd5.html](http://www.brandonstaggs.com/filecheckmd5.html)
[http://www.fastsum.com/download.php](http://www.fastsum.com/download.php)

These are md5 verifiers for Windows.

---

### Post by wolves on 2005-03-09
i am a newb techie so im a little confused.
I also had a free disk that i picked up at a store, and it said the same error so i im almostsure it was not the download.
anything else that could help?

---

### Post by maruchan on 2005-03-09
Can you give the exact error message?

---

### Post by wolves on 2005-03-09
[QUOTE=maruchan]Can you give the exact error message?[/QUOTE]
 ok, ill post it in about 40 minutes.  I got some stuff i need to do.

---

### Post by wolves on 2005-03-09
[QUOTE=maruchan]Can you give the exact error message?[/QUOTE]
 The error message is:

BOOTSTRAP ERROR

couldn't   retrive console-tools.  This could be due to a network problem or a bad CD, depending on your instalation method.  
If you are installing from CD-R or CD-RW burning the CD at a lower speed may help.
<go back>                                                                       <continue>

" the next message was:"

Failed to install the base system

The base system installation into /target/ failed.
Cheak /var/log/messages or see virtual console 3 for the details.

<go back>                               <continue>

---

### Post by wolves on 2005-03-09
plz reply soon, i need to go in like 15 minutes.

---

### Post by jfreak on 2006-04-16
This is a huge problem and i'm almost certain from the research and tests that I’ve done that it's not a burning problem.
This is obvious because it occurs with ordered pressed disks.
It's also not a cd drive error.

I think i am getting closes to the answer and i think it has to do with your hard drive.

Some people have gotten ubuntu to work using a program called killdisk, but it doesn’t work most of the time and it is dangerous for your drive.

---

