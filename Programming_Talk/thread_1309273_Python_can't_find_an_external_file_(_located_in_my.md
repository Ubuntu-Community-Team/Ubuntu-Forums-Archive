---
title: "Python can't find an external file ( located in my home directory )."
date: 2009-11-01
forum: Programming Talk
---

### Post by liquidbee on 2009-11-01
What I'm doing wrong ?

```
from xml.dom.minidom import parse, parseString
mydom = parse('~/.config/xfce4/xfconf/xfce-perchannel-xml/xsettings.xml')
```

```
IOError: [Errno 2] No such file or directory: '~/.config/xfce4/xfconf/xfce-perchannel-xml/xsettings.xml'
```

```
/home/liquid/.config/xfce4/xfconf/xfce-perchannel-xml/xsettings.xml: XML  document text
```

Update: appearantely Python doesn't know what ~/ means - works as expected if I replace it with /home/user.

---

