---
title: "[SOLVED] Frequency scaling gone ?"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by laffinet on 2008-06-28
Hi !

I'm using a Pentium Dual CPU T2330 and used to have frequency scaling.

Now (don't know since when) frequency scaling is not available anymore. 

When I try to add the scaling applet to the gnome panel I get an error message saying "CPU frequeny scaling not supported".

When I try "powersave -A" in a terminal I get "Speedstepping is not supported.". 

What happened ? Where is my scaling gone ?

Thanks for any help

PS I'm running hardy 2.6.24-19 generic

---

### Post by laffinet on 2008-06-29
bump

---

### Post by sayakb on 2008-06-29
Open gconf-editor and goto /apps/gnome-power-manager/cpufreq and change CPU frequencies from there.

---

### Post by laffinet on 2008-06-30
I'm afraid I don't have that option.

All I've got under /apps/gnome-power-manager/cpufreq is:

consider nice (unticked)
performance_ac (85)
performance_battery (25)
policy_ac (nothing)
policy_battery (nothing)

So I wouldn't know where to change any frequency settings.

Any ideas ?

---

### Post by Canis familiaris on 2008-06-30
Try:
sudo dpkg-reconfigure gnome-applets

---

### Post by sayakb on 2008-06-30
The **performance_ac** and **performance_battery** are the %ages of CPU used with AC power and battery respectively. 
If you want a good UI, install [Ubuntu Tweak]("http://getdeb.net/release.php?id=2750"). Goto Applications->System Tools->Ubuntu Tweak. Now Expand **System** and click **Power Manager** and **check** the *Show CPU frequency option* checkbox.
Quit Ubuntu tweak, goto System->Preferences->Power Management and change **Computer speed policy** to change frequency. For example, if you have a 1.6GHz processor, setting it to powersave will scale the frequency to 1GHz

---

### Post by laffinet on 2008-06-30
> **Anurag_panda said:**
> Try:
sudo dpkg-reconfigure gnome-applets

Okay, that didn't do anything. :(

> The performance_ac and performance_battery are the %ages of CPU used with AC power and battery respectively.
If you want a good UI, install Ubuntu Tweak. Goto Applications->System Tools->Ubuntu Tweak. Now Expand System and click Power Manager and check the Show CPU frequency option checkbox.
Quit Ubuntu tweak, goto System->Preferences->Power Management and change Computer speed policy to change frequency. For example, if you have a 1.6GHz processor, setting it to powersave will scale the frequency to 1GHz 

I tried that too but still have no scaling. I ticked the "Show frequency control option" box, set the policies to "performance" on AC and "powersave" on battery.

I have no frequency settings at all in >Preferences>Power Management, gconf-editor hasn't changed (other than it is now showing the policies) and if I add the CPU frequency monitor applet to the gnome panel it still says that frequency scaling is not supported by my computer. But it used to be and I'm not aware that I changed anything. :confused:

To be clear: my computer used to scale the frequency depending on the load. I never set that up, it was there "out of the box" and now it's gone. Weird. That's what I'm trying to get back.

Sorry for the lengthy post, just trying to provide as much information as possible. Hopefully someone can help.

Thanks

---

### Post by sayakb on 2008-06-30
```
sudo apt-get install powertop
```
Now, set the policy to powersave for AC and battery. Then open a terminal and type:
```
sudo powertop
```
Note the CPU's frequency from there.

PS: Even after setting it to powersave, if the frequency remains unchanged, then your ACPI doesn't support frequency scaling as indicated.

---

### Post by laffinet on 2008-06-30
I won't be able to try this until later today, will report back how it went.

> PS: Even after setting it to powersave, if the frequency remains unchanged, then your ACPI doesn't support frequency scaling as indicated.

What has changed ? As mentioned, it used to work (without any fiddling on my behalf) so where did it go ? More importantly, how can I get it back ?

Wrong kernel ? Install different kernel ? Re-install power management ?

If any of the above, how ?

---

### Post by laffinet on 2008-07-01
Okay, I think I solved my problem.

Looks like I somehow uninstalled powernowd. Re-installed it and everything is working fine now. 

Thanks for all the help.

---

