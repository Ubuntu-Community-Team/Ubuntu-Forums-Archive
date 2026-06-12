---
title: "where can i download nvidia kernel ?"
date: 2012-11-08
forum: New to Ubuntu
---

### Post by anandharaja on 2012-11-08
hi,
i downloaded nvidia driver from official site if i try to install the driver i got the following error **"unable to find the kernel source tree for the currently running kernel. please make sure you have installed the kernel source file for your kernel and that they are properly configure..................................."**.

Where can i download the driver .deb package?

---

### Post by dannyboy79 on 2012-11-08
what kernel are you using?

```
uname -r
```

within synaptic, do you have "sources" box ticked for updates? once you have that, do a search for your kernel version source files.

---

### Post by anandharaja on 2012-11-08
just now installed ubuntu 12.10

3.5.0-17-generic

---

### Post by anandharaja on 2012-11-08
can i use this ppa:francisbrwn9/kernels ? i think this kernel is not properly working with nvidia driver.
where can i download .deb nvida kernel for ubuntu 12.10

---

### Post by dannyboy79 on 2012-11-08
first, what is your graphics chipset? and what driver are you trying to get working? Also, I would never trust PPA's for kernel related stuff unless you really understand what you're doing. THe kernel is the heart of your system.

---

### Post by anandharaja on 2012-11-08
Nvidia GTX 560ti

---

### Post by dannyboy79 on 2012-11-08
did you install the kernel source for your kernel? within the software center, do a serach for kernel, and one will be kernel source for your kernel number, install that. If you don't see "source" files, you need to enable the source repository within the perferences of the software center.
check out this thread:
[http://ubuntuforums.org/showthread.php?t=1766510](http://ubuntuforums.org/showthread.php?t=1766510)

---

### Post by anandharaja on 2012-11-08
i downloaded driver from nvidia website, which kernel i need to enable?
[IMG]https://lh6.googleusercontent.com/-u9Wnwq5nfjo/UJvYQAl68oI/AAAAAAAAAiQ/bJd-pLJQ3nU/s576/Screenshot%2520from%25202012-11-08%252021%253A32%253A26.png[/IMG]

---

### Post by dannyboy79 on 2012-11-08
just do these commands

```
sudo apt-get install linux-source
```
```
sudo apt-get install linux-headers-generic
```

that should do it I think. :)

---

### Post by anandharaja on 2012-11-08
Thank you for you help, i successfully installed driver but the GPU temperature is always above 40*C is it ok? and the animation not showing why?

[IMG]https://lh5.googleusercontent.com/-XjK1LAUhM3M/UJvg2iAnhUI/AAAAAAAAAig/20SYylGnY8U/s743/Screenshot%2520from%25202012-11-08%252022%253A08%253A42.png[/IMG]

---

