---
title: "script...run in terminal...."
date: 2012-11-24
forum: New to Ubuntu
---

### Post by amin021023 on 2012-11-24
hi all

I have a scrip which runs by this commands:
```
cd ~/ami
chmod +x get-config.sh
sh get-config.sh

```
but I want it to run simply by double click...


thanks in advance

---

### Post by newb85 on 2012-11-24
Perhaps you should understand those commands.

```
cd ~/ami
```
This merely takes you to the directory where the script is.

```
chmod +x get-config.sh
```
This merely makes the script executable.

```
sh get-config.sh
```
This runs the script.

Before any script can be run, it must be made executable, but this doesn't have to be done every time, just once for each script.  So, if you've made it executable once, that second step isn't necessary anymore.  Once it's executable, you should be able to double-click it and it should execute.

You could also make the file executable by right-clicking it and hitting Properties.  Under the Permissions tab, there's a check-box for "Allow executing file as program".

---

### Post by amin021023 on 2012-11-24
> **newb85 said:**
> 
You could also make the file executable by right-clicking it and hitting Properties.  Under the Permissions tab, there's a check-box for "Allow executing file as program".

I already done that...but it still needs that second command otherwise I get this error:
```
sh: 0: Can't open get-config.sh

```


my question is how can I run the script with just a double click?

or how can I run the script without doing the second command? (chmod +x get-config.sh)

---

### Post by newb85 on 2012-11-24
Odd...  You get that error when you double-click the file after making it executable?

Perhaps you could attach this script or tell us where you got it so we can better understand what you're doing.

---

### Post by amin021023 on 2012-11-24
> **newb85 said:**
> Odd...  You get that error when you double-click the file after making it executable?

Perhaps you could attach this script or tell us where you got it so we can better understand what you're doing.

no I get that error when I try with terminal...

ok this is my goddamn script:
```
#!/system/bin/sh

cd ~/android/AminKernel/MSM8660-6.1.A.2.45/kernel/
ARCH=arm CROSS_COMPILE=~/android/AminKernel/toolchains/arm-eabi-linaro-4.6.2/bin/arm-eabi- make fuji_nozomi_defconfig
```

it can be run by this commands in terminal:
```
cd ~~~
chmod +x get-config.sh
sh get-config.sh
```

but I want it to run simply by double click...I already made it executable by right-clicking it and hitting Properties but it still doesn't work that way....

---

### Post by newb85 on 2012-11-24
It looks like your script is a dash script.  My shell script experience is limited to bash scripts, so I don't know if there's some nuance of dash causing the hangup.

Just checking, when you get that error message in the terminal, are you already in the directory containing the script?

---

### Post by evilsoup on 2012-11-24
Try changing the first line of your script to
```
#!/bin/sh
```

I'm not sure that the rest of the script is syntactically correct, one line per command is the usual standard... but then, I only know bash. What is the script supposed to do?

---

