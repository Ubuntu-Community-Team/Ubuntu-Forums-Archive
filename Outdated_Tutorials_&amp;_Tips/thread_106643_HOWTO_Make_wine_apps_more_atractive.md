---
title: "HOWTO: Make wine apps more atractive"
date: 2005-12-21
forum: Outdated Tutorials &amp; Tips
---

### Post by Omer on 2005-12-21
By default, applications installed by Wine inherit Win9x ugly dark grey theme.
Latest wine release support .MSStyle for theming.

Create the themes directory:
```

mkdir ~/.wine/drive_c/windows/resources/themes

```
Assuming *~/.wine* is your wine install path.

Run *winecfg* and select the **Appearance** tab.
Install a .msstyle from your local windows install (C:\Windows\Resources\themes\) or download any theme from the net.
Choose your theme, and apply it.

The resault:
[IMG]http://img288.imageshack.us/img288/9632/winecfg0jp.png[/IMG]

EDIT: matching Clearlooks theme available [here]("http://www.deviantart.com/deviation/17870413/") (less updated, but more stable) and [here ]("http://www.deviantart.com/deviation/18591720/") (more buggy).

[SIZE="1"]* Tested with wine 0.9.3 from [http://www.winehq.com/](http://www.winehq.com/)[/SIZE]

---

