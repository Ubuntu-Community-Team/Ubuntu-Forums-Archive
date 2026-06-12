---
title: "ssh remote computer file transfer"
date: 2013-08-22
forum: New to Ubuntu
---

### Post by KylePhys on 2013-08-22
Hi,

I am trying to use a cluster and logging in into it through ssh, i was just wondering how can i transfer files from my computer and vice versa? What directory path line should I use when logged in ssh session? 

Thanks.

---

### Post by papibe on 2013-08-22
Hi KylePhys.

You can't transfer files in a ssh interactive session, however you can transfer files using other command tools the would use ssh underneath.

Take a look at:
[LIST]
[*]scp
[*][sftp]("https://help.ubuntu.com/community/SSH/TransferFiles"), and
[*][rsync]("https://help.ubuntu.com/community/rsync")
[/LIST]
Does that help? Let us know if you have more questions.
Regards.

---

### Post by KylePhys on 2013-08-22
thanks a lot , just one clarification:

Supposed i logged in: ssh [email]user@....edu[/email], put my password. 

so i can put now: scp <file> [email]user@...edu[/email]:files ?

how should i write the path for <file>?

---

### Post by papibe on 2013-08-22
> **KylePhys said:**
> Supposed i logged in: ssh [email]user@....edu[/email], put my password. 
You don't have to create an interactive ssh session as a prerequisite.
> **KylePhys said:**
> so i can put now: scp <file> [email]user@...edu[/email]:files ?
If the username is the same in the local machine and the remote machine you can omit it:
```
scp localfile servername:remotefile
```
The files are basically the same as you would use on a cp command. Since ssh is use underneath, 'remotefile' would be located as you were reference it just as you were logged into an ssh interactive shell. In this case would end up just under your home directory.

Does that help?
Regards.

---

### Post by KylePhys on 2013-08-22
thanks a lot, it worked. ))

---

### Post by papibe on 2013-08-22
Glad it worked :D

Please mark this thread as SOLVED when you have the chance ([here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")'s how to do it).

Regards.

---

