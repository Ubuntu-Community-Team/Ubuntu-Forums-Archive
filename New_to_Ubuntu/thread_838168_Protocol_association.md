---
title: "Protocol association"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by Ev1L on 2008-06-23
Hi,
I need to associate an application as default for handling SIP protocol calls.

Example:
I want to modify Pidgin with a custom command when right clicking on xmpp buddy.(i will ask how to do this elsewhere)
assuming i can do it, the command should be something like sip:bob@example.com, and i want to associate such link to x-lite as default SIP application (something like skype integration i think, or torrent file association, that i can do from Firefox preferences).

so, to make it simple, what should i change to tell the system to start a call with X-Lite when i launch a sip: call?

---

### Post by samder123 on 2008-06-23
hi to associate the application for handling sip protocol is very simple.
==============================================
sam
[http://www.christian-drug-rehab.org](http://www.christian-drug-rehab.org) Christian Drug Rehab

---

### Post by jnylen on 2008-09-09
[http://ubuntuforums.org/showthread.php?t=890029](http://ubuntuforums.org/showthread.php?t=890029)

...run gconf-editor and look under the key path /desktop/gnome/url-handlers/ (the existing handlers should serve as sufficient examples of what needs to be added)...

---

