---
title: "HOWTO: Edgy Install of Gnome Network Manager without connection"
date: 2006-10-27
forum: Outdated Tutorials &amp; Tips
---

### Post by gotgenes on 2006-10-27
I recently installed Ubuntu 6.10 Edgy Eft and to my horror, support for my wireless NIC was terrible with the Network Settings application, even worse than with Dapper. To make matters worse, I couldn't even get my NIC to work with Network Settings. I had no connection to the Internet from my computer which needed Network-Manager to do so, thus, a Catch-22.

Here I offer those who find themselves in a similar situation (needing to get NM to get to the net, but unable to get to the net to get NM in the first place via apt-get) a bit of help. Please note this is for Ubuntu (Gnome) only; KDE users will need knetworkmanager, so if a Kubuntu user wants to wrap up those respective debs and post them here, please, do.

What you will need:
[LIST]
[*]a computer that does have access to the net (presumably how you're reading this)
[*]portable storage (USB key, thumb drive, portable hard disk, etc)
[/LIST]

How To:
[LIST=1]
[*]Download the debs from [http://gotgenes.com.nyud.net:8080/network-manager-gnome_debs.tar.gz](http://gotgenes.com.nyud.net:8080/network-manager-gnome_debs.tar.gz) and place the file somewhere convenient (I'll use /tmp/)
[*]Extract the contents
```

tar -xzvf network-manager-gnome_debs.tar.gz

```
[*]Add this folder as a local repository to your /etc/apt/sources.list file. Add the following line
```

deb file:/tmp nm-debs/

```
Please use the appropriate paths for your situation. Here is assuming you have followed as I did and have unpacked the files into /tmp/nm-debs/
[*]Update apt
```

sudo apt-get update

```
[*]Install Network Manager
```

sudo apt-get install network-manager-gnome

```
[/LIST]

I hope this helps.

Chris

---

