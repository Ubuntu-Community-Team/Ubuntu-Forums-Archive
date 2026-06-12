---
title: "Fuzzy Text in Terminal"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by kkireyev on 2008-05-08
Hi,

I just installed Ubuntu FF (and it rocks!). The only slightly annoying issue is the characters in Terminal application are a bit fuzzy (compared to the crisp hi-res text everywhere else). Is there a way to fix it? Should I try different Fixed-width fonts?

Thanks a lot,
Kirill

---

### Post by kkireyev on 2008-05-08
Ah, it has to do with anti-aliasing in gnome Terminal. I think the solution is to used bitmap fonts. I'm figuring that out right now.

---

### Post by glennric on 2008-05-08
Go to System->Preferences->Appearance and under the Fonts tab play with the different rendering options.  I use Subpixel Smoothing (LCDs) and get nice results.  You should also check that your terminal profile is using the system fixed width font.

---

### Post by unutbu on 2008-05-08
You can also control the font and colors that gnome-terminal uses by clicking on Edit->Current Profile... on the gnome-terminal menu bar.

For some reason I have to click it twice before I get the customization window -- but I'm not sure if this is a communal weirdness or just my machine's own personal quirk.

---

### Post by glennric on 2008-05-08
> **unutbu said:**
> You can also control the font and colors that gnome-terminal uses by clicking on Edit->Current Profile... on the gnome-terminal menu bar.

For some reason I have to click it twice before I get the customization window -- but I'm not sure if this is a communal weirdness or just my machine's own personal quirk.

There is something quirky about that menu selection, and has been for a long time.  I don't have to click it twice, but when I select it it does a double system beep.  Like it is trying to play the system beep twice at once.

---

### Post by unutbu on 2008-05-08
Ah. Nice to know. Thanks.

---

### Post by noynac on 2008-05-08
> **kkireyev said:**
> Hi,

I just installed Ubuntu FF (and it rocks!). The only slightly annoying issue is the characters in Terminal application are a bit fuzzy (compared to the crisp hi-res text everywhere else). Is there a way to fix it? Should I try different Fixed-width fonts? Thanks a lot, Kirill

First I would try different fonts from within gnome-terminal as explained above. This did nothing on my computer but you should give it a try. The fix that worked for me involved creating a file named .confs.conf in my home directory. This is explained in the following thread:

[http://ubuntuforums.org/showthread.php?t=780946](http://ubuntuforums.org/showthread.php?t=780946)

BTW, what is Ubuntu FF?

---

