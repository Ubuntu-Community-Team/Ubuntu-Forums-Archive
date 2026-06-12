---
title: "Server 11.10 - set a static IP and now can't access the proxy"
date: 2012-03-02
forum: New to Ubuntu
---

### Post by iangarforth on 2012-03-02
Hi all,

Am very new to this.

I've set my IP on the server on /etc/network/interfaces from

```

auto eth0
iface eth0 inet dhcp

```

to 

```

auto eth0
iface eth0 inet static
address 10.15.187.20
netmask 255.255.25.192
broadcast 10.15.187.255
gateway 10.15.187.1

```

I checked /etc/resolve.conf but it already the correct DNS servers.  

In desperation, I changed /etc/apt/apt.conf to the actual IP address rather than proxy.local, but I'm still getting nowhere - apt-get update doesn't work and I can't ping anything.

Any ideas?

---

### Post by praseodym on 2012-03-02
> netmask 255.255.25.192
IMHO it needs to be
> netmask 255.255.25[COLOR="Red"]5[/COLOR].192

---

### Post by iangarforth on 2012-03-02
Thanks for the thought - I think I just mistyped that here on the forum, though - I'm certain it's 255.255.255.192 on the machine.  I'll check though (though even this surprised me - I thought it would be 255.255.255.0..?)

---

### Post by Iowan on 2012-03-02
> **iangarforth said:**
>  I thought it would be 255.255.255.0..?)
That would be more common, but if you want/need/have a smaller subnet, that subnet mask (AKA /26) will provide 62 hosts from  10.15.187.1 to 10.15.187.62.

---

### Post by iangarforth on 2012-03-04
Hi all,

Sorry all, I originally posted this [here]("http://ubuntuforums.org/showthread.php?t=1934565"), but I haven't really had any ideas yet that I can try...  I hope it's ok to ask it here.

I asked my system administrator to reserve me a static IP (10.15.187.20) which would be barred from the DHCP for a trial server I'm building (Ubuntu Server 11.10) on my school network.

I've set my IP on the server by changing /etc/network/interfaces from

```

auto eth0
iface eth0 inet dhcp

```

to 

```

auto eth0
iface eth0 inet static
address 10.15.187.20
netmask 255.255.255.192
broadcast 10.15.187.255
gateway 10.15.187.1

```

I checked /etc/resolve.conf but it already the correct DNS servers.  

In desperation, I changed /etc/apt/apt.conf to the actual IP address rather than proxy.local, but I'm still getting nowhere - apt-get update doesn't work and I can't ping anything ('host unknown'.

Any ideas?  I don't actually know that the IP I've tried to set is either working or barred from the DHCP but presume that there's no real way for me to test this?  Can anyone see anything I've done that's obviously wrong?

Cheers

---

### Post by nothingspecial on 2012-03-04
Merged.

Hi, rather than posting a new thread about the same subject, click the report abuse button and request that the staff move it to a different forum.

"Report Abuse" is confusing but you can use it to request a move also.

Thanks.

---

