---
title: "LCD Backlight"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by siddharthshukla on 2008-08-11
Whenever i run ubuntu during booting my laptop's LCD's brightness reduces to 0% and it requires me to increase it manually every time. Is there a way in which i can set the default brightness of the lcd  to something like 80% whenever it loads.

---

### Post by unutbu on 2008-08-11
Perhaps try
```

echo -n 80 | sudo tee /proc/acpi/video/VGA/LCD/brightness

``` (I'm getting this command from
[http://www.linuxscrew.com/2007/10/25/ajust-lcd-brightness-from-command-line-works-at-dell-1501/](http://www.linuxscrew.com/2007/10/25/ajust-lcd-brightness-from-command-line-works-at-dell-1501/)
) This command should allow you to change the brightness of the LCD from the command-line. The "sudo tee" is to give you root power to alter the /proc/.../brightness file.

If it works, then you can make it part of your boot process by editing /etc/rc.local: Put
```

echo -n 80 > /proc/acpi/video/VGA/LCD/brightness

```
before the final line, "exit 0".

Also, there is a bug discussion which seems relevant:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/12637](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/12637)

You might pick up other solutions there if the above does not work.

---

