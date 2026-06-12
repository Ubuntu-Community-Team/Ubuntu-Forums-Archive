---
title: "chmod options"
date: 2013-11-26
forum: New to Ubuntu
---

### Post by thatredbird on 2013-11-26
I have been messing around with vi and creating scripts and noticed that I am unable to run scripts until I use the chmod 755 file option is this always the way that it is done? Or am I saving things in the wrong file? It seems as though if I can edit it I should be able to execute it?  I don't mind doing the typing. I just wanted to ensure that I wasn't missing something.

I have been using lubuntu for four days, so I am still low on the learning curve.

---

### Post by Bashing-om on 2013-11-26
thatredbird; Hi ! Welcome to the forum.

Permissions:
755 is Read, Write, eXecute for the Owner of the file;
Read and Write for Others;
and Read Write for the rest of the world.

See:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
and in terminal do:
```

man chmod
man chown

```

Permissions and access are the major strengths of linux (ubuntu).

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by thatredbird on 2013-11-27
If I understand the numbers, if I am the only one that is using it, i could just as easily use 700?

---

### Post by Sudo_SU_Root on 2013-11-27
Yes, chmod 700 is read, write, & execute by owner. Be careful though  and make sure you pay specific attention to what user you are when you  chmod 700, if you have multiple users, and also to what user or programs  may need to access that file or program. If a file is needed by a  certain program (some have their own user/group) you could block it from  being accessed by that program which needs to access it or even block  yourself. If you have root access you can pretty much always fix it, but  I am sure everyone has made this simple mistake before (I know I have)  and spent the next 30 minutes becoming the file Owner user/group again  to go back and correct it, just so it can be accessed by a program or by  another username. 

As long as we are not talking about a web server with sensitive data, I  think it is always better to be a bit more relaxed with the file  permissions than 700 unless it is absolutely necessary. If you just use **775 Owner: Read Write Execute, Group: Read Write Execute, Other: Read Execute **or **755 Owner: Read Write Execute, Group: Read Execute, Other: Read Execute** or **770** or **750**.  For instance if you are root user (su root OR sudo su root) and you set  chmod 700 to a file or program, and then you exit root user... back to  user1234xyz you cannot view, edit, or execute that file or change the  permissions without becoming the Owner again. If you set 770 or 750 at  least the same group (ex: administrator) can read, write, and execute or  read and execute.

*Just remember*: **read, write, execute  ===  4, 2, 1**  ...which add up to  **seven**! 
So...

**7** = **4 + 2 + 1**... *read + write + execute*
**6** = **4 + 2**... *read + write*[B]
5[/B] = **4 + 1**... *read +  execute*
**4 **= **4**... *read*
**3** = **2 + 1**... *write + execute*
**2** = **2**... *write*
**1** = **1**... *execute*

*See examples below: *

[html]
   7          6           5
 owner      group        world
 r+w+x       r+w          r+x
 4+2+1      4+2+0        4+0+1      =      765


   7            5          0
 owner        group      world
 r+w+x        r + x   
 4+2+1        4+0+1      0+0+0      =      750
[/html]

---

