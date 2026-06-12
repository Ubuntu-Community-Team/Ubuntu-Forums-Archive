---
title: "HOW-TO: Adobe Photoshop CS2 working on Wine (a bit unstable tho)"
date: 2007-07-28
forum: Outdated Tutorials &amp; Tips
---

### Post by proxess on 2007-07-28
[COLOR="Red"][SIZE="5"]In case of doubts, PM me.[/SIZE][/COLOR]


This is a very simple way of doing things, I have no idea how legal it is. I guess if you have a legal copy of CS3 it shouldn't be too bad.


[COLOR="Red"][SIZE="5"]1: Get Photoshop CS3 Lite Edition[/SIZE][/COLOR]
Get this off some dodgy location. I recommend you have an original copy. This is the only way I got it working.


[COLOR="Red"][SIZE="5"]2: Install through Wine.[/SIZE][/COLOR]
Nothing much to do here, just double click and next next next.


[COLOR="Red"][SIZE="5"]3: Get gdiplus.dll[/SIZE][/COLOR]
Grab your favourite browser, write "gdiplus dll" and the first link is probably what you want.


[COLOR="Red"][SIZE="5"]4: Put gdiplus.dll in wine's System32[/SIZE][/COLOR]
Copy the gdiplus.dll into /home/<youruser>/.wine/drive_c/windows/system32 folder.


[COLOR="Red"][SIZE="5"]5: Set native gdiplus.dll[/SIZE][/COLOR]
Run "winecfg", go to the "Libraries" tab, add new override for library gdiplus and set it to native, apply and ok.


[COLOR="Red"][SIZE="5"]6: Double click the PS3 Icon.[/SIZE][/COLOR]
The installer generated a PS3 Icon on your desktop, double click it and all is well.

---

### Post by luisbg on 2007-07-29
What about After Effects? or all the rest of the CS suite?

luisbg

---

### Post by proxess on 2007-07-29
I've never given it a try.

---

### Post by proxess on 2007-08-04
I wasn't able to get ImageReady to work so, I doubt theres much I'm able to do about the rest.

---

### Post by bogolisk on 2007-08-04
If you had a legal CS2 license then it would be perfectly legitimate (IMHO but INAL) to wander into the darkside and get the Portable version of CS2. This would *just work* with wine as long as you use it in a wine desktop, i.e. something like
```

wine explorer /desktop=CS2,1024x768 'c:\blah\foo\bar\PortablePhotoshopCS2.exe'

```

for most windows apps, the portable image work much better under wine than the standard version.

---

### Post by proxess on 2007-08-10
wouldn't that just kill the reason you bought it legally?

---

### Post by boast on 2007-11-24
I couldn't get it to work; it still tells me to activate.

my name shows up during the plug-in / loading though.

---

### Post by Rizado on 2007-12-18
For those of you with problems activating Photoshop CS2 I have the solution! :)

[http://bugs.winehq.org/show_bug.cgi?id=10018#c16](http://bugs.winehq.org/show_bug.cgi?id=10018#c16)
The first method didn't work for me, might be because I have software raid drives or something. But the second method (SMART one) works great! You have to compile wine yourself though, but that's not very hard.

I linked to a usb flashdrive instead of my regular drives. That way I didn't have to change any permissions. Install, activate and all done!

If someone wants it I have a .deb with patched wine 0.51.

---

### Post by proxess on 2008-10-23
*bump* Just bumping this up, used to be a CS2 tutorial, now a CS3 tutorial.

---

