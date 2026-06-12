---
title: "SSH - Explanation for newbies"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by Lorelei- on 2008-10-03
Hello all,

A term I see banded about on here a lot is SSH but all the explanations of what this is and what it does and how to use it seem to be written in a very convoluted manner. So I was wondering if anyone on here could answer these questions in plain English and explain how relevant it is (if at all) to a newbie?

Thanks

---

### Post by eolson on 2008-10-03
Unless your using rlogin or telnet it's not an issue.

---

### Post by handydan918 on 2008-10-03
> **Lorelei- said:**
> Hello all,

A term I see banded about on here a lot is SSH but all the explanations of what this is and what it does and how to use it seem to be written in a very convoluted manner. So I was wondering if anyone on here could answer these questions in plain English and explain how relevant it is (if at all) to a newbie?

Thanks
What questions did you have in mind?

---

### Post by Paul41 on 2008-10-03
SSH is a way to remotely connect to another computer.

---

### Post by semitone36 on 2008-10-03
Here you go! :D
[http://wiki.archlinux.org/index.php/SSH](http://wiki.archlinux.org/index.php/SSH)

---

### Post by Lorelei- on 2008-10-03
Thanks for the response. I was asking more out of curiousity than anything at the moment because if I ever did want to use it (and therefore look into the ins and outs of how to do so properly) most of the information I've found out there would only create more confusion rather than less :)

---

### Post by Dr Small on 2008-10-03
Don't let it intimidate you. It's really rather simple, than complex. I use it every day between scp (secure copy) and just logging into my server from a terminal with SSH.

Basically, if a system is running OpenSSH-Server (the listening server, for connections), you can SSH into that system from another system at a remote location. (Of course, you must have a username/password on this remote system, to login.)

Secure, means that all of your commands, data, passwords, and entire connection is encrypted in a tunnel to the SSH server which then decrypts it and reads it as raw data. Basically, to SSH to another computer, you would run:
```
ssh remoteuser@remotehost
```

You would then be prompted to enter "remoteuser"'s password, and then you will be given a prompt at that system. From there, you can execute commands just like you were sitting at that system with a terminal open. You can also forward X applications (graphical applications) through your SSH tunnel and have them workable on your monitor. (Notice, it is slow across the internet.)

Dr Small

---

