---
title: "Bluetooth not working on Dell XPS 13 9300 (new)"
date: 2020-06-12
forum: New to Ubuntu
---

### Post by picea-sitchensis on 2020-06-12
Hello,

I have a new Dell XPS 13 9300 with Ubuntu pre-installed, 18.04. The bluetooth was working totally fine and now it isn't. When it first stopped working the toggle to turn it on and off wouldn't respond so I updated through the terminal and restarted my computer. Now the on/off works but no devices are showing up to connect to.

I searched around online and found these: 

This one isn't solved:

[https://askubuntu.com/questions/1071397/bluetooth-not-working-on-ubuntu-18-04](https://askubuntu.com/questions/1071397/bluetooth-not-working-on-ubuntu-18-04) 

This one is but it's for an older kernel:

[https://askubuntu.com/questions/1032417/ubuntu-18-04-lts-bluetooth-0cf33004-discovery-not-working](https://askubuntu.com/questions/1032417/ubuntu-18-04-lts-bluetooth-0cf33004-discovery-not-working)

Fixing it could just be some minor thing, but I'm very much a beginner with Linux (and really computers in-general).

Any ideas where to start? 

Thanks for any help that can be provided.

Here's what I got from the terminal when I put in sudo service bluetooth status:



&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
   Active: active (running) since Thu 2020-06-11 16:04:56 EDT; 1 day 1h ago
     Docs: man:bluetoothd(8)
 Main PID: 1727 (bluetoothd)
   Status: "Running"
    Tasks: 1 (limit: 4915)
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;1727 /usr/lib/bluetooth/bluetoothd

Jun 11 16:04:56 jonathan-XPS-13-9300 systemd[1]: Starting Bluetooth service...
Jun 11 16:04:56 jonathan-XPS-13-9300 bluetoothd[1727]: Bluetooth daemon 5.48
Jun 11 16:04:56 jonathan-XPS-13-9300 systemd[1]: Started Bluetooth service.
Jun 11 16:04:56 jonathan-XPS-13-9300 bluetoothd[1727]: Starting SDP server
Jun 11 16:04:56 jonathan-XPS-13-9300 bluetoothd[1727]: Bluetooth management interface 1.14 initi
Jun 11 16:05:23 jonathan-XPS-13-9300 bluetoothd[1727]: Endpoint registered: sender=:1.168 path=/
Jun 11 16:05:23 jonathan-XPS-13-9300 bluetoothd[1727]: Endpoint registered: sender=:1.168 path=/
Jun 12 17:03:51 jonathan-XPS-13-9300 bluetoothd[1727]: Failed to set mode: Blocked through rfkil
~

---

