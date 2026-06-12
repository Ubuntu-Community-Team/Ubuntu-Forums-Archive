---
title: "How do you set a default brightness setting?"
date: 2014-04-17
forum: New to Ubuntu
---

### Post by jrozo17 on 2014-04-17
Hey guys sorry, I just have one more question.

I'm running Xubuntu 14.04 and have been messing with Ubuntu since back in 08. One thing I've noticed is that every time I've reset my laptop, the brightness gets cranked up to it's full setting again.

I prefer my brightness on the lowest setting and want it to stay that way... I've looked for solutions online but they just end up confusing me.

Would someone mind walking me through this step by step please?

---

### Post by Toz on 2014-04-17
You can add a command to /etc/rc.local to set the brightness on boot. However, we need to figure out the proper value and backlight interface. Can you open a terminal, run the following command and post back the results? It will return info about your backlight interface)s:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/{brightness,max_brightness,actual_brightness}; done
```

---

### Post by jrozo17 on 2014-04-17
> **Toz said:**
> You can add a command to /etc/rc.local to set the brightness on boot. However, we need to figure out the proper value and backlight interface. Can you open a terminal, run the following command and post back the results? It will return info about your backlight interface)s:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/{brightness,max_brightness,actual_brightness}; done
```

This is what I got:

```
/sys/class/backlight/acpi_video0
3
15
3
/sys/class/backlight/intel_backlight
306
4882
1225

```

---

### Post by Toz on 2014-04-17
First, determine which set of the following commands actually changes brightness:
```
echo 15 | sudo tee /sys/class/backlight/acpi_video0/brightness
echo 3 | sudo tee /sys/class/backlight/acpi_video0/brightness
```
...OR:
```
echo 4882 | sudo tee /sys/class/backlight/intel_backlight/brightness
echo 306 | sudo tee /sys/class/backlight/intel_backlight/brightness
```

-----

Now, open /etc/rc.local for editing with root privileges:
```
sudo -i mousepad /etc/rc.local
```
...and you're going to enter your command _above_ the *exit 0* line.

If the first set of commands adjusted brightness, then enter:
```
echo 3 > /sys/class/backlight/acpi_video0/brightness
```

If the second set of commands adjusted brightness, then enter:
```
echo 306 > /sys/class/backlight/intel_backlight/brightness
```

-----

Save the file and reboot to test.

---

### Post by ajgreeny on 2014-04-17
You might also be able to set a lower gamma level with something like ```
xgamma gamma 0.5
``` but experiment with the value by running it manually in terminal to get what you want.  You can then add the command to a script and run that after the gui has started in the list of autostart applications by using ```
bash -c "sleep 10; xgamma gamma 0.5"
```in the command box.

How you add to the autostart list will depend on the version of *ubuntu you use, but that should be easy for you to find.

See [http://ubuntuforums.org/showthread.php?t=764113](http://ubuntuforums.org/showthread.php?t=764113) for some more info.

---

### Post by jrozo17 on 2014-04-17
> **Toz said:**
> First, determine which set of the following commands actually changes brightness:
```
echo 15 | sudo tee /sys/class/backlight/acpi_video0/brightness
echo 3 | sudo tee /sys/class/backlight/acpi_video0/brightness
```
...OR:
```
echo 4882 | sudo tee /sys/class/backlight/intel_backlight/brightness
echo 306 | sudo tee /sys/class/backlight/intel_backlight/brightness
```

-----

Now, open /etc/rc.local for editing with root privileges:
```
sudo -i mousepad /etc/rc.local
```
...and you're going to enter your command _above_ the *exit 0* line.

If the first set of commands adjusted brightness, then enter:
```
echo 3 > /sys/class/backlight/acpi_video0/brightness
```

If the second set of commands adjusted brightness, then enter:
```
echo 306 > /sys/class/backlight/intel_backlight/brightness
```

-----

Save the file and reboot to test.

Works like a charm, thank you so much! You made it a very simple process. :)

Thank you also to ajgreeny for your help... Hopefully this can help people going through the same problem.

---

