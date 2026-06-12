---
title: "[SOLVED] Network Manager fails to connect"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by slughappy1 on 2008-11-18
While using 8.04 Network Manager "just worked", but now it doesn't. I can not connect to my Universities wireless network anymore. I think I need a certificate ( which I didn't need in 8.04 ), but it doesn't offer to download it like it does in Vista and OSX. What can I do?

---

### Post by gn2 on 2008-11-18
Have you tried using [Wicd]("http://wicd.sourceforge.net/") instead of Network Manager?

---

### Post by SamNSane on 2008-11-18
> **slughappy1 said:**
> While using 8.04 Network Manager "just worked", but now it doesn't. I can not connect to my Universities wireless network anymore. I think I need a certificate ( which I didn't need in 8.04 ), but it doesn't offer to download it like it does in Vista and OSX. What can I do?

Under the circumstances, you might be best served by asking the people who run the uni's wireless network for help. Much (practically all) of the requirements for connecting to that network are under their control.

It doesn't make sense that Intrepid would require a cert and Hardy wouldn't. I think that you may have misunderstood something about the connection process, and that misunderstanding may be (at least part of) what's preventing you from connecting now. If you have to retrieve a cert from the uni's intranet, it could be that you have to have javascript allowed in your browser or you won't be offered the cert. Like I said, the people running the network ought to be able to help you get this done.

BTW, I am as big a fan of WICD as you're likely to find, but I don't think I would use it to replace the network manager in Intrepid -- at least not as a first shot at fixing a problem like this. (I do use it under Hardy, however.) Prior to Intrepid, the network manager was horribly limited, and made life miserable for people who needed to move a laptop around among multiple networks, especially if fixed IP addresses were in use on any of those networks. But the Intrepid version is excellent, and it is well-integrated with the rest of the gnome desktop. If it ain't broke, it probably ain't necessary to fix it.

---

### Post by superprash2003 on 2008-11-18
does it see other wifi networks?? check system->admin->hardware drivers, to see if there any wifi drivers you can use..

---

### Post by slughappy1 on 2008-11-18
It can see all of the other networks. It also has problems sometimes connecting to a open network up on the same campus.

---

