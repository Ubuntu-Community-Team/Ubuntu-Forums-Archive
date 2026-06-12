---
title: "Need Help Installing rTorrent on a Dedicated Server"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by TehEnergy on 2008-06-15
Hello eveyone,

I need some help with a seedbox.

I am thinking about setting up an account with OVH and purchasing [this dedicated server](http://www.ovh.co.uk/individual/products/kimsufi08.xml).

I don't want to pay an extra £30 (about $58.40) per month for Windows.

I have a choice of these Linux distrobutions for my operating system.

Cpanel
Ubuntu Desktop
Ubuntu Server
Debian
Open Suse
Linux Plesk 8.0
Fedora Core
CentOS
Extranet Group Work
Release 2
Release 1
Gentoo
Slackware
Easy Streaming
Xen
Proxmox

Which operating system should I chose to install rTorrent? Also, how would I go about installing rTorrent and remotely controlling it from a Windows box? Thanks.

Many thanks.

---

### Post by freduardo on 2008-06-15
Since its for a server I would either pick Debian or Centos (which is a rebuild of RHEL). But that's my opinion of course.

As for running and managing rtorrent remotely. I'd do it over ssh and screen.

You install and setup openssh on the server, and install Putty on the windows machine to connect to it. Then install and run screen on the server and run rtorrent within the screen session.
That way, you can always connect to the server via Putty (and ssh) and re-attach the screen session to get back to rtorrent.

---

