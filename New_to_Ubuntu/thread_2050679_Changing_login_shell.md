---
title: "Changing login shell"
date: 2012-08-31
forum: New to Ubuntu
---

### Post by grove001 on 2012-08-31
How can I change my default (login) shell to /usr/bin/ksh from /bin/bash?  Using chsh rejects ksh as a "valid" shell.  I am running Ubuntu 12.04 and ksh installed on the machine satisfactorily.  I can enter ksh by typing "ksh" at a bash prompt, but I want to open directly to ksh.

Thanks in advance for the help.

---

### Post by codemaniac on 2012-08-31
> **grove001 said:**
> How can I change my default (login) shell to /usr/bin/ksh from /bin/bash?  Using chsh rejects ksh as a "valid" shell.  I am running Ubuntu 12.04 and ksh installed on the machine satisfactorily.  I can enter ksh by typing "ksh" at a bash prompt, but I want to open directly to ksh.

Thanks in advance for the help.

checkout the ksh absolute path in your system.

```
grep ksh /etc/shells
```

Now change your shell .
```
sudo chsh -s /bin/ksh your_username
```

Now, logout and login back again to use ksh as the default shell.

---

### Post by Lars Noodén on 2012-08-31
I notice in 12.04 that /bin/ksh is missing from /etc/shells.  It needs to be added.  

That said, using [usermod](http://manpages.ubuntu.com/manpages/precise/en/man8/usermod.8.html) didn't complain when I changed my shell to ksh even though it was not in /etc/shells.

---

### Post by codemaniac on 2012-08-31
> **Lars Noodén said:**
> I notice in 12.04 that /bin/ksh is missing from /etc/shells.  It needs to be added.  

That said, using [usermod](http://manpages.ubuntu.com/manpages/precise/en/man8/usermod.8.html) didn't complain when I changed my shell to ksh even though it was not in /etc/shells.

You are correct Lars Noodén , i cannot find it listed on my Ubuntu server 12.04 's /etc/shells .

still ```
which ksh
``` returns it is /usr/bin/ksh .

---

### Post by grove001 on 2012-08-31
Thanks for all the good advice.  I got it the way I want it now.

Regards,
Will Grove

---

### Post by codemaniac on 2012-09-01
You are welcome and please dont forget to mark the thread as solved to help the next guy .:)

---

### Post by Bachstelze on 2012-09-01
> **codemaniac said:**
> 
Now change your shell .
```
sudo chsh -s /bin/ksh your_username
```


sudo is not needed if you are changing your own shell. And of course the rule about sudo is that if it is not needed, you don't use it. :)

---

### Post by codemaniac on 2012-09-01
> **Bachstelze said:**
> sudo is not needed if you are changing your own shell. And of course the rule about sudo is that if it is not needed, you don't use it. :)

The OP has not explicitly mentioned if he is about to change his own shell or some other users .So in this situation ,the intention was to come up with something that works in both the scenario .

---

### Post by Bachstelze on 2012-09-01
> **codemaniac said:**
> The OP has not explicitly mentioned if he is about to change his own shell or some other users.

Yes, he has.

> **grove001 said:**
> How can I change **my** default (login) shell to /usr/bin/ksh from /bin/bash?

Besides, it's extremely rude to change another user's shell.

---

### Post by codemaniac on 2012-09-01
> **Bachstelze said:**
> 
Besides, it's extremely rude to change another user's shell.

Cummon , there are ample situations when a user is not enough privileged to change his shell 
(for security or other reasons), he needs to request a admin user to change his shell .

---

