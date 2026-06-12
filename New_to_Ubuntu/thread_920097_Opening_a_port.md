---
title: "Opening a port"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by h8uthemost on 2008-09-14
Hey guys,

I'm currently using Ubuntu through Wubi. And I'm deciding to switch to the KTorrent bittorrent client. So hopefully someone here has used and knows this client.

I'm having trouble opening a port for it. Before I was using Deluge. And I had no problem opening a port for Deluge. I went into my routers setting, and simply opened a new port, and added that port to Deluge.

But now I tried the samething for KTorrent, but the little triangle on the bottom left hand side of KTorrent is still yellow. I posted this on the KTorrent forums, but the only response I've gotten so far is that I must be firewalled.

Well, don't you have to manually enable a firewall in Linux? Because as I mentioned, Deluge has no problem with the port I opened for it. And I didn't allow Deluge in any Linux firewall.

So what do you guys think? Am I firewalled(which I've never messed with the Linux firewall before, so I have no idea how to use it), or is there something else I need to do?

Thank you for any help.

---

### Post by pavel989 on 2008-09-14
I still think its a problem in your router, maybe u need to set up port forwarding?

also have a look at [https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)

---

### Post by iaculallad on 2008-09-14
By default, all ports in Ubuntu are opened. You have to manually allow the configured port (port-forward) your KTorrent app is using on your router/firewall.

---

### Post by tuxxy on 2008-09-14
What is the problem, slow download or no conectivity?

---

### Post by h8uthemost on 2008-09-14
Pretty much both tuxxy. If I open the same torrent in Deluge that I have in KTorrent, and I'll connect to a bunch of people. In KTorrent, I'll be lucky if I'm connecting to one.

> **iaculallad said:**
> By default, all ports in Ubuntu are opened. You have to manually allow the configured port (port-forward) your KTorrent app is using on your router/firewall.

What do you mean by this? Do you mean to type the port that I opened in my router into KTorrent? If so, then I've done this already.

> **pavel989 said:**
> I still think its a problem in your router, maybe u need to set up port forwarding?

also have a look at [https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)

I don't see how since another client had no problem becoming connected. But I'll take a look at the link you gave me. Thank you.

---

### Post by iaculallad on 2008-09-14
> **h8uthemost said:**
> 
What do you mean by this? Do you mean to type the port that I opened in my router into KTorrent? If so, then I've done this already.


Yes, the port you opened in your Router/Firewall should be similar to the configured port your KTorrent is using.

> i.e:
65530 = Router/Firewall
65530 = KTorrent


---

### Post by h8uthemost on 2008-09-14
Yeah, that's what I did iaculallad.

Ok, so I tried what I found in this thread:

[http://www.ubuntu-unleashed.com/2008/05/howto-take-use-setup-and-advantage-of.html](http://www.ubuntu-unleashed.com/2008/05/howto-take-use-setup-and-advantage-of.html)

It's for the uncomplicated firewall. Now, once I typed sudo ufw enable in terminal, Deluge was no longer connectable. So I then typed this sudo ufw allow "number of my port" in terminal, and Deluge was then connectable again.

So, I tried typing that same command with the port number that I opened for KTorrent, but I'm still getting the yellow triangle. So this makes me to believe that has absolutely nothing to do with the firewall.

EDIT: Do I have to manually allow KTorrent, kind of like how you have to do in Windows firewall?

---

### Post by nowshining on 2008-09-15
are u seeding or downloading in ktorrent?

---

