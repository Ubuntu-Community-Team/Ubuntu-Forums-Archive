---
title: "After installing Asus GTX 560ti GPU not get diplay"
date: 2012-10-13
forum: New to Ubuntu
---

### Post by anandharaja on 2012-10-13
hi,
Today i purchased and installed Asus GTX 560ti GPU. i have windows 7 and Ubuntu 12.04, when i try to enter in to Ubuntu not get any display. and also i try to install fresh copy of Ubuntu but no luck.

---

### Post by Pilot6 on 2012-10-13
You need to boot into Ubuntu with nomodeset patameter and install proprietary Nvidia driver.

---

### Post by anandharaja on 2012-10-13
> **Pilot6 said:**
> You need to boot into Ubuntu with nomodeset patameter and install proprietary Nvidia driver.

You talking about this method [http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

i don't understand after "try ubuntu without installing"

how can i install the nvidia drivers?

---

### Post by Bashing-om on 2012-10-13
"try ubuntu without installing" -> in this instance is a test to see that you can indeed boot into ubuntu. If so, the advise in the link's following section is to be followed for installing the required driver.

 "try ubuntu without installing" -> press enter: and see if you do indeed boot up.

[INDENT][INDENT]hth <==BDQ
 
[/INDENT][/INDENT]

---

### Post by anandharaja on 2012-10-13
Ok Finally i installed fresh copy of ubuntu and updated my Nvidia drivers.
i want to monitor the GPU and CPU usage in my taskbar. i tried system indicator but it only show cpu and ram usage.

---

### Post by pqwoerituytrueiwoq on 2012-10-13
on xfce (xubuntu) i use a generic monitor and have it call this script
edit:
opps thought you said temperature, i would like to know how to get the gpu usage also

---

### Post by mips on 2012-10-14
[http://www.matrix44.net/blog/?p=876](http://www.matrix44.net/blog/?p=876)
[http://unix.stackexchange.com/questions/38560/gpu-usage-monitoring-cuda](http://unix.stackexchange.com/questions/38560/gpu-usage-monitoring-cuda)
[http://ubuntuforums.org/showthread.php?t=1926767](http://ubuntuforums.org/showthread.php?t=1926767)

---

### Post by anandharaja on 2012-10-14
i updated nvidia driver to latest version. but viewport rendering in blender the cursor hangs. what is the solution to my problem?

---

### Post by pqwoerituytrueiwoq on 2012-10-15
to my knowledge there is a cuda bug in 304.53, in ubuntu 12.10 they downgraded it to 304.43
edit:

the shell script does not work for my 550 ti you may find this useful
```
nvidia-smi | head -9 | tail -1 | awk '{print "FAN: "$2"\nTEMP: "$3"\nUSAGE: "$9"\nMEM: "$10}'
``````
nvidia-smi | head -9 | tail -1 | sed 's/[^0-9 ]//g' | awk '{print "FAN:\t"$1"%\nTEMP:\t"$2"°C\nUSAGE:\t"$3"%\nMEM:\t"$4/$5*100"%"}'
```

---

### Post by anandharaja on 2012-10-19
Today i going to install Ubuntu 12.10, need to install Ubuntu with nomodeset ?

---

### Post by anandharaja on 2012-10-20
ok finally i installed ubuntu 12.10, but unable to find additional driver option in system settings. and in software sources there is no option in additional drivers. so i download driver manually in nvidia website
but the file format in .run, i try to install i got**  Nouveau kernal driver is currently in use.....................**

Anyone give the step by step procedure to install .run file.

---

### Post by anandharaja on 2012-10-20
This is the error when i trying to install

[IMG]https://lh5.googleusercontent.com/-rqGz8FnBp1I/UIJqWu-IHJI/AAAAAAAAAgY/YKRhk3_u9wA/s734/Screenshot%2520from%25202012-10-20%252014%253A27%253A20.png[/IMG]

---

### Post by anandharaja on 2012-10-20
ok i disabled the nouveau as per instruction provided in nvidia readme file. after changing that my display goes worst and screen resolution also changed, when i press CTRL + ALT + F1 to F6 my display is black.
Please tell me the solution to install .run file.

---

