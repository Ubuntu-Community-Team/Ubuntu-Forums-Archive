---
title: "execute local program into remote machine by ssh or anything ?"
date: 2007-12-28
forum: Programming Talk
---

### Post by mokkai on 2007-12-28
how to execute local program into remote machine by ssh or anything ?

suppose 
if i have 2 ubuntu  (u1,u2) computer
now i have a program name as "p"  in u1 .
i want to execute that "p" into u2 machine 
but i should not copy that "p" from u1 to u2.

any idea.

---

### Post by p_quarles on 2007-12-28
No. The program would need to be installed on the remote machine. The only way you could get around that would be to map the local application into the remote machine's command path -- and that would be *far* more work than simply copying the program over to the remote machine. 

If you can provide some details about what you're trying to accomplish, it might turn out that there are other solutions.

---

### Post by mokkai on 2007-12-28
actually i am a rails developer .in rails there are lot of new versions came last months
in my system i am using old version .If i upgrade it to new one then my old projects will not work properly. but i want to execute( migration tool in rails ) some part of my old project in new rails version

(but i must not install new rails version because old version will not work )..i installed new rails version in other ubuntu pc .so i want to run only migration tool from other PC ,then after that i can run remaining from my comp old rails .

and one more thing i want to tell ,those rails tools is not a single one program.
it is a package . so i can't run new migration tool in my old rails version..
actually rails have lots of tool (migration is one of them )

that is my problem..
any idea

---

### Post by p_quarles on 2007-12-28
Sorry, I have no clue about RoR. You might get better help if you request your thread be moved to the Programming sub-forum. You can do this by clicking on the "report" button on the first post, and asking a moderator to move the thread. Doing that improves the chances that this post will be seen by people who have solutions to this problem.

---

### Post by Sef on 2007-12-28
Moved to Programing Talk.

---

### Post by -Rick- on 2007-12-29
You can 'mount' a directory from 'u1' to 'u2' via sshfs ([http://fuse.sourceforge.net/sshfs.html](http://fuse.sourceforge.net/sshfs.html)). This way you can get access to any files from u1 in u2.

---

