---
title: "July 14 oneiric-alternate-amd64: installation failed"
date: 2011-07-15
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by iClouseau88 on 2011-07-15
Hi,

I just burned the July 14 iso of oneiric-alternate-amd64 after checking sha256.  Disk integrity OK.  Hit F6 and selected acpi=off. My PC has Nvidia GeForce 7300GT video card.

Installation proceeded nicely until the part where software packages are downloaded.  After the 119th package is downloaded, the screen shows:

"[COLOR="red"]Installation step failed at "Select and install software""
[/COLOR]
Normally there are about 900-odd packages, this time I only see 119 packages at the start.

Has anyone got the same issue with July 14 build? Any suggestions?

:confused:

---

### Post by ratcheer on 2011-07-15
I had the same problem a week or two ago. In my case, it was because I had no network connection because Ubuntu is defaulting to a driver that does not work with my NIC.

Cariboo907 suggested I try to install from the LiveCD image, and that worked for me.

Tim

---

### Post by iClouseau88 on 2011-07-15
Hello Tim,

I did not see the Live CD sources from the daily image download page.  Can you show me how to get the Live CD iso?

Thanks a lot for your help.

PS: Never mind.  Found "daily-live" further up the directory.

Cheers!

---

