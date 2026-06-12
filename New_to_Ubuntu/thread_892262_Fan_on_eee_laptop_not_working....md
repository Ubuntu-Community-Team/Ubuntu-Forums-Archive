---
title: "Fan on eee laptop not working..."
date: 2008-08-17
forum: New to Ubuntu
---

### Post by deathvalleyjoker on 2008-08-17
I installed ubuntu from [http://ubuntu-eee.com/index.php5?title=Main_Page](http://ubuntu-eee.com/index.php5?title=Main_Page) on my eeepc. i have the first generation which i think they call the 701 now. The sd card slot is never recognized, and the fan never turns on. 

Of course i am more concerned about he fan not working . When i had hte default xandros turned on i def heard the fan turn on bc it was kinda loud, but with the new install, it never turns on. i am too new to Linux to even know where to begin with this one.

---

### Post by deathvalleyjoker on 2008-08-18
Bump. anyone?

---

### Post by sdennie on 2008-08-18
Maybe it's just not turning on very often.  Try running the following command once every 30 seconds or so and see if the temperatures steadily rise to a dangerous level:

```

acpi -t

```

If after a few minutes the temperatures are still rising, it probably indicates a problem.

---

### Post by deathvalleyjoker on 2008-08-21
> **vor said:**
> Maybe it's just not turning on very often.  Try running the following command once every 30 seconds or so and see if the temperatures steadily rise to a dangerous level:

```

acpi -t

```

If after a few minutes the temperatures are still rising, it probably indicates a problem.


So i did some testing:

At35min after boot-up, my temp was running at 48C 

```

mikeee@mikeee-laptop:~$ acpi -t
     Battery 1: discharging, 50%, rate information unavailable.
     Thermal 1: ok, 48.0 degrees C

```

Then i did some spot checks and it steadily rose till 15-20 min later it peaked at 68C after leaving the lid closed for 5min. When i opened it, the keyboard was hot to the touch.

```

mikeee@mikeee-laptop:~$ acpi -t
     Battery 1: charging, 70%, rate information unavailable.
     Thermal 1: ok, 68.0 degrees C

```

I opened the lid again and after a few min it cooled off to 62C. The keyboard was still warm to the touch.

```

mikeee@mikeee-laptop:~$ acpi -t
     Battery 1: charging, 70%, rate information unavailable.
     Thermal 1: ok, 62.0 degrees C

```

I have no idea where to begin fixing this. I am also new to Ubuntu and Linux.

Thanks!

---

