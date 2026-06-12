---
title: "[SOLVED] Ubuntu &amp;amp; XP Synergy"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by gregbzh on 2008-10-14
Hi.  Could someone please help me set up synergy using Ubuntu as the server and XP as the client?  I have no problem doing it the other way around (XP=Server & Ubuntu=Client).  I'm completely lost despite using quick synergy and searching through the forums.

I get the following on the XP box when trying to connect to Ubuntu as server:
WARNING: failed to connect to server: address not found for: camilla
DEBUG: retry in 60 seconds

Cheers.

---

### Post by Liviu-Theodor on 2008-10-14
I don't know about synergy, but for Windows clients to access Linux servers, you must install first the SMB (samba) service.

---

### Post by gregbzh on 2008-10-14
Thanks mate!  After trying all morning to get this to work and wasting far too much time, as soon as I installed Samba Synergy started working perfectly.  Thanks again.:D

---

