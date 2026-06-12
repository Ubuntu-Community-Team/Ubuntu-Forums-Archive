---
title: "Printers from System Settings"
date: 2011-09-20
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by chlorox on 2011-09-20
I'm trying to setup a printer. It appears that autodiscovery is the only supported method. When I hit "Add", I get a warning that FirewallD isn't running and that IPP, SMBClient, MDNS and a few other things are not enabled in FirewallD. I don't want a firewall running. Is there another way?

What if I've setup thousands of printers in my lifetime? What if I know the IP address as well as what driver I'd like to use. Is it possible to not automagically configure a printer???

---

### Post by cariboo on 2011-09-20
My Brother HL-5250DN, network printer is auto detected, and the drivers installed automagically, the only thing the setup asks for is the number of trays, and a description of the printer and it's location.

On the other hand, my Epson R340, is detected as being connected to a Windows system, which it it, but I have to select the make and model in the printer installation dialogue in order to set it up.

---

### Post by chlorox on 2011-09-20
All I'd like is a "manually configure" possibility. Automatic configuration is nice... but we NEED a fallback if it doesn't work.

---

### Post by cariboo on 2011-09-20
Doesn't the cups interface:

```
http://localhost:631
```

allow you to manually setup your printer? I's been a while since I've used it, as my printers are both well supported.

---

### Post by chlorox on 2011-09-20
Sure, the CUPS web backend is the unknown backdoor. (And that's what I ended up doing)

I think my concern comes in when we try to hold the user's hand TOO much... without ANY other option. A simple "manual install" should be there for anyone that knows what they're doing.

What I've noticed lately is the trend to make it all magic. And if the magic fails, do nothing.

Not all of this falls on Ubuntu. In Gnome3, if one selects a theme that Gnome can't find, GTK fails to load, leaving a user with just their desktop picture and NOTHING else. A simple try/catch block should be there to load a default theme if the chosen one cannot be loaded.

Wine 1.3.28 wants to automatically configure your audio setting. Only problem is, if it doesn't detect your sound driver correctly, sound flat out doesn't work.

I realize this is sort of turning into a rant, so I apologize. I think we're just going too far down the path of, "the user will completely bork everything if we give them the chance". And really, how much can a user mess up by manually configuring a printer and picking either the wrong interface, the wrong IP address or the wrong driver. Worst case scenario, the printer doesn't print.

It's not like we are giving them the option to ln -s /dev/lp /dev/sda0 and thus ruin their day.

Please, let me click on the "unlock" and manually add a printer by filling out a couple of fields.

---

### Post by cariboo on 2011-09-21
As far as printer setup goes, there have been far fewer threads with printer setup problems since printer setup became automagic, previous to that there seemed to be  tens if not hundreds of threads were someone was having a problem setting up a printer. 

I agree that Gnome is going to far, as far as hand holding is going, but if it gets to bad, there are always the alternatives, Xubuntu, Lubuntu and Kubuntu, or another distribution completely.

---

