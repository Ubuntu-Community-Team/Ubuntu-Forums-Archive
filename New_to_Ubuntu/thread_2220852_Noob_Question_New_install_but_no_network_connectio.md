---
title: "Noob Question: New install but no network connection"
date: 2014-04-29
forum: New to Ubuntu
---

### Post by WiredWorm on 2014-04-29
Hi there,

I'm a total noob to Ubuntu so please go easy on me ;)

I've just done a totally fresh install of Ubuntu Server 14.04 LTS onto a HP Proliant DL380 G7 Server.

The install process itself seemed to go nice and smoothly and the network setup side of things seemed to work as I managed to open another terminal session and succesfully ping remote hosts.

But now, the process has completed and it's done it's final reboot.  Now when I try to ping a host it tells me 'unknown host [hostname]' and pinging by IP gives me a big fat 'Network unreachable'.

Can someone please help me get the IP side of things up and running again?

Many thanks

Pete

---

### Post by migs73 on 2014-04-29
Had the same problem my self and this worked for me;

In a terminal type

```
sudo nano /etc/NetworkManager/NetworkManager.conf
```

put in your password when requested (nothing will show as you type)

this should open a file with something like this in it;

```

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

```

if there is a line that says 'managed=false' as above, change it to 'managed=true' and press Ctrl+X to exit, then Y (this will save changes), and then enter to keep the same file name.
Then in the terminal;

```
sudo service network-manager restart
```

and that should now work. If the file does not say 'managed=false' then you don't have the same issue as I did so just exit the file (Ctrl+X) and then press N to destroy any changes you may have accidentally made!

Good Luck

Mike

BTW We all go easy on Noobs on this forum, we all were once and even although I've used linux for over 5 years I'm still learning new stuff, so I'm still a Noob myself
:lolflag:

---

### Post by WiredWorm on 2014-04-29
Hi,

Thanks for the suggestion.

It looks like the network manager service isn't installed though.  There's no NetworkManager folder under /etc, nor is there a conf file.  And trying to restart the service results in a 'unrecognised service' error message.

I did a vanilla install and didn't add any additional options or modules.

Regards

Pete

---

### Post by migs73 on 2014-04-29
OK thats because you are running the server version, I'm not sure if network manager will work on a headless system as it is made for Gnome.
Maybe somebody with more experience with this version will be able to help........as I said I'm still learning :)

---

### Post by Iowan on 2014-04-29
What are the results of ```
ifconfig -a
```
and ```
route -n
```
and can you post the contents of */etc/network/interfaces*

---

### Post by WiredWorm on 2014-04-29
Hello again,

The route -n command returned nothing bar the headers so I presume that means the routing table is empty.

The other two commands returned these.

[ATTACH=CONFIG]252647[/ATTACH][ATTACH=CONFIG]252648[/ATTACH]

Apologies for posting as images and not just copy-pasting, but i'm connected via an ILO so I can't actually copy as text.

No clue about the strange interface names.  That's also how they appeared during the installer and the one named differently was the only one where the autoconfig worked, so i'm presuming it's the one which was patched to the LAN.

Many thanks

Pete

---

### Post by Iowan on 2014-04-29
I've never seen emX designations before (still on 12.04 here) , but [this]("http://ubuntuforums.org/showthread.php?t=2150517") thread discusses them.  Looks like a lot of interfaces... none of which have an IP address. :(
Was that all of the interfaces file... looks like more after "iface" line.

---

### Post by WiredWorm on 2014-04-29
That's it all - what you see chopped is just the prompt for the next command.

If it's easier then I can try a reinstall with a previous version.

The machine it's installed on is an HP DL380 G7, which, if I remember correctly, has 4 NIC's on the mainboard.  As mentioned previously the network was working fine up until the first reboot after installing.

---

### Post by Iowan on 2014-04-29
[Here]("http://ubuntuforums.org/showthread.php?t=2220120") is another, similar thread that might be worth checking...

---

### Post by WiredWorm on 2014-04-30
Thanks.  So I understand this is basically a way of binding an interface name to specific interfaces?

So I can do an ifconfig -a command and then use the information from that to build the required file.  I just need to make sure the right interface has the 'renamed4' name and that should fix the problem?

---

### Post by WiredWorm on 2014-04-30
Just to confirm that creating the [COLOR=#000000]/etc/udev/rules.d/70-persistent-net.rules file with the correct entries fixed the problem :-)

Pete

[/COLOR]

---

