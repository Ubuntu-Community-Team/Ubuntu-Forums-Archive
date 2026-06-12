---
title: "[SOLVED] networking tutorial"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by LTFC2020 on 2008-08-11
hi
I've been searching myself about this for a while but cannot seem to get what I need
does anyone know a tutorial that explains _very simply_ how to set up a network between ubuntu computers?
I am completely new to this and require a straightforward explanation of each part of the process and the jargon involved
preferably for gutsy
thanks

---

### Post by decoherence on 2008-08-11
If all you want to do is share files, Download the openssh-server package on to each Ubuntu machine. Then under the Places menu go to Network. The machines should show up there thanks to the magic of Zeroconf.

---

### Post by LTFC2020 on 2008-08-11
I don't want to sound stupid, but I am, so thats how it comes across ;)
Ok so I installed the application on each machine and went to places - network where there is a icon for windows network
whats next?

---

### Post by decoherence on 2008-08-12
Hmm... you're not stupid, there should be no "what's next." I must've left something out.

Can you confirm that avahi is running on the machines? Follow the menus...

System > Administration > Services

Check that "Multicast DNS Service Discovery (avahi-daemon)" is present and enabled.

Often things 'just work' for me and I forget what all I've set up to make it that way...

---

### Post by LTFC2020 on 2008-08-13
yeah I know what you mean about trying to remember how you set up something when you need to explain it to someone else....
anyway I checked that part of the system
Multicast DNS Service Discovery is present and enabled but not the  avahi-daemon part

---

### Post by cariboo on 2008-08-13
Here is a link to a networking tutorial, once you master networking, you can almost set up a working network anywhere.

[http://www.aboutdebian.com/network.htm](http://www.aboutdebian.com/network.htm)

This is for debian, but ubuntu is based on debian so everything will be the same.

Jim

---

### Post by decoherence on 2008-08-13
Ah, I think I'm the stupid one now!

Do you have the openssh-server package installed? That's one thing I forgot to mention that could be the missing link.

On a subconscious level I guess I think everybody must be running an ssh server!

Before you say "but i don't want a remote shell!" Nautilus will actually treat it as a secure FTP connection, allowing file sharing and remote browsing in the standard, friendly (and encrypted!) way.

---

