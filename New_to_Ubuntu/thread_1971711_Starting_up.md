---
title: "Starting up"
date: 2012-05-02
forum: New to Ubuntu
---

### Post by crestmount on 2012-05-02
OK the situation is that I have set a password for my Ubuntu, specifically to prevent the 14yo daughter from getting on the computer too much.  However whenever we start the PC it seems to bypass the need for a password--this basically means that she gets on the computer early morning and stays on for way too long.  Help please.

Am using Ubuntu 12.04

---

### Post by Zukaro on 2012-05-02
1. Did you enable automatic login during installation?
2. Is the guest account enabled (I'm assuming it is)?

These are the only things I can think of which would cause you to need no password to be able to use the computer.

If you want to disable the guest account open up a terminal and type "sudo gedit /etc/lightdm/lightdm.conf" then at the bottom of the few lines of code in the document which opens type "allow-guest=false" (all without quotes).  Then restart your system.
If there's a bug causing you to automatically login (or if you've enabled automatic login upon installation) then I'm not sure how to fix that (sorry).

---

### Post by crestmount on 2012-05-03
Thanks--works a treat

---

