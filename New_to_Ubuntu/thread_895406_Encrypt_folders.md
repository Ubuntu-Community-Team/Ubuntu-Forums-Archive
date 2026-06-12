---
title: "Encrypt folders?"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by BluePlum on 2008-08-20
How do i encrypt a folder so it requires a password to open?

---

### Post by kirsis on 2008-08-20
This may be helpful: [http://ubuntuforums.org/showthread.php?t=829526](http://ubuntuforums.org/showthread.php?t=829526)

---

### Post by t0p on 2008-08-20
> **BluePlum said:**
> How do i encrypt a folder so it requires a password to open?

**Truecrypt** is a good encryption program.  Unfortunately it isn't in the repos, but you can get a .deb at [www.truecrypt.org]("http://www.truecrypt.org").

There is a command-line utility called **cfs** which *is* in the repos - install it with command:

```
sudo apt-get install cfs
```

---

### Post by BluePlum on 2008-08-21
I installed it, now how do i run it?

---

### Post by t0p on 2008-08-21
Okay, you need to check out the man pages for the commands **cmkdir**, **cattach** and **cdetach**.  But I can walk you through it now if you want.

First you need to create an encrypted directory with cmkdir command. It will ask for a key (pass phrase) which must be at least 16 characters long.  You type it in twice.

Example:

```
t0p@ubunty:~$ cmkdir lock
Key:
Again:
t0p@ubunty:~$
```

---

### Post by t0p on 2008-08-21
I'll quickly run through the rest of the instructions for encrypted directories with cfs...

You created an encrypted directory with the command cmkdir, right?  Let's say it's called lock and it's in your home directory, **~/lock**

Now, you want to put stuff in it.  So you have to **attach** a directory to it.  We do this like with the command **cattach**.  cfs will ask for the key - that's the passphrase you just made up.

```
t0p@ubunty:~$ cattach lock clock
Key:
t0p@ubunty:~$ 
```

Now, if you look in the **/crypt** directory, you'll find your attached directory, clock.

```
t0p@ubunty:~$ ls /crypt
clock

```

Get your secret files and put them in /crypt/clock

```
t0p@ubunty:~$ mv file /crypt/clock/
t0p@ubunty:~$ 
```

Risht, now you unattach the directories with the **cdetach** command.

```
t0p@ubunty:~$ cdetach clock
t0p@ubunty:~$ 
```

Now it's detached, the file /crypt/clock has vanished!  Just leaving ~/lock, which contains your file in an encrypted form.

```
t0p@ubunty:~$ ls lock
a6b99285c8385ef3
t0p@ubunty:~$ 

```

---

### Post by t0p on 2008-08-21
3rd and final part of this little cfs walk-through :)

When you want to access your secret file, or if you want to put more stuff in the encrypted directory, you need to attach it again.

```
t0p@ubunty:~$ cattach lock stock
Key:
t0p@ubunty:~$ ls /crypt/stock
file
t0p@ubunty:~$ 
```

You must always remember to detach the directory when you finish to ensure no one can get at it.

```
t0p@ubunty:~$ ls /crypt
stock
t0p@ubunty:~$ cdetach stock
t0p@ubunty:~$ ls /crypt
t0p@ubunty:~$ 

```

So, that's how to create an encrypted directory with cfs.

---

### Post by hyper_ch on 2008-08-21
just keep in mind, that fragments and copies of the files you keep in there can also be found in other parts of the system.

---

### Post by t0p on 2008-08-21
> **hyper_ch said:**
> just keep in mind, that fragments and copies of the files you keep in there can also be found in other parts of the system.

I believe that if you do all the above in one of the consoles Ctrl-Alt F1-F6, the only place you might find copies is in the swap.  cfs was designed by Matt Blaze, who's pretty hot on security issues.

---

### Post by BluePlum on 2008-08-21
> **t0p said:**
> I believe that if you do all the above in one of the consoles Ctrl-Alt F1-F6, the only place you might find copies is in the swap.  cfs was designed by Matt Blaze, who's pretty hot on security issues.


Ill do all of this now :P, two thanks for you!

---

