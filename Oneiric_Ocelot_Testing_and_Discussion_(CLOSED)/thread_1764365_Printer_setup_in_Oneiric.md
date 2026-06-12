---
title: "Printer setup in Oneiric?"
date: 2011-05-21
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by scradock on 2011-05-21
I have a networked HP printer, which I have configured with its own local IP address. Previous Ubuntu releases have a "gnome printer configuration" tool, which in my experience efficiently finds such printers and allows me to select an appropriate driver.

In Oneiric, at the moment, Printer configuration seems to be handled by a much more limited tool, part of the system configuration app. This fails to set up an appropriate driver and so the printer will not accept jobs. I suppose that this is in line with the trend to fewer configuration options..

I tried using the CUPS configuration mechanism (via [http://localhost:631/](http://localhost:631/)).
This allows me to find and address the printer, but finally fails to allow completion with the message 'device-uri "hp"' does not exist, or something to this effect.

Does anyone know if I need to install an additional package to get the printer configured, or if it is just a matter of waiting until it all comes together?

Yes, I know this is pre-alpha software. I'm here to post bugs on launchpad if they are needed, but I would rather not clutter launchpad up if this is going to be fixed in the next few days.

---

### Post by dino99 on 2011-05-22
> **scradock said:**
> 

Yes, I know this is pre-alpha software. I'm here to post bugs on launchpad if they are needed, but I would rather not clutter launchpad up if this is going to be fixed in the next few days.

As you knows, there is a bunch of coming changes under the hood, and we still have had a small part of them yet; so we cant says your problem will be fixed in the coming days, and flooding launchpad with such issue is useless due to that changes flow (wait "beta" to report)

---

### Post by VinDSL on 2011-05-22
> **scradock said:**
> I have a networked HP printer, which I have configured with its own local IP address. Previous Ubuntu releases have a "gnome printer configuration" tool, which in my experience efficiently finds such printers and allows me to select an appropriate driver.[...]

Does anyone know if I need to install an additional package to get the printer configured, or if it is just a matter of waiting until it all comes together?[...]
I'm using:

[LIST]
[*]system-config-printer-commom
[*]system-config-printer-gnome
[*]system-config-printer-udev
[*]python-cupshelpers
[*]foo2zjs
[/LIST]

They found my USB printers, and config'ed them with no intervention on my part.

LPT1 printer required me to choose a driver.

I don't have a network printer, but I can see options to add a URI (et cetera) in the printer settings.

---

### Post by scradock on 2011-05-22
> **VinDSL said:**
> I'm using:

[LIST]
[*]system-config-printer-commom
[*]system-config-printer-gnome
[*]system-config-printer-udev
[*]python-cupshelpers
[*]foo2zjs
[/LIST]

.....

I don't have a network printer, but I can see options to add a URI (et cetera) in the printer settings.

Thanks VinDSL; I have all those packages, plus some of the hp-specific ones like hplip-cups. Should be enough; always has been in the past. (This Oneiric is an upgrade from Natty).

Which specific printer-settings dialog exposes the "Add URI" option? I didn't seem to find it when I was investigating.

Any help and advice appreciated.

PS - Problem Solved! I waded through the jumble of Applications again, and saw that as well as the item "Printers", which leads to the simplified setup tool, there is also "Printing". This leads to the gnome-printer-configuration dialog, where all the necessary things can be fixed, in the Properties tab. It is a bit confusing - if I want to configure a printer I don't choose "Printers" but "Printing"?????

I also copied a file "hp" from /usr/lib/cups/backends/ in another install to the same place in Oneiric, as it seemed it was missing. That may have been what did the trick. Again, I don't know why it wasn't there in Oneiric......

---

### Post by VinDSL on 2011-05-22
> **scradock said:**
> Problem Solved! I waded through the jumble of Applications again, and saw that as well as the item "Printers", which leads to the simplified setup tool, there is also "Printing". [...]
You know...

I was going to mention that (**Printers** / **Printing**), but I feared it was too rudimentary.  Some take offense to that... LoL!  :D

Anyway, glad you got it working.

---

