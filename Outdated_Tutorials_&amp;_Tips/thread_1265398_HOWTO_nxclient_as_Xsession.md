---
title: "HOWTO: nxclient as Xsession"
date: 2009-09-13
forum: Outdated Tutorials &amp; Tips
---

### Post by misha680 on 2009-09-13
```

sudo gedit /usr/share/xsessions/nxclient.desktop

```

Copy and paste:
```

[Desktop Entry]
Encoding=UTF-8
Name=NX
Comment=NoMachine
Exec=/usr/bin/nxclient-run
Icon=
Type=Application

```

```

sudo gedit /usr/bin/nxclient-run

```

Copy and paste:
```

#!/bin/sh
/usr/NX/bin/nxclient &
exec xterm

```

```

chmod +x /usr/bin/nxclient-run

```

Reboot. Presto. (On login you need to select Sessions in the bottom left hand corner and change your session to NX).

Misha

---

