---
title: "Set ownership recursively?"
date: 2012-05-03
forum: New to Ubuntu
---

### Post by bornagainpenguin on 2012-05-03
I have an XBMC profile I copied over to a shared folder from my laptop (running Lucid 10.04) to my parent's desktop (also running Lucid 10.04) and in the copying everything lost its ownership settings despite the fact that I am the same user on both computers.  How can I set read and write permissions and ownership back to my user account on the copy I made to the desktop?

Sorry for asking such a noob question, but I'm having a brainfart and cannot make heads or tails of the directions I tried googling.

Thanks in advance for any help received.

--bornagainpenguin

---

### Post by sandyd on 2012-05-03
> **bornagainpenguin said:**
> I have an XBMC profile I copied over to a shared folder from my laptop (running Lucid 10.04) to my parent's desktop (also running Lucid 10.04) and in the copying everything lost its ownership settings despite the fact that I am the same user on both computers.  How can I set read and write permissions and ownership back to my user account on the copy I made to the desktop?

Sorry for asking such a noob question, but I'm having a brainfart and cannot make heads or tails of the directions I tried googling.

Thanks in advance for any help received.

--bornagainpenguin
Perms:
```
chmod xxx **-R** /path/to/directory

```

Owner:
```
chown **user:group -R** /path/to/directory
```
Replace user:group with your user and group. Replace xxx with the perm levels.

The -R flag controls recursiveness.

---

### Post by nothingspecial on 2012-05-03
It is the uid/gid that is important for permissions.

So if you are user bob with uid 1000 on your computer but user bob with uid 1003 on your parents then the permissions will not work.

---

### Post by nothingspecial on 2012-05-03
> **sandyd said:**
> No PMs. No exceptions.

/offtopic Hiya sandyd :)

---

### Post by bornagainpenguin on 2012-05-03
> **sandyd said:**
> Perms:
```
chmod xxx **-R** /path/to/directory

```

That results in this:

```
bornagainpenguin@Optiplex:~/Public$ sudo chmod xxx -R /home/bornagainpenguin/Public/XBMC-DDC
[sudo] password for bornagainpenguin: 
chmod: invalid mode: `xxx'
Try `chmod --help' for more information.
```



> **sandyd said:**
> Owner:
```
chown **user:group -R** /path/to/directory
```
Replace user:group with your user and group. Replace xxx with the perm levels.

The -R flag controls recursiveness.

This results in a wall of text saying operation not permitted.

Did I do something wrong when I copied over the commands?

--bornagainpenguin

**UPDATE:** Never mind, I kept googling to see if I could figure this out with a combination of what was posted and what I found in Google.  I somehow ended up deleting the files, so I'm going to try clearing some space on the laptop and see if archiving the files will preserve the permissions.  Whatever works, works--right?  Thanks any way.

PS: we really need a never mind option in thread tools that allows that an issue isn't solved but is no longer pending.

---

### Post by sandyd on 2012-05-03
> **bornagainpenguin said:**
> That results in this:

```
bornagainpenguin@Optiplex:~/Public$ sudo chmod xxx -R /home/bornagainpenguin/Public/XBMC-DDC
[sudo] password for bornagainpenguin: 
chmod: invalid mode: `xxx'
Try `chmod --help' for more information.
```



This results in a wall of text saying operation not permitted.

Did I do something wrong when I copied over the commands?

--bornagainpenguin

**UPDATE:** Never mind, I kept googling to see if I could figure this out with a combination of what was posted and what I found in Google.  I somehow ended up deleting the files, so I'm going to try clearing some space on the laptop and see if archiving the files will preserve the permissions.  Whatever works, works--right?  Thanks any way.

PS: we really need a never mind option in thread tools that allows that an issue isn't solved but is no longer pending.
ya forgot to replace xxx with the permission codes.
i.e. 777, 744, 644, 444....

---

### Post by sandyd on 2012-05-03
> **nothingspecial said:**
> /offtopic Hiya sandyd :)
Hi to you too :)

---

