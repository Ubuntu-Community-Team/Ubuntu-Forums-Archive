---
title: "Trying to install Ubuntu from USB - Does nothing"
date: 2013-03-17
forum: New to Ubuntu
---

### Post by Doggins on 2013-03-17
When I choose to boot from my USB stick in the bios the screen just flashes and nothing happens. I've tried two different USB sticks with two different versions of ubuntu and nothing seems to work.
It's a zotac motherboard with usb 3.0. I've tried it wth 3.0 enabled as well as disabled but haven't had any luck. I've also tried every usb port on the mobo


edit: I used unetbootin to create a bootable usb drive of 12.10, i've done this one a 1g and a 32g stick
Any ideas? :)

---

### Post by Moose on 2013-03-17
Have you tried putting usb at the top of the boot devices list?

---

### Post by Doggins on 2013-03-17
Thanks for the quick response.
I just tried 1) disabling the harddrive so only the usb drive is available
and 2) putting USB above the internal harddrive

1) results in it booting to setup after a couple seconds
2) results in it just booting to the harddrive after a slight delay

---

### Post by Doggins on 2013-03-17
I have the worst possible reply to this for any future people who had the same problem

I just tried it again, and it seems to have worked...
thanks for the help :)

---

### Post by Moose on 2013-03-17
Ah. This is pretty common you wouldn't believe!

Have you verified the md5sum? If the Iso is corrupted it won't boot. If the iso is not corrupted, maybe try a different program to burn the iso. Also, try to enable legacy boot. (I think that is what it's called, I don't have access to a non-mac computer right now) If all else fails, I would probably pin point it to either being an issue with the CD itself, or a hardware error.

Edit: I am glad you got it working!

---

