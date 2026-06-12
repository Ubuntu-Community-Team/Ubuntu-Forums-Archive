---
title: "Gnome temperature sensors?"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by schnauzer93 on 2008-05-18
When I add the GNOME temperature sensor applet to my panel, I get four temperatures: 11, 1, 6, and -8 degrees, none of which are even close to correct. Thoughts anyone?

---

### Post by mano cazalet on 2008-05-18
[Here]("http://www.techthrob.com/tech/linuxsensors.php") is a good guide. 
I hope it helps you.

---

### Post by marcgh on 2009-01-01
Thanks for the tip, got the temp. sensors for CPU and mainboard working.

Just one more question: I don't have any of my 2 HDD monitored.
In the sensor applet preferences I can see them as /dev/sda and /dev/sdb but I don't know how to show their values.

Thanks in advance

---

### Post by SuperSonic4 on 2009-01-01
Do you have hddtemp installed? It is in the repos.

If/when you do it is just ```
sudo hddtemp /dev/sd[COLOR="Red"]*x*[/COLOR]
```

where x is a letter a, b, c, ..., z

---

