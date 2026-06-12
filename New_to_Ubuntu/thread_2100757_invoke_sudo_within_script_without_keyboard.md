---
title: "invoke sudo within script without keyboard"
date: 2013-01-02
forum: New to Ubuntu
---

### Post by allynm on 2013-01-02
Hello everyone,

I am attempting to invoke sudo in a bash script.  The sudo man page indicates that the -S option allows reading the password from stdin, not just the keyboard.

So I write the following tiny script ("echosudo").

```
#!/bin/bash
echo "password\n" | sudo -S -u dave command

```"dave" is another user on the same box that I'm trying to allow using the command .  After doing chmod +x echosudo and running it as ./echosudo--I get a bunch of man page stuff that seems to have the good intentions of helping me fix what I've done wrong.

So, it is possible that the sudo man page is incorrect.  It is also possible that Ubuntu has not implemented this function, or chosen deliberately not to implement it.  Hopefully this is not the case, because if it is the case I'm going to have to mess with /etc/sudoers and I'd really really rather not.

As a newcomer, if I have to mess with /etc/sudoers/ could someone tell me what the code in visudo would look like?

Thanks,
Mark Allyn aka allynm

---

### Post by JKyleOKC on 2013-01-02
Did it not work for you in that other thread about USB and Zenity? Could it be anything so simple as the -S option needing to be parsed after the -u option?

I'm not in any position to test various aspects of this, but if it worked in another script then it has to be something you're doing slightly differently in this one...

---

### Post by fdrake on 2013-01-02
> **allynm said:**
> Hello everyone,

I am attempting to invoke sudo in a bash script.  The sudo man page indicates that the -S option allows reading the password from stdin, not just the keyboard.

So I write the following tiny script ("echosudo").

```
#!/bin/bash
echo "password\n" | sudo -S -u dave command

```"dave" is another user on the same box that I'm trying to allow using the command .  After doing chmod +x echosudo and running it as ./echosudo--I get a bunch of man page stuff that seems to have the good intentions of helping me fix what I've done wrong.

So, it is possible that the sudo man page is incorrect.  It is also possible that Ubuntu has not implemented this function, or chosen deliberately not to implement it.  Hopefully this is not the case, because if it is the case I'm going to have to mess with /etc/sudoers and I'd really really rather not.

As a newcomer, if I have to mess with /etc/sudoers/ could someone tell me what the code in visudo would look like?

Thanks,
Mark Allyn aka allynm


you shouldn't write yourpassword into a script! Instesad creat a script and add it the root SUID bit. Make sure that the file can be run by the group you want and edited only by root and nonelse.

[http://nixshell.wordpress.com/2007/04/21/suid-shell-scripts-setting-the-sticky-bit/](http://nixshell.wordpress.com/2007/04/21/suid-shell-scripts-setting-the-sticky-bit/)

---

### Post by allynm on 2013-01-02
Hii JKyleOKC and fdrake:

JKyleOKC--yes, I know!  I thought the whole business would be trivial, and then ,after spending just about all afternoon after returning from the dentist, in a new script I tried the same technique and it simply wouldn't budge.  I have pored over the two scripts and can't see anything different.  This led me to the current post.  But.  I'll go back and check the order of the options just to be sure.

fdrake.  Your approach looks to me to be preferable, but  could you explain in a bit more detail how I would do this:

 > Instesad creat a script and add it the root SUID bit.Thanks for your help on this.

Regards,
Mark Allyn aka allynm

---

### Post by allynm on 2013-01-02
Hello again, fdrake and JKyleOKC,

Turns out a bit of research on permissions turned up the answer to the question I posed to fdrake as to how to set the suid bit.  Well, it works!  At least on 12.04 Ubuntu, but in doing research on this I ran across a posting that claimed that the bit on many distros cannot be set on bash scripts.  Apparently not the case with Precise.  

But, suppose worst case and suid bit can't be set.  What then?

JKyleOKC:  I downloaded inotify--tools.  Haven't looked at them.  They look pretty cool, however.   I'll try something out.  May need some help from you.

Regards to you,

Mark Allyn aka allynm

---

