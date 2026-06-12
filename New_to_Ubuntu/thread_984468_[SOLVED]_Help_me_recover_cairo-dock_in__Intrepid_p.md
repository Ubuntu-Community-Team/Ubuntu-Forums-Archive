---
title: "[SOLVED] Help me recover cairo-dock in  Intrepid please!"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by iClouseau88 on 2008-11-16
Hi,

I used to have cairo-dock in Ubuntu Hardy but somehow lost it when upgrading to Intrepid.  In applying today's 59 updates which includes cairo-dock 1.6.3.1, I cannot install this application.  Here's the message:

E: /var/cache/apt/archives/cairo-dock_1.6.3.1_all.deb trying to overwrite usr/share/cairo-dock/icon-mouse.png, which is also in pkg cairo-dock data.

I don't understand this message, but would appreciate guidance on how to get cairo-dock back.

Thank you.

---

### Post by sirjoebob on 2008-11-16
I wish I could help but I don't know much about Cairo-Dock. I use AWN and don't have any issues with it.

---

### Post by iClouseau88 on 2008-11-17
Thanks for your reply but I just found a solution from [www.cairo-dock.org](www.cairo-dock.org).  I modified it to suit my machine and hope that this will benefit some users who face the same problem:

1) go to a terminal and purge all cairo-dock related applications:

sudo apt-get remove cairo-dock* --purge

2) update the sources (then "save" the sources file) if you have not changed "hardy" to "intrepid", as I found I haven't:

sudo gedit /etc/apt/sources.list

deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) intrepid cairo-dock

3) sudo apt-get update, then close the terminal

4) re-open the terminal and re-install cairo-dock and related applications:

sudo apt-get install cairo-dock cairo-dock-data cairo-dock-plug-ins

5) At the terminal, type "cairo-dock" (of course without quotation marks):

$cairo-dock <ENTER>

Now the cairo-dock applets show up on your screen.  You can also check by clicking Application > System Tools on the tool bar.  It now shows Cairo Dock as one of the menu items.

Cheers!

---

