---
title: "Ubuntu resolution problem"
date: 2012-12-31
forum: New to Ubuntu
---

### Post by Zuhair1 on 2012-12-31
hello
i am using ubuntu for more then 6 months now and so far i like it very much.
but when i installed it in my new pc it did not detect the monitor and consider it as "Unknown" and only offer a low resolutions

i tried some command ... like "xrandr" and it works for adding the wanted resolution 
but the problem is when i reboot the system i have to do it all over again

---

### Post by Zuhair1 on 2012-12-31
and i cant find the xorg.conf any where 
I am using ubuntu 12.10

---

### Post by Cheesemill on 2012-12-31
Have you installed any drivers for your graphics card?
Go to System Settings > Software Sources and click on the 'Additional Drivers' tab. Is anything listed?

Also nowadays the Xorg.conf file is optional, your machine will run OK without it. You can create the file if you need to but this is usually handled by your cards graphic driver.

If you need any more help can you post back with the output of the following command so we can see what graphics card you have:
```
lspci | grep VGA
```

---

### Post by Zuhair1 on 2012-12-31
nothing is shown in the Additional Drivers tab

and this is the command output
```
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)

```

---

### Post by 90Ninety on 2012-12-31
Have you tried using the 'resize- auto resize ' feature on your display monitor ?

Fixed it for me !

---

### Post by Zuhair1 on 2013-01-01
> **90Ninety said:**
> Have you tried using the 'resize- auto resize ' feature on your display monitor ?

Fixed it for me !
no ... still can't detect my monitor

---

