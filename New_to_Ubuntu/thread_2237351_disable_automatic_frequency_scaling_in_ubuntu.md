---
title: "disable automatic frequency scaling in ubuntu"
date: 2014-08-01
forum: New to Ubuntu
---

### Post by prashant6 on 2014-08-01
hello everyone. i am pretty new to ubuntu. i have a quad two core processor & all the frequencies are in discrete levels. i want that the CPU frequency be fixed at a value that it does not change. for example if i fix my CPU governor to say performance mode, it runs at highest system frequency irrespective of the amount of load on CPU. it is possible to fix the CPU frequency to other values 800 MHz so that they don't change during the execution of my application.

---

### Post by Jesse_Campton on 2014-08-01
Have a look here: [http://askubuntu.com/questions/3924/disable-ondemand-cpu-scaling-daemon](http://askubuntu.com/questions/3924/disable-ondemand-cpu-scaling-daemon)

---

### Post by Doug S on 2014-08-01
Hi and welcome to Ubuntu forums.

The answer depends on your processor and which scaling driver you are using (and maybe if a different driver can be used). What is your processor? Intel or AMD or? And what do you get for this:```
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver
```

---

### Post by prashant6 on 2014-08-02
hi. the processor is Intel(R) Xeon(R) CPU E3-1240 v3

---

### Post by prashant6 on 2014-08-02
regarding this command, cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver
 i m getting acpi-cpufreq

---

### Post by prashant6 on 2014-08-02
hi all. i have been able to achieve the automatic frequency disabling in ubuntu. here are the steps:
Step 1: switch the ubuntu into user space cpu frequency governor mode as by using the command-->
sudo cpufreq-set-r -g userspace
Step 2: select the frequency at which u want your system to work by running these commands-->
sudo apt-get install indicator-cpufreq
indicator-cpufreq -f
Step 3: the cpu frequency indicator will appear in upper left corner of screen. you can select the desired frequency for your system.

---

### Post by prashant6 on 2014-08-02
please any one tell me how to mark the thread as [solved]??

---

### Post by Impavidus on 2014-08-02
Click "thread tools" near the top of the page, then "mark as solved".

---

