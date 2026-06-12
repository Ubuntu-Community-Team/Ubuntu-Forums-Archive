---
title: "Team Viewer problem"
date: 2013-12-30
forum: New to Ubuntu
---

### Post by lucie.oehlmann on 2013-12-30
Hi guys,

I've got Ubuntu running on a server which doesn't have a monitor and I can access it using putty, so I've got access to the command line. Now I initially set up team viewer so I could have access to the GUI but it doesn't seem to be working any more. If I type teamviewer --info it give me the status teamviewerd start/running and the correct teamviewer id. But when teamviewer 9 tries to connect from my windows machine nothing happens. It says "connecting" but doesn't prompt me for a password.

I can't see it in the network any more. Could these things be related?

Has anyone got any ideas?

Thanks

Lulu

---

### Post by Kirboosy on 2013-12-30
Welcome to the forums! :D

What if you try initiating a connection  from the server to the windows computer? I don't think it will fully  work but just to see if its able to communicate with the Teamviewer  servers.

```
teamviewer -i <ID> --Password <Password>
```

Have you recently changed any of your network settings on anything?

Hope that helps!
~Caboose

---

