---
title: "Bash script help"
date: 2007-09-02
forum: Programming Talk
---

### Post by GiantRobot on 2007-09-02
Hey, so basically at my university, to use the internet we need to authenticate ourselves via ssh.  Opening a shell every time that I want to connect to the internet is getting quite annoying so I'm trying to create a bash script to do it automatically.  Kind of like a one click thing.

So when I log in it usually goes like this:
ssh userid@10.0.0.1
Prompts for password

And I was just wondering if there was an easy way to automate this with a simple bash script?

I'm pretty much a complete newbie at this kind of thing so this is all I have so far:

```
#!/bin/bash
echo Logging in...
ssh userid@10.0.0.1
echo Logged in!
```

I'm not sure how to get it to automatically enter my password.

Anyways, help would be much appreciated.  :)

-GiantRobot

---

### Post by boopyg on 2007-09-02
-

---

### Post by Genecks on 2007-09-02
1. install xmacro

sudo apt-get install xmacro

2. create a macro to automate the password entering
2b. launch the macro from the batch script

3. create a menubar "application launcher" that directs to the script

done.

i recommend xnee, though, for this kind of thing. You'll be using cnee, which is part of xnee.

xnee is not xmacro.

xmacro tend to leave a trail of info inside the terminal window it launches a macro from. You need two terminal boxes in order to insert info into another terminal box.

box 1: launch macro and state what the macro is doing
box 2: macro accesses this box and strings the ssh commands


* this is one method but probably not thee best method.

---

### Post by nanotube on 2007-09-03
easiest way is probably to create a public/private keypair, and use that auth method instead of the password. :)
man ssh, or google for it, if you need info.

---

### Post by dwhitney67 on 2007-09-03
> **nanotube said:**
> easiest way is probably to create a public/private keypair, and use that auth method instead of the password. :)
man ssh, or google for it, if you need info.

That's right.  Here's a [site]("http://www.hurring.com/scott/howto/cvs_ssh/") with good reference material to read.

---

