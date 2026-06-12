---
title: "How to unlock my files to modify them"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by dragon2knight on 2008-05-04
Hi all.I installed 8.04 and got everything going smoothly,and then uploaded my files(docs,pics,etc)into it.The problem is that after they uploaded,they got a little lock symbol on them,and I cant do a thing with them.How do I unlock them permanently?I like to add to them directly,without having to start a new folder,and I cant as it is now.Thanks for the help,Mike.:)

---

### Post by tamoneya on 2008-05-04
```
sudo chown <username> -R /home/<username>
```
Currently they are owned by root so they appear locked.

---

### Post by Oldsoldier2003 on 2008-05-04
> **dragon2knight said:**
> Hi all.I installed 8.04 and got everything going smoothly,and then uploaded my files(docs,pics,etc)into it.The problem is that after they uploaded,they got a little lock symbol on them,and I cant do a thing with them.How do I unlock them permanently?I like to add to them directly,without having to start a new folder,and I cant as it is now.Thanks for the help,Mike.:)

```
sudo chown -hR yourusername:yourusername ~
```

---

### Post by dragon2knight on 2008-05-04
Ok,I tried that,and replaced username with my username,and got this:
"bash: syntax error near unexpected token `newline'"

---

### Post by dragon2knight on 2008-05-04
Tried old soldiers and got this:
"chown: cannot access `/home/username/.gvfs': Permission denied"
I replaced my name with "username" above.

---

### Post by tamoneya on 2008-05-04
try placing the -R before the username.  Sorry```
sudo chown -R <username> /home/username
```

---

### Post by Sinkingships7 on 2008-05-04
You are removing the < and > symbols, right?

---

### Post by PeterJS on 2008-05-04
> **dragon2knight said:**
> Tried old soldiers and got this:
"chown: cannot access `/home/username/.gvfs': Permission denied"
I replaced my name with "username" above.

GVFS is like that, it's kinda funky when it comes to permissions*. On the other files that are locked who are they owned by and what permissions do they have currently? You can right click on them and select properties and there is a tab for permissions that should be informative.

*It's a pseudo-file system where gvfs automatically mounts things on remote machines.

---

### Post by dragon2knight on 2008-05-04
Lets try again...I get this:
"bash: username: No such file or directory"
I used my username,of course,but it dosent work.

---

### Post by dragon2knight on 2008-05-04
No I didnt remoce the <> symbols,I forgot,rusty on this stuff...thanks.Ill try again.

---

### Post by |{urse on 2008-05-04
.

---

### Post by |{urse on 2008-05-04
oh lol dint see ur last post
:lolflag:

---

### Post by dragon2knight on 2008-05-04
I still get permission denied,tricky little bugger.Im finding my permissions as we speak,BRB,thanks.

---

### Post by tamoneya on 2008-05-04
```
ls -la ~
```

---

### Post by dragon2knight on 2008-05-04
Thanks,PeterJS,I looked and changed my permissions,and I can now access them,didnt know I could do that! Learning all the time!! Thanks again everyone for the help,your the best!:)

---

### Post by dvader on 2008-05-04
""sudo chown <username> -R /home/<username>""

Try a single dir/folder , like /home/Folder name

You may have to do each folder one at a time , time consuming... if there are sub folders the will have to be done as well if the "-R " switch does not work

Dvader

---

