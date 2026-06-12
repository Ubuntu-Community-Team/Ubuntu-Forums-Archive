---
title: "Blueprints for Ubuntu Developer Summit - O"
date: 2011-05-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-05-01
1) Default e-mail client (Thunderbird <-> Evolution)
[https://blueprints.launchpad.net/ubuntu/+spec/desktop-o-default-email-client](https://blueprints.launchpad.net/ubuntu/+spec/desktop-o-default-email-client)

2) Default browser (Chromium <-> Firefox)
[https://blueprints.launchpad.net/ubuntu/+spec/desktop-o-default-browser](https://blueprints.launchpad.net/ubuntu/+spec/desktop-o-default-browser)

3) Display Management (LightDM <-> GDM)
[https://blueprints.launchpad.net/ubuntu/+spec/desktop-o-lightdm](https://blueprints.launchpad.net/ubuntu/+spec/desktop-o-lightdm)

4) Xorg plans (xserver 1.11 <-> 1.10.x)
[https://blueprints.launchpad.net/ubuntu/+spec/desktop-o-xorg-stakeholders-request](https://blueprints.launchpad.net/ubuntu/+spec/desktop-o-xorg-stakeholders-request)

5) GTK 3/GNOME 3
[https://blueprints.launchpad.net/ubuntu/+spec/desktop-o-gtk3-gnome3](https://blueprints.launchpad.net/ubuntu/+spec/desktop-o-gtk3-gnome3)

---

### Post by MacUntu on 2011-05-01
The rest: [https://blueprints.launchpad.net/sprints/uds-o](https://blueprints.launchpad.net/sprints/uds-o)

---

### Post by Starks on 2011-05-01
[https://blueprints.launchpad.net/ubuntu/+spec/foundations-m-rsync-based-deb-downloads](https://blueprints.launchpad.net/ubuntu/+spec/foundations-m-rsync-based-deb-downloads)

> 2011-04-22 robbie.w: We are going to look into implementing the debdelta suite: [http://debdelta.debian.net/](http://debdelta.debian.net/) There will be a new blueprint for this.

Delta debs for oneiric or oneiric+1?

---

### Post by jtfolden on 2011-05-02
My preference is for Evolution over Thunderbird. It's a perfectly serviceable app and the roadmap for v3.2 is looking interesting, including support for Exchange Web Services for 2007 (and 2010 ?), a move to WebKitGTK+ and a decent refresh of the UI if some mockups are an indication.
[https://live.gnome.org/Evolution/Planning32](https://live.gnome.org/Evolution/Planning32)
[http://afaikblog.wordpress.com/2010/11/25/evolution-re-evolved/](http://afaikblog.wordpress.com/2010/11/25/evolution-re-evolved/)

...and if they are looking to move to a WebKit based browser then I would think Epiphany would fit the bill.

---

### Post by chrisccoulson on 2011-05-03
> **jtfolden said:**
> My preference is for Evolution over Thunderbird. It's a perfectly serviceable app and the roadmap for v3.2 is looking interesting, including support for Exchange Web Services for 2007 (and 2010 ?), a move to WebKitGTK+ and a decent refresh of the UI if some mockups are an indication.
[https://live.gnome.org/Evolution/Planning32](https://live.gnome.org/Evolution/Planning32)
[http://afaikblog.wordpress.com/2010/11/25/evolution-re-evolved/](http://afaikblog.wordpress.com/2010/11/25/evolution-re-evolved/)

...and if they are looking to move to a WebKit based browser then I would think Epiphany would fit the bill.

Well, we already decided at the last UDS that Exchange support wouldn't be a deciding factor in the default e-mail client. Exchange support is important in corporate environments, but it just isn't important for Ubuntu's main target audience (I've never met a single person outside of a corporate environment who uses it).

And we aren't switching to Epiphany ;)

---

### Post by ikt on 2011-05-03
My post on evolution:

[https://lists.launchpad.net/ayatana/msg05334.html](https://lists.launchpad.net/ayatana/msg05334.html)

> **jtfolden said:**
> My preference is for Evolution over Thunderbird. It's a perfectly serviceable app

Given how sour the response has been I question whether many corporations find it useful or whether they use a switch over to linux to move away from exchange and onto other services like zimbra etc.

---

### Post by Harry33 on 2011-05-03
I consider Evolution is a bit of a history now.
However its components are deeply buried into Gnome (evolution-data-server), also in the Gnome3 and Gnome-shell.

---

### Post by Starks on 2011-05-03
A bit more on debdelta
[https://blueprints.edge.launchpad.net/ubuntu/+spec/foundations-o-debdelta](https://blueprints.edge.launchpad.net/ubuntu/+spec/foundations-o-debdelta)

Delta-based syncing of debs is on the table for Oneiric, but any implementation is tied to how well the GSoC project goes and how much work on the Ubuntu-side of things is needed. The window for inclusion will be very tight.

---

### Post by benjamimgois on 2011-05-03
I think that if we switch evolution to thunderbird it would be improbable that we also switch firefox to chromium. Maybe use both applications would be a great way to encourage the mozilla foudation and it's investment on linux platform.

---

### Post by juancarlospaco on 2011-05-04
Web Browsers are for Surfing the Internet, if you surf the internet you are downloading things,
Installation recommends having Internet working, no one surf offline web pages saved on local disk,
if you are downloading things you can download .DEB's, then make a Big Simple GUI with 3 buttons 
"Firefox, Chromium, Others(not recommended)", no Options, no Configs, no Menus, no Minimize-able, as simple as posible,
it have a 60 seconds TimeOut that fallback into Firefox if the user dont move Mouse/Keyboard to choose (user AFK),
it have a 120 seconds TimeOut that fallback into Firefox if the user dont clicked an option to choose (user No0b),
a few lines of Python, with U1 like GUI.

---

### Post by jtfolden on 2011-05-04
I don't really see the need for an install choice in that manner. General/newbie users won't care what the default is as long as the browser functions as they expect. They're, also, unlikely to know which browser may be best.

On the opposite end, people who have a specific preference, probably already know how to install it.

---

