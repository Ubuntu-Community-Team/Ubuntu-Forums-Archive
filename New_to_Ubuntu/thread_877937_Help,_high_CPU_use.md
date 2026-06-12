---
title: "Help, high CPU use"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by RAJESHKSV on 2008-08-02
hi guys,

   I have been using ubuntu 7.10 for 4 months and recently I shifted to 8.04 .I installed compiz and now my lap became very slow:( CPU usage will always be minimum 40% even if no applications are running(for my friends it will be around 10% only). When i open firefox and play songs ,songs will stop a number of times and even it takes a lot of time for firefox to open.When i open linux dc++ the condition becomes too worse( BUT MY OTHER O.S. VISTA IS WORKING FINE ).My lap with 2Gb ram behaves as if it has 256MB ram in 8.04 .

My lap config:
Dell vostro 1500 model
ram-2gb
harddisk 120gb(30 gb for ubuntu -10gb free space in ubuntu)
Intel core 2 duo-1.60Ghz

I think a number of applications might be running in background(as well as in startup).plz tellme  how to speed up my lap..thanks in advance ...

---

### Post by bumanie on 2008-08-02
Type > top in terminal; you will be able to see which processes are hogging the cpu. Post the list if you are not sure what to do with it.

---

### Post by neurostu on 2008-08-02
When you installed 8.04 did you take the automatic upgrade or fresh install route?

---

### Post by sayakb on 2008-08-02
Can you post the output of the following command?
```
top
```

---

### Post by knightcoder on 2008-08-02
Are you using any Nvidia graphics card ??

---

### Post by northern lights on 2008-08-02
Run```
top
```and you can check who the culprit is.

> **RAJESHKSV said:**
> plz tellme  how to speed up my lapAs an aside, you might want to check "lap" in your dictionary of choice. Might also tell you why portable PCs are called "laptops" in the first place...
:)

---

### Post by RAJESHKSV on 2008-08-02
Thanks 4 ur suggestion .this is the output

top - 21:11:04 up  7:08,  2 users,  load average: 1.20, 1.47, 1.61
Tasks: 169 total,   4 running, 165 sleeping,   0 stopped,   0 zombie
Cpu(s): 52.3%us,  1.4%sy,  0.4%ni, 44.1%id,  1.5%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   2074316k total,  1998636k used,    75680k free,   130004k buffers
Swap:   996020k total,      288k used,   995732k free,  1357360k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+ COMMAND                                                                                         
 6480 root      20   0  844m  45m  14m R   89  2.2  63:01.84 Xorg                                                                                            
25076 rajeshks  20   0 41348  21m  12m S   13  1.1   3:03.35 gnome-system-mo                                                                                 
 6877 rajeshks  20   0 88592  29m  13m S    2  1.5   2:01.25 gnome-panel                                                                                     
10896 rajeshks  20   0 93576  68m  21m S    2  3.4  27:42.95 compiz.real                                                                                     
 6271 haldaemo  20   0  6308 4356 3592 S    0  0.2   0:16.32 hald                                                                                            
 6978 rajeshks  20   0 26348  13m 9104 S    0  0.7   0:13.58 nm-applet                                                                                       
23785 rajeshks  21   1  165m  27m  11m S    0  1.3   0:43.33 linuxdcpp                                                                                       
26050 rajeshks  20   0 81472  20m  11m R    0  1.0   0:00.88 gnome-terminal                                                                                  
 6755 rajeshks  20   0 31596 6256 3504 S    0  0.3  10:02.71 pulseaudio                                                                                      
23133 rajeshks  20   0  151m  47m  18m S    0  2.4   8:00.22 totem                                                                                           
23358 rajeshks  20   0  209m  98m  24m S    0  4.9   3:13.74 firefox                                                                                         
    1 root      20   0  2844 1692  544 S    0  0.1   0:01.60 init                                                                                            
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                        
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.34 migration/0                                                                                     
    4 root      15  -5     0    0    0 S    0  0.0   0:02.36 ksoftirqd/0                                                                                     
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                      
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.10 migration/1                                                                                     
    7 root      15  -5     0    0    0 S    0  0.0   0:00.70 ksoftirqd/1                                                                                     
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                      
    9 root      15  -5     0    0    0 S    0  0.0   0:00.26 events/0                                                                                        
   10 root      15  -5     0    0    0 S    0  0.0   0:00.22 events/1                                                                                        
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                                                         
   47 root      15  -5     0    0    0 S    0  0.0   0:00.30 kblockd/0                                                                                       
   48 root      15  -5     0    0    0 S    0  0.0   0:00.26 kblockd/1                                                                                       
   51 root      15  -5     0    0    0 S    0  0.0   0:00.02 kacpid                                                                                          
   52 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                                                    
  145 root      15  -5     0    0    0 S    0  0.0   0:00.02 kseriod                                                                                         
  189 root      15  -5     0    0    0 S    0  0.0   0:07.76 kswapd0                                                                                         
  230 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0                                                                                           
  231 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/1                                                                                           
 1459 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                                                                                   
 1462 root      15  -5     0    0    0 S    0  0.0   0:00.00 khubd                                                                                           
 1578 root      15  -5     0    0    0 S    0  0.0   0:00.00 khpsbpkt                                                                                        
 1608 root      15  -5     0    0    0 S    0  0.0   0:01.84 ata/0

---

### Post by stevoo on 2008-08-02
where is it ?

---

### Post by CatKiller on 2008-08-02
> **RAJESHKSV said:**
> I installed compiz and now my lap became very slow:(

If your graphics card is not very powerful, or you don't have the correct drivers installed, then all of the Compiz effects will be handled by the processor. As you have noticed, this can slow things down fairly dramatically. Even with the correct drivers, some of Compiz' effects can be very demanding for all but the most powerful hardware.

Try turning off some of the Compiz plugins, or set the effects lower, and see if that improves things. If it doesn't help, post details of your graphics hardware and the driver you are using, and hopefully someone here will be able to help you boost your performance.

---

### Post by bigbrovar on 2008-08-02
what graphic card are u running and can y try disabling compiz so we see what the problem could be

---

### Post by RAJESHKSV on 2008-08-02
@stevoo :I am sry I dnt get you

I had nvidia 8400 graphic card
I installed nvidia beta driver released on april 10
NVIDIA-Linux-x86-173.08-pkg1.run 
Tell me onething.. why is root taking 89%(I think I installed apache and all stuff..Is it due to that??)
PID USER PR NI VIRT RES SHR S %CPU %MEM TIME+ COMMAND
6480 root 20 0 844m 45m 14m R 89 2.2 63:01.84 Xorg

shd i have to stop it??

---

### Post by sdowney717 on 2008-08-02
scott@scott-desktop:~$ kill
kill: usage: kill [-s sigspec | -n signum | -sigspec] pid | jobspec ... or kill -l [sigspec]
scott@scott-desktop:~$ 

type kill then the pid number to kill anything you want to stop

---

### Post by philinux on 2008-08-02
> **RAJESHKSV said:**
> @stevoo :I am sry I dnt get you

I had nvidia 8400 graphic card
I installed nvidia beta driver released on april 10
NVIDIA-Linux-x86-173.08-pkg1.run 
Tell me onething.. why is root taking 89%(I think I installed apache and all stuff..Is it due to that??)
PID USER PR NI VIRT RES SHR S %CPU %MEM TIME+ COMMAND
6480 root 20 0 844m 45m 14m R 89 2.2 63:01.84 **[COLOR="Red"]Xorg[/COLOR]**

shd i have to stop it??
```
PID USER PR NI VIRT RES SHR S %CPU %MEM TIME+ COMMAND
6480 root 20 0 844m 45m 14m R 89 2.2 63:01.84 **[COLOR="Red"]Xorg[/COLOR]**
```

Thats xorg using 89% could have been a spike. As has been said disable desktop effects just to see what difference it makes.

It helps if you wrap code marks around text like the above.

---

### Post by knightcoder on 2008-08-02
I had the same problem with Nvidia graphics card. There is a bug in the old driver of Nvidia that opens up a memory leak.

I installed EnvyNG and it pretty much did everything to remove the old drivers and install the new ones for me. Now, its working perfectly.

You might want to check Envy here :

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by RAJESHKSV on 2008-08-03
I have checked disabling desktop effects but still root is taking >50% cpu ..when i enabled desktop effects it is taking 80% all the time and is not a spike.I wanna ask one more thing ....

Mem:   2074316k total,  2012744k used,    61572k free,    54576k buffers

Why is 2012744k of memory is being used(this is not a spike)

@knightcoder--have u faced the same prob(cpu usage is very high and lap is very slow)??you told there is a prob with old dirver of nvidia naa..Did u mean there is a problem with NVIDIA-Linux-x86-173.08-pkg1.run 
plz temme how did envy solved the prob.. 


My cpu usage will always be >40% irrespective of number of applications..plz help..

---

### Post by bodhi.zazen on 2008-08-03
To all : Please keep this thread on topic. I am going to change the title to one less inviting of OS discussion / recurrent discussions and more appropriate to assistance.

Specifically , if you want to help, please feel free to do so. If you want to discuss Ubuntu vs. windows use recurrent discussions.

---

### Post by knightcoder on 2008-08-04
My CPU usage was about normal. The memory was the one getting used a lot.
With no extra applications open, I would have initially 30% memory usage and if I leave my laptop idle for 2 hours, it would go up to about 70%. I googled a lot and found that it was a problem(memory leak bug) with the Nvidia card which was using old drivers.

Install EnvyNG from the link in the prev post and it'll do the replacement of drivers for you. Its pretty straightforward.

Think it should help.

---

