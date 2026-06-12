---
title: "vino problem on 20.4 - stops apps opening after startup - and after killed."
date: 2020-06-27
forum: New to Ubuntu
---

### Post by propolis2 on 2020-06-27
Hi and Good morning to all...

I installed Ubuntu on a clean machine 2 weeks ago. I followed instructions for screen sharing gnome with vino.
This included setting permissions and a password and allowing unencrypted screen using dconf
I used tightvnc on win7 and got a beautiful copy of the reddish gnome screen.
Both direct and remote worked perfectly, beautifully.

After re-booting, some time later, many things changed...
After re-booting, working direct on the machine is normal and terminal etc work ok.
When 'vncserver' is run, however, the remote now shows a blue screen with a mouse and the direct screen won't run many apps including terminal (once it has been closed).
When the command 'vncserver -kill :1' is entered in xfce terminal (which does run) the tightvnc window closes 'gracefully' but the direct screen still won't run terminal, todo and other apps until a reboot.
I have made a few mods to the xstartup file (i don't know what it was in the beginning now) but nothing has helped.
I am running on a LAN not across the internet.

I can't imagine what has happened, being a newbie to Ubuntu, so any help would be greatly appreciated.

---

