---
title: "Temporarily preventing suspend"
date: 2010-04-12
forum: Programming Talk
---

### Post by Nathan_M on 2010-04-12
Hi all,
I've written a text-based program in Ruby, but I'd like it to prevent the computer from suspending when the laptop lid is closed. At the moment, I have to go into power manager to do this, then change it back when I'm done. Was wondering if there's some command-line way of doing this, or will I have to create C bindings for it? I know it can be done, because Rhythmbox does it.
Thanks,
Nathan

---

### Post by kostkon on 2010-04-12
Just a hint: you can easily communicate with the screensaver and power manager through D-BUS.

I hope Ruby has bindings for D-BUS.

---

