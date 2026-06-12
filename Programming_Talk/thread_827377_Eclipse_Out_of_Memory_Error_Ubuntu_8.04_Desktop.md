---
title: "Eclipse Out of Memory Error Ubuntu 8.04 Desktop"
date: 2008-06-12
forum: Programming Talk
---

### Post by Wild Sheep on 2008-06-12
This post is to report my findings on how I fixed (so far so good) this issue.

I'm using Ubuntu 8.04 and installed the supported version of the Eclipse IDE.

I kept getting out of memory errors so I edited /usr/lib/eclipse/eclipse.ini

and added the following lines:

-vmargs
-Xms256m
-Xmx1024m
-XX:PermSize=256m
-XX:MaxPermSize=512m

However this had no effect as the launcher runs the script at:
/usr/bin/eclipse 

and the eclipse.ini file is ignored.

So, I opened up /usr/bin/eclipse and changed:

VMARGS=""

to:

VMARGS="-Xms256m -Xmx1024m -XX:PermSize=256m -XX:MaxPermSize=512m"

and ran eclipse.

Doing a ps -ef, I verified that these vmargs were used, and it seems to have done the trick.

Wondering if others have seen this and what are the alternative fixes. Thanks.

---

### Post by lordmetroid on 2008-07-21
I run Ubuntu on my not so old laptop(from around 2003). I have up until yesterday been runnning on 6.10 but as the repositories was taken offline a while ago, I decided to upgrade to 8.04.

Eclipse worked excellent on 6.10, not so on 8.04 :(

The little memory I have(256MiB) is completely consumed by Eclipse and it the system has to start using the swap disk. Resulting in an execution that takes seconds for registring my typing and up to minutes for other IDE functionality such as code compleation.

I am desperate, I have uninstalled compiz and other software that could possibly be hogging my memory. I'll try this.

---

### Post by txcrackers on 2008-07-21
lordmetroid - Setting those VM args isn't your problem, it's that you don't have enough *physical* memory. Those settings actually increase the memory-footprint of Eclipse.

Eclipse uses a lot of memory (in my opinion, 'way too much). A lot of the other Java IDE's **can** use a lot of memory. These days, 256Mb of memory is just not going to be able to handle any of these programs. You're going to need to add memory (which I don't know is even possible in your case) - 5 year old laptops are actually **very** old. Or you're going to have to bite the bullet and actually get a newer machine.

Wild Sheep - yes, I've had to do that myself on more than one occasion. Which is why I kicked Eclipse to the curb and switched to Netbeans (may not have all of the bells and whistles that Eclipse does, but it appears to be much lighter on system requirements and not as bloated).

---

