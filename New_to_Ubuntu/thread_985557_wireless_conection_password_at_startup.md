---
title: "wireless conection password at startup"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by tochtli on 2008-11-17
Hello everyone i hope that life treated well to all.

Actually this is not a problem, its just something that i want to skip every time i start my pc.
After install ubuntu 8.10 (before i was using 8.04) something that i liked vey much was that automatically can start the sesion, no more that not annoying, but yes a little reppetitive task, and it was all ok, now the only thing is that everytime that i start the sesion, because i'm conected to the internet and to other machines under wireless every time i start it ask me about the password to connect to the net. I want to do something to make that the computer do this task automatically.
I hope that you could help me with this thing, it has not alot of importance but yet, im interested in solve this thing.
So, every help is valuable, thanks in advance, and sorry for the bad english.
seeya.

---

### Post by stoogiebuncho on 2008-11-17
Does your computer log into your account automatically when you start it up, or do you have to enter your user name and password?

Also, do you know if your user password is the same as your keyring password?

---

### Post by tochtli on 2008-11-17
> **stoogiebuncho said:**
> Does your computer log into your account automatically when you start it up, or do you have to enter your user name and password?

Also, do you know if your user password is the same as your keyring password?

Hi there thanks for helping me.
My computer automatically make the process (username: tochtli and password: XXXXXXXX) and charges the session, but then ask me that some miniapplication (aplication that menage the networks) requires the password, the same password that the session or the command sudo requires (i dont know if i'm explaining).

resuming the answers to make it clearer.
Yes, automatically log-in to the session.
And Yes, the user password is the same as the keyring password.
seeya later and thanks again.

---

### Post by rossjman1 on 2008-11-17
You can manage your keyring passwords through Applications > Accessories > Paswords & Encryption Keys

I know only one way to do it, but I can't tell you because I'll get modded.

---

### Post by Keen101 on 2008-11-17
I've heard of something called the "sudoers file", but i don't know much about it. Basically what i think it is a file that you can set to automatically have root access.

In theory i suppose you could add the keyring manager to this file, and never be bothered by a password again. But, like i said... i don't realy know anything about it.

---

### Post by sirjoebob on 2008-11-17
The sudoers file does not deal with the keyring and is also not to be in the "absolute beginner talk" forum. There is a method of doiing this. I found it here:
[http://ge.ubuntuforums.com/showthread.php?t=951315]("http://ge.ubuntuforums.com/showthread.php?t=951315")

I must warn though that it will store the passwords unencrypted and I would not recommend doing this unless you are aware of the risks.

---

