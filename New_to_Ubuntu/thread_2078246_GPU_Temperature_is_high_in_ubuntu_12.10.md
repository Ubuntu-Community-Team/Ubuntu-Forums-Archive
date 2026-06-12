---
title: "GPU Temperature is high in ubuntu 12.10"
date: 2012-10-30
forum: New to Ubuntu
---

### Post by anandharaja on 2012-10-30
hi
i installed ubuntu 12.10, my GPU temperature in idle not come below 40*C, if i just open firefox it goes to 45*C and opening more tab or doing some other work increased the temperature to 50*C even a normal work.

But in windows i don't get these problem in idle temperature is around 34*c to 38*C and not more that 43*C during normal work.

What can i do?

---

### Post by wojox on 2012-10-30
Compiz is a little wonky for you it sounds. Try installing:
```
sudo apt-get update; sudo apt-get install gnome-panel
```
Reboot and login to Gnome Classic no effects

---

### Post by anandharaja on 2012-10-30
my system configuration is
Intel i5 2500
8GB RAM
GTX 560ti GPU

These configuration is not enough to handle compiz?

---

### Post by wojox on 2012-10-30
> **anandharaja said:**
> 

These configuration is not enough to handle compiz?

Looks good. Remember this is still a work in progress. Compiz is known to become a little untamed at times. I would install the panel and compare the diffrences.

---

### Post by anandharaja on 2012-10-30
Anyway downloading gnome-panel.

Psensor  not showing unity launch counter, but in guest account it showing why?

---

### Post by dodo3773 on 2012-10-30
Is this a laptop? Also, what is your cpu temperature when your gpu heats up? Are they related?

---

### Post by anandharaja on 2012-10-30
Hmm lots of error

[IMG]https://lh6.googleusercontent.com/-zo7-78hxx34/UJASFkxzq3I/AAAAAAAAAhw/iZ4J3t9XpyY/s1152/1.png[/IMG]

Still Temperature Not reduced 40 to 50*c  range for normal browsing.

---

### Post by anandharaja on 2012-10-30
[IMG]https://lh6.googleusercontent.com/-gO54LHaG2Z8/UJAT_UT0FCI/AAAAAAAAAh4/oxwh5VEvI58/s640/Screenshot%2520from%25202012-10-30%252023%253A21%253A31.png[/IMG]

Crash Report Window

---

### Post by wojox on 2012-10-30
[Troublesome Nvidia]("https://www.google.com/search?q=nvidia+on+ubuntu+12.10&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:unofficial&client=firefox-a")

---

### Post by anandharaja on 2012-10-30
Another Crash report

[IMG]https://lh5.googleusercontent.com/-t5h85rcug10/UJAV28cl1JI/AAAAAAAAAiA/ZFWDmPiahUY/s720/Screenshot%2520from%25202012-10-30%252023%253A28%253A43.png[/IMG]

---

### Post by anandharaja on 2012-10-30
After installed nvidia driver i try to open settings i got this error **"You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."**

after system restart setting open but lots of crash report.

---

### Post by anandharaja on 2012-10-31
What is the solution to my heating issue? anyone have heating problem?

---

### Post by HiImTye on 2012-11-01
sounds like your drivers aren't installed right. I had issues with the nvidia drivers not installing the kernel headers, and therefore not compiling, resulting in them not actually installing. I would start by checking to see if the kernel headers are installed
```
sudo apt-get install aptitude; aptitude search linux-headers~i
```if it doesn't end in lines like
```
tye@T:~$ aptitude search linux-headers~i
i A linux-headers-3.5.0-17          - Header files related to Linux kernel versi
i   linux-headers-3.5.0-17-generic  - Linux kernel headers for version 3.5.0 on 
```then you need to install the headers for your current kernel by first
```
aptitude search linux-image~i
```this will show you what kernel version in installed. once you know your kernel version, install the corresponding header package
```
aptitude search linux-headers
sudo apt-get install <header package>
```then finally
```
sudo apt-get install --reinstall nvidia-current
```

---

### Post by Yezinki on 2012-11-01
Is it a laptop?

---

### Post by anandharaja on 2012-11-01
> **Yezinki said:**
> Is it a laptop?
No Desktop


What kernel use? i using "ppa:francisbrwn9/kernels"

---

### Post by Yezinki on 2012-11-01
Nvidia do run hot....how is the environment & air flow?

---

### Post by Linuxisfast on 2012-11-01
My nvidia card on desktop even when playing games or doing intense HT movies never ever touches 55C and it idles at 45C. I have never ever seen temps below 40C even using Windows.

---

### Post by anandharaja on 2012-11-01
> **Yezinki said:**
> Nvidia do run hot....how is the environment & air flow?

Front, Side and Back 120mm fan, cabin cooler master elite 310. but in windows i don't get this heating problem.

and i noticed one thing after installed the nvidia driver the minimize and maximize animation shows just as a line.

---

### Post by anandharaja on 2012-11-04
> **Linuxisfast said:**
> My nvidia card on desktop even when playing games or doing intense HT movies never ever touches 55C and it idles at 45C. I have never ever seen temps below 40C even using Windows.
Really 45*C is normal in idle?

---

### Post by resruta on 2012-11-04
My older GeForce 9800GT is at 69°C in idle, around 80°C under heavy load.
I clean it periodically to prevent to much dust in the cooler. I have not had any problems since I bought it five years ago, even running 24/7.
I would not care that much, about the temperature. You could try cleaning the cooler, if there's a huge amount of dust. I'd recomment using compressed air. But be carefull not to let the fan spin to fast. It might generate far to high voltage and damage the board.

---

