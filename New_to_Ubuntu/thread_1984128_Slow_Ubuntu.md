---
title: "Slow Ubuntu"
date: 2012-05-21
forum: New to Ubuntu
---

### Post by 3dmatrix on 2012-05-21
My Ubuntu is graudually geting slower. Simple applications like Gedit (and many others) are taking much longer to open or respond. What could be the reason ? What can I do to make the system work faster ?

---

### Post by mörgæs on 2012-05-21
Please give a complete hardware description.

---

### Post by 3dmatrix on 2012-05-21
> **mörgæs said:**
> Please give a complete hardware description.

Well i do not have problem providing the hardware details but i think that does not has much to do with my problem as when i installed Ubuntu several months back, it was running very well but progressively it is getting slower. And if this continues it might get terribly slow in weeks / months to come so i wish to get some advise to ascertain what might be going wrong and how i could make it run as it was doing when i installed it.

---

### Post by fermin on 2012-05-21
You might be running more background/startup applications than at the beginning. Check "Startup Applications" from the Dash menu and also any aplication showing in the Unity panel. I've also found that if you activate Gwibber with accounts it is always running in the background thereafter, updating your broadcast accounts, and sucking a great deal of reasources every now and then. Hope this helps.

---

### Post by cortman on 2012-05-21
Also, what version of Ubuntu are you using?
If an older version, it might be smart to do a clean reinstallation of the current LTS, 12.04.

---

### Post by 3dmatrix on 2012-05-21
> **cortman said:**
> Also, what version of Ubuntu are you using?
If an older version, it might be smart to do a clean reinstallation of the current LTS, 12.04.

Its Ubuntu 11.10. I had tried to upgrade to 12.04 abt 3 weeks back but was facing errors and so posted a thread here but received no reply so did not upgrade.

[http://ubuntuforums.org/showthread.php?t=1966048](http://ubuntuforums.org/showthread.php?t=1966048)

---

### Post by 3dmatrix on 2012-05-21
> **fermin said:**
> You might be running more background/startup applications than at the beginning. Check "Startup Applications" from the Dash menu and also any aplication showing in the Unity panel. I've also found that if you activate Gwibber with accounts it is always running in the background thereafter, updating your broadcast accounts, and sucking a great deal of reasources every now and then. Hope this helps.

Gwibber is deactivated. And there are not too many start up applications in that list. How can i make a list of those applications ? So that i cud post it here.

---

### Post by Rodney9 on 2012-05-21
I would install htop, it is a small file that runs in terminal, see screenshot

```
sudo apt-get install htop
```

It will show you what's using your cpu and memory.

Rodney

---

### Post by 3dmatrix on 2012-05-22
> **Rodney9 said:**
> I would install htop, it is a small file that runs in terminal, see screenshot

```
sudo apt-get install htop
```

It will show you what's using your cpu and memory.

Rodney

Dont we get the same info through System Monitor - under the processes tab ?

---

### Post by Nick_Kats on 2012-05-22
Not exactly. Htop gives more information about services and processes, and how much resources each one uses

---

### Post by nguyenphivu on 2012-05-22
You should check in the System Monitor to see how many processes are running and then select some to stop and see.

---

### Post by 3dmatrix on 2012-05-22
> **nguyenphivu said:**
> You should check in the System Monitor to see how many processes are running and then select some to stop and see.

I am worried i might kill some important process and that might crash the system. So i rather wanted to print a list here to get everyone's opinion. How can i copy/paste a list here ?

---

### Post by Rodney9 on 2012-05-22
You could take a screenshot of system monitor or copy and paste top in the terminal.

Rodney

---

### Post by 3dmatrix on 2012-05-22
I have attached two snapshots, one based on memory and the other arranged as per cpu usage.
Kindly advise if u see any abnormal usage.

---

### Post by Rodney9 on 2012-05-23
Nothing looks to strange or hungry of your resources.

A lighter Flavour of Ubuntu like [Xubuntu]("http://xubuntu.org/tour/") or [Lubuntu]("http://lubuntu.net/") would run faster for you.

Rodney

---

### Post by juustahiker on 2012-05-23
you might want to try reducing your swappiness, this will reduce the number of read/writes the the hard disk. and will ease up RAM usage. most computers have enough ram that the swap space shouldn't be used but without a hardware description I have no way of knowing.

---

### Post by 3dmatrix on 2012-05-24
> **juustahiker said:**
> you might want to try reducing your swappiness, this will reduce the number of read/writes the the hard disk. and will ease up RAM usage. most computers have enough ram that the swap space shouldn't be used but without a hardware description I have no way of knowing.

I have 2 Gb of RAM

---

### Post by 3dmatrix on 2012-05-25
> **3dmatrix said:**
> I have 2 Gb of RAM

How do we do that ? Moreover do we have things like Temp folder / catche / history etc that might be geting full so anyone who could give some suggestion.

I do not wish to change my OS from Ubuntu to any LowerBuntu because if my hardware was not suitable for it then how is it that it worked well for many months and just since last one month or so it has become slow.

---

### Post by Hadaka on 2012-05-25
There are many possibilities for your slow down, start with your modem/router
see if there are internal log files filled,or grime inside,or others using your
connection. its also a good thing to check the cpu fan and cooling fins in the pc
to see if dust and dirt have caused it to run hotter and slowing it down. You can 
choose to not save history if you are using firefox. and then there is just plain 
age factor,older the machine, the electronics tend to weaken over time, slowing
things down. log files for other activities you do on your machine. 2 gig ram should
be plenty for 11.10  but..most older machines run at 400mhz, no matter what speed
ram you choose. I doubt ram is the issue any way, as you have stated it used to seem
alot faster. pretty much all you can do is start going through whatever possibilities
you can think of and check them out. Probably not the answer you were looking for
but there are countless reasons systems slow down after time.
good luck

---

### Post by 3dmatrix on 2012-05-25
> **Hadaka said:**
> There are many possibilities for your slow down, start with your modem/router
see if there are internal log files filled,or grime inside,or others using your
connection. its also a good thing to check the cpu fan and cooling fins in the pc
to see if dust and dirt have caused it to run hotter and slowing it down. You can 
choose to not save history if you are using firefox. and then there is just plain 
age factor,older the machine, the electronics tend to weaken over time, slowing
things down. log files for other activities you do on your machine. 2 gig ram should
be plenty for 11.10  but..most older machines run at 400mhz, no matter what speed
ram you choose. I doubt ram is the issue any way, as you have stated it used to seem
alot faster. pretty much all you can do is start going through whatever possibilities
you can think of and check them out. Probably not the answer you were looking for
but there are countless reasons systems slow down after time.
good luck

I am not talking abt slow internet - i said slow ubuntu. even simple applications like gedit at times take very long to open.

Its also not a problem of old computer - this notebook was purchased 5 months back and ubuntu was running well but as i install more applications and update the system it keeps getting slow. So what could be a solution for this ? What could be going wrong ?


.

---

### Post by 3dmatrix on 2012-06-24
Any suggestion to make my Ubuntu run faster - as it did earlier when it was installed.

---

### Post by alenn on 2012-06-24
- Install BleachBit (you have it in software center)
- Install Preload (sudo apt-get install preload)
- disable any unnessery applications from startup

---

### Post by zombifier25 on 2012-06-24
Since you have 2 GB of RAM, decrease swappiness like juustahiker has stated. The higher the swappiness value, the more often your system moves running processes into swap, which is much slower than RAM. How to [here](https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F).

---

