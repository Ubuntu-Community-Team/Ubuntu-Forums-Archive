---
title: "Getting Semagic to run under Wine?"
date: 2011-11-20
forum: New to Ubuntu
---

### Post by hamstermoon on 2011-11-20
Can anyone give me any advice about this? I have googled a bit and it said something about needing to put mfc42.dll somewhere; that sounds complex.

---

### Post by lechien73 on 2011-11-20
Hi,

I have the latest version of Semagic running under wine. It was downloaded and installed from here.

To copy MFC42.DLL, you first need to check if you have it in your wine installation. So, open a terminal window, and type:

```
ls ~/.wine/drive_c/windows/system32/mfc42.dll
```

If this returns a result, then you can copy it to the Semagic folder by typing:

```
cp ~/.wine/drive_c/windows/system32/mfc42.dll ~/.wine/drive_c/Program\ Files/Semagic/

```

If it doesn't return a result, then you can install it through winetricks.

Firstly, get and install the winetricks script by following the instructions [here]("http://wiki.winehq.org/winetricks").

Then run:

```
sh winetricks mfc
```

And then follow the copy procedure above.

---

