---
title: "[SOLVED] network behind firewall?"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by slughappy1 on 2008-09-06
I am curious how I can set up a network between my Desktop and Laptop. Both are running Ubuntu 8.04, but I have a Linksys router. I have looked in the past, but I couldn't find out how to set it up. Where can I find a how-to or guide?

---

### Post by ggaaron on 2008-09-06
And what exactly do you want?

net--router--pc--pc
net--pc--pc
net--pc--router--many times pc
or something else?

---

### Post by slughappy1 on 2008-09-06
I want it to be internet -> router -> 2 computers. That should be the setup to share files between them, right?

---

### Post by ggaaron on 2008-09-06
It can be, for sharing files there are many possible layouts.

Seems pretty straightforward - configure router's internet connection, turn on dhcp. Now any computer connected to your router will be able (or should be) to contact the internet, also they should be able to contact themselves.

There is no setting up PCs, just configure your router - follow the manual for it or something.

---

### Post by slughappy1 on 2008-09-06
Well I found a site that said that all I needed to install is openssh-server and openssh-client. So I installed both and was able to use gFTP to SSH2 into my other computer. I was expecting it to transfer faster, it is only transferring around 2400 KB/s. Shouldn't it be going faster?

---

### Post by cwsnyder on 2008-09-06
It will be faster if both computers are wired to the router.  If one or more is connected wirelessly, you are limited to the slowest rating of the wireless LAN cards/router speeds.  For example, if one of the cards was only rated at 802.11b, your fastest speed would be about 54 Mbps, the top speed for that rating.

---

### Post by Paul41 on 2008-09-06
> **slughappy1 said:**
> Well I found a site that said that all I needed to install is openssh-server and openssh-client. So I installed both and was able to use gFTP to SSH2 into my other computer. I was expecting it to transfer faster, it is only transferring around 2400 KB/s. Shouldn't it be going faster?

Right now I only have a Ubuntu server and I am using it to share files with Windows (unfortunately) laptops. I am using Samba to do this since it is sharing with Windows. Samba is not required for sharing between Linux machines but it will work and you could then mount a directory instead of using FTP. You may be able to do this without Samba also for Linux to Linux but I have never done it so I am not sure how.

I use FTP to this server also for my work computer instead of putting it on my home network and FTP seems slower to me.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by slughappy1 on 2008-09-06
Wow I didn't even think of that. I had my laptop connected wirelessly and it was transferring around 2400 KB/s. I plugged an ethernet cable to my laptop, and now it's transferring aroung 6700 - 6900 KB/s.

---

### Post by ggaaron on 2008-09-07
I think that your first question was a wrong one, you've asked how to connect two computers with a network, but you wanted to know how to exchange files between them. Ssh is one option, personally usually I just use apache web server and symlinks to files that I want to share, fast, easy for both server and client (only web browser needed to connect) downside is that you can't upload anything in this layout. You can also use an ftp server, but I find it a lot more complicated than ssh or apache.

For the speed - ssh will be slower than for example http+apache as it is encrypted.

---

