---
title: "Need some info....."
date: 2008-10-03
forum: New to Ubuntu
---

### Post by loyaleagle on 2008-10-03
hello everyone,

I am connected to the net through ethernet straight into my cable modem.
When I boo into Ubuntu, I get an error that flashes so quickly...
It reads as follows... (numbers followed by) 8254 timer not connected to I0-APIC.

What is this? All works well with my instalation of Ubuntu. Since I am not using wireless, does this have to do with my wireless not working properly or is it something else.

Just wondering... I would like to avoid wireless problems when I start hitting the road.

Thanks!!

---

### Post by Crafty Kisses on 2008-10-03
I'd try doing what it said, open a terminal, and do the following:
```
sudo gedit /boot/grub/menu.lst
```
Then add  **noapic** to the end of the line, possibly. Here's more info on this > [http://ubuntuforums.org/showthread.php?t=148761](http://ubuntuforums.org/showthread.php?t=148761)

---

### Post by Dr Small on 2008-10-03
I don't think it's anything you need worry about. I have seen it before on mine, too.

---

### Post by Crafty Kisses on 2008-10-03
> **Dr Small said:**
> I don't think it's anything you need worry about. I have seen it before on mine, too.

Yeah, if it's not really causing any issues with Ubuntu, I wouldn't worry too much about it.

---

### Post by snova on 2008-10-03
That's the kernel spitting out system diagnostics. It's nothing to worry about. 

In any case, it probably doesn't have anything to do with networking.

As for adding "noapic" to the end of the kernel command line, why would that help? There doesn't appear to be anything wrong with it.

---

### Post by loyaleagle on 2008-10-03
Thanks...

If it is not broke, don't fix it.

All is well with my install.... I LOVE UBUNTU....and to make it even better, it is all FREE...

So, I'll just leave it alone...

Thanks for all the replies.

loyaleagle

---

