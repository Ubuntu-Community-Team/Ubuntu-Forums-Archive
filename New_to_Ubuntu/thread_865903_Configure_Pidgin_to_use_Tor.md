---
title: "Configure Pidgin to use Tor"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by person8451 on 2008-07-21
I really looked for a while and I am apparently too dense to get this.

How do I get Pidgin to use Tor?  Everything I see tells me to use the "Advanced" tab and as far as I can tell there is no such thing in Pidgin.  I dread that I will find this elusive "advanced" tab 10 seconds after posting this, but at the moment I see no such thing. Perhaps there used to be one--all the guides I have found were a year old or more.  

So just assume I am an idiot, (if you hadn't already), and please tell me what buttons to push in which order to cause Pidgin to use the Tor proxy thingamajigger.

---

### Post by stoneybroke on 2008-07-21
Its been a while since I used tor but I think u have to go to preferences in pidgin click on network and configure proxy to get it to work but i'm not 100% sure about it.

Hope thats of some help

---

### Post by sdennie on 2008-07-21
The "Advanced" tab is only seen when you edit an individual account.  However, in Hardy, pidgin is setup to use the default gnome proxy by default so, if you've got gnome setup to use Tor (System->Preferences->Network Proxy), you should already be using Tor for pidgin.

---

### Post by mc4100 on 2008-07-21
This might be helpful if you don't want a system-wide proxy, i.e., just to use Tor for pidgin traffic...

[https://wiki.torproject.org/noreply/TheOnionRouter/TorifyHOWTO/InstantMessaging](https://wiki.torproject.org/noreply/TheOnionRouter/TorifyHOWTO/InstantMessaging)

> "Pidgin (formerly Gaim)

For application wide settings, goto Preferences -> Network -> Proxy server and enter these settings:

Proxy type: SOCKS 5
Host: 127.0.0.1
Port: 9050

Do not use the SOCKS 4 setting; this leaks DNS. "

---

