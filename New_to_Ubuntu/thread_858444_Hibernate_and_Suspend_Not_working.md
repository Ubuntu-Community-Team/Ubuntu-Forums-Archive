---
title: "Hibernate and Suspend Not working"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by katdadee on 2008-07-13
I was wondering if I can get someone to assist me in figuring out what could possibly be causing hibernate and suspend to not work since I upgraded to Ubuntu 8.04. Before upgrading I was on 7 something, I can't remember the exact version, but hibernate and suspend were both working.

---

### Post by mali2297 on 2008-07-13
In what way does hibernate and suspend not work? What happens when you try those actions?

From the terminal, try
```
sudo /etc/acpi/sleep.sh
```
or
```
sudo -i
echo mem > /sys/power/state
```

For hibernate, try
```
sudo /etc/acpi/hibernate.sh
```
or
```
sudo -i
echo disk > /sys/power/state
```

Also, check that you have swap enabled with
```

free -m

```

---

### Post by katdadee on 2008-07-13
Hey Martin,
What's happening is that the system seems to start to hibernate or suspend, the monitor shuts off but the computer remains on. If I attempt to press any button to wake the machine nothing happens, I end up having to press the reset button on the computer.

---

### Post by mali2297 on 2008-07-13
There is a similar problem reported here:
[http://ubuntuforums.org/showthread.php?t=847772](http://ubuntuforums.org/showthread.php?t=847772)

Try suspending by typing
```

sudo /etc/acpi/sleep.sh force

```
in the terminal. Any luck?

---

### Post by katdadee on 2008-07-14
Hey Fam,
I tried this one sudo /etc/acpi/sleep.sh force and it turned off my monitor, left the computer on, and the only way I could access anything was to press the reset button.

---

### Post by andy6363 on 2008-07-16
I'm having the same problem as you.  Just waiting and searching around for answers.
Sony Vaio VGN-CR123E running Hardy Heron here.

---

