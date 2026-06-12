---
title: "UFW  prompting me for a response?"
date: 2018-08-27
forum: New to Ubuntu
---

### Post by ubantunovice2 on 2018-08-27
I'm reading about the linux firewall and how to create rules both at the command line and by gui. 

Creating rules ahead of time requires imagining all possiblities. Not easy to do. In Windows, my firewall alerts me with a _popup_ when anything tries to access the internet and asks me what to do (allow once, always allow, never allow, etc.). I have UFW on but have not yet seen such popups. Is it possible to configure ufw to issue such popups? The only options I see are allow, deny, reject. What about "_prompt_"? Do I need a different app for that?

Thank you.

---

### Post by TheFu on 2018-08-28
no.  end users don't control the firewall.  Only an admin can.
I've never seen any popups.

Actually, the firewall is built into the kernel.  Whatever program you use is just an interface into the kernel firewall.
ufw is a highly, highly, simplified interface.  It should be sufficient for normal desktop users.  If you want more advance capabilities, you'll need a different interface like iptables.   It can accomplish pretty much anything that any world-class firewall does.  There is no GUI. 

GUIs don't work on servers, since servers don't have a GUI.

If you want to see blocked packets by the firewall, check the system logs.

---

