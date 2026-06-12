---
title: "Tip: Fix extremely slow BitTorrent speeds with port forwarding"
date: 2006-10-29
forum: Outdated Tutorials &amp; Tips
---

### Post by purifyyourmind on 2006-10-29
I wrestled with this for the better part of the evening, so I figure I should try saving other people time. I see a *ton* of other people having this problem. I did a quick search and didn't see another how-to on this issue; forgive me if I'm copying anything.

I was getting *extremely* slow download and upload speeds in Azureus. The fix for me, after trying a bunch of things, was simple. I hope this works for you too:

1. Go to your DHCP IP in a browser (there are sites that can show you your IP, Google it)
2. Go to the port forwarding section in your settings (varies with each model)
3. Add the range 49152-65534 to map to the DHCP IP address for both UDP and TCP.
4. Apply the settings and wait a little.

If it worked, the NAT firewall test should say "OK!" and your speeds will be decent. I'm still not sure if I'm getting quite the same speeds I was getting in Windows, but at least my torrent is only taking a few hours instead of days to finish.

---

### Post by purifyyourmind on 2006-10-29
Some clarification...

I found you need to specify *two* ranges of ports to get it fully working. If you just do one range, it'll work, but slowly.

Please see the attached screenshot. This is part of the configuration page for my Actiontec router/DSL modem. It shows all the TCP and UDP port ranges you need to forward.

Note that the local IP address may be different on your machine. Get it by running ifconfig at a console window. I was wrong in stating earlier that it had to be the DHCP IP you use.

Right now I'm downloading at 90 KB/s and uploading at 25 KB/s.

Now I hope there will be no more ](*,) for Ubuntu people trying to do BitTorrent.

---

