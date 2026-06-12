---
title: "Nextcloud and apache"
date: 2023-08-11
forum: New to Ubuntu
---

### Post by sergbotan on 2023-08-11
Hi all,

I installed Apache2, that works well and I run my site on it, but now I do not know how to access Nextcloud. Could you please help me? Ubuntu 23.04.

Thank you.

---

### Post by TheFu on 2023-08-12
If you are running a server, probably need to stick with an LTS release.  6 months of real support isn't really worth the effort to setup something like nextcloud.  Use 22.04 or 20.04 for nextcloud.
Did nextcloud work BEFORE you installed apache?

If you aren't a Linux nerd, perhaps the easiest way to get nextcloud working is to install the nextcloud-snap package server.  This has liabilities and complexities if you need to do anything odd with nextcloud, but it does work and it does make lots of things easier.  For example, it will self-upgrade (whether you want that or not).  You can also backup the snap package - there's a built in tool for this for all snap packages. So moving to the next LTS is possible, in theory.  Occasionally, the automatic upgrades for nextcloud snap does break things, so beware.  [https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-nextcloud-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-nextcloud-on-ubuntu-20-04)

I've been running nextcloud nearly a year as a snap package.  I use a reverse proxy outside the system to terminate TLS certs, so I don't know how to add certs inside the nextcloud snap. Sorry.

---

### Post by sergbotan on 2023-08-12
Thank you for the reply. Yes, when I just installed Ubuntu nextcloud worked. So, it is installed as a snap package. And after Apache installation I just don't know how to access nextcloud. I wonder if I can just find the location of the nextcloud directory, put that path to nextcloud.conf instead of '/var/www/nextcloud' and then configure Apache appropriately so that nextcloud is available at **localhost/nextcloud**. I've done a bit of other network configurations on my server and I wouldn't like to reinstall the whole server.

---

### Post by TheFu on 2023-08-12
You cannot have 2 webservers listening on the same port.  The nextcloud snap brings a webserver with it.  If you want to run another instance, might I suggest using an lxd container or virtual machine with a different IP for the other needs?

Are you 100% certain that nextcloud is installed via snap?

**snap list**
will show the snap packages.

For example:
```
$ snap list
Name       Version      Rev    Tracking       Publisher   Notes
core18     20230530     2785   latest/stable  canonical&#10003;  base
nextcloud  26.0.2snap1  35830  latest/stable  nextcloud&#10003;  -
snapd      2.59.5       19457  latest/stable  canonical&#10003;  snapd
```

---

### Post by sergbotan on 2023-08-12
I don't believe I need two servers. I would like one webserver that serves two directories: 1. my personal site that is in '/var/www/html' and 2. nextcloud at 'nextcloud location' wherever it is, so that when i type in the browser **localhost** I get my site and when I type **localhost/nextcloud** I get nextcloud.

That's what I have after running snap list.

Name       Version       Rev    Tracking         Publisher    Notes
core18     20230530      2785   latest/stable    canonical**  base
core22     20230725      858    latest/stable    canonical**  base
docker     20.10.24      2893   latest/stable    canonical**  -
lxd        5.15-002fa0f  25112  latest/stable/&#8230;  canonical**  -
nextcloud  26.0.3snap1   35878  latest/stable    nextcloud**  -
snapd      2.59.5        19457  latest/stable    canonical**  snapd

---

### Post by TheFu on 2023-08-12
You understand that the nextcloud snap provides a pre-configured, read-only, webserver, right?  You can't change it.  It listens on port 80 and 443 (if you install a TLS cert).
Look at /snap/nextcloud/35830/bin/httpd-wrapper. Perhaps that will provide some ideas.

You can setup a different server, say apache, on the base OS, but it cannot listen on the same port used by the nextcloud web server.

But I really think you want to setup a reverse proxy that handles all inbound HTTP/HTTPS requests, terminates the HTTPS with TLS certs and proxies the different web domains to many different back end websites.  I do this ... by  running nginx, but apache or ht-proxy or a few others can all do it .... provided you allow them to own port 80 and/or 443 on the computer.

Only one process can listen on a specific IP and port on the same system. I don't know how to put is any clearer. Maybe someone else can.  Perhaps there's a way to convince the nextcloud snap to use a different port?  IDK, then you can use apache on the base OS as a reverse proxy into both nextcloud on a non-standard port AND whatever other website names you want to create under the vhosts.

Now, maintaining all these non-standard things will probably cause issues.  What I did was setup nextcloud into an LXC linux container, managed by lxd.  It runs just the nextcloud snap and has a dedicated IP just for that container.  LXC isn't like docker.  It appears to be more like a very, very, very, light virtual machine, but needs to be maintained like a VM, just without the overhead and some restrictions around firewalls and kernel modules.

But you do what you think is best.

---

### Post by sergbotan on 2023-08-12
[QUOTE=TheFu;14154229]You understand that the nextcloud snap provides a pre-configured, read-only, webserver, right?  You can't change it. - Absolutely. Probably, the problem is that it is a snap. Maybe I should delete snap nextcloud and install it just manually. Here is one of possible solutions:
[https://help.nextcloud.com/t/multiple-websites-on-same-web-server-as-nextcloud/138691](https://help.nextcloud.com/t/multiple-websites-on-same-web-server-as-nextcloud/138691)

---

### Post by TheFu on 2023-08-12
> **sergbotan said:**
> [QUOTE=TheFu;14154229]You understand that the nextcloud snap provides a pre-configured, read-only, webserver, right?  You can't change it. - Absolutely. Probably, the problem is that it is a snap. Maybe I should delete snap nextcloud and install it just manually. Here is one of possible solutions:
[https://help.nextcloud.com/t/multiple-websites-on-same-web-server-as-nextcloud/138691](https://help.nextcloud.com/t/multiple-websites-on-same-web-server-as-nextcloud/138691)

Maybe.

I ran nextcloud for about 3 yrs with a custom install.  The required software stack conflicted with other webapps on that same system and after about 6 months, the 1-click update never worked again.  I had to ssh into the system and run the updates from the shell.  Not a big deal for me - I'm a long time Unix/Linux admin, but it was just the hassles of broken addons/extensions that bothered me.

Nextcloud as a snap solves some of those issues and brings 1 new issue.  It keeps updated - sometimes breaking the addons which aren't compatible even when I specifically told the snap package to stay on v24/stable of the nextcloud snap.  My request was ignored.  It silently moved to v25.x and I didn't notice, because it kept working, but when it silently went to v26.x and the primary addon that I use broke, I was pissed.  It wouldn't revert to v25.  Reverting across major releases isn't allowed.  So I was stuck.  I had backups, but no time to restore them due to other life priorities.

Anyway, we all need to learn some things ourselves.  At a minimum, you will learn a bunch, even if you make mistakes which are well-known and are told how to avoid them.  That's your call.

---

### Post by sergbotan on 2023-08-27
Another option, probably, could be setting up an old PC with a drive as big as possible as a separate Nextcloud server. I already have 10 different devices in my home network, so one more doesn't make much of a difference. :)

---

### Post by TheFu on 2023-08-27
> **sergbotan said:**
> Another option, probably, could be setting up an old PC with a drive as big as possible as a separate Nextcloud server. I already have 10 different devices in my home network, so one more doesn't make much of a difference. :)

I used to be device crazy, then realized they were all eating power, generating heat and had hardware failures.  Every 5 yrs, I'd work through a "consolidation" effort to reduce the number of devices.  In 2010, I was down to 3 systems running 22 VMs.  Then my count slowly increased again.  

In 2015, I consolidated back to 3 desktops, 2 laptops and 2 raspberry pis.  Heck, I was going the wrong way!
In 2018, I replaced an older Core i7 with a much faster Ryzen that used less than 50% the power and was 5x faster.
In 2021, I replaced a Pentium G3258 with a faster Ryzen ... about the same power use, but the Pentium motherboard had started showing failures (NIC died, couldn't get into the BIOS), and a few other issues.
In 2022, I replaced the new Ryzen with an identical Ryzen for a 40% speed improvement + AMD iGPU.  Now I had 2 nearly identical desktops with 20K passmarks and sufficient RAM to run everything.  In 2020, I stopped using laptops, but kept the 2 raspberry pis, waiting for the pi4 USB power fix to become mainstream and the hardware to be available without scalper pricing.  That was a very long wait.
In 2023, I finally retired the 2010 125W Core i5 that was a backup server and migrated the RAID storage to one of the Ryzens. The system is still in the house, but hasn't been powered on for nearly a month.  Also, was able to get a pi4 at list price, so vp8/h.265 videos can be handled.  The pi3 is still used, but the pi2 will probably become a specialty device.
Additionally, over all this time I've reduced the number of VMs and Linux Containers down to about 10 in production.  More and more are becoming containers (managed by lxd, not docker).  This uses fewer resources, but since running containers in privileged modes is needed for things like VPNs or firewalls, some of those containers will always be behind a full VM handling reverse proxy tasks.  For example, my Nextcloud instance runs inside LXC and is only available on my LAN.  To access it when traveling or even just out for the day, I have to connect to my home VPN server (also a full VM).

Right now, in this room, I have 2 desktops powered on. That's it.
The raspberry pi v4 is in the theater room, also powered on.  There's an 8inch  tablet used to control media selection for the Pi in there as well. That tablet was a $50 Amazon one until it died last January. Got 5 yrs of solid, daily, use from it.  Also 5 yrs of Amazon tracking.  The new tablet isn't connected to google or amazon. It only uses f-droid packages.  Most importantly, it has a real GPS, so it will be great for road trips, unlike the amazon tablets.

Anyway, back to nextcloud. Whatever you do, be certain you setup daily, automatic, versioned, backups.  When nextcloud has problems, sometimes restoring the system is the only solution.  Putting a DB onto a huge HDD isn't good for consumer HDDs.  You'll burn them out fast that way.  My Plex Server, now jellyfin server, went through 3 4TB HDDs when I had the DB and OS on the same large HDD.  That taught me a lesson.   BTW, don't use USB connected storage for anything except backups.  I have 2 backup 8TB HDDs and about once a month one of them will just drop off the USB bus.  These things aren't moving.  There's just something about USB that doesn't keep things connected. I think both drives are well beyond their 1 yr warranty, so I should "shuck" them and connect them to SATA instead.  

Having storage disappear is a bit scary.

---

