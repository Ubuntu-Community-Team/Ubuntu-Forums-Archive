---
title: "e-mail my computer"
date: 2006-12-19
forum: Programming Talk
---

### Post by cornish on 2006-12-19
hi

I want to try something different, I want to send an email to my computer which contains bash commands (script) for the computer to then execute and then email me back once its completed?

Any thoughts on where I would start?

Do you need more information

An example would be

from:me
to:myPc
subject: ****RUN

Message: wget [http://www.mirrorservice.org/sites/releases.ubuntu.com/edgy/ubuntu-6.10-desktop-i386.iso](http://www.mirrorservice.org/sites/releases.ubuntu.com/edgy/ubuntu-6.10-desktop-i386.iso)

once completed it would be handy if it replied back

---

### Post by hod139 on 2006-12-19
To be honest, this sounds like a bad idea.  Why would you want to purposefully make your system less secure?  An email reader should never automatically start executing anything, look at all the trouble that has caused Microsoft with Outlook.  This is why tools such as SSH have been created.  It allows you to securely authenticate yourself with the remote system before executing anything.  I really would suggest not pursuing this idea, allow execution of code from an untrusted source is asking for trouble.

---

### Post by lnostdal on 2006-12-19
> **cornish said:**
> hi

I want to try something different, I want to send an email to my computer which contains bash commands (script) for the computer to then execute and then email me back once its completed?

Any thoughts on where I would start?

Do you need more information

An example would be

from:me
to:myPc
subject: ****RUN

Message: wget [http://www.mirrorservice.org/sites/releases.ubuntu.com/edgy/ubuntu-6.10-desktop-i386.iso](http://www.mirrorservice.org/sites/releases.ubuntu.com/edgy/ubuntu-6.10-desktop-i386.iso)

once completed it would be handy if it replied back


```

lars@ibmr52:~$ ssh lars@nostdal.org wget http://ubuntuforums.org/images/uf/buttons/reply.gif
--16:57:21--  http://ubuntuforums.org/images/uf/buttons/reply.gif
           => `reply.gif'
Resolving ubuntuforums.org... 82.211.81.186
Connecting to ubuntuforums.org|82.211.81.186|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 467 [image/gif]

    0K                                                       100%   27.84 MB/s

16:57:22 (27.84 MB/s) - `reply.gif' saved [467/467]

lars@ibmr52:~$ ssh lars@nostdal.org ls
%backup%~
BACKUP
dina-backup-description.lisp
dina-backup-description.lisp~
getenv.lisp
getenv.lisp~
mounts
notes.txt
programming
public_html
reply.gif <------------- and it's downloaded at the remote host
rmfasl
symbolicweb-conf.lisp
lars@ibmr52:~$ 

```

..note that i do not have to type in passwords as the public key of the laptop i have here is added to the authenticated keys at the server at nostdal.org .. this is the "correct" way to do things like this :)

---

### Post by thomasaaron on 2006-12-19
1. Write an email reader in python that runs every so often via anacron and stores email attachments in a certain location.
2. As a secondary function, the program could occasionally check that location for anything new. If it finds something new, it copies it to another location, makes it executable with the bash chmod command, and runs it. If the attachment is a bash script, it will run. If it is not, Python will call an exception, which you can use to trigger the deletion of the copy. The original attachment will remain untouched in its primary location.

Let me know how it works out. It's probably not a good idea security-wise. But experimenting is fun.

Best,
Tom

---

