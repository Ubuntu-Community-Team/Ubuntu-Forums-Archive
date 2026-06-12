---
title: "How do I view &quot;/var/log/rkhunter.log&quot; a page at a time?"
date: 2014-01-18
forum: New to Ubuntu
---

### Post by bc.haynes on 2014-01-18
This is my 2nd try at Ubuntu. I have forgotten all I learned on my 1st try. This is a two part question - how do I view It and how do I read it a page at a time?   Ben

---

### Post by Iowan on 2014-01-18
Try **less /var/log/rkhunter.log**
**sudo** might be necessary if it balks at 'permission denied"

---

### Post by Frogs Hair on 2014-01-18
I use the following, but the log is only available when open immediately after running rkhunter  while the output is still visible in the terminal. 

```
gksudo gedit /var/log/rkhunter.log
```

---

### Post by coldcritter64 on 2014-01-19
> **bc.haynes said:**
> This is my 2nd try at Ubuntu. I have forgotten all I learned on my 1st try. This is a two part question - how do I view It and how do I read it a page at a time?   Ben

As as been noted above "gksu gedit" for graphical, is the easiest (gksu or gksudo, as the log is owned by root and gedit is a graphical application).

For "one page at a time" in terminal, I just "cat" the file and pipe its output through "more". From which point using the spacebar will scroll a page at a time, or the enter button a line at a time; to quit during the output use "q" on the keyboard. The command,
```
sudo cat /var/log/rkhunter.log | more -d
``` the "-d" switch on "more" causes it to give out instructions for use.

---

### Post by squakie on 2014-01-19
Iown's is the easiest way to go, and the less command being used lets you constantly scroll up or down in the output - not just a pause and then dump another page.  Piping to more only gives a pause then dumps the next page - no scrolling up or down (at least when I hvae used it - that's why I've stuck with "less").

---

### Post by coldcritter64 on 2014-01-19
> **squakie said:**
> Iown's is the easiest way to go, and the less command being used lets you constantly scroll up or down in the output - not just a pause and then dump another page.  Piping to more only gives a pause then dumps the next page - no scrolling up or down (at least when I hvae used it - that's why I've stuck with "less").

True, Iowan's command supports scrolling better / natively. 

If gnome-terminal is set to not "scroll on output" in preferences, ie the tick box is cleared you can mouse button scroll back through previous output or scroll back fully to the end and continue using the command, just tested here on a Debian 7 install, gnome desktop, I'm sure this also works on my Ubuntu installs, I use it regularly. Cheers.

Edit: I should also note I always set gnome-terminal to "unlimited" for scrollback on the scrolling tab. It stops any loss of output when using the terminal this way.

---

