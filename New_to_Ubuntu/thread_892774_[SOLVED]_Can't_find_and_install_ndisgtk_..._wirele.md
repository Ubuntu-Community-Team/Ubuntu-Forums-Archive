---
title: "[SOLVED] Can't find and install ndisgtk ... wireless won't work.. please help"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by binobooks on 2008-08-17
I can't find ndisgtk in synaptic package manager.  It is apparently supped to be there so I can install it to install my driver for my netgear wg311v2 wireless card.. please help

---

### Post by nicedude on 2008-08-17
Your card is an Ateros chipset based one so if you want you can use the Madwifi family of drivers which are Linux based drivers and the best ones for your equipment. Ndiswrapper is a program to use a Windows XP driver for your adapter when Linux based ones are not available, which is not the case in your case. Not to say Ndiswrapper won't work it probably will, but it might not perform as well as the Madwifi ones. It also will not allow you to put your card into MONITOR mode to use utilities like Kismet ( a wireless scanner that shows you what is going on around you ) or if you plan to learn anything about Wifi hacking.

So if I were you I would read up on Madwifi in conjunction with your specific adapter as I am sure someone has written on the subject ( its a common adapter, I just don't have one so specifics I cant say for sure ).

---

