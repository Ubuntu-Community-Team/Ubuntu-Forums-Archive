---
title: "Shut Down Problem"
date: 2011-10-01
forum: New to Ubuntu
---

### Post by technosysind on 2011-10-01
Hey Guys!!
I'm using Kubuntu 11.04 and whenever I shutdown my laptop, it shows that it is shutting down but then the backlight of my screen does not turn off. I have to hard boot everytime because of this.
Strangely, whenever I restart my laptop, everything works fine.

Any idea what could be the problem??

---

### Post by 2F4U on 2011-10-01
Did you already look into the system log files? Maybe it contains information about what goes wrong.

---

### Post by technosysind on 2011-10-01
I did check and everything seems to be fine. There is just one small output that might be something to look into. Please see it below and tell me if there is something that i have worry about?
> [    34.911] (II) No input driver/identifier specified (ignoring)
[  5856.695] (II) XKB: reuse xkmfile /var/lib/xkb/server-9A8405F3FE0A780485714A4B6DD41909C2CF9F83.xkm
[  5881.675] (II) XKB: reuse xkmfile /var/lib/xkb/server-9A8405F3FE0A780485714A4B6DD41909C2CF9F83.xkm
[  5881.680] (II) XKB: reuse xkmfile /var/lib/xkb/server-9A8405F3FE0A780485714A4B6DD41909C2CF9F83.xkm
[  5881.705] (II) XKB: reuse xkmfile /var/lib/xkb/server-9A8405F3FE0A780485714A4B6DD41909C2CF9F83.xkm
[  5881.710] (II) XKB: reuse xkmfile /var/lib/xkb/server-9A8405F3FE0A780485714A4B6DD41909C2CF9F83.xkm
[  5881.716] (II) XKB: reuse xkmfile /var/lib/xkb/server-9A8405F3FE0A780485714A4B6DD41909C2CF9F83.xkm
[  5881.718] (II) XKB: reuse xkmfile /var/lib/xkb/server-9A8405F3FE0A780485714A4B6DD41909C2CF9F83.xkm
[  5881.725] (II) XKB: reuse xkmfile /var/lib/xkb/server-9A8405F3FE0A780485714A4B6DD41909C2CF9F83.xkm
[  5881.728] (II) XKB: reuse xkmfile /var/lib/xkb/server-9A8405F3FE0A780485714A4B6DD41909C2CF9F83.xkm
[  5881.735] (II) XKB: reuse xkmfile /var/lib/xkb/server-9A8405F3FE0A780485714A4B6DD41909C2CF9F83.xkm
[  5881.742] (II) XKB: reuse xkmfile /var/lib/xkb/server-9A8405F3FE0A780485714A4B6DD41909C2CF9F83.xkm
[  5881.747] (II) XKB: reuse xkmfile /var/lib/xkb/server-9A8405F3FE0A780485714A4B6DD41909C2CF9F83.xkm
[  5881.756] (II) XKB: reuse xkmfile /var/lib/xkb/server-9A8405F3FE0A780485714A4B6DD41909C2CF9F83.xkm

---

### Post by Junior41180 on 2011-10-01
I get the same problem on my laptop, Blue bar on top of screen with black screen below blue bar. I was thinking problem with nvidia/any laptop driver because of Laptop's different usage of power settings (I.E. sleep when lid closed etc...)

Are you using Default installed driver or one provided from card vendor?

---

### Post by WinterMadness on 2011-10-01
I dont know what the problem is, perhaps another program is cancelling its logout?

Anyway, just so that you can shutdown correctly, you can open the terminal ad type sudo shutdown -h now and it will shut down immediately

---

### Post by josephmills on 2011-10-01
umm sounds like something is not shutting down right I have had this happen to me in the past and use the sudo reboot command to reboot the system then when the plymouth boot splash comes up press up and see if anything fails if so please report

---

### Post by Junior41180 on 2011-10-01
> **josephmills said:**
> umm sounds like something is not shutting down right I have had this happen to me in the past and use the sudo reboot command to reboot the system then when the plymouth boot splash comes up press up and see if anything fails if so please report
will do, just to let ya know it's not doing it on the desktop, so it seems to be a laptop thing.


i'm running 11.04 with the stock(from install cd) installed kernel, i haven't updated it yet.


Running on a Toshiba X505-Q870 ([http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=SB&os=&category=&moid=2523347&rpn=PQX33U&modelFilter=&selCategory=2756709&selFamily=804517](http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=SB&os=&category=&moid=2523347&rpn=PQX33U&modelFilter=&selCategory=2756709&selFamily=804517))

detailed specs

---

### Post by technosysind on 2011-10-02
My query is still not answered :(

---

### Post by Redblade20XX on 2011-10-03
> **technosysind said:**
> My query is still not answered :(

Do you have proprietary video card software installed or Buntu's  default? Also did this just recently started to occur or always happened  since installation?

---

### Post by technosysind on 2011-10-03
I have a proprietary driver installed for my Nvidia card and this problem has started occurring recently

---

### Post by SeijiSensei on 2011-10-03
I find the most reliable method for shutting down is to use the Hibernate and Sleep functions via the KDE launcher (the big "K" button at the left of the panel).  Click the launcher, pick Leave, then Hibernate, to save the image to disk.  That works more reliably than closing the lid on my Asus 1201n.  It also has an NVIDIA card; I don't know if that matters, though.

---

### Post by Redblade20XX on 2011-10-03
> **technosysind said:**
> I have a proprietary driver installed for my Nvidia card and this problem has started occurring recently

What type of card do you have?

---

### Post by anewguy on 2011-10-03
Try the following:

- at the boot menu, edit the ubuntu boot line and add "noapic" and try booting and then shutting down.  If that doesn't work, try the following:

- at the boot menu, edit the ubuntu boot line and add "noacpi" and try booting and then shutting down.  If that doesn't work, try the following:

- at the boot menu, edit the ubuntu boot line and add "nomodeset" and try booting and then shutting down.  

That's what I can think of for now, but it's probably going to end up being something between your proprietary driver and an update done recently.

Dave ;)

---

### Post by Junior41180 on 2011-10-03
> **anewguy said:**
> Try the following:

- at the boot menu, edit the ubuntu boot line and add "noapic" and try booting and then shutting down.  If that doesn't work, try the following:

- at the boot menu, edit the ubuntu boot line and add "noacpi" and try booting and then shutting down.  If that doesn't work, try the following:

- at the boot menu, edit the ubuntu boot line and add "nomodeset" and try booting and then shutting down.  

That's what I can think of for now, but it's probably going to end up being something between your proprietary driver and an update done recently.

Dave ;)

I have nomodeset enabled, but lemme double check to see if that is indeed true, I had it set at install. But i was never sure if that passed on in grub2 after install.

---

