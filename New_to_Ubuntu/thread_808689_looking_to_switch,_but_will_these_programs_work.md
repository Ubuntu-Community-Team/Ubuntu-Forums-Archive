---
title: "looking to switch, but will these programs work?"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by kmanpwnudwn on 2008-05-26
I am looking to switch to Ubuntu, but before I do that I need to know if these programs will work with it. I have some basic knowledge of Fedora and Red Hat because of Cisco class, but I know it will take getting used to. 

First of all, my main priority is will the Zune software work? If not, will it work in Wine? I love having portable music and movies, and it would suck majorly if I couldn't update my Zune with new music. 

Second of all, does Utorrent work in Ubuntu? Or, are there different torrent programs that will work? I've heard talk of Azerus (sp?), but I don't know. 

And my final major concern would be a media player. Right now I am using Winamp and it keeps connected to my Last.FM account. Just curious as to whether or not Winamp will work in Ubuntu (Wine?) and if the Last.FM application will work in Ubuntu (again, Wine?)

I would like to completely remove Vista and switch to Ubuntu full time, but if Zune wont work in Ubuntu then I will have to obviously keep Vista on a separate partition. Unless if there is somehow a way to update my Zune without the Zune program. 

Thanks for any help anyone can provide!!

---

### Post by bm13084 on 2008-05-26
not sure about the zune software, but my ipod AND last.fm needs are met with amarok. as far as torrents go, hardy comes with "Transmission BitTorrent Client".  So you should be set.  I'd assume you can update the zune somehow in ubuntu...

---

### Post by kmanpwnudwn on 2008-05-26
Thanks for the info, I'll look more into Amarok.

---

### Post by philinux on 2008-05-26
I use deluge for torrents. It's very good.

---

### Post by sam_delta on 2008-05-26
for the torrent client, id look into deluge-torrent

for the zune you might want to look at post #2 from
[http://ubuntuforums.org/showthread.php?p=2340145](http://ubuntuforums.org/showthread.php?p=2340145)

as suggested in the thread of the previous link, zune might be a pain, you might also consider setting up a virtual machine with windows in it or setting up a dual boot, just to control your zune
sam

---

### Post by kk0sse54 on 2008-05-26
Deluge for torrents and Exaile for a media player which will work with Last.FM

---

### Post by inportb on 2008-05-26
If you must have utorrent, you would find that Wine is one of its supported Windows platforms.

---

### Post by Joeb454 on 2008-05-26
True uTorrent works under Wine, though I believe Deluge is actually a very good alternative (and runs Natively under Linux).

And Amarok should do fine for your media player :)

---

### Post by kmanpwnudwn on 2008-05-26
Thanks for all the help guys (and gals), I'll look into Amarok and Deluge. 

I'll just keep a small 15GB or so partition for Vista and Zune software.

---

### Post by wdaniels on 2008-05-26
> **kmanpwnudwn said:**
> First of all, my main priority is will the Zune software work? If not, will it work in Wine?

I've seen reports that it can at least be made to work with VMWare (whether or not the issue with USB 2.0 drivers is fixed yet in VMWare I don't know, nor do I know about other VMs like VirtualBox). As for running the Zune software under Wine - no, not yet. It's based on Windows Media Player 11, which still isn't working with Wine, and even then you would never be able to get it to sync via USB with Wine because the Zune is not some generic USB device that Wine can use via the underlying Linux system - Wine does not emulate the Windows kernel and cannot therefore use Windows device drivers. Syncing via wireless has more potential, but I wouldn't hold your breath; the bottom line is that locked-down proprietary systems such as the Zune are not at all conducive with the whole point of Linux and if you want to use them you are always going to have problems with Linux.

> **kmanpwnudwn said:**
> Second of all, does Utorrent work in Ubuntu? Or, are there different torrent programs that will work?

Yes, last time I tried it uTorrent worked almost flawlessly under Wine. The exceptions being UPnP and some wierd problem with the default mode of minimizing to the tray, both of which are easy enough to deal with. However, there are plenty of good and similar torrent apps native to Linux. I use Deluge these days myself.

> **kmanpwnudwn said:**
> And my final major concern would be a media player. Right now I am using Winamp and it keeps connected to my Last.FM account. Just curious as to whether or not Winamp will work in Ubuntu (Wine?) and if the Last.FM application will work in Ubuntu (again, Wine?)

Most Linux media players have plugins for updating to Last.fm and I believe the standard Last.fm software is also available for Linux natively. WinAMP runs under Wine also, but it does have a few glitches - you would be better off with one of the native Linux players.

---

