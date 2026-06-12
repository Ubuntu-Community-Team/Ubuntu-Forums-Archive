---
title: "cannot execute binary file from remote"
date: 2016-10-11
forum: New to Ubuntu
---

### Post by jyarce on 2016-10-11
I have a script to run earthquake locations, but is taking a while in my laptop, I requested access to my institution to use a faster computer.

I'm logged in by ssh and my bashrc profile is in the same way as my own profile in my laptop, however I receive the following message:

[jeya8456@login02 All]$ ../Bayesloc_backup/BayesLocRelease/bayesloc/bin/bayesloc bayesloc.cfg 
-bash: ../Bayesloc_backup/BayesLocRelease/bayesloc/bin/bayesloc: cannot execute binary file

I also checked permissions and everything looks fine. Also checked uname -m and the ssh processor is the same as my laptop

Thanks for your help

---

### Post by TheFu on 2016-10-11
Not that I don't believe you, but ... er ... I don't believe you. Please post the cmds and output for 
```
ls -al  ../Bayesloc_backup/BayesLocRelease/bayesloc/bin/bayesloc
file  ../Bayesloc_backup/BayesLocRelease/bayesloc/bin/bayesloc
id
uname -a

```

Please use "code tags" so things line up. Like I did above.
Where is the bayesloc.cfg located? 

I really find the ../ at the beginning to be suspicious.
Also, might make sense to swap in the default .profile and .bashrc files for the system. Often we edit things and break others.

---

### Post by SeijiSensei on 2016-10-12
Is the program text-based, or does it use a GUI and require X?  If the latter, you need to use "ssh -X" to connect to the server.  When you run the remote program, the output will display on the client machine.

You also need to grant the remote server rights to write onto your machine with the command "xhost servername".  See "man xhost" for details.

---

