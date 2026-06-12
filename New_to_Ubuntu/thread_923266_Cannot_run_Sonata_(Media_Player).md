---
title: "Cannot run Sonata (Media Player)"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by xwhisper on 2008-09-18
Hello!
I installed Sonata via:
```
sudo apt-get install mpd python-soappy python-zsi python-tagpy libtag1-dev sonata -y
```

When I run it from terminal it says:
```
Traceback (most recent call last):
  File "/usr/bin/sonata", line 47, in <module>
    app = sonata.Base()
  File "/usr/lib/python2.5/site-packages/sonata.py", line 590, in __init__
    self.connect(blocking=True)
  File "/usr/lib/python2.5/site-packages/sonata.py", line 1623, in connect
    self.connect2(blocking, force_connection)
  File "/usr/lib/python2.5/site-packages/sonata.py", line 1635, in connect2
    self.conn = Connection(self)
  File "/usr/lib/python2.5/site-packages/sonata.py", line 146, in __init__
    if not host: host = Base.host[Base.profile_num]
IndexError: list index out of range
```
When I try it with root account it runs.
And does it works with PulseAudio?


Ubuntu Hardy

---

### Post by Nepherte on 2008-09-18
mpd/sonata works with pulseaudio as well. Is mpd set up correctly? Post the output of:
```
cat /etc/mpd.conf
```

---

### Post by xwhisper on 2008-09-18
I just solved the pulseaudio problem
I hate mpd! (but Sonata is great!)

---

