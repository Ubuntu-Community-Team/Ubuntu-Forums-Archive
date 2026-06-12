---
title: "Kernel module small question"
date: 2008-04-29
forum: Programming Talk
---

### Post by heikaman on 2008-04-29
hello everyone...
I'm working on a kernel module for my laptop buttons, and every thing is working just fine.

my module generates input events using key codes #defined in linux/input.h BTN_0-BTN_7 0x100-0x107 like this:

[PHP]
set_bit(EV_KEY, button_dev->evbit);
set_bit(BTN_0, button_dev->keybit);
....

//interrupt handler code:
...
input_report_key(button_dev, BTN_0, 1);
...
[/PHP]

The problem is how do I map these input events to shell commands ? 

I mean there must be a daemon or something that I can use to set the mapping :confused: but I can't seem to find something like this ](*,), or do I need to write it myself ?

Thanks for your time...

---

### Post by heikaman on 2008-04-30
anyone :( ?

I also can't find detailed documentation about the input device subsystem, if you can post some links that would be great.

---

### Post by heikaman on 2008-05-01
I just used 
[PHP]
set_bit(KEY_*, button_dev->keybit);
[/PHP]
instead, and now I can see the key codes with xev. :)

here's a link to the module if anyone's interested.

[https://sourceforge.net/projects/lt20button]("https://sourceforge.net/projects/lt20button")

---

