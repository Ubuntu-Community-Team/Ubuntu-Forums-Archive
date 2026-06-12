---
title: "Performance - Ubuntu Vs Zenwalk"
date: 2007-05-08
forum: Other OS Talk
---

### Post by ahaslam on 2007-05-08
After a lengthy absence from Ubuntu I installed Feisty on a spare partition & was pleasantly surprised with its speed increase over Dapper. With this in mind I decided to bench it against my daily OS, Zenwalk 4.4. My Zenwalk install is pretty standard with only a custom kernel (using the standard config, adding only extra hardware support & removing nothing). The Fiesty install is fresh & lean, there's no added packages & most easily disabled services have been stopped (logging, power management, cron, the rest...). 

The tests that I carried out were: Glxgears, Super_pi & Nexuiz timedemo. For my tests, all configurations of hardware & software were identical (drivers, governors, video settings, etc), the only differences are the distro's themselves. The results:

GLXGEARS 
Ubuntu:
```
ahaslam@Desktop:~$ glxgears
101646 frames in 5.0 seconds = 20329.074 FPS
102155 frames in 5.0 seconds = 20430.816 FPS
102242 frames in 5.0 seconds = 20448.335 FPS
102215 frames in 5.0 seconds = 20442.914 FPS
102261 frames in 5.0 seconds = **20452.032 FPS**
102254 frames in 5.0 seconds = 20450.768 FPS
```
Zenwalk:
```
ahaslam[~]$ glxgears
97840 frames in 5.0 seconds = 19567.875 FPS
99617 frames in 5.0 seconds = 19923.301 FPS
99669 frames in 5.0 seconds = 19933.686 FPS
99916 frames in 5.0 seconds = **19983.147 FPS**
99741 frames in 5.0 seconds = 19948.170 FPS
99721 frames in 5.0 seconds = 19944.192 FPS

```
I'm using the same Nvidia driver version for each distro & Ubuntu shows a noticeable improvement over Zenwlak here.

SUPER_PI
Ubuntu:
```
------ Started super_pi run : Tue May 8 20:06:45 BST 2007
 Start of PI calculation up to 1048576 decimal digits
 End of initialization. Time=       0.188 Sec.
 I= 1 L=       0        Time=       0.612 Sec.
 I= 2 L=       0        Time=       0.708 Sec.
 I= 3 L=       1        Time=       0.712 Sec.
 I= 4 L=       2        Time=       0.708 Sec.
 I= 5 L=       5        Time=       0.712 Sec.
 I= 6 L=      10        Time=       0.704 Sec.
 I= 7 L=      21        Time=       0.700 Sec.
 I= 8 L=      43        Time=       0.704 Sec.
 I= 9 L=      87        Time=       0.704 Sec.
 I=10 L=     174        Time=       0.704 Sec.
 I=11 L=     349        Time=       0.704 Sec.
 I=12 L=     698        Time=       0.700 Sec.
 I=13 L=    1396        Time=       0.704 Sec.
 I=14 L=    2794        Time=       0.700 Sec.
 I=15 L=    5588        Time=       0.696 Sec.
 I=16 L=   11176        Time=       0.696 Sec.
 I=17 L=   22353        Time=       0.680 Sec.
 I=18 L=   44707        Time=       0.664 Sec.
 I=19 L=   89415        Time=       0.620 Sec.
 End of main loop
 End of calculation.    Time=      13.869 Sec.
 End of data output.    Time=       0.080 Sec.
 Total calculation(I/O) time=      **13.949(       0.384) Sec.**
 ------ Ended super_pi run : Tue May 8 20:06:59 BST 2007
```
Zenwalk:
```
------ Started super_pi run : Tue May 8 20:13:31 BST 2007
 Start of PI calculation up to 1048576 decimal digits
 End of initialization. Time=       0.188 Sec.
 I= 1 L=       0        Time=       0.613 Sec.
 I= 2 L=       0        Time=       0.709 Sec.
 I= 3 L=       1        Time=       0.710 Sec.
 I= 4 L=       2        Time=       0.711 Sec.
 I= 5 L=       5        Time=       0.709 Sec.
 I= 6 L=      10        Time=       0.712 Sec.
 I= 7 L=      21        Time=       0.709 Sec.
 I= 8 L=      43        Time=       0.710 Sec.
 I= 9 L=      87        Time=       0.710 Sec.
 I=10 L=     174        Time=       0.712 Sec.
 I=11 L=     349        Time=       0.709 Sec.
 I=12 L=     698        Time=       0.709 Sec.
 I=13 L=    1396        Time=       0.709 Sec.
 I=14 L=    2794        Time=       0.709 Sec.
 I=15 L=    5588        Time=       0.706 Sec.
 I=16 L=   11176        Time=       0.701 Sec.
 I=17 L=   22353        Time=       0.691 Sec.
 I=18 L=   44707        Time=       0.672 Sec.
 I=19 L=   89415        Time=       0.630 Sec.
 End of main loop
 End of calculation.    Time=      13.979 Sec.
 End of data output.    Time=       0.078 Sec.
 Total calculation(I/O) time=      **14.057(       0.511) Sec.**
 ------ Ended super_pi run : Tue May 8 20:13:45 BST 2007
```
However small the difference, high 13's is always better than low 14's. As the result was close I decided to repeat the test after a reboot for each distro, the gap remained constant with Feisty in the lead.

So the gpu & cpu both perform better individually under Feisty, let's see how it copes with a 3d game:

NEXUIZ TIMEDEMO
Ubuntu:
```
date 2007-05-08 20:10:08 | enginedate 10:42:09 Jan 23 2007 | demo demos/demo1.dem | commandline ./nexuiz-linux-686-glx  | **result 1909 frames 20.4632991 seconds 93.2889655 fps** min/avg/max: 22.5600446/93.2889655/371.1732072
```
Zenwalk:
```
date 2007-05-08 20:17:02 | enginedate 10:42:09 Jan 23 2007 | demo demos/demo1.dem | commandline ./nexuiz-linux-686-glx  | **result 1909 frames 17.7829022 seconds 107.3503065 fps** min/avg/max: 24.5067330/107.3503065/517.6388494
```
So Zenwalk pulls the trump & performs noticeably better when both cpu & gpu are in high demand. I wondered if it were due to memory usage but that never exceeded 60% and swap wasn't utilised, so I guess not :-k

I was quite surprised by this. Initially I thought Zenwalk would wipe the floor. When Ubuntu won the 1st  two I then assumed it would go on utilise that speed & translate it into real performance.


Feel free to add your performance observations/benches. ;)

---

### Post by jinx099 on 2007-05-08
glxgears is not a benchmark

I think the nexuiz timedemo really says it all.  That is the only thing you posted that tests most of the system instead of one specific component.

---

### Post by ahaslam on 2007-05-09
> **jinx099 said:**
> glxgears is not a benchmark

I think the nexuiz timedemo really says it all.  That is the only thing you posted that tests most of the system instead of one specific component.

Of course it's a benchmark, it doesn't have to stress the entire system, as long as the results are consistent it's useful for comparing performance. I thought it would be interesting to test cpu & gpu separately as well as together, using only Linux app's. Calculating pi is the definitive cpu bench for any speed freak.

It's very true that the Nexuiz timedemo shows the true leader as it excels when the key components are all under moderate stress. Though I am very impressed & equally surprised that Ubuntu performs better at the individual tasks, if you could shed some light on this it would be appreciated.

Feel free to add your own comparisons :)

---

### Post by kazuya on 2007-05-09
That is surprising news to me as well. I have noticed that Feisty is much faster than edgy. The speed is comparable to pclinuxos2007 and zenwalk now. There is one other thing to check for..:

By default, Ubuntu goes to two virtual desktops, while Zenwalk uses or has four by default. Did you ensure that the two distros had the same DEs installed and identical applications running..

I would test this out myself. Ubuntu Feisty has greatly improved in speed though.

---

### Post by RAV TUX on 2007-05-09
Those numbers are great but I have found Wolvix and rPath based distros to be reliably faster, and more stable. elive is great also, especially in speed.

---

### Post by ahaslam on 2007-05-10
@kazuya, the main difference was Gnome, though I stopped every service other than dbus in Ubuntu, both had 2 virtual desktops. For fairer comparison, I installed xfce4 but the Timedemo results were the same (=/-1.0).

@Rav Tux, is Wolvix noticeably faster than Zenwalk? I just installed Arch 64 last night, that currently kicks Zenwalk's 455 in Nexuiz, though it's not playing the sound properly atm, shouldn't be much & it looks promising ;)

---

### Post by RAV TUX on 2007-05-10
> **Anthony Haslam said:**
> 
@Rav Tux, is Wolvix noticeably faster than Zenwalk?

Yes, at least for me. 

Give [**Wolvix**]("http://www.google.com/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fwolvix.org%2F&ei=zPFCRs2xCJjgggTEgd2dCw&usg=AFrqEzc3DXdN63-gNuf_i1vmZPNEcjRCAQ&sig2=V2raYktxV_CK51LLa-cwnw") a try.

---

