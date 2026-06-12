---
title: "Deluge problem and question"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by SpinningAround on 2008-11-20
I have a problem with deluges interface, the interface have simply stopped updating and is basically breezed until I close and open deluge then it update but then freeze again. deluge is working but not the interface.

Also I would like to know if deluge 1.x.x is possible to get by respiratory?

---

### Post by shifty_powers on 2008-11-20
thought of using utorrent?

i know it needs wine but it is by far my favourite torrent client...

---

### Post by SpinningAround on 2008-11-20
> **shifty_powers said:**
> thought of using utorrent?

i know it needs wine but it is by far my favourite torrent client...

utorrent lacks some of the parts I request in a bittorrent client :)

---

### Post by shifty_powers on 2008-11-20
such as? (out of curiosity :D)

---

### Post by aeiah on 2008-11-20
> **shifty_powers said:**
> such as? (out of curiosity :D)

well deluge lets me close the gui and keep the daemon running and downloading. i can have the daemon running on my computer, on another on my LAN, or somewhere in internet land (like on a seedbox or at a friends house or something) and still have a proper GUI to manage torrents with. also, i have the choice of a web interface or a CLI interface if im on the move, so i could ssh into my home computer to add new torrents if i wanted, or set a script up to add something as you'd expect from any other CLI program. i dunno if utorrent does this or not, i havent bothered with it for ages now. 

im sure it has some nice tricks up its sleave as its very popular and lightweight.


anyway, back to the problem. what version are you using? the newest available? what happens when you launch deluge from the terminal, does it still stall? have you added anything massive recently that may be causing it to struggle? i know some people have said that the new version sometimes has trouble with 60GB torrents and such

---

### Post by SpinningAround on 2008-11-20
> **aeiah said:**
> anyway, back to the problem. what version are you using? the newest available? what happens when you launch deluge from the terminal, does it still stall? have you added anything massive recently that may be causing it to struggle? i know some people have said that the new version sometimes has trouble with 60GB torrents and such

deluge --version 0.5.9.3


did run deluge using the terminal and notice this that look a little out of place :)
```

Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/deluge/interface.py", line 1111, in update
    self.manager.handle_events()
  File "/var/lib/python-support/python2.5/deluge/core.py", line 739, in handle_events
    callback(event)
  File "/usr/share/deluge/plugins/EventLogging/tab_log.py", line 218, in handle_event
    event_message = _("Other") + " {" + _("event message: ") + event['message'] + "}"
UnicodeDecodeError: 'utf8' codec can't decode byte 0x91 in position 111: unexpected code byte

```

---

### Post by aeiah on 2008-11-20
you should probably upgrade deluge really. it seems like this is caused by a torrent either containing a weird character in its name / information or because a tracker site has sent an error message back with weird characters that've confused it. i suggest just upgrading. current version is 1.05 but i think it involves a reinstall. your .torrent files should be in ~/.config/deluge/ somewhere if you want to back them up. i cant remember if it picks them up automatically or not.

---

### Post by SuperSonic4 on 2008-11-20
It is not in the repos but you can get the deb from their site which is always more up to date lol

[http://deluge-torrent.org/downloads.php](http://deluge-torrent.org/downloads.php)

I upgraded to the latest version and it all runs fine

---

### Post by SpinningAround on 2008-11-20
Looked around a little since I repository make updating so much easier and I found this

[https://launchpad.net/~deluge-team/+archivev](https://launchpad.net/~deluge-team/+archivev)
is it real or fake?

also it usually is some authenticity file, but haven't find any.

---

### Post by kostkon on 2008-11-20
> **SpinningAround said:**
> Looked around a little since I repository make updating so much easier and I found this

[https://launchpad.net/~deluge-team/+archivev](https://launchpad.net/~deluge-team/+archivev)
is it real or fake?

also it usually is some authenticity file, but haven't find any.
Fake? No, of course not! Nothing is fake on Launchpad. This is the official repo for Ubuntu, so use it! ;)

---

