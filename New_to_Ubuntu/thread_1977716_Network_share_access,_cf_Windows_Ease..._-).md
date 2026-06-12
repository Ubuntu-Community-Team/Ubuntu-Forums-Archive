---
title: "Network share access, cf Windows Ease... :-)"
date: 2012-05-10
forum: New to Ubuntu
---

### Post by n3mmr on 2012-05-10
Under Windows, accessing a network share from a Solaris ZFS host seems difficult.

With Gigolo I specified the share, and gave the name and password for the file and dir owner on the CIFS server,

When I then tried to access the share, I was told I had no access right.

What is the proper way in Ubunto/Gigolo to deal with that? Must I set up a UID mapping, or change my numeric UID on Ubuntu?

On any flavor of Windows, you just give the name and password, and off you go.

---

### Post by jerome1232 on 2012-05-10
[Gigolo?]("http://en.wikipedia.org/wiki/Male_prostitution")

Anyways, does anything [HERE]("https://help.ubuntu.com/community/MountWindowsSharesPermanently") help?

---

### Post by n3mmr on 2012-05-13
> **jerome1232 said:**
> [Gigolo?]("http://en.wikipedia.org/wiki/Male_prostitution")

Anyways, does anything [HERE]("https://help.ubuntu.com/community/MountWindowsSharesPermanently") help?

I forgot to say this is for ubuntustudio 12.04.

Gigolo is a small tool that supposedly mounts anything it's told to mount. But it seems not to do it the easy and direct way a windows machine can.

The [HERE]("https://help.ubuntu.com/community/MountWindowsSharesPermanently") link above explains an unbearably complex way to permanently mount a windows network share, what I was looking for was a way to do it like they do in windows: i e a tool that mounts a share w/o much hassle beyond telling a tool what machine/ip address and share name to mount and provide the passwd of a user on that server, and then have the same access rights to the share as that user would have locally on the server. Or at least nearly so.

---

### Post by jerome1232 on 2012-05-13
Open Nautilus, click on Browse the Network in the left hand pane, then double click to your server.

If it doesn't for some reason show up in there, try pressing ctrl+L, then typing 'smb://ipaddress/sharename' or 'smb://hostname/sharename' without the quotes of course.

---

### Post by n3mmr on 2012-05-14
> **jerome1232 said:**
> Open Nautilus, click on Browse the Network in the left hand pane, then double click to your server.

If it doesn't for some reason show up in there, try pressing ctrl+L, then typing 'smb://ipaddress/sharename' or 'smb://hostname/sharename' without the quotes of course.

I tried gigolo again, and this time it works. I hadn't understood how to enter things like the server and the share names.

It works perfectly.

Nautilus complains there's no windows server telling it what's there.

All my shares are on an OpenIndiana server using Solaris CIFS controlled from within ZFS, so maybe it doesn't let on it has anything until you show you already know. Gotta look at that, I suppose.

I'll try your other suggestions. It's always preferable not to use any extra tools, if you don't have to.

---

