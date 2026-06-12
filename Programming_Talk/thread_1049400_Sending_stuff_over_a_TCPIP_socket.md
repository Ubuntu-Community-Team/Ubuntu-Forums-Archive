---
title: "Sending stuff over a TCP/IP socket?"
date: 2009-01-24
forum: Programming Talk
---

### Post by onlineapps on 2009-01-24
OK, I apologize for the noobishness of this post, but honestly, I can't find the answer after lots of searching.

How do you send information (not files, but commands and such) over an internet socket? What do I need to set up/install (SSH? A firewall config? Other?)? Does anyone know of a good tutorial?

---

### Post by s1ightcrazed on 2009-01-24
What exactly are you trying to accomplish? If your intention is just to run some commands on a remote machine then you can do that through ssh. 

For example:

ssh user@host "dmesg"

would run the command 'dmesg' as user 'user' on machine 'host'

---

### Post by The Cog on 2009-01-24
If you dhon't have the programming experience to be able to use your chosen language's socket library, you could perhaps just write scripts that pipe stuff to the program **nc** which I think is included in the default Ubuntu install. Use **man nc** or google for **netcat** for instructions and examples.

---

