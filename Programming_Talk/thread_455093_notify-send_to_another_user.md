---
title: "notify-send to another user"
date: 2007-05-26
forum: Programming Talk
---

### Post by info2 on 2007-05-26
Hi,

i made a little script that tries to reproduce Fujitsu-Siemens-Computer's "Cool 'N' Quiet" - function if you press the C'n'Q - Button on a FSC-Laptop.

I want to notify the user weather it has been enabled or disabled.
I tried notify-send but since the script is run by "sudo" it cannot send to the users session.

Is there a way to get notify-send to send to eather all users or at least to the user who called the script?
Or is there another tool i can use to notify the user?

Edit:

I found a workaround using
  sudo -u $SUDO_USER
to run notify-send with the users session. Maybe there is a smarter way?


Thanks in advance.

---

### Post by jamesisin on 2012-02-12
How would the full command look in this case?  I'm trying to get notify-send to work and I get an error.

---

