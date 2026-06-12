---
title: "High-level harware accessing"
date: 2008-08-09
forum: Programming Talk
---

### Post by clinux on 2008-08-09
Hello,

I would like to know if and how it's possible to access hardware components, like sensors, in high-level languages. Maybe a good guide?
Also I'm missing a linux developer network with some serious API/(ABI?) documentation under linux.

thanks.

---

### Post by pmasiar on 2008-08-09
Which language? How you define "high-level"?

Sensor manufacturer should provide a library, usually for C (and languages which can build wrapped for C libraries, like Python). Or you mean open-source drivers for non-disclosed hardware?

You may want to read "how to ask questions" in my sig.

---

### Post by Zugzwang on 2008-08-11
> **clinux said:**
> I would like to know if and how it's possible to access hardware components, like sensors, in high-level languages. Maybe a good guide?
Also I'm missing a linux developer network with some serious API/(ABI?) documentation under linux.


Things are often a little bit more complicated "here" (others might disagree). You should note that "Linux" is a bunch of packages build together to a "linux distribution". Since all packages are made by different people, they are very different and there is no *single* API documentation. They are separate for each component/package you are dealing with.

Talking of hardware and sensors (you did forget to mention whether you want to access the "internal" sensors of your computer, like CPU temperature or you connect something external (e.g. a USB temperature sensor). Since such information is provided by different parts of the system there is no unique source but you will have to find the respective part and read its manual. Note that for external sensors there might be no Linux driver existing.

However, sometimes its even easier to access this stuff using Linux. The main reason is that some device access capabilities are mapped to the file system. For example the current CPU temperature on my computer can be read from the "virtual file" /proc/acpi/thermal_zone/THM/temperature. You might want to try out the following (in a terminal):

```

cat /proc/acpi/thermal_zone/THM/temperature

```

---

