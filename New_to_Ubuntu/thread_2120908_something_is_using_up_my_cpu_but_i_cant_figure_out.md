---
title: "something is using up my cpu but i cant figure out what it is"
date: 2013-02-27
forum: New to Ubuntu
---

### Post by libihero on 2013-02-27
for the past week, i would randomly get high usage of my cpu, but i can not figure out what it is. when i go to system monitor, it shows all my cores are working, but when i try to figure out what program is hogging it, they are all quiet. i attached two pics to try to explain what i mean

---

### Post by matt_symes on 2013-02-27
Hi

Have you considered using a terminal program such as 

```
top
```

or its improved brother

```
htop
```

```
sudo apt-get install htop
```

They can give you detailed cpu usage information for user space programs.

Run it in a terminal and keep it minimized. Keep an eye on system monitor and when you get high cpu usage, take a look at top/htop in the terminal.

It should tell you what is using your cpu.

Kind regards

---

### Post by chadk5utc on 2013-02-27
> **libihero said:**
> for the past week, i would randomly get high usage of my cpu, but i can not figure out what it is. when i go to system monitor, it shows all my cores are working, but when i try to figure out what program is hogging it, they are all quiet. i attached two pics to try to explain what i mean

go to a terminal and simply type sudo top
[http://www.cyberciti.biz/tips/how-do-i-find-out-linux-cpu-utilization.html](http://www.cyberciti.biz/tips/how-do-i-find-out-linux-cpu-utilization.html)
you can also use sudo iftop which may have to be installed this will show network connections.

---

### Post by Ms. Daisy on 2013-02-27
Open a terminal by pressing ctrl + alt + T

Then type
```
top
``` which will display the processes running and the percentage of cpu they are using. It will report the PID, which you can use to kill the cpu-hogging process.

---

### Post by libihero on 2013-02-27
it has been a reallyyy long time since i posted here since ubuntu has been running fantastic for me the last couple years

i forgot how amazing the community is :)

thanks everyone!

---

