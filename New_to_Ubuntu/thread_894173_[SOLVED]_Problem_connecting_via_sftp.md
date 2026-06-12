---
title: "[SOLVED] Problem connecting via sftp"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by echelonIV on 2008-08-19
Hey everyone, I'm having a little trouble connecting to my university via sftp in Ubuntu. Every time I try to connect to the server, it just keeps prompting me for my password, and after three tries, it gives me this message:
```
Permission denied (publickey,keyboard-interactive).
Couldn't read packet: Connection reset by peer

```
I can successfully connect to the server when I boot my machine into Windows XP (using WinSCP) so I'm pretty sure this is a problem in Ubuntu.

Any help would be much appreciated.

---

### Post by scorp123 on 2008-08-19
Can you SSH into your University? Try this: ```
ssh -vvv your_remote_username@your_University
``` ... This will generate tons of debug output. Please post all of it here.

You could try the same with sftp ... ```
sftp -vvv your_remote_username@your_University
``` ... Again, this will generate a lot of output which is useful for debugging. Please post that here!

---

### Post by echelonIV on 2008-08-19
I just figured out that I made a stupid mistake, I forgot to put my username in the username@university, due to my misinterpretation of their directions.  I can't ssh into my account, but I learned that I cannot access the server via ssh because of my account type.  
Anyways thanks for the help scorp123.

---

