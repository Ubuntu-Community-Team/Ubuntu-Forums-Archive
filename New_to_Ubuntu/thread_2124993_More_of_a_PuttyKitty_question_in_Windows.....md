---
title: "More of a Putty/Kitty question in Windows...."
date: 2013-03-12
forum: New to Ubuntu
---

### Post by EvertMeirion on 2013-03-12
Why cannot I not get lines to properly display in KiTTY, and instead I get characters like l,q,k,x instead.  

See here for reference image:  [http://i.imgur.com/Z58kK9o.png](http://i.imgur.com/Z58kK9o.png)

I think this is a terminal emulation or font issue, but I have tried a few variation of those settings and various google searches have come up empty.

Thanks in advance to whoever knows!

---

### Post by schragge on 2013-03-12
Yes, it's terminal emulation issue. Specifically, DEC VT100 terminal emulation. Can't say for KiTTY, but in PuTTY it's controlled by the *Translation* tab in the settings. I believe something like *Use Unicode line drawing code points*.

BTW, what does *echo $TERM* show when you're logged in through KiTTY?

---

### Post by EvertMeirion on 2013-03-12
Edit: I got it, I compared settings with PuTTY that was working, and KiTTY was set to UTF-8.  Changed it to Latin-1 and it looks normal.

Hmm... I expected KiTTY to be the same as PuTTY since the former is based off the later, but I just looked in PuTTY and it's appearing correctly.  

$TERM is xterm

Translation is one of the locations I checked, it was originally set to Unicode, and I changed it a few times.  Changed it back.  That doesn't seem to be the specific issue.

---

