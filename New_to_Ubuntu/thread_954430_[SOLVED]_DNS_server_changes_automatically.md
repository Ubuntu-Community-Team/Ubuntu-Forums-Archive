---
title: "[SOLVED] DNS server changes automatically"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by omkarwagh on 2008-10-21
Hello.

Ive been using Ubuntu for over a year now and I am having a trivial but recurring problem that keeps irritating me. 
I'm not sure if it's a bug or a design feature or my comp being hacked into so I'm posting it here first.

I am connected to a LAN network that has a certain DNS server. When add the server into the list of DNS servers, the network seems to work perfectly fine. 

However, for some unknown reasons, the DNS server simply disappears from the list after a few days and is (sometimes) replaced by some other server that I have no idea of. This is especially noticed whenever I connect to a  wireless network although I have not been able to replicate this. 

Is there any way for me to find out what the problem may be?

Thanks in advance

---

### Post by jemate18 on 2008-10-21
Is the DNS you entered completely lost? Or is it that a new one gets added?

---

### Post by omkarwagh on 2008-10-21
it's not completely lost. another one get's added in it's place.

---

### Post by fiztlen on 2008-10-21
Are you using DHCP?  If your lease refreshes every few days the client may clobber your DNS settings.

Check this thread:
[http://ubuntuforums.org/showpost.php?p=2465391&postcount=5](http://ubuntuforums.org/showpost.php?p=2465391&postcount=5)

Note that using "prepend" will keep the DHCP-specified values as fallback.

---

### Post by omkarwagh on 2008-10-21
i am using static ip's for my lan(eth0 connection)
and the roaming mode for my wifi(wlan0 connection)

---

### Post by Sealbhach on 2008-10-21
You could perhaps switch to Open DNS. 

Instructions are here:

[https://www.opendns.com/homenetwork/start/device/ubuntu](https://www.opendns.com/homenetwork/start/device/ubuntu)

If you prepend the domain names to

/etc/dhcp3/dhclient.conf

it makes them stick.


.

---

### Post by omkarwagh on 2008-10-22
well i'm not sure if the problem is solved but it certainly hasn't changed the DNS servers after i added the prepend line.

if this was the problem, then there's something i don't understand here. if i'm using static ip's, why is it that the dhcp configuration is happening? meaning if i choose 

that's a bit confusing...or is it being called when i connect to a wireless network? i'd like to understand what happens. thanks to all.

---

