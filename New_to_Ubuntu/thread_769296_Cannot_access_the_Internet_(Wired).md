---
title: "Cannot access the Internet (Wired)"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by egan_mccomb on 2008-04-26
Hey guys, I finally decided to install Ubuntu, so yay!

The install went fine, and there are only a few problems (just some driver stuff that looks pretty easy to fix), but it is impossible to fix them because I cannot access the internet. :(

I'm a complete newbie to Linux (I do know a bit of terminal commands though), so please bear with me.

network card: Broadcom 440x 10/100 Integrated Controller

I'm on a Dell Laptop (specs in my sig). It's on a DSL, hooked up through an ethernet LAN. (Just so you know, I really don't know much about networking, either, and I didn't set the preceding up.)

I really don't know what information to give, so just ask me if you need anything.

Thanks a for any help!

---

### Post by RichardG891 on 2008-04-26
Gutsy and Hardy changed their default network handling from automatic DHCP to a "roaming" mode. Go to System>Administration>Network. Click the "unlock" button (to type your password; highligh "Wired Connection" and then select Properties... uncheck "enable roaming mode" and from the drop-down menu choose Automatic Configuration (DHCP). Exit and you should be good to go.

---

### Post by egan_mccomb on 2008-04-26
Thanks for the reply, but that has't worked for me. :(
It's a real bummer.

EDIT: Setting it manually works!

---

