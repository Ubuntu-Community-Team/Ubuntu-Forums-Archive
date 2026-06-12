---
title: "ubuntu media server for windows net"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by murdison on 2008-10-28
may not be the best place to ask... this is my first time posting!!

1) have installed Cowbell to try and tag some of my ripped CDs, ongoing mega project to bring all of my CDs into a server running Ubuntu Hardy H.  Program will not/cannot connect to soap.amazon.com...   therefore doesn't work.  Anyone have any ideas?

2) how do I remote access my Ubuntu desktop from a networked connected Windows machine? I've used Windows Remote Access to run other networked windows boxes... would be helpful to monitor the progress of the mega project in 1)

3) anyone know whether I can run Linksys Music Bridge directly from Ubuntu? Currently have it on a Windows box that runs iTunes with the library on the Ubuntu box on the network... run into problems with bandwidth when the network is used by my kids

4) is there a way to have my Media Drive automount when Ubuntu starts up...  thinking of the situation of power loss/restart and not having my music library available without physically remounting the drive

Thanks in advance for your input!!

---

### Post by billgoldberg on 2008-10-28
> **murdison said:**
> may not be the best place to ask... this is my first time posting!!

1) have installed Cowbell to try and tag some of my ripped CDs, ongoing mega project to bring all of my CDs into a server running Ubuntu Hardy H.  Program will not/cannot connect to soap.amazon.com...   therefore doesn't work.  Anyone have any ideas?

2) how do I remote access my Ubuntu desktop from a networked connected Windows machine? I've used Windows Remote Access to run other networked windows boxes... would be helpful to monitor the progress of the mega project in 1)

3) anyone know whether I can run Linksys Music Bridge directly from Ubuntu? Currently have it on a Windows box that runs iTunes with the library on the Ubuntu box on the network... run into problems with bandwidth when the network is used by my kids

4) is there a way to have my Media Drive automount when Ubuntu starts up...  thinking of the situation of power loss/restart and not having my music library available without physically remounting the drive

Thanks in advance for your input!!

1. /

2. see [http://linuxowns.wordpress.com/2008/10/28/share-ubuntu-folders-with-windows-samba/](http://linuxowns.wordpress.com/2008/10/28/share-ubuntu-folders-with-windows-samba/)

This is just to share/stream media/files/printers with windows machines. 

Remote access:

[http://www.howtoforge.com/configure-remote-access-to-your-ubuntu-desktop](http://www.howtoforge.com/configure-remote-access-to-your-ubuntu-desktop)


3. /

4. I'll leave this one to someone else. Google will help you on this one.

---

### Post by aeiah on 2008-10-28
1. i dont know about cowbell. if it doesnt work and you're sure it isnt a network/firewall issue then its probably because amazon has updated their website structure and cowbell is out of date. perhaps the developers have brought out a new version to solve this problem. you're best going on their website to find out. 

there are alternatives like ex falso and easytag which may be decent alternatives

2.

3. probably not. but what do you use this for? is it just so you can, on a computer on your network running itunes, stream music from the server? because there are options such as daap (which should work fine for itunes) and UPnP which will also allow you to stream other media.

4. do you mean mount the media drive on the server or on the client pcs? where is the media drive currently? if the media drive is just a harddrive or partition pysically attatched to your server, you can have it automount by configuring /etc/fstab. there are plenty examples on this forum for that.

if you meant something involving networking, then you'll use samba, and set it to mount on boot or at a specific time after boot perhaps, if a lot goes on during boot.

---

### Post by murdison on 2008-10-29
> **aeiah said:**
> 1. i dont know about cowbell. if it doesnt work and you're sure it isnt a network/firewall issue then its probably because amazon has updated their website structure and cowbell is out of date. perhaps the developers have brought out a new version to solve this problem. you're best going on their website to find out. 

there are alternatives like ex falso and easytag which may be decent alternatives

2.

3. probably not. but what do you use this for? is it just so you can, on a computer on your network running itunes, stream music from the server? because there are options such as daap (which should work fine for itunes) and UPnP which will also allow you to stream other media.

4. do you mean mount the media drive on the server or on the client pcs? where is the media drive currently? if the media drive is just a harddrive or partition pysically attatched to your server, you can have it automount by configuring /etc/fstab. there are plenty examples on this forum for that.

if you meant something involving networking, then you'll use samba, and set it to mount on boot or at a specific time after boot perhaps, if a lot goes on during boot.
Thanks for the replies.

I don't have any problems seeing the internet and downloading, so I'm not sure if there is any issue with firewall, but I'm not sure how to test that out otherwise. I'll do some research for the alternatives that you suggest.

I may have a problem with vnc since my windows box is on VISTA. I've contacted with request for edu version of "personal version"

The music bridge is a little wired/wifi box that plugs into my amplifier and receives streamed music via a utility program that runs in windows. My library lives on the ubuntu box and is accessed by share as a mapped network drive through the VISTA box. iTunes on VISTA points to the library on the ubuntu box and the utility works with iTunes to play through the amp, and onto the speakers around the house.

I was hoping to have the hard drive in the ubuntu box (a separate drive just for the library) automount in ubuntu whenever it restarts. Currently I have to physically go to ubuntu and "remount" the hard drive by selecting it in "Places".  I've looked around Samba a little, but haven't found where to do what you suggest...

Thanks again!!

---

