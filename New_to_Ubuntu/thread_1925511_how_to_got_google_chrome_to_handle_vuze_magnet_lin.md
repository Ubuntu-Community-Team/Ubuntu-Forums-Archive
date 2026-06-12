---
title: "how to got google chrome to handle vuze magnet links"
date: 2012-02-14
forum: New to Ubuntu
---

### Post by jbb1996 on 2012-02-14
I'm so confused
I click in a magnet links and nothing

I am using ubuntu 11.10 64bit 
and vuze and  google chrome :confused:

---

### Post by Magic_Spehar on 2012-03-04
Same issue here.  I did already some "research" and the former solution with gconftool doesn't work anymore ...

---

### Post by haqking on 2012-03-04
[http://wiki.vuze.com/w/Magnet_link](http://wiki.vuze.com/w/Magnet_link)

---

### Post by Magic_Spehar on 2012-03-09
Hi Haqking, thx for the link but that doesn't work for me.

I have found a solution to this problem in Ubuntu 11.10.

* sudo gedit /usr/share/applications/azureus.desktop
* Now look for a line that contains "MimeType=application/x-bittorrent". Change this line to "MimeType=application/x-bittorrent;x-scheme-handler/magnet"
* sudo gedit home/YOUR USERNAME/.local/share/applications/mimeapps.list 
Look for a line that contains "x-scheme-handler/magnet"
Change this line to "x-scheme-handler/magnet=azureus.desktop"
If there is no such line, just add the line above completely.
* sudo gedit /usr/share/applications/defaults.list
Look for a line that contains "x-scheme-handler/magnet"
Change this line to "x-scheme-handler/magnet=azureus.desktop"
If there is no such line, just add the line above completely.
* Restart your pc (may not be necessary)
* After clicking the magnet link in Chrome Vuze should open.
* Unfortunately in Vuze the dialog box doesn't open automatically 
* Go to Vuze:  File - Open Torrent file - Add URL (the URL should already be filled in automatically) - Press OK 

Last remark : Make sure you have the "distributed database" plugin enabled in your Vuze otherways you may get a "DHT error".

---

### Post by frownlayer on 2012-03-11
follow the post before this, but in /usr/share/applications/azureus.desktop u might also change the info "Exec=azureus %f" to "Exec=azureus %u" and the box jumps up in azureus when u click on a magnet link. :)

it worked for me.

---

### Post by darktowermage on 2012-03-14
Worked like a charm with full integration!  Thanks!

---

### Post by Morlok8k on 2012-03-16
> **Magic_Spehar said:**
> Hi Haqking, thx for the link but that doesn't work for me.

I have found a solution to this problem in Ubuntu 11.10.

* sudo gedit /usr/share/applications/azureus.desktop
* Now look for a line that contains "MimeType=application/x-bittorrent". Change this line to "MimeType=application/x-bittorrent;x-scheme-handler/magnet"
* sudo gedit home/YOUR USERNAME/.local/share/applications/mimeapps.list 
Look for a line that contains "x-scheme-handler/magnet"
Change this line to "x-scheme-handler/magnet=azureus.desktop"
If there is no such line, just add the line above completely.
* sudo gedit /usr/share/applications/defaults.list
Look for a line that contains "x-scheme-handler/magnet"
Change this line to "x-scheme-handler/magnet=azureus.desktop"
If there is no such line, just add the line above completely.
* Restart your pc (may not be necessary)
* After clicking the magnet link in Chrome Vuze should open.
* Unfortunately in Vuze the dialog box doesn't open automatically 
* Go to Vuze:  File - Open Torrent file - Add URL (the URL should already be filled in automatically) - Press OK 

Last remark : Make sure you have the "distributed database" plugin enabled in your Vuze otherways you may get a "DHT error".

> **frownlayer said:**
> follow the post before this, but in /usr/share/applications/azureus.desktop u might also change the info "Exec=azureus %f" to "Exec=azureus %u" and the box jumps up in azureus when u click on a magnet link. :)

it worked for me.

These made it work perfectly!  Now chrome works with magnet links with vuze.  (and firefox works too, although i rarely use it)

(for me, Magnet links were associated with Transmission, but i dont use that, so i uninstalled it, and found out my magnets were left broken)

---

### Post by strickja on 2013-01-08
any idea how to make this work with utorrent server 3.x on ubuntu 12.1

I replicated all the steps using ut instead of az, but chrome still just opens another chrome instance 

nothing against az, just like ut interface better.  any help appreciated

---

