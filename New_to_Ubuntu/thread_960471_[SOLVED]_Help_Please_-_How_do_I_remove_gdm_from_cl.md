---
title: "[SOLVED] Help Please - How do I remove gdm from clamTK quarantine?"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by bwallum on 2008-10-27
Hi

For my sins I ran clamTK. It found 'viruses'. One was gdm or the Gnome Desktop Manager. I had set clamTK to quarantine viruses.

I then switched off my machine. When I returned and switched on I received a message saying that gdm could not be found and I was dumped to the command line.

I tried to install the desktop using sudo apt-get install ubuntu-desktop but no joy.So I have the command line only to work with.
 
Any offers on how to get gdm out of clamTK's clutches and get my desktop back please?

Here's the solution. It has been guided by others although I lost reference, apologies for that:-

At the command line type startx
When the desktop comes up go to System>Administration>Synaptic Package Manager
Search for gdm
Select reinstall package and apply
Reboot the pc (you might have to simply switch it off)

---

