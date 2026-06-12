---
title: "External modem problems"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by Rapic on 2008-10-15
O/S Ubuntu 8.04
Having difficulty to get an external modem V92 (Conexant on the box) to work.Filled out info Netwoks-Connections - dial up
as best I could. phone # etc. It refuses to keep DNS # in ADD box.

If turned on at boot it starts to dial.
If turned on after start-up it refuses to dial.
If and when it does dial it appears to talk to ISP server but fails to connect.

Can anyone suggest any assistance for a newbie,
Tks

---

### Post by robert shearer on 2008-10-15
> **Rapic said:**
> O/S Ubuntu 8.04
Having difficulty to get an external modem V92 (Conexant on the box) to work.Filled out info Netwoks-Connections - dial up
as best I could. phone # etc. It refuses to keep DNS # in ADD box.

If turned on at boot it starts to dial.
If turned on after start-up it refuses to dial.
If and when it does dial it appears to talk to ISP server but fails to connect.

Can anyone suggest any assistance for a newbie,
Tks

Dial-up is a troublesome thing at best of times and after several months of using it I changed to broadband.
The update downloads just got too big to leave any useful time to use the computer for other internet uses.!

Having said that I realise that not everyone has access to faster internet providers so..

1) can you contact a local Linux users group in your area?  Google for Linux user group  and add your town/city .
As Ubuntu is so popular there should be someone that is using it and dial-up and would help you.
Dial-up configuration varies from country to country and isps so local knowledge can be of great use.

2) My own breakthrough was to use the kppp package to manage the modem and configuration. The downside is that it requires a lot of kde libraries to be installed as well. Big download needed.
I got round this by ordering a copy of Kubuntu on cd (making sure that it was the same release as the Ubuntu I had installed) and adding this to my synaptic repository.

System=>Administration=>Synaptic Package manager
Then Settings=>Repositories=>Third party software=>add cdrom

This adds the information on packages on the Kubuntu disc and then search for kppp in synaptic and mark it for installation.
The package/s will be downloaded from the disc.

There was still a great deal of set up needed but the KDE kppp help pages were useful and if you need more details then post again.

Happy experimenting!

---

