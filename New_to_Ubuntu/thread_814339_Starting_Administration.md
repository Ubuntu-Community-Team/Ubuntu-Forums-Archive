---
title: "Starting Administration"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by Diggla on 2008-05-31
Hi Folks

I have recently upgraded to Hardy Heron from Gutsy Gibbon.
This has given me some problems one being that when I try to access some administration applications, the computer will hang with "Starting Administration" being displayed on the toolbar. This will disappear and the application won't open.

---

### Post by alienexplorers on 2008-06-03
Try reinstalling sudo in synaptic.

---

### Post by hesjnet on 2008-06-03
I have this same problem. I tried to re-install sudo(i had to do "sudo synaptic" in the terminal to get it to open), but nothing changed!

I have downloaded a skype debian package that wont even open because of the system administrator process.

I'm really new to this and just ported from vista a month ago. I'm very pleased with ubuntu but I cant seem to get this to work.

Any ideas?

---

### Post by hesjnet on 2008-06-03
I fixed it!

check this to see if it works for you:
[http://ubuntuforums.org/showthread.php?t=723361&highlight=sudo%3A+unable+resolve+host]("http://ubuntuforums.org/showthread.php?t=723361&highlight=sudo%3A+unable+resolve+host")

[quote=PmDematagoda]Open the hosts file for editing with:-
Code:

gksudo gedit /etc/hosts

and edit it to make it look like this:-
Code:

127.0.0.1 localhost
127.0.1.1 icarus-laptop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

save the file.

That should fix the problem.[/quote]

You can do it in the GUI, like I did:
1. Left-Click the network icon (next to the clock)
2. Choose "Manual configuration"
3. Click "Unlock" and enter your password
4. Choose "Hosts"
5. Click "+Add"
6. Enter Ip-adress: 127.0.1.1 Alias: "YOUR-COMPUTER-NAME"
7. Click Ok

Done!

YOUR-COMPUTER-NAME should ofcourse be changed to the network name of you computer(you named it when you installed ubuntu)

---

### Post by Diggla on 2008-06-11
Hi Folks

Thanks for taking an interest in my query, sorry I haven't got back to you sooner with the fine weather i've been busy tending to my vegetable plot.  
Will hopefully try out the suggestions in the next few days and let you know how I get on.

Many thanks again.

Regards

Andy

---

