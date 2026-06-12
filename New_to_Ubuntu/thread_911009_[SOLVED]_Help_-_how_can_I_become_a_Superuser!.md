---
title: "[SOLVED] Help - how can I become a Superuser!"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by jmacg on 2008-09-05
I recently put Ubuntu on my old Dell P4-1500 desktop and had problems as soon as I tried to look at a Flash movie. It told me I needed to install a plugin. That plugin was Flash. I told it to go ahead, but got the following message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
---------------------

When I tried to run 'dpkg --configure -a' in the Terminal I got:

jmacg@jmacg-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
jmacg@jmacg-desktop:~$ 

What is this superuser privilege? How do I get such a privilege? Typing in my normal password doesn't work.

That was part of the problem, but the message also said: "E: _cache->open() failed, please report."

Do I have to worry about this statement as long as I can sort out the "dpkg --configure -a" issue? And who would I report it to anyway?

---

### Post by iaculallad on 2008-09-05
Just add the sudo to your command to be in a temporary "superuser" mode:

```
sudo dpkg --configure -a
```

and input your own password.

---

### Post by nothingspecial on 2008-09-05
You need to sudo it

```
 sudo dpkg --configure -a
```

---

### Post by forger on 2008-09-05
'superuser' is a user that has administrator privileges, i.e. the 'root' or 'admin'. In Ubuntu, by default the first user is always set with administrator privileges.

You can execute:
```
sudo dpkg --configure -a
```

It will ask you for your password (your own username password, with which you logged in).
Note: It will **not show** anything like "asterisks" instead of the characters you type, but you type in your password and press enter.

If the password is correctly typed, the command will be executed :)

---

### Post by Saint Angeles on 2008-09-05
yes... all three of these replies are correct.

but you know what?
to me, you're ALREADY super!!


( i meant this as a friendly joke. i worded it as politely as i could. i hope i didn't offend anybody. i wish i could call EVERYBODY super but it didn't work into the joke very well. maybe i will next time!)

---

### Post by jmacg on 2008-09-05
> **jmacg said:**
> I recently put Ubuntu on my old Dell P4-1500 desktop and had problems as soon as I tried to look at a Flash movie. It told me I needed to install a plugin. That plugin was Flash. I told it to go ahead, but got the following message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
---------------------

When I tried to run 'dpkg --configure -a' in the Terminal I got:

jmacg@jmacg-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
jmacg@jmacg-desktop:~$ 

What is this superuser privilege? How do I get such a privilege? Typing in my normal password doesn't work.

That was part of the problem, but the message also said: "E: _cache->open() failed, please report."

Do I have to worry about this statement as long as I can sort out the "dpkg --configure -a" issue? And who would I report it to anyway?

Many thanks to all of you who told me to type 'sudo' first. It did the trick. As well as allowing me to sort out the problem I had at the time, it's also fixed whatever was making this Ubuntu install run extremely slowly. I will persevere now - I was on the point of reverting to XP Home.

---

### Post by iaculallad on 2008-09-05
> **jmacg said:**
> Many thanks to all of you who told me to type 'sudo' first. It did the trick. As well as allowing me to sort out the problem I had at the time, it's also fixed whatever was making this Ubuntu install run extremely slowly. I will persevere now - I was on the point of reverting to XP Home.

Just don't try giving up. Remember that the command line is always your friend, and not something to be afraid of. Go Ubuntu.

---

### Post by steveneddy on 2008-09-05
> **saint angeles said:**
> yes... All three of these replies are correct.

But you know what?
To me, you're already super!!

:lolflag:

---

