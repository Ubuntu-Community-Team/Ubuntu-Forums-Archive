---
title: "faster using the torrent on Apr 34 2008 for 8.04"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by metalf8801 on 2008-04-24
The downloading from one of the mirrors was going really slow so when I was a link on [http://distrowatch.com/](http://distrowatch.com/) for a torrent I tried it and its download much faster 

just something i thought people might want to know sins there is no link to a torrent on the download page on the Ubuntu website that I could find at lest

---

### Post by tyblu on 2008-04-24
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

--> [http://releases.ubuntu.com/hardy/](http://releases.ubuntu.com/hardy/)

---

### Post by metalf8801 on 2008-04-24
ok my be bittorrents not the best way to go 
got this crazy error message when the download got to 99% 
I hope I'm the only one this happens to (sins I'm having a really bad week) but just incases I thought I should let people know it bittorrent might not be the best way to go after all 
sorry 
dan
 

oh and here the message I got

Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/BitTorrent/RawServer.py", line 231, in listen_forever
    self.handle_events(events)
  File "/usr/lib/python2.5/site-packages/BitTorrent/RawServer.py", line 183, in handle_events
    s.handler.data_came_in(s, data)
  File "/usr/lib/python2.5/site-packages/BitTorrent/Encrypter.py", line 210, in data_came_in
    self.connections[connection].data_came_in(data)
  File "/usr/lib/python2.5/site-packages/BitTorrent/Encrypter.py", line 130, in data_came_in
    x = self.next_func(m)
  File "/usr/lib/python2.5/site-packages/BitTorrent/Encrypter.py", line 96, in read_message
    self.encoder.connecter.got_message(self, s)
  File "/usr/lib/python2.5/site-packages/BitTorrent/Connecter.py", line 200, in got_message
    toint(message[9:]))
  File "/usr/lib/python2.5/site-packages/BitTorrent/Uploader.py", line 49, in got_request
    self.flushed()
  File "/usr/lib/python2.5/site-packages/BitTorrent/Uploader.py", line 36, in flushed
    piece = self.storage.get_piece(index, begin, length)
  File "/usr/lib/python2.5/site-packages/BitTorrent/StorageWrapper.py", line 200, in get_piece
    return self._get_piece(index, begin, length)
  File "/usr/lib/python2.5/site-packages/BitTorrent/StorageWrapper.py", line 215, in _get_piece
    return self.storage.read(self.piece_size * self.places[index] + begin, length)
  File "/usr/lib/python2.5/site-packages/BitTorrent/Storage.py", line 75, in read
    h.seek(pos)
ValueError: I/O operation on closed file

---

### Post by Kleist on 2008-04-24
I download the whole iso in about an hour in demonoid.com

There're about 6000 seeders over there.


[http://www.demonoid.com/files/?category=0&subcategory=All&quality=All&seeded=0&external=2&query=ubuntu+hardy&uid=0&sort=](http://www.demonoid.com/files/?category=0&subcategory=All&quality=All&seeded=0&external=2&query=ubuntu+hardy&uid=0&sort=)
:)

---

### Post by Ub1476 on 2008-04-24
Rechecking torrents is always a good idea.

---

