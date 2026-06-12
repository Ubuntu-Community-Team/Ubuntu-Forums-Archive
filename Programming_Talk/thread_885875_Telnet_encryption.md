---
title: "Telnet encryption"
date: 2008-08-10
forum: Programming Talk
---

### Post by Sydius on 2008-08-10
I've been trying to make a simple MUD, just for practice and fun.  I haven't gotten past the (non-blocking/multi-client) echo server stage because I started research the telnet protocol.  I noticed it supports encryption (Wikipedia says it even supports TLS), and want to implement that in my echo (telnet/MUD) server, but I can't figure out how. I can't even find a telnet client that TLS support.

If TLS is too hard (I thought about using GnuTLS, if it works with a telnet client that supports TLS (if I found one)), then I'm willing to use some other form of encryption that telnet supports, but again, I can't figure out how.

Any advice?

---

### Post by CptPicard on 2008-08-10
How about using **ssh** with some kind of tunneling to your server's port, or something similar?

---

### Post by Sydius on 2008-08-10
> **CptPicard said:**
> How about using **ssh** with some kind of tunneling to your server's port, or something similar?

I thought about that, but then every player would have to have an account, right? I'm not sure how I could still make the MUD in charge of user accounts and do it that way.  Is it possible to setup SSH without actually giving them a shell (effectively just the "S" in "SSH")?

---

### Post by CptPicard on 2008-08-10
[http://en.wikipedia.org/wiki/Tunneling_protocol#SSH_tunneling](http://en.wikipedia.org/wiki/Tunneling_protocol#SSH_tunneling)

---

### Post by Sydius on 2008-08-10
But to do an SSH tunnel, don't you need to have a (shell) account on the remote computer?  Since this is for a game, I wouldn't want to distribute shell access of any kind.

---

### Post by mssever on 2008-08-10
> **Sydius said:**
> But to do an SSH tunnel, don't you need to have a (shell) account on the remote computer?  Since this is for a game, I wouldn't want to distribute shell access of any kind.
I've never tried something like this, but you could set the shell in /etc/passwd to a no-op, such as /bin/false. That's what a number of system accounts do.

---

### Post by Sydius on 2008-08-10
> **mssever said:**
> I've never tried something like this, but you could set the shell in /etc/passwd to a no-op, such as /bin/false. That's what a number of system accounts do.

That's an idea.  I suppose the MUD would still have to create/update/delete Unix/Linux accounts, but it would work.  The main thing I don't like about this idea is that it would make the user list on the computer very messy (assuming there were enough players).

---

