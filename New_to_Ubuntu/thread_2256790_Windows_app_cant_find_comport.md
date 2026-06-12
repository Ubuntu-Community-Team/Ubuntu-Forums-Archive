---
title: "Windows app cant find comport"
date: 2014-12-14
forum: New to Ubuntu
---

### Post by mitch_smith2 on 2014-12-14
Hi, have had Ubuntu for a few days now.

I have loaded a windows program for programming the Baofeng UV5R radio into wine. The app is looking for com 0, but can't find it. I create a link in the dosdevices folder, but the link has a "lock" symbol on it and tells me the link is broken because it cannot find /dev/ttyUSB0/com0. It won't, /dev exists, but there is no folder in /dev called ttyUSB0 - only a file called that when I plug the cable into the usb port, and therefore there is no file called "com0" either.

How does it all work? How do I get the windows software to see com 0? The cable is definitely showing as ttyUSB0 in /dev when I plug it in.

PLEASE, PLEASE, PLEASE DON"T TELL ME TO USE CHIRP SOFTWARE!

Yes, I have it installed, and yes, I have the ubuntu version, and yes, it all works perfectly - BUT - I cannot program the DTMF ani number with it, and that's ALL I need to do, so I have no option but to make the original Baofeng software work in Ubuntu.

---

### Post by CRYy0OKmKpJgc on 2014-12-14
[SIZE=2][FONT=arial]Use:
```
[COLOR=#484848]sudo gpasswd --add ${USER} dialout[/COLOR]
```

After that, you will need to log out and log back in. That should at least give you permission to access the ttyUSB0 port.[/FONT][/SIZE]

---

### Post by lisati on 2014-12-14
It's been a while since I've used a COM port on Windows or via Windows software, but seem to recall that the Windows numbering started with COM1, rather than COM0.

---

### Post by mitch_smith2 on 2014-12-14
Thanks guy's, but basically I think all I need to do is create a link that says ttyUSB0 is Com0. When I create it as was suggested on another forum somewhere, it just says the link is broken, it's target doesn't exist, so I need to make a link whose target does actualy exist. I don't know how to do that.

---

### Post by CRYy0OKmKpJgc on 2014-12-14
Perhaps:
```
sudo ln -s /dev/ttyUSB0 /dev/ttyCOM0
```

---

