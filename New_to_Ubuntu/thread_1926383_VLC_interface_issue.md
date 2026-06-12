---
title: "VLC interface issue"
date: 2012-02-16
forum: New to Ubuntu
---

### Post by manox on 2012-02-16
I have installed Lubuntu on my HTPC and try to set up remote connection from phone to vlc by HTTP but now I can't even open VLC nor reinstall it 

> VLC media player 1.1.12 The Luggage (revision exported)
[0x95d1f1c] main interface: creating httpd
[0x95d1f1c] main interface error: socket bind error (Permission denied)
[0x95d1f1c] main interface error: cannot create socket(s) for HTTP host
[0x95d1f1c] oldhttp interface error: cannot listen on 192.168.1.14:8080
[0x95d1f1c] main interface error: no suitable interface module
Remote control interface initialized. Type `help' for help.
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x95e0824] main interface: creating httpd
[0x95e0824] main interface error: socket bind error (Permission denied)
[0x95e0824] main interface error: cannot create socket(s) for HTTP host
[0x95e0824] oldhttp interface error: cannot listen on 192.168.1.14:8080
[0x95e0824] main interface error: no suitable interface module
[0x953b164] main libvlc error: interface "default" initialization failed
status change: ( stop state: 0 )
status change: ( quit )

---

### Post by mpascall on 2012-03-20
I'm having the same issue, and have yet to be able to resolve it.  

However, you can get VLC running again by removing your config file:

```
rm ~/.config/vlc/vlcrc
```

---

### Post by flurospar on 2012-03-20
If mpascall's method doesn't work, then you might want to try:
```

sudo dpkg-reconfigure vlc

```

---

### Post by hungry_pete on 2012-04-05
I did this too. It was when I selected 'http' as the main interface. It wouldn't even start after a remove and re-install. I went in and adjusted the config file manually to remove the http server settings. Started fine after that.

---

