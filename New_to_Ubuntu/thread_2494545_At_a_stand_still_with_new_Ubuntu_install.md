---
title: "At a stand still with new Ubuntu install"
date: 2024-01-19
forum: New to Ubuntu
---

### Post by eappell on 2024-01-19
I've recently bought a mini pc (Geekom IT13 i5) and have installed Ubuntu 22.04.03 LTS. The purpose of this machine is to offload Plex, Sonarr, Radarr, SABnzbd, etc. from my old Synology NAS and use it only for storage. 

Here are some of the reuiqrements:

[LIST]
[*]Access the box from outside the network. Essentially making it a headless server. (VNC?)
[*]Run Plex and the other apps in Docker containers
[*]Ability to access all of those apps from outside the network
[*]Preferably run all of them through an SSL cert
[/LIST]
The first thing I did was find a video on how to setup Guacamole to access the system from any web browser. This involved setting up an account with Cloudflare, using a domain name that I purchased, and setting up VNC access. It works for SSH, but not VNC. It fails instantly. I am using x11vnc.

 The next thing I did was get Plex running inside a Docker container. That is working almost perfectly other than a couple issues:

[LIST=1]
[*]There is one volume that I cannot add to the container and I don't know why. It's a volume created using an NFS share, as are all of my volumes, but every time I try to add it to my Plex container and redeploy it fails with a 500 error.
[*]The remote access in Plex settings show not accessible outside the network. If I set the port manually and click Retry, it says it is available, but then after a short time it goes back to not available...
[/LIST]
Then I installed the other apps I want to use, like Sonarr, SABnzbd, etc. I've set them up in Docker and they all have ports assigned, but when I try to access any of them they all return "ERR_CONNECTION_REFUSED". I should note that I have Portainer running and I am managing Docker from that app.

So I'm struggling a bit here... I realize these all involve other technologies other than Ubuntu, but I thought if I posted the whole thing here some might be able to point me in the right direction in terms of how to resolve those other issues. I'm worried that the whole Guacamole/Cloudflare thing might have messed me up. I've checked and nginx is running, if that's what those apps use to serve their UIs...? At this point I worry that anything else I do will just make it worse so I'm hoping to find some answers or direction here. 

Thank you for your help!

---

### Post by TheFu on 2024-01-19
> **eappell said:**
>  
Here are some of the reuiqrements:

[LIST]
[*]Access the box from outside the network. Essentially making it a headless server. (VNC?)
[*]Run Plex and the other apps in Docker containers
[*]Ability to access all of those apps from outside the network
[*]Preferably run all of them through an SSL cert
[/LIST]


I've been around a while and using Unix-like OSes for 30 yrs.  I'll ignore what you did and post what I would do - actually, what I have done.

If you want a headless server, ssh is the way.  Servers don't have a GUI. Period.

If you require a GUI, install a light desktop distro - perhaps xubuntu or Ubuntu-Mate and call that a "server" if you like.  DO NOT INSTALL Gnome.  For remote access, use x2go. There are clients for x2go for Windows, OSX, and Linux.  I've used it from 5 continents to access my desktop back home. It uses ssh for the tunnel and for the remote credentials, so it is as secure as possible, assuming you don't use  passwords over the internet. Never use passwords as the only credential over the internet. Never. Never. Never.  1000x more secure than SSL junk.  Sure, the business world uses SSL, but that doesn't mean is is actually secure.  There's a reason govts use IPSec for their VPNs and not a weenie SSL-based tunnel.
x2go feels 2-3x faster than other remote desktop options like VNC or RDP.  Install the server on your "server" - headless is fine. Install the x2go-client on each of your client systems - with MS-Windows, be certain to install the font package.  Setup a connection, choose to use ssh-keys for authentication (you did setup ssh-keys for authentication right?!!!), and pick the DE you installed from the list. Beware that KDE and Gnome either aren't supported or work really, really bad. Avoid them.  Or don't use any DE at all  and go with just a window manager, WM, setup. This will be the lightest and fastest.  I usually tell x2go that my connection is 1 lower than the truth and set the compression to be 4k-png so the interface is extra snappy.  Most people who used VNC or RDP before switching to x2go say it is like comparing night to day. It is THAT good.

I'm not a fan of docker, but I like linux containers.  Docker is the MSFT version of linux containers. It is very popular, but has lots of issues and baggage.  I don't think I'll convince you to use a different, more secure, container, so I won't bother trying.

Plex - ah ... the company that watches everything you click, listen to, and view.  They have a slick setup.  Do you really want to allow a company that strips your privacy to have direct access to your LAN?  That's what running Plex does.  There is an alternative, jellyfin. It isn't a slick, but it handles more types of content, especially audio files and it is 100% F/LOSS, so nobody is watching what you are watching or getting a list of music in your collection. Additionally, jellyfin supports OTA TV broadcasts - all for free.

To access any webapp from outside your LAN, there are multiple ways.  The easiest is using ssh as a SOCKS proxy.  I've posted a script in these forums to do just that and it works perfect from any Linux workstation to make almost all your web traffic appear to come from your house, regardless of where you are in the world.  It also allows access to your LAN webapps - including Jellyfin for video streaming through the web interface.

The other method is to run your own wireguard VPN server, which is surprisingly easy, especially for someone like you.  Wireguard makes LAN access from almost any client, anywhere in the world, like being there.  Jellyfin fat clients on a laptop or tablet will connect to your jellyfin server through the wireguard VPN and support streaming.  Wireguard is fast - something like 3x faster than openvpn, so most broadband connections won't feel slow.  I used wireguard over Xmas for a week to keep working at home when I was away. It was just like being there.

Best of all, none of these solutions requires trusting anyone else with the security of your LAN.  Basically, you would forward the ssh port and the wireguard port to your "server" on the LAN and setup any LAN access you like from the different wireguard clients.  Different clients can be limited to specific locations only or to the entire LAN subnet.  It is up to you, but hopefully, if you are hosting any public-facing servers, you would segment your LAN by security zone and have firewalls between each zone/LAN.  For example, I assume my android devices are all cracked, always, so they have limited access to LAN resources.  OTOH, if I'm traveling with a laptop, depending on where my travel takes me, I'll have light to extreme security, so the wireguard settings will allow more access when the risks are low.  If I'm in an authoritarian country with a laptop, I'll only boot from a microSD card that never leaves my person except when it is used in the laptop. That's the only way to know it hasn't been compromised.

If you do it this way, you won't need an SSL cert, which provides dubious security anyways.  Stick with ssh and a real VPN if you want security. If you need even more security than wireguard provides, IPSec is the only answer remaining.  I've never setup an IPSec VPN on Linux, but I have setup them on UNIX systems, but that also had dedicated concentrators with SecurID management and tokens for 25K users, 5K concurrent.  Not exactly home-lab friendly, certainly not home budget friendly.

---

### Post by eappell on 2024-01-21
Wow, lots to process here. THANK YOU for the very detailed response! Can't respond to all of it right away, but a couple things:

[LIST=1]
[*]I suppose I don't require a GUI, but I'm used to using a GUI with my old Synology. I'm fairly comfortable on the command line, but when things break or don't work I get stressed.
[*]Linux containers... I'm not married to Docker, I just like all of the tools that make the containers easy to manage. I don't know if linux containers have the same...?
[*]I've been a lifetime Plex member for the past 15 years or so, so I would have a hard time switching. I haven't ever experienced any ill effects from whatever access they have to my media, LAN, etc.
[*]I've tried Jellyfin a couple times and it always gets stuck indexing my media. I mean like I wait DAYS, and in one case, a couple WEEKS, and it never finishes indexing. Not sure what I was doing wrong, but now that I have a new machine I'll try it again.
[*]I will hunt down that script, thank you. Sounds like exactly what I need. So that would also work with Docker/containerized apps?
[*]I appreciate the perspective on using SSH and VPN instead of an SSL cert!
[/LIST]
Thanks again for all of this great info. I will read it a couple more times and then take some action, most likely starting from scratch and get it working the way I want it to.

---

### Post by TheFu on 2024-01-21
> **eappell said:**
> Wow, lots to process here. THANK YOU for the very detailed response! Can't respond to all of it right away, but a couple things:

[LIST=1]

> **eappell said:**
> 
[*]I suppose I don't require a GUI, but I'm used to using a GUI with my old Synology. I'm fairly comfortable on the command line, but when things break or don't work I get stressed.
Things are harder to fix when broken by a GUI than directly using the real commands in a shell, without any GUI layer.  Almost always, a GUI is just a 20% solution over the real tool that was created first and gets tested much better because testing CLI/shell interfaces can easily be automated, but testing GUIs is much harder.

> **eappell said:**
> 
[*]Linux containers... I'm not married to Docker, I just like all of the tools that make the containers easy to manage. I don't know if linux containers have the same...?
Docker is just a brand-name on a Linux Container.  Docker shows the power of marketing, not the best technology winning. MS-Windows is very popular, like Docker is very popular, but whether it is the best technology is completely debatable.  The same applies to Docker, especially since their containers run privileged by default.  Be wary of downloading containers from the docker-hub from people you don't know and trust.  It is basically like handing over your computer for someone else to run random software and abuse your internet connection for whatever purpose they choose.  

We do the same with Canonical and Ubuntu, but they've proven to be fairly trustworthy and have a good reputation with years of doing what they say - or at least trying to do it.

If you have a choice between 2 nextcloud docker containers - one provided by the nextcloud project team and the other prebuilt to installed 20 popular addons built by Joe Blowe, don't trust Joe.  Get the version from the nextcloud project.  

Often times, we are our own worst enemy by making the easy choice, not necessarily the wisest choice.

> **eappell said:**
> 
[*]I've been a lifetime Plex member for the past 15 years or so, so I would have a hard time switching. I haven't ever experienced any ill effects from whatever access they have to my media, LAN, etc.
That's like being stuck in the Apple ecosystem where everything seems easy, until it isn't and where everything costs money, when other solutions are 100% F/LOSS.  I've moved back and forth between Plex and Jellyfin a few times.  If your libraries are setup in the standard way, there shouldn't be any issues. I do find that Jellyfin's scrapers find the correct metadata more often than Plex ever did.  Plus, when Plex doesn't find the metadata, it just ignored the media. In Jellyfin, the media shows up in the library so I can manually use the "Identify" tool to find the correct information.  If you want this stuff to always work, you can add the IMDB ID to each Movie's directory name and that will ensure the correct metadata is always found.  I don't do that. Instead, for items that are trouble, I'll add the IMDB ID to the .nfo file for that movie's directory.  Same works for TV shows, especially when it is a remake - like Hawaii Five-O or Doctor Who which has 2 distinct versions.

With Plex, I think you are paying twice.  They got your $90 AND they are selling your watch/listen data to facebook/google/axion and every other data broker. If you agree, great. Enjoy.

> **eappell said:**
> 
[*]I've tried Jellyfin a couple times and it always gets stuck indexing my media. I mean like I wait DAYS, and in one case, a couple WEEKS, and it never finishes indexing. Not sure what I was doing wrong, but now that I have a new machine I'll try it again.
I can only guess that your directory layouts are wrong.  XMBC, Kodi, Plex, Jellyfin all use the same layout.

> **eappell said:**
> 
[*]I will hunt down that script, thank you. Sounds like exactly what I need. So that would also work with Docker/containerized apps?
A service on a network IP and port is all that matters. Doesn't matter at all if it is running on hardware, inside a virtual machine or inside a container.

> **eappell said:**
> 
[*]I appreciate the perspective on using SSH and VPN instead of an SSL cert!
SSL certs are weaker. That's the important thing. We also know that TLS v1.2 has been completely hacked, so if you have an older device that doesn't support TLS v1.3 it is probably negotiating the lower, hacked, version.  BTW, SSL is a generic term. Nobody should be using SSL the last 10-15 yrs. TLS has replaced it.  BTW, TLS doesn't secure anything.  It just provides point-to-point assurance that the packets aren't molested between those two points. In theory, it should provide assurances that the server is actually the server you intend, but even that can be spoofed if the DNS used has been hacked.  Almost all security has important, subtle, caveats that must also be true to work.  Beware.
[/LIST]
> **eappell said:**
> Thanks again for all of this great info. I will read it a couple more times and then take some action, most likely starting from scratch and get it working the way I want it to.

Practice makes perfect.
Don't forget to setup and test your backup and recovery methods BEFORE you put anything important on these systems.  Things break all the time.  Eventually, everything breaks, especially storage.  We can only hope that our storage doesn't break until after we're done using it for anything important. In the meantime, backups - automatic, daily, versioned, backups are the best solution to make failed storage an inconvenience, not a terrible year.

---

### Post by eappell on 2024-01-23
Ok, so the bottom line is you would recommend I use Ubuntu, running Jellyfin (my directories are the same as they were when I used XBMC back in the day, and have always worked with Plex, so I'm not sure why Jellyfin is so slow for me) and other apps in linux containers, access the machine from outside the network using SSH as a SOCKS proxy using your script, and Wireguard VPN or x2go. I don't know what some of these are, or how to use them, but I guess I'll have to invest some time in learning these, as well as the other technologies you mentioned like SSH-keys (Sorry!!). Did I get all of that right?

I was about to buy a newer Synology for all of this, but was convinced to instead purchase a dedicated machine for running plex and the other apps, leaving my NAS to just manage storage. I didn't expect to be spending so much time and effort to get this new machine working, but as a developer I am a big fan of doing it the "right way", rather than the "fast way". 

Thanks again for the help!
Eddie

---

### Post by TheFu on 2024-01-23
> **eappell said:**
> Ok, so the bottom line is you would recommend I use Ubuntu, running Jellyfin (my directories are the same as they were when I used XBMC back in the day, and have always worked with Plex, so I'm not sure why Jellyfin is so slow for me) and other apps in linux containers, access the machine from outside the network using SSH as a SOCKS proxy using your script, and Wireguard VPN or x2go. I don't know what some of these are, or how to use them, but I guess I'll have to invest some time in learning these, as well as the other technologies you mentioned like SSH-keys (Sorry!!). Did I get all of that right?

I was about to buy a newer Synology for all of this, but was convinced to instead purchase a dedicated machine for running plex and the other apps, leaving my NAS to just manage storage. I didn't expect to be spending so much time and effort to get this new machine working, but as a developer I am a big fan of doing it the "right way", rather than the "fast way". 

Thanks again for the help!
Eddie

I said how I do it.  Only you can decide what is best for your needs.  I don't know your full situation.  Like if you use an Apple tablet or phone, I have ZERO ideas.  I was a developer for about 20 yrs.  I still scratch itches today, but tend to do that with scripts, not C++. 

ssh and ssh-keys are the core for almost everything connecting machines together, so start there.  There are things about jellyfin that are slow, but there were things about plex that were slow too.  I know that the DB and metadata for Plex used over 100GB of storage while for Jellyfin, it used just 8GB for about 2x the amount of media.  Plus, Jellyfin can use my network tuner to record TV OTA and don't get me started about the ugly plex players.  Their on-screen overly always covered the subtitles, which drives me crazy.  Don't have that issue using Kodi for playback with the Jellyfin addon.

Jellyfin isn't perfect, but it is 1000x better for privacy.

Wireguard is the easiest, most secure, VPN to host at home.  Deploying it for 50 devices would be cumbersome, but for 5, it isn't a big deal.  There are some things about the setup I don't like, but compared to openvpn, it is by far easier to configure and less likely to have undesired security failures.

x2go is a fallback for a remote desktop, which should be avoided.  OTOH, x2go is the best of bad choices. There are better methods that don't use remote desktops. Certainly, nobody should be running video over any remote desktop. I hope that's obvious.  Media needs to be played locally, transferred as data to the local machine, if you don't just download it in advance, which is even smarter.  Humans can think ahead and plan.  Cellular data is for people bad at planning, IMHO.   Plus, I don't get any spam text messages. BONUS!

---

### Post by eappell on 2024-01-25
I think if I knew what was best for me I wouldn't have posted this. I don't know what's best for me. I just want a secure, decent, media server that I can use headless which will use my NAS for storage. What will accomplish that is what I've come here for. I appreciate your help! I will follow your suggestions because they are the most complete answer I've received. Hopefully it ends up accomplishing my goals.

---

