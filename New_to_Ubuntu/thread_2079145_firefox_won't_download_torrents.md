---
title: "firefox won't download torrents"
date: 2012-11-01
forum: New to Ubuntu
---

### Post by sallymc on 2012-11-01
Hi hi.  Firefox won't  download torrents in 12.04.  The "open with" option is Movie Player (default) and I can't change it to "Transmission (default)", so nothing happens.  Have tried changing the default through Firefox/Applications/magnet/ to use transmission  default, but no luck.  Please help!
Sallymc

---

### Post by sallymc on 2012-11-01
Hi hi.
I've got Transmission installed on my box but when I download a torrent file, I am forced to open it through Music Player (default), so of course nothing works.    I have changed the Firefox Application for bittorrent seed file and magnet from Always Ask to Transmission (default), but it makes no difference.

Perhaps I need to change it through the Terminal.  I have put in the following codegksudo gedit /etc/gnome/defaults.list
but no application/x-bittorrent= line comes up.

Hope someone can help, so thanks in advance.
Sallymc

---

### Post by zeroseven0183 on 2012-11-01
Hi sallymc, please try this

1. click Preferences > Option
2. go to the Applications tab and look for "magnet" on the list.
3. select "Always ask"
4. then click OK

Now, when you download a torrent file from the web you will be asked the action needed. If Transmission is not in the options, click on  "Use other"  and navigate to /usr/bin on your file system. Please kook for "transmission"  or "transmission-gtk" then select that.

---

### Post by mike555 on 2012-11-01
perhaps this will help;
[https://help.ubuntu.com/community/BitTorrent](https://help.ubuntu.com/community/BitTorrent)

---

### Post by sallymc on 2012-11-01
> **mike555 said:**
> perhaps this will help;
[https://help.ubuntu.com/community/BitTorrent](https://help.ubuntu.com/community/BitTorrent)

Thanks Mike.  Unfortunately, this is what I have been doing, but it ALWAYS opens in Music Player, and I can't seem to change the default to Transmission.  Most annoying.  Is there a way to do it through the Terminal?  Even if I save it to Downloads, it still doesn't download from there.
Sallymc

---

### Post by philinux on 2012-11-02
Try this.

Right click on any torrent file and choose "save link as" and save it to your desktop.

Then right click on the downloaded torrent file and choose properties.

Click the open with tab then choose Transmission and then click "make this default"

{Threads Merged - please only start one thread per problem cheers)

---

