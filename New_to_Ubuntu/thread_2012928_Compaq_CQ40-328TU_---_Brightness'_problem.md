---
title: "Compaq CQ40-328TU --- Brightness' problem"
date: 2012-06-30
forum: New to Ubuntu
---

### Post by czgirb on 2012-06-30
Currently, I installed **Ubuntu 12.04** in my **Compaq CQ40-328TU** lappie.
Everything works fine ... **Sound, Plugged Network, WiFi, and Bluetooth**.
Except one thing ... it was the **Brightness**.

When inside Ubuntu, the brightness was set to be 35%.
But after re-start ... the brightness will back to default brightness.
How can I solved this problem?
Please guide me ... thank you.

**PS:**
I'm a newbie to Ubuntu. Pangolin is my first Ubuntu.
So, do not use any **ubuntu's expert language**, please?
Cos I will not understand.
**Sorry for my english.**

---

### Post by sandyd on 2012-07-01
> **czgirb said:**
> Currently, I installed **Ubuntu 12.04** in my **Compaq CQ40-328TU** lappie.
Everything works fine ... **Sound, Plugged Network, WiFi, and Bluetooth**.
Except one thing ... it was the **Brightness**.

When inside Ubuntu, the brightness was set to be 35%.
But after re-start ... the brightness will back to default brightness.
How can I solved this problem?
Please guide me ... thank you.

**PS:**
I'm a newbie to Ubuntu. Pangolin is my first Ubuntu.
So, do not use any **ubuntu's expert language**, please?
Cos I will not understand.
**Sorry for my english.**
Go to Unity Dash, and Type in "terminal".

post output of
```

ls /sys/class/backlight/*
cat /sys/class/backlight/*/brightness
```

---

### Post by czgirb on 2012-07-02
> **sandyd said:**
> 
Go to Unity Dash, and Type in "terminal".
post output of
```

ls /sys/class/backlight/*
cat /sys/class/backlight/*/brightness
```


**Here is the required output:**

> 
***@***:~$ ls /sys/class/backlight/*
/sys/class/backlight/acpi_video0:
actual_brightness  brightness  max_brightness  subsystem  uevent
bl_power           device      power           type

/sys/class/backlight/intel_backlight:
actual_brightness  brightness  max_brightness  subsystem  uevent
bl_power           device      power           type
***@***:~$ cat /sys/class/backlight/*/brightness
4
0
***@***:~$ 


---

### Post by sandyd on 2012-07-02
> **czgirb said:**
> **Here is the required output:**
Adjust the brightness each reboot by running
```

  echo "brightness_value" > /sys/class/backlight/intel_backlight/brightness

```, where brightness_value is the brightness of your display. The max brightness can be found by running
```

cat /sys/class/backlight/intel_backlight/max_brightness
```

add it to somewhere like /etc/rc.local so that it runs on boot

---

### Post by czgirb on 2012-07-03
> **sandyd said:**
> Adjust the brightness each reboot by running
```

  echo "brightness_value" > /sys/class/backlight/intel_backlight/brightness

```, where brightness_value is the brightness of your display. The max brightness can be found by running
```

cat /sys/class/backlight/intel_backlight/max_brightness
```add it to somewhere like /etc/rc.local so that it runs on boot

SORRY! Maybe I'm not say it clearly.
I said my brightness is 50%, cos I see the triangle is in the middle.
So ... 50% is estimation only.
Now, I tried to totally reduce my brightness to none. Is it 0%?

How can I know the brightness' value?

---

### Post by sandyd on 2012-07-04
> **czgirb said:**
> SORRY! Maybe I'm not say it clearly.
I said my brightness is 50%, cos I see the triangle is in the middle.
So ... 50% is estimation only.
Now, I tried to totally reduce my brightness to none. Is it 0%?

How can I know the brightness' value?
If it is about 50%, then it is half of max_brightness (see the second command)

---

### Post by czgirb on 2012-07-06
> **sandyd said:**
> Adjust the brightness each reboot by running
```

  echo "brightness_value" > /sys/class/backlight/intel_backlight/brightness

```, where brightness_value is the brightness of your display. The max brightness can be found by running
```

cat /sys/class/backlight/intel_backlight/max_brightness
```add it to somewhere like /etc/rc.local so that it runs on boot

> 
***@***:~$ cat /sys/class/backlight/intel_backlight/max_brightness
1
***@***:~$ echo "1" > /sys/class/backlight/intel_backlight/brightnessbash: /sys/class/backlight/intel_backlight/brightness: Permission denied
***@***:~$ echo "0" > /sys/class/backlight/intel_backlight/brightness
bash: /sys/class/backlight/intel_backlight/brightness: Permission denied
***@***:~$ echo 0 > /sys/class/backlight/intel_backlight/brightness
bash: /sys/class/backlight/intel_backlight/brightness: Permission denied
***@***:~$ 


Any opinion?

---

### Post by sandyd on 2012-07-06
> **czgirb said:**
> Any opinion?
Run sudo -i before those.

You don't need to do that if you stick it in /etc/rc.local.

---

### Post by czgirb on 2012-07-07
> **sandyd said:**
> 
Run sudo -i before those.


Do you mean I should type the following command in Terminal:
> sudo -i echo "0" > /sys/class/backlight/intel_backlight/brightness
or
> sudo -i echo 0 > /sys/class/backlight/intel_backlight/brightness

> **sandyd said:**
> 
You don't need to do that if you stick it in /etc/rc.local.


What it means ???
Hei bro! This is my first time for having using Ubuntu.
So, please do not use any expert's word, OK ???
It will makes me looks so silly, don't you?
Hahahaha

---

### Post by sandyd on 2012-07-08
> **czgirb said:**
> Do you mean I should type the following command in Terminal:

or




What it means ???
Hei bro! This is my first time for having using Ubuntu.
So, please do not use any expert's word, OK ???
It will makes me looks so silly, don't you?
Hahahaha
```
 sudo -i
echo "0" > /sys/class/backlight/intel_backlight/brightness 			 		
```

---

### Post by czgirb on 2012-07-08
> **sandyd said:**
> ```
 sudo -i
echo "0" > /sys/class/backlight/intel_backlight/brightness                      
```

> 
***@***:~$ sudo -i
[sudo] password for ***: 
root@***:~# echo "0" > /sys/class/backlight/intel_backlight/brightness
root@***:~# 


Any suggestion?

---

### Post by czgirb on 2012-07-25
Until today ... NO change at all
Any suggestion ....

---

