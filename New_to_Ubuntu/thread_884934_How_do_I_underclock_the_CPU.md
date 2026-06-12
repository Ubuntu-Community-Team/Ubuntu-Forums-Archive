---
title: "How do I underclock the CPU?"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by mlinchits on 2008-08-09
I want to underclock the 1.7 Ghz CPU on my Thinkpad as I can no longer bear the fan noise. Since I am in Gnome, I've tried the "Scaling Monitor" and "Emifreq" panel applets, but changing the settings in their drop down menus does nothing to the CPU frequency. I then tried changing the settings in BIOS and now my CPU runs at a constant 1.4 Ghz. Is it possible to go lower than that or to have the CPU alternate between say 0.8 and 1.4 depending on demand? If so, could anyone please recommend an app/solution?

By the way here a console output - not sure if contains any useful info:

mlinchits@MIBM:~$ lsmod | grep acpi_cpufreq
acpi_cpufreq 10796 1
freq_table 5536 3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
processor 36872 3 acpi_cpufreq,thermal


Thanks,
Max

---

### Post by neurostu on 2008-08-09
I was able to downclock my CPU on my T61 with:
```

sudo dpkg-reconfigure gnome-applets

```
Click OK
Select YES
then add **CPU frequency monitor** to your panel...
You can then set the frequency on your CPU.

---

### Post by Diabolis on 2008-08-10
If I don't use gnome, is there a system value that can be adjusted?

---

### Post by sdennie on 2008-08-10
> **Diabolis said:**
> If I don't use gnome, is there a system value that can be adjusted?

Try the cpufreq-info and cpufreq-selector utilities.  They should allow you to change how the CPU frequency scaling happens.

---

### Post by mcduck on 2008-08-10
You could also try this:

1. Press Alt-F2 and run "gconf-editor" to open the Configuration editor.

2. Browse to apps/gnome-power-manager/cpufreq

3. Change the value of the "policy_ac" key to "powersave".

(alternatively, you could set it to "nothing" and try changing the value of the "performance_ac" key.)

This trick only works if your CPU supports frequency scaling, and you can't just select *any* speed you want, the available speeds deend on the CPU itself. Because of this using the "policy_ac" key would be the easier way, as setting it to "powersave" should keep the CPU at the slowest available speed all the time.

You can also use "conservative" instead of "powersave". This allows CPU to use higher speeds when under heavy load, but tries to keep the speed as low as possble.

---

### Post by wangsacl on 2008-09-12
> **neurostu said:**
> I was able to downclock my CPU on my T61 with:
```

sudo dpkg-reconfigure gnome-applets

```
Click OK
Select YES
then add **CPU frequency monitor** to your panel...
You can then set the frequency on your CPU.

After I run the command, and click OK, then select yes, the window just disappear..:confused::confused: What should I do?

---

### Post by Gepetto on 2008-09-18
> **wangsacl said:**
> After I run the command, and click OK, then select yes, the window just disappear..:confused::confused: What should I do?

Right click your little gnome bar, click "add to panel" and add the Gnome CPU Scaling Applet

---

