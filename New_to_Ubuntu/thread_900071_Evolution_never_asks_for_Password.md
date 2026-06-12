---
title: "Evolution never asks for Password"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by mevets on 2008-08-25
I configured evolution to work using IMAP with my college email. It connects to the smtp server fine but works forever then eventually fails when trying to reach mail.gmu.edu (recieving). What confuses me is that evolution never asks me for a password, which it most definetly needs. I also tried thunderbird and it also never asked for a password. Starting to think there is something wrong with the server.

I followed this guide to setup the mail client: [http://www.gmu.edu/email/memo/configuration.htm](http://www.gmu.edu/email/memo/configuration.htm)

IMAP
Incoming: mail.gmu.edu
Outgoing: smtp.gmu.edu

---

### Post by HereInOz on 2008-08-25
Those instructions are for Netscape 4.7, which is around 8 years old.  Given that Thunderbird is loosely based on the Netscape 6/7/8 mail client, and they specifically state that Netscape 6 is not recommended, it is reasonable to think that Thunderbird would not work.  Evolution is totally different from Netscape 4.7.

Either they are well behind the times as far as current technology goes, or you have been steered to an old configuration page which has been sitting on their server since last century (sounds good, that).

I would contact the support people if you haven't already and try to get hold of a later model set up guide.

Normally for IMAP you enter the IMAP server name, the port, usually 143, and your username, and that is it until you need to access the server, then the authentication password prompt appears.  I notice that they mention that there is a field into which you can put a password during the setup, and this field does not exist in either Thunderbird or Evolution. If this is the latest setup they have, perhaps you need to talk to them about it.

---

