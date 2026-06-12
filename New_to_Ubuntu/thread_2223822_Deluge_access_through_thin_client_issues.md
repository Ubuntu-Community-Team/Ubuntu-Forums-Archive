---
title: "Deluge access through thin client issues"
date: 2014-05-13
forum: New to Ubuntu
---

### Post by karl14 on 2014-05-13
So I have setup deluge headless server using this guide ([http://www.havetheknowhow.com/Install-the-software/Install-Deluge-Headless.html](http://www.havetheknowhow.com/Install-the-software/Install-Deluge-Headless.html)) and I'm now trying to find/edit auth file to setup users to access the daemon via thin clients from windows. I can't find the auth file in the place where most older threads state /.config/deluge/auth.

I have managed to track this down /var/lib/deluged/config but I cannot get into the config folder as I get an error message saying permission denied.

---

### Post by dannyboy79 on 2014-05-13
i use transmission for what you're trying to accomplish. it's very versatile, it has a client but as well as a webui for adding torrents from anywhere in my LAN. Have you tried the password "deluge"?

I am curious why you want to run a deluge client on the windows side, deluge has the same ability as transmission where you can admin the server through a web browser. here's a great guide IMO [https://wiki.archlinux.org/index.php/deluge#Setup](https://wiki.archlinux.org/index.php/deluge#Setup)

---

### Post by HiImTye on 2014-05-13
the simplest setup is to use the webui and then use a browser plugin, such as [BitTorrent WebUI++](https://addons.mozilla.org/en-US/firefox/addon/bittorrent-webui-0222/)

---

### Post by dannyboy79 on 2014-05-15
you don't need a browser plugin if you enable the webui of your transmission daemon

---

### Post by HiImTye on 2014-05-15
you don't 'need' a browser plugin for Deluge either, the plugin lets you automagically add magnets or torrents to the WebUI of your configured torrent client
(which you could have discovered by clicking on it)

---

### Post by dannyboy79 on 2014-05-15
oh so the plugin allows you to easily add torrents to your webui without having to open the webui? as it stands now all i have to do is find a torrent i want, right click on it and tell it to copy the torrent link, then i go to my webui and click add torrent, then I paste what's in the clipboard and it auto starts downloading the torrent.

---

### Post by HiImTye on 2014-05-15
yes, it saves you the trouble of doing that, which is esp useful if you want to download 10 or more torrents at once ;)

---

