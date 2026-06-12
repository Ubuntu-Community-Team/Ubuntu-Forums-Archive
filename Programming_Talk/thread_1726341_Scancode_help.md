---
title: "Scancode help"
date: 2011-04-11
forum: Programming Talk
---

### Post by Changowero on 2011-04-11
Hey!

I'm trying to make a Keylogger, just to learn Linux a little better. 
I have already Googled some info, and I think I have to read from a dev/input. In my computer,
when I "cat /dev/input/event1" a lot of junk appears on the terminal (when I hit a key), so I
think I already found the correct event. However, it's just weird symbols and nonsense. I read
those are the scancodes, but I can't get any meaning out of them.

How can I interpret them? Also, in what language would you do it? Python? C?

Thanks!

---

### Post by Changowero on 2011-04-11
Hey!

I'm trying to make a Keylogger, just to learn Linux a little better. 
I have already Googled some info, and I think I have to read from a dev/input. In my computer,
when I "cat /dev/input/event1" a lot of junk appears on the terminal (when I hit a key), so I
think I already found the correct event. However, it's just weird symbols and nonsense. I read
those are the scancodes, but I can't get any meaning out of them.

How can I interpret them? Also, in what language would you do it? Python? C?

Thanks!

---

### Post by fct on 2011-04-11
You are seeing the ASCII symbols corresponding to each scan code.

If you want to get the scan codes themselves you need to use either python or C and read the device event1 as if it was a binary file.

---

### Post by lisati on 2011-04-11
Threads merged.

Please do not start multiple threads on the same topic

---

### Post by tweaktolive on 2011-04-11
There is an ecellent website and you ll get whatever you need to interpret the ASCII symbols.

[http://www.asciitable.com/](http://www.asciitable.com/)

---

### Post by Changowero on 2011-04-11
Thanks! Let's see how that goes xD

---

