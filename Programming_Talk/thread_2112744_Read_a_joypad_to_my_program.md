---
title: "Read a joypad to my program"
date: 2013-02-05
forum: Programming Talk
---

### Post by cazz on 2013-02-05
Hi
I have see that USB joypad read when I start my linux.

And when I use

```
jstest /dev/input/js0
```

I can see it change when I push a button or joystick.

But now I like to make a basic program that read the joystick and write what I doing.

I mean some kind of if statement so if I push a button it do something I like it to do.

For example

if I do not do anything it show

```
Axes:  0:     0  1:     0  2:-32767  3:     0  4:     0  5:     0  6:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:off
```

but when I use a joystick it say

```
Axes:  0:-32767  1:     0  2:-32767  3:     0  4:     0  5:     0  6:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:off
```

or

```
Axes:  0:     0  1:     0  2:-32767  3:     0  4:     0  5:     0  6:     0 Buttons:  0:off  1:off  2:off  3:on   4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:off
```

as you can see it change "0" to "-32767" or "off" to "on"
if I do something with the joypad.

So I like to make it say what I doing

like

```
echo "Left"
echo "Right"
```

But I don't know how.
I have read alot of HID and that and even pygame and that but I do not get it what I have to install and make it to work with my own code.

I was thinking use Batch but if I have to use something else then I have to do that.

---

### Post by cazz on 2013-02-06
After a little reading I found this

[http://www.mjmwired.net/kernel/Documentation/input/joystick-api.txt](http://www.mjmwired.net/kernel/Documentation/input/joystick-api.txt)

But I guess I can't use BASH and it maybe for C++ but I have never use that in Linux only a little in windows?

---

