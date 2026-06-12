---
title: "how can I tell what is using my CPU"
date: 2011-09-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by basilwatson on 2011-09-12
I THINK its or could be zeitgeist as per other thread

but I cant be sure 

ran TOP, it says CPU at 43 % , at idle.  but top says , one process at 3 % or something like that 
I can hear my fan , CPU going overtime , ie 40 odd percent 

I Really want to solve this ....

Question; how do I find out what is causing my cpu  to be so hoggy 

any help, most kind 

Stephen

---

### Post by SlugSlug on 2011-09-12
sure its your CPU fan not graphics card?  CPU looks idle

---

### Post by basilwatson on 2011-09-12
> **SlugSlug said:**
> sure its your CPU fan not graphics card?  CPU looks idle

Maybe how can I tell ?

when I run system monitor , it says cpu 80 %....

either way it shouldn't be like that 


Stephen

---

### Post by SlugSlug on 2011-09-12
incorrect drives etc can cause graphics card fan to spin.

can u post top and also sys mon at same time when its looking like that?

or look in sys mon processes and sort by cpu

---

### Post by basilwatson on 2011-09-12
> **SlugSlug said:**
> incorrect drives etc can cause graphics card fan to spin.

can u post top and also sys mon at same time when its looking like that?

or look in sys mon processes and sort by cpu

try this , 

somethings whirring away ,  slowed down now as I type , oh no back it comes 80% 

which means I can use cpu intensive apps as it will lock ( Vlc player for example ) 

anyway here is top and system monitor posted side by side 

I couldnt find software to monitor the graphics card 

Oh btw 

I tried unity 2d and it was the same , but another windows manager also the same ,( if I remember correctly ) the cpu loading 

Stephen

---

### Post by SlugSlug on 2011-09-12
sorry I ment the sys mon showing cpu usage and top -- as both of them show cpu idle

try screen shot it when cpu goes up

---

### Post by Basher101 on 2011-09-12
I just had the same issue. In my case it was Gimp that slowed down on me, CPU went to 70-80% and Compiz did not react. When i killed Gimp, Compiz stablezied and i just had to reopen gimp to continue working..

---

### Post by lucazade on 2011-09-12
there is a zombie process in your 'top' screenshot

try to see if cpu pike is due to this:

```
ps aux | awk '{ print $8 " " $2 }' | grep -w Z

```

and kill it with
```
kill -9 idnumber

```where idnumber is the result of the previous command

---

### Post by basilwatson on 2011-09-12
> **lucazade said:**
> there is a zombie process in your 'top' screenshot

try to see if cpu pike is due to this:

```
ps aux | awk '{ print $8 " " $2 }' | grep -w Z

```

and kill it with
```
kill -9 idnumber

```where idnumber is the result of the previous command


s@main-desktop:~$ ps aux | awk '{ print $8 " " $2 }' | grep -w Z
Z 32297

but it did drop the cpu for a second then the same .......

Now what be this process

Stephen


ps just tried , the process is killed ie not showing again and cpu is still at 60 % .....................................

---

### Post by lucazade on 2011-09-12
> **basilwatson said:**
> s@main-desktop:~$ ps aux | awk '{ print $8 " " $2 }' | grep -w Z
Z 32297

but it did drop the cpu for a second then the same .......

Now what be this process

Stephen


ps just tried , the process is killed ie not showing again and cpu is still at 60 % .....................................

if it drops the cpu for some seconds and then it raise again probably that process has been restarted automatically.

before killing the process you can look at its name with:

```
ps -aux | grep idnumber
```
where idnumber is the result of previous command

---

### Post by basilwatson on 2011-09-12
> **lucazade said:**
> if it drops the cpu for some seconds and then it raise again probably that process has been restarted automatically.

before killing the process you can look at its name with:

```
ps -aux | grep idnumber
```
where idnumber is the result of previous command
Sorry 

s@main-desktop:~$ ps -aux | grep 32297
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
s         3609  0.0  0.0   5660   804 pts/0    S+   19:49   0:00 grep --color=auto 32297
s@main-desktop:~$ 

because after a reboot 

s@main-desktop:~$ kill -9 32297
bash: kill: (32297) - No such process
s@main-desktop:~$ 

but cpu still 70 %


Stephen

thanks all

---

### Post by lucazade on 2011-09-12
> **basilwatson said:**
> Sorry 

s@main-desktop:~$ ps -aux | grep 32297
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
s         3609  0.0  0.0   5660   804 pts/0    S+   19:49   0:00 grep --color=auto 32297
s@main-desktop:~$ 

because after a reboot 

s@main-desktop:~$ kill -9 32297
bash: kill: (32297) - No such process
s@main-desktop:~$ 

but cpu still 70 %


Stephen

thanks all

because 32297 it doesn't exist anymore, you have to find out the new zombie process with the first command i wrote before.

---

### Post by basilwatson on 2011-09-12
> **lucazade said:**
> if it drops the cpu for some seconds and then it raise again probably that process has been restarted automatically.

before killing the process you can look at its name with:

```
ps -aux | grep idnumber
```
where idnumber is the result of previous command
yes sorry I did that 

s@main-desktop:~$ ps aux | awk '{ print $8 " " $2 }' | grep -w Z
s@main-desktop:~$ 

so no more zombies 

but still excessive cpu ............................

Stephen

---

### Post by cariboo on 2011-09-12
Both of your screenshots show apport running, could that be the problem, as it isn't running on my system. Could you try disabling apport, and see if the high cpu usages persists?

---

### Post by basilwatson on 2011-09-12
> **cariboo907 said:**
> Both of your screenshots show apport running, could that be the problem, as it isn't running on my system. Could you try disabling apport, and see if the high cpu usages persists?

nope 
s@main-desktop:~$ kill -9 9171
bash: kill: (9171) - No such process
s@main-desktop:~$ 


still running at 80 

just as a though , why dont the ubuntu developers visit here , this is where the real problems occur

remind me NEVER to use a beta ,,,,,,,

Luckilu this isnt my work machine , ...so no problem .....

but a bug this bad , shouldn't get to beta ....... alpha maybe , but a month before general release is again just plain ruinous 

Stephen

---

### Post by cariboo on 2011-09-12
How are you finding the apport pid? Use:

```
ps ax | grep apport
```

and note the pid, it is the first number on the left, then use the kill command on that pid.

---

### Post by basilwatson on 2011-09-13
still havent found what is causing mu cpu to run so high 

Any ideas , 

Stephen

---

### Post by lucazade on 2011-09-13
> **basilwatson said:**
> still havent found what is causing mu cpu to run so high 

Any ideas , 

Stephen

run a daily cd image and see if this issue is present...
if it runs normal then your installation is compromised, probably because of NN>OO upgrade before the final release.

---

### Post by basilwatson on 2011-09-13
> **lucazade said:**
> run a daily cd image and see if this issue is present...
if it runs normal then your installation is compromised, probably because of NN>OO upgrade before the final release.

how would I do that , separate partition?

Stephen

---

### Post by lucazade on 2011-09-13
> **basilwatson said:**
> how would I do that , separate partition?

Stephen

no need of separate partitions or installation.

download a .iso image from here:
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

for 32bit take this:  oneiric-desktop-i386.iso

burn it to a cd using brasero or copy to a usb pendrive (at least 1gb) using usb-creator-gtk

then reboot, start cd/pendrive and you can try it without installing anything to hd.

ps.. if you are not familiar with these tools it is probably better to stick with a stable ubuntu release.

---

