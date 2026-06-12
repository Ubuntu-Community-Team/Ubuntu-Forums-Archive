---
title: "where are sftp commands located"
date: 2011-04-16
forum: Programming Talk
---

### Post by flyingsliverfin on 2011-04-16
I want to add my own help command to the set of commands that you can use interactively when in sftp. I added one as a help when a person used ssh instead of sftp by accident by simply adding a little bash script in /usr/bin directory. Is there something similar I can do for sftp?

---

### Post by slavik on 2011-04-17
no

edit: wait, what? what kind of help did you add for 'ssh'? ssh open a connection to a remote system and starts a shell on it ... there is no "ssh help" except for the man page which documents arguments and other info related to ssh.

---

### Post by flyingsliverfin on 2011-06-11
Oh sorry i haven't checked this for a while;
when i set up my server i was expecting some of my friends to use it as storage and i also expected them to get lost. I just added the optional banner message with the ssh login to remind them there was a command called sshHELPme, which was a script in /usr/bin that just said 'echo thehelp'. 

Just realized i wont be needing it anyway; thanks though :)

---

### Post by conradin on 2011-06-11
too bad, because i know for a fact its possible to change all sorts of things in (s)ftp, like the welcome msg, insert a banner or mod the commands if you really feel like it.

---

### Post by flyingsliverfin on 2011-06-11
Hey it would be fun to know anyway :)

---

