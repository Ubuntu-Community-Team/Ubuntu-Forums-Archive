---
title: "DreamWeaver 8, Nero, Utorrent"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by mac143_01 on 2008-05-30
Please help me and teach me on how to install and run Dream Weaver 8, Nero, Utorrent on Xubuntu?

---

### Post by rolnics on 2008-05-30
Is there any specific reason you want to install these? Why not try the linux alternatives?

I'm not sure of an alternative for Dreamweaver, but for Nero, there's Gnome baker, k3b as examples. Utorrent, well have a quick search on these forums, i've read a load of torrent threads, but if you really want these programs then install wine.

Open up Synaptic Program Manger. Click the following System -> Administration -> Synaptic.  Then once there do a search for wine, click the box and apply, enter your password. Once you've got that installed, assuming you have the Dreamweaver and Nero disks pop them in and see what happens. Or better still have a look on wine's website. do a google search for wine hq.

---

### Post by Joeb454 on 2008-05-30
You need to look at [Wine]("http://www.winehq.org/site/download-deb") and install that.

I know uTorrent can be installed under Wine and rn perfectly - it says so on their website, though I think you'll have more issues with Dreamweaver and Nero. The best way to check is on the [Wine AppDB]("http://appdb.winehq.org")

---

### Post by eriqjaffe on 2008-05-30
There are Linux-native alternatives for all of those.

Dreamweaver's the trickiest to truly replicate, but you might want to look into Kompozer.

As far as Nero, there's Brasero.

For uTorrent, there's Transmission or Deluge.

All of these are available in the repositories, and are a mere "sudo apt-get install" away.  Heck, Brasero and Transmission are installed by default with Xubuntu.

---

### Post by Joeb454 on 2008-05-30
Deluge is a better torrent alternative to uTorrent, simply because Transmission is what I tend to call a "Click & Go" torrent client. Whereas Deluge offers a lot more control over the things such as the ports, bandwidth per torrent etc. :)

---

