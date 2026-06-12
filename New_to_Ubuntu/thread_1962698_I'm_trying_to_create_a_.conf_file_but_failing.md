---
title: "I'm trying to create a .conf file but failing"
date: 2012-04-21
forum: New to Ubuntu
---

### Post by TheBearNecessities on 2012-04-21
STRAIGHT TO THE POINT:  I'm trying to create an /etc/synergy.conf file with the command &#8220;**sudo vi /etc/synergy.conf**&#8221; but it's not working.  I type the above into my lubuntu LX Terminal and I get a series of this symbol # followed by **"etc/synergy.conf" [New File]**

What am i doing wrong?

Any help gratefully received.
:)


BACKGROUND:  I'm trying to use my linux laptop as a remote keyboard and mouse for my windows xp computer.

A programme called Synergy seems to be the way forward but i'm stuck at a very basic first step because I have no idea what i'm doing in linux.

(I'm trying to follow these instructions [http://www.mattcutts.com/blog/how-to-configure-synergy-in-six-steps/](http://www.mattcutts.com/blog/how-to-configure-synergy-in-six-steps/))

---

### Post by 23dornot23d on 2012-04-21
The article you have shown is quite old ....

To do that can you use a Remote Desktop ...... think that is all you need ....

[http://www.makeuseof.com/tag/ubuntu-remote-desktop-builtin-vnc-compatible-dead-easy/](http://www.makeuseof.com/tag/ubuntu-remote-desktop-builtin-vnc-compatible-dead-easy/)

---

### Post by TheBearNecessities on 2012-04-21
> **23dornot23d said:**
> The article you have shown is quite old ....

To do that can you use a Remote Desktop ...... think that is all you need ....

[http://www.makeuseof.com/tag/ubuntu-remote-desktop-builtin-vnc-compatible-dead-easy/](http://www.makeuseof.com/tag/ubuntu-remote-desktop-builtin-vnc-compatible-dead-easy/)

well, i've got remote desktop and i've got vnc but neither of them are really doing what i want (one of them doesnt show the whole screen on my laptop screen, and one of them doesn't show the PC screen; the pc screen goes blank when you are controlling it).  So I want to try synergy.

---

### Post by 23dornot23d on 2012-04-21
I cannot try it at the moment as I am on on single screen and one computer ..... if I get
time tommorow - will have a go at setting something up ...... but meanwhile I hope someone
that has got this running can help you out here ......

---

### Post by lisati on 2012-04-21
> **TheBearNecessities said:**
> STRAIGHT TO THE POINT:  I'm trying to create an /etc/synergy.conf file with the command “**sudo vi /etc/synergy.conf**” but it's not working.  I type the above into my lubuntu LX Terminal and I get a series of this symbol # followed by **"ect/synergy.conf" [New File]**

What am i doing wrong?

Any help gratefully received.
:)


BACKGROUND:  I'm trying to use my linux laptop as a remote keyboard and mouse for my windows xp computer.

A programme called Synergy seems to be the way forward but i'm stuck at a very basic first step because I have no idea what i'm doing in linux.

(I'm trying to follow these instructions [http://www.mattcutts.com/blog/how-to-configure-synergy-in-six-steps/](http://www.mattcutts.com/blog/how-to-configure-synergy-in-six-steps/))
 "ect/synergy.conf" looks like a typo. It should be "/etc/synergy.conf"

---

### Post by timcredible on 2012-04-21
vi is fine if you know how to use it, but most people don't like non-gui editors anymore, try
```

sudo leafpad /etc/synergy.conf

```
instead.

---

### Post by TheBearNecessities on 2012-04-21
> **lisati said:**
> "ect/synergy.conf" looks like a typo. It should be "/etc/synergy.conf"

well spotted thanks. it was a typo in my forum post.  but i didnt do a typo when trying to create the file so thats not the problem.

ive edited my post to correct the typo now.

---

### Post by TheBearNecessities on 2012-04-21
> **timcredible said:**
> vi is fine if you know how to use it, but most people don't like non-gui editors anymore, try
```

sudo leafpad /etc/synergy.conf

```
instead.

And...we have a winner!

That worked.   i have now been able to create my conf file! whoop.  thanks.

I also have managed to get synergy working.  so now i can type stuff onto my laptop keyboard and it appears on-screen on my Home Theatre PC (HTPC).  So i've just saved myself £30 on buying a remote keyboard & mouse.  slow clap for synergy and for the helpful people of this forum.

---

