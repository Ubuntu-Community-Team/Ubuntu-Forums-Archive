---
title: "Windows Network"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by gullfounder on 2008-08-23
Hi i am on windows Network. 
Many of the friends share music and more but i cannot see them neither i can view them from Ubuntu 8.04LTS.
When i go to network place i can see Windows network clicking theme reveals Windows Work groups but after clicking them i cannot see any computers What should i do.

---

### Post by Dedoimedo on 2008-08-23
Hello,

To be able to share with your network peers, there are some things you should consider:

1. You need Samba sharing running. You can install it via Synaptic, or the command line: sudo apt-get install samba. After you do that, ask if you need more help configuring samba.

In the meanwhile, see if this helps you:
[http://www.dedoimedo.com/computers/linux_commands.html](http://www.dedoimedo.com/computers/linux_commands.html)

See Network sharing...

2. Your friends need to allow sharing. Are they using any firewalls? It is possible that they allow only specific hosts to connect. Please check this also.

Cheers,
Dedoimedo

---

### Post by gullfounder on 2008-08-23
Thanks for the help but after installing samba i can see computers of the work group i join. still when i click them i get a blank page i have confirmed the sharing on Windows it is working fine.

---

### Post by Iowan on 2008-08-23
There are a few other threads about invisible Samba/Windows shares. [Here]("http://ubuntuforums.org/showthread.php?t=891876") is a recent one.

---

