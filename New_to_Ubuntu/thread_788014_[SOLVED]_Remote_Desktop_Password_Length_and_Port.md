---
title: "[SOLVED] Remote Desktop Password Length and Port"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by H.Callahan on 2008-05-09
I got the Remote Desktop function to fundamentally work.  But I have a couple of questions.

First, the GUI (System>Preferences>Remote Desktop) only allows for an eight character password.  On all my Windows <> Windows VNC installations, I have a MUCH longer password than that.  Is it possible to lengthen the password either but changing the number of characters allowed in the GUI or by editing a conf file somewhere with a longer password?

Second, the Remote Desktop seems to default to port 5900 -- and no option to change that in the GUI.  Is it possible to change that elsewhere, perhaps in a config file?

---

### Post by Monicker on 2008-05-09
Normal VNC authentication has an 8 character password limit.  This has been the case for quite some time.  The only version of vnc I know of which supports other authentication methods and can actually use a longer password is ultravnc, which is heavily modified and only runs on Windows AFAIK.


[http://www.realvnc.com/support/faq.html#password8can]("http://www.realvnc.com/support/faq.html#password8can")

---

### Post by H.Callahan on 2008-05-09
Actually, TightVNC supports longer passwords, but I have not been able to get it to work in place of the built-in remote desktop.  I got the server running and attaching to it from a client on another machines allows me to enter the password (longer than 8 characters, BTW), but when it completes the connection, I am presented with blank gray screen and a mouse cursor that I can move around.  No desktop, no icons, no CLI -- nada.

Do you know if, at least, the default port can be changed?

---

### Post by timcredible on 2008-05-09
why are you using vnc instead of rdesktop?  unless you have a really good reason, use the windows native protocol, RDP to access a windows machine, then there's no limitations on anything.  It's at Applications -> Internet -> Terminal Server Client.

---

### Post by Monicker on 2008-05-09
> **H.Callahan said:**
> Actually, TightVNC supports longer passwords, but I have not been able to get it to work in place of the built-in remote desktop.  I got the server running and attaching to it from a client on another machines allows me to enter the password (longer than 8 characters, BTW), but when it completes the connection, I am presented with blank gray screen and a mouse cursor that I can move around.  No desktop, no icons, no CLI -- nada.


[http://www.tightvnc.com/faq.html#howsecure]("http://www.tightvnc.com/faq.html#howsecure")

*VNC uses a DES-encrypted challenge-response scheme, where the password is limited by 8 characters*

Just because it lets you enter more than 8 characters does not mean that it is using all of them.

---

### Post by H.Callahan on 2008-05-09
> **timcredible said:**
> why are you using vnc instead of rdesktop?  unless you have a really good reason, use the windows native protocol, RDP to access a windows machine, then there's no limitations on anything.  It's at Applications -> Internet -> Terminal Server Client.

Mostly because I am going the other way.  I want to access an Ubuntu desktop from several Windows machines.

> **Monicker said:**
> [http://www.tightvnc.com/faq.html#howsecure]("http://www.tightvnc.com/faq.html#howsecure")

*VNC uses a DES-encrypted challenge-response scheme, where the password is limited by 8 characters*

Just because it lets you enter more than 8 characters does not mean that it is using all of them.

CARP!

You are correct.  I just tried my long password truncated to 8 characters on my existing Windows <> Windows setups and 8 characters are enough to authenticate.

Dang, talk about a false sense of security.

---

