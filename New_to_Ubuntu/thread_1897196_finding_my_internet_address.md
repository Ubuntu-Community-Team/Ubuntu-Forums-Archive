---
title: "finding my internet address"
date: 2011-12-18
forum: New to Ubuntu
---

### Post by Autodave on 2011-12-18
How do I find my internet address?

---

### Post by lechien73 on 2011-12-18
If you mean your public IP address on the Internet, then [http://www.whatismyip.com](http://www.whatismyip.com) is the easiest.

If you mean the IP address of your machine, then open a terminal window and type:

```
ifconfig
```

This lists all the network cards in your system, and the "inet addr" is the IP address.

Hope this helps.

---

### Post by HunterDX77M on 2011-12-18
> **Autodave said:**
> How do I find my internet address?

I just tried this and maybe its what you need:

```
/sbin/ifconfig
```

There is something called "inet addr." Is that what you are looking for?

---

### Post by Autodave on 2011-12-18
> **lechien73 said:**
> If you mean your public IP address on the Internet, then [http://www.whatismyip.com](http://www.whatismyip.com) is the easiest.

If you mean the IP address of your machine, then open a terminal window and type:

```
ifconfig
```This lists all the network cards in your system, and the "inet addr" is the IP address.

Hope this helps.


I am going to try and setup and remote desktop program to access my mom's computer that will be running Linux next week. (Finally got tired of fixing Windows crashes.)  I want to be able to "fix" things or show her how to do something from my home w/o running over there.

I am assuming that I will need her internet address to be able to set that up?

---

### Post by lechien73 on 2011-12-18
In that case, I'd recommend something like TeamViewer ([http://www.teamviewer.com](http://www.teamviewer.com)). I use it for remote support all the time. It works ok with Linux and is easy for the end-user to figure out.

Unless you were planning on installing a VPN or something, then opening up a remote desktop on the public IP address would be very risky.

---

### Post by CharlesA on 2011-12-18
+1 to TeamViewer. It's the least messy of the possible solutions.

---

### Post by Minnie1 on 2011-12-18
Hi,
   Check your internet IP address at [ip-details.com]("http://www.ip-details.com/") . it'll show your IP address, IP location, Geographic location map everything..

---

### Post by bodhi.zazen on 2011-12-19
My favorite has always been curl

```
curl ifconfig.me
```

At any rate, for you mother, just be sure you understand the security implications of VNC. I would advise you tunnel it over ssh or use FreeNX. Of the two, FreeNX is going to be faster.

---

### Post by Lars Noodén on 2011-12-19
> **bodhi.zazen said:**
> ...or use FreeNX. Of the two, FreeNX is going to be faster.

FreeNX is not yet in the Ubuntu repositories.  Do you have a recommended way for beginners to get it?  All the *.berlios.de links seem to have died.

---

### Post by MartijnNL on 2011-12-19
Like other's said: for remote support Teamviewer is one of the best solutions, no need for a VPN or something like that. And you don't need to know the IP address for it either (which makes it easy if this tends to change a lot).

---

### Post by CharlesA on 2011-12-19
> **Lars Noodén said:**
> FreeNX is not yet in the Ubuntu repositories.  Do you have a recommended way for beginners to get it?  All the *.berlios.de links seem to have died.

I have been using the version from here: [http://www.nomachine.com/download.php](http://www.nomachine.com/download.php)

> **MartijnNL said:**
> Like other's said: for remote support Teamviewer is one of the best solutions, no need for a VPN or something like that. And you don't need to know the IP address for it either (which makes it easy if this tends to change a lot).

Indeed. I've been known to use it to help friends or family out. Sometimes it's easier to just connect than try to squeeze information out of them over the phone. :)

---

### Post by anbinal on 2012-08-24
> **Autodave said:**
> How do I find my internet address?


You can easily  find your ip address at[ ip-details.com]("http://www.ip-details.com/") .Recently i checked my ip details here.I got accurate result.

---

