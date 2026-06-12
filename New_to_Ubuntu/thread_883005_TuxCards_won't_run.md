---
title: "TuxCards won't run"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by rsnow on 2008-08-07
I am trying to do an exercise from a book wherein I downloaded the tuxcards-1.2.1mdk.i586.rpm file from the [www.tuxcards.de/requirements.html](www.tuxcards.de/requirements.html) web site. I followed the instructions to use the command "sudo alien --scripts tuxcards*.rpm" (yes, I have alien installed) This seemed to work OK as I got the message 'tuxcards_1.2.2_i386.deb generated'. The book said this was what I should expect.

Next, I used "sudo dpkg -i tuxcards*.deb" to install tuxcards. The terminal message I got was--(Reading database ... 108890 files and directories currently installed.)
Preparing to replace tuxcards 1.2-2 (using tuxcards_1.2-2_i386.deb) ...
Unpacking replacement tuxcards ...
Setting up tuxcards (1.2-2) ...

I assume the reference to 'replace tuxcards' is due to my prior attempts to install tuxcards.

After getting this far the book says to run tuxcards. I use the Run Application applet and type tuxcards in the command box and then click the Run button and nothing happens.

Can anyone see where I am not doing right?

---

### Post by rsnow on 2008-08-08
libqt-mt.so.3 was missing.

---

