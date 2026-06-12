---
title: "What's the echo command in Hardy to turn on the Asus email LED?"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by hotweiss on 2008-05-20
What's the echo command in Hardy to turn on the Asus email LED? All previous references have been made to mled, but that file is not found in Hardy anymore. The Asus acpi files have been moved to /sys/devices/platform/asus-laptop. The only file there pertaining to LED's is ledd, but when I try to echo it I get permission denied. I want to get my email LED working checkgmail. Your help would be appreciated.

---

### Post by hotweiss on 2008-05-22
bump

---

### Post by mali2297 on 2008-05-22
Put the echo line in a script, say mail_led.sh, then run it with sudo,
```

sudo sh mail_led.sh

```
Alternatively, make the script executable and run it with
```

sudo ./mail_led.sh

```

---

### Post by neurostu on 2008-05-22
have you tried using sudo?

what about using sudo su and then making the echo command.

---

### Post by hotweiss on 2008-05-23
> **mali2297 said:**
> Put the echo line in a script, say mail_led.sh, then run it with sudo,
```

sudo sh mail_led.sh

```
Alternatively, make the script executable and run it with
```

sudo ./mail_led.sh

```

Hmm, when I ran sh mail_led.sh, I received this error:

> mail_led.sh: 1: cannot create /proc/acpi/asus/mled: Directory nonexistent

I've searched the entire drive for mled and could not find it.

---

### Post by mali2297 on 2008-05-23
Did you try *ledd* instead?

---

### Post by hotweiss on 2008-05-23
> **mali2297 said:**
> Did you try *ledd* instead?

I tried the following:

> sudo su
echo 1 > /sys/devices/platform/asus-laptop/ledd

I got a permission denied error.

---

### Post by mali2297 on 2008-05-23
Have you seen this [README]("http://acpi4asus.sourceforge.net/README")?
> 
  You can modify LEDs be echoing values to /sys/class/leds/asus:*/brightness :
    echo 1 >  /sys/class/leds/asus:mail/brightness
  will switch the mail LED on ...
 


---

### Post by hotweiss on 2008-05-23
Oh wow, that did the trick. Thank-you very much mali2297.

---

