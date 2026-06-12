---
title: "[SOLVED] quick question"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by hyperhopper on 2008-08-27
I have some different desktops that have linux on them but have unknown specs... how can I find their specs?

---

### Post by iaculallad on 2008-08-27
> **hyperhopper said:**
> I have some different desktops that have linux on them but have unknown specs... how can I find their specs?

Using your terminal:

```
sudo lshw
```

---

### Post by unutbu on 2008-08-27
This will list the hardware:

```
sudo lshw
lspci -nnvv
lsusb
```

---

### Post by hyperhopper on 2008-08-27
WOW- I am scarred for life- too much info

how do Ijust get proccesor-ram and storage capabilities--maybe graphics driver too...

---

### Post by iaculallad on 2008-08-27
> **hyperhopper said:**
> WOW- I am scarred for life- too much info

how do Ijust get proccesor-ram and storage capabilities--maybe graphics driver too...

For your CPU:

```
sudo lshw | grep CPU
```

For your VGA:

```
lspci | grep VGA
```

---

### Post by hyperhopper on 2008-08-30
it just says "description:cpu"

---

### Post by gmxgeek on 2008-08-30
If your processor is intel, try
```

sudo lshw | grep -i intel

```

---

### Post by hyperhopper on 2008-08-30
then I get ```
configuration: driver=Intel ICH latency=64 maxlatency=11 mingnt=52 module=snd_intel8x0
```

---

### Post by gmxgeek on 2008-08-30
Well now you know your processor config :)

but in all seriousness try 
```

sudo apt-get install sysinfo
sysinfo

```

should be more what you are looking for

---

### Post by hyperhopper on 2008-08-30
and then what just to find my ram...

---

### Post by gmxgeek on 2008-08-30
click on "Memory" in tht application. It should tell you all about it.

---

### Post by SunnyRabbiera on 2008-08-30
Or you can just check out the control panel under system> administration > system monitor
the first tab :D

---

### Post by gmxgeek on 2008-08-30
meh. sysinfo goes into a little more depth. But yeah, i actually forgot about that tab. Only use system monitor to watch performance and kill processes ^^"

---

### Post by SunnyRabbiera on 2008-08-30
> **gmxgeek said:**
> meh. sysinfo goes into a little more depth. But yeah, i actually forgot about that tab. Only use system monitor to watch performance and kill processes ^^"

well its good if you want base information of a system.

---

### Post by hyperhopper on 2008-08-30
thank you!

---

