---
title: "Logging in as root"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by NotLikingIt on 2008-05-29
Well..I just installed Ubuntu 8.0 today, and I'm having lots of problems

I really liked how Ubuntu detected my wireless connection immediately, no other Linux has been able to do that for me yet

but here are the reasons that's keeping me away from liking it

The main reason why I like Linux is the root user setting

so when I found out that Ubuntu gives the first user created as much power as root, I did not quite like it, so I disabled the "administrate the system" privilege for me. Then the problem appeared.

As I logged out and logged back in, I discovered that, the package installer (whatever it's called) is no longer there, I tried using su in the terminal, but that does not seem to have any effect on GNOME. So I tried to log in as root only to find out that I cannot. So I googled around, people say you can go to the Administration ->login something to fix it...but I'm not seeing it (I believe I have seen it before I got rid of my admin privilege)

Oh btw, I did set a password for root user

Next thing is with the language,
I tried to install Chinese input on the system, but it simply won't work, the only language available under SCIM and that syn something package manager is English. What can I do to fix that?

oh, and one more thing, is it possible to exit GNOME and go into the command prompt? I would really love to use that, it simply looks so much cooler to use vi in command prompt environment...well, to me anyways.


So, any ideas?

---

### Post by Joeb454 on 2008-05-29
To get to a terminal only environment, use Ctrl+Alt+F1 :)

And you may need to boot into recovery mode if you cannot use sudo anymore =/

---

### Post by Ripfox on 2008-05-29
ctrl+alt+F1 kicks you to a prompt, tty1 I believe.

---

### Post by aysiu on 2008-05-29
> **NotLikingIt said:**
> 
so when I found out that Ubuntu gives the first user created as much power as root, I did not quite like it, so I disabled the "administrate the system" privilege for me. Then the problem appeared. The first user is not the root user.

The first user belongs in the *admin* group, which allows her to temporarily escalate to root privileges for certain tasks after a password authentication.

You need to add yourself back as an admin:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by NotLikingIt on 2008-05-29
lol, daaamn, I tried like ctrl+alt+F12, F3, F6, and a few others, just not F1 :(

and thanks for the link aysiu, that's something I was trying to do

---

### Post by Joeb454 on 2008-05-29
Ctrl+Alt+F1-6 do take you to tty's 1-6 I believe :)

Ctrl+Alt+F7 takes you back to the X-Session (GUI)

---

### Post by NotLikingIt on 2008-05-29
> **Joeb454 said:**
> Ctrl+Alt+F1-6 do take you to tty's 1-6 I believe :)

Ctrl+Alt+F7 takes you back to the X-Session (GUI)

Lol, nice, I was just gonna ask which one takes me back to the one I was working on =p

but as to F1-6...what happened to me is when I pressed those, they opened up GUI again, in these sessions, gonna try F1 now

---

### Post by Joeb454 on 2008-05-29
Don't forget to hit Ctrl+Alt at the same time as the F key! :p

---

