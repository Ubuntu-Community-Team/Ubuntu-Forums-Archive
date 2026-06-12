---
title: "Remmina Remote Desktop Issues"
date: 2015-11-03
forum: New to Ubuntu
---

### Post by moolman-juandre on 2015-11-03
Good Day Gentleman.

I have come across an interesting issue regarding Remmina Remote desktop. I have installed Ubuntu 15.04 on my PC, but I can not launch remmina I only get a send error report and the application does not open. I have booted with a live disk and it works just fine, but after install it refuses to open. When I try to open it in the terminal, I get this:

[B]juandre@juandre-ThinkCentre-M58p:~$ remmina
Remmina plugin VNC (type=Protocol) registered.
Remmina plugin VNCI (type=Protocol) registered.
Remmina plugin RDP (type=Protocol) registered.
Remmina plugin RDPF (type=File) registered.
Remmina plugin RDPS (type=Preference) registered.
Segmentation fault (core dumped)

[/B]and the aplication does not open.

So I uninstalled the rdp-plugin, and then remmina launches. But I need the rdp-plugin to connect to my Windows servers.
When I reinstall the rdp-plugin I'm back at square one where Remmina refuse to launch.
Again... all works well when I boot live.

Can anyone think of a solution I might try?

Thanks in advance.

---

### Post by TheFu on 2015-11-03
Create a new userid.
Login with that.
Test.

If it works, the issue is inside the config of the other userid. Find those  settings and either delete them or just move them to a different location for later, careful, merging.

---

