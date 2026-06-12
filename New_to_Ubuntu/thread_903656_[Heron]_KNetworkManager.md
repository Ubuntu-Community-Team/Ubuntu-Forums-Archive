---
title: "[Heron] KNetworkManager"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by Obso1337 on 2008-08-28
Hey again everyone. 
My university is cool enough to supply free wifi reaching all around the university area of Akron. In order to use it though,they recommend ubuntu users install KNetworkManager. I did as much with no problems, but then when I went to Apps-->Internet it was not there. When I try just double clicking it in the Add/Remove screen, I get a wait signal like it is going to open, but nothing happens. 
I really don't get how it can just disappear after a simple install.

---

### Post by Heinzelotto on 2008-08-28
try launching "knetworkmanager" from a terminal and see what happens (and if it fails, what the output is).

---

### Post by Obso1337 on 2008-08-28
obso1337@Proust:~$ knetworkmanager
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
kbuildsycoca running...
Reusing existing ksycoca
org.freedesktop.NetworkManagerInfo already owned.
obso1337@Proust:~$ Launched ok, pid = 10262

Kind of odd. Not sure what it means, but it did load in the tray after this. It's still not present in App-->Internet though. Any way I can get it there?

---

