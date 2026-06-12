---
title: "Put only once password to execute a script"
date: 2017-09-15
forum: New to Ubuntu
---

### Post by sed_faster on 2017-09-15
Hello,

I need copy a big amount data between destops. For this tasks I am thinking use the scp program. On this task I will copy at least five directory which are on different disks. Therefore, on computer 1 I have two disks, where are five directors and on computer 2 I have an only disk. My question is: When I executer the command scp between different hosts I need write the user and password to able this process. But, if the first directory take a long time to execute, when passed the second directory I need put again password to able this task. But, on this time I won't be on pc. What can I do to execute various task which sudo and put only once password on script?

Thanks

---

### Post by TheFu on 2017-09-15
No. Use **rsync**.  rsync will use ssh-based authentication.

Learn about ssh-keys.  Use them.
Learn about **ssh-copy-id** to push the public 
Learn about the ~/.ssh/config file. Use it. Easy to change userids, ports, even keys, for the different connections.  

There are manpages for each of these things.

All ssh/scp/sftp/sshfs/rsync ... anything that uses libssh will honor those configs and keys.

As for timeout stuff with accessing ssh-keys, just setup an **ssh-agent**. ssh-agent is kinda like gpg-agent, if that helps.  Then you control how quickly or not the password revalidation is needed.  It is also possible to have an ssh-key without any passphrase, but this should only be used for things that run batch, under a different, non-login, userid.

---

