---
title: "transmission doesn't work"
date: 2012-03-22
forum: New to Ubuntu
---

### Post by Carnivorum on 2012-03-22
Bs'd

When I try to download something, Transmission opens, but the downloads remain on 0%

What can I do about that?

---

### Post by ashhab2010 on 2012-03-22
does it happen for one torrent or for all??... there might be no seeds or if ur using an ip blocking software ,it might be causing problems.

---

### Post by ashhab2010 on 2012-03-22
try using ktorrent from Ubuntu soft centre... i found it better than deluge and transmission. if ur torrent works on ktorrent then transmission has a prob..

---

### Post by Carnivorum on 2012-03-22
> **ashhab2010 said:**
> does it happen for one torrent or for all??... there might be no seeds or if ur using an ip blocking software ,it might be causing problems.

Happens for all.

As far as I know, I have no ID blocking software.

---

### Post by ajgreeny on 2012-03-22
Direct connection or on a proxy?
Have you enabled port forwarding in transmission preferences network tab?
Have you made any other changes to the preferences?

---

### Post by ashhab2010 on 2012-03-22
Transmission is recognized as a seriously buggy bittorrent client
try using ktorrent
```
sudo apt-get install ktorrent
```

---

### Post by ajgreeny on 2012-03-22
> **ashhab2010 said:**
> Transmission is recognized as a seriously buggy bittorrent client
try using ktorrent
```
sudo apt-get install ktorrent
```
Really?  I've used it for many years without a problem.  It regularly gives me download speeds at the maximum of my ISP's line rate.

I have used ktorrent in the past when using kubuntu-deskltop on top of an original ubuntu install, but I found it cumbersome and unwieldy in comparison with transmission.

---

### Post by asmoore82 on 2012-03-22
> **ajgreeny said:**
> Really?  I've used it[transmission] for many years without a problem.  It regularly gives me download speeds at the maximum of my ISP's line rate.

[SIZE="3"]Big +1[/SIZE]

---

### Post by 3Miro on 2012-03-22
> **ashhab2010 said:**
> Transmission is recognized as a seriously buggy bittorrent client
try using ktorrent
```
sudo apt-get install ktorrent
```

I used Ktorrent some time ago when I was using KDE, but now that I use XFCE I use Transmission and it is simply awesome. I don't know what you mean when you say "recognized as buggy".

@OP: Issues with torrents can come from blocked ports. Check the firewall settings and you can change the default ports just in case the ISP has blocked them.

---

### Post by blueshead on 2012-03-22
Are you running a firewall ? In your router or computer?

You might have a port blocked that affects Transmission..

---

### Post by JodiBosa on 2012-03-22
first question is whether it's your network, gateway, etc...

---

### Post by Carnivorum on 2012-03-25
Works OK now, without any problems, thanks everybody.

---

### Post by chipbuster on 2012-03-25
> **Carnivorum said:**
> Works OK now, without any problems, thanks everybody.

Would be nice to know what you did, for the people from the future.

---

### Post by Carnivorum on 2012-03-27
> **chipbuster said:**
> Would be nice to know what you did, for the people from the future.

Bs'd

I didn't do anything, I think I was trying to download two files that just didn't want to.  

All the rest works now, and also the old ones that refused to do anything, work now.   

Don't really know what happened.

---

