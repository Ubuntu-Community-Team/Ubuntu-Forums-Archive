---
title: "[SOLVED] Simple BASH query"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by rxtx on 2008-06-18
Hi there,

I want to copy default bash properties to the mythtv user. I've copied ~/.bashrc and ~/.profile, but this doesn't seem to give the same terminal prefixes and bash completion.

Can anyone help with what is such a surely simple problem? Thanks.

---

### Post by hyper_ch on 2008-06-18
hmmm, it should.... hmmm....

are the permissions right of the files? did you check whether they were actually copied.... is the content of the files right?

---

### Post by rxtx on 2008-06-18
Yeah. Well, I have tried both copy and overwrite as well as physically editing the files with nano and pasting the contents of MY .bashrc and .profile into them.

---

### Post by hyper_ch on 2008-06-18
and then you did log in as mythtv user?

---

### Post by rxtx on 2008-06-18
Yes, the machine logs in automatically as the mythtv user on boot.

There can't be anything in /etc overiding the user settings as the prompt and bash completion are fine for the default user. :(

---

### Post by hyper_ch on 2008-06-18
no clue

---

### Post by pedro_orange on 2008-06-18
It may not be using the ones in your home/username folder. It could infact be using the ones in /etc/profile

---

### Post by rxtx on 2008-06-18
> **pedro_orange said:**
> It may not be using the ones in your home/username folder. It could infact be using the ones in /etc/profile

Isn't that a system-wide file though? Surely if mythtv was using that then the default user would too?

If this isn't the case, how do I point the mythtv user's shell to the configuration that I want it to use?

---

### Post by rxtx on 2008-07-10
I found the solution for this. My bad, bash was not set as the default shell.

For anybody else who may have the same issue and has ended up bashing (no pun intended!) their head against a brick wall. Here is how to change youur default shell.

At a terminal, type:

```
which bash
```

this should echo the location of bash which is typically /bin/bash, but it can't hurt to check.

Next up, use chsh to set the default shell:

```
chsh -s /bin/bash username
```

where "/bin/bash" is your path to bash and "username" is the name of the user that you wish to change the default shell for.

This is a simple way to update /etc/passwd which can also be done manually by editing it with vi/nano etc.

Hope this helps.

---

