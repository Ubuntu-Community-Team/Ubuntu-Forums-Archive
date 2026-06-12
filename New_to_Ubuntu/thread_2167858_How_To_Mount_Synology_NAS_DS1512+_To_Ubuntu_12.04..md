---
title: "How To Mount Synology NAS DS1512+ To Ubuntu 12.04.2???"
date: 2013-08-15
forum: New to Ubuntu
---

### Post by desmond_t2 on 2013-08-15
Hi guy,

I have just install Ubuntu 12.04.2 on my computer and I am a noob in this new OS.
I use to have windows 7 but i have some issue with the OS so i decided to try out Ubuntu.

I have a Synology NAS that is connected to my computer but i just cant mount the network folder onto my new OS.

Can anybody help me? Thanks in advance

---

### Post by newbie-user on 2013-08-17
I assume that your NAS has smb capabilities, since you were using it with Win7. So for Ubuntu, go open your home folder, then go up to the menu bar and click File > Connect to Server. Enter the settings as shown below and your username and password.
[ATTACH=CONFIG]245446[/ATTACH]

---

### Post by desmond_t2 on 2013-08-17
Hi newbie-user,thanks for the reply=)

I have manage to mount  4 of my main folder (See attachment Selection_001). But i just cant mount one of them(See attachment Selection_002).

Don't understand why its like that...

Thanks

---

### Post by newbie-user on 2013-08-18
Hmm... Is there a limit on how many smb shares are allowed by the NAS? Maybe the share settings are incorrect? Maybe you can try sharing the folder via another method, like FTP or NFS.

---

### Post by desmond_t2 on 2013-08-18
hi [COLOR=#000000]newbie-user,

[/COLOR]> [COLOR=#000000]Is there a limit on how many smb shares are allowed by the NAS?[/COLOR][COLOR=#000000]

I dont think so....

[/COLOR]> [COLOR=#000000]Maybe the share settings are incorrect? [/COLOR][COLOR=#000000]

The share setting are all the same for all the folders...

[/COLOR]> [COLOR=#000000]Maybe you can try sharing the folder via another method, like FTP or NFS.[/COLOR][COLOR=#000000]

How do I share the folder via NFS?[/COLOR]

---

### Post by sandyd on 2013-08-18
> **desmond_t2 said:**
> hi [COLOR=#000000]newbie-user,

[/COLOR][COLOR=#000000]

I dont think so....

[/COLOR][COLOR=#000000]

The share setting are all the same for all the folders...

[/COLOR][COLOR=#000000]

How do I share the folder via NFS?[/COLOR]
According to [Amazon]("http://www.amazon.com/Synology-DiskStation-DS1512-Network-Server-DS1512/dp/B005XY0QW0"), the unit supports NFS. Unfortunately, I can't find a user manual for it (and I use a SAN instead of  a NAS) so you may have to browse around the settings page to find out the correct settings to use with NFS.

---

