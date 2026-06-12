---
title: "python twisted conch shell"
date: 2008-09-18
forum: Programming Talk
---

### Post by cdenley on 2008-09-18
I've been looking through the examples and documentation, and I cannot figure this out. How can I create a server which lets the user interact with a real shell like bash. I can get a server that responds to commands created in a custom protocol, and I can get a python shell prompt. Can I let the user interact with another python function as if they were running it from a console?

---

### Post by mssever on 2008-09-18
I don't know if I understand you correctly, but is [pexpect]("http://www.noah.org/wiki/Pexpect") what you're after?

---

### Post by cdenley on 2008-09-18
> **mssever said:**
> I don't know if I understand you correctly, but is [pexpect]("http://www.noah.org/wiki/Pexpect") what you're after?

Something like pexpect, but it has to run inside a conch ssh session so the user can interact with the real shell through their ssh client. The only way I know how to do it with pexpect would result in the shell being interactive only from the server's local terminal, not through the ssh client.

---

