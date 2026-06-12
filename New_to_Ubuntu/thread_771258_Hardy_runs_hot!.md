---
title: "Hardy runs hot!"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by wheels. on 2008-04-27
So with the release of 8.04 I decided it was time to wipe windows clean and start afresh with 8.04, got it almost completely set up now, Wow installed, compiz fusion, everything is working, but one thing I have noticed is that my laptop hpdv9000 is getting extremely hot!
I decided to install lm-sensors to investigate, as it turns out I was right cpu's approaching 70 degrees Celsius and gpu up over 75 at times, this is definitely not a standard operating temperature, checked sysmonitor no processes using all of my cpu, so I tried disabling compiz, no effect on the temperatures either. My cpus are not even running at half frequency and temperature remains high and the fans never really seem to pick up and cool things down!

Thanks for the help!

My laptop:
HP Pavilion Dv9000
Amd Turion 64x2 2.00ghz (running 32bit 8.04)
2GBs ram
2 120gb seagate hdds
nvidia integrated graphics card, using drivers 169.12

---

### Post by daimaru on 2008-04-27
I just posted a thread to fix the nvidia gpu on toshiba p100's not sure if this also helps with a HP laptop, but since it's a nvidia problem it might just work. You could give it a try but keep your original dsdt.dsl file (make a copy of it before editing) so you can undo the stuff by recompiling the old dsdt.dsl file (step 5 and 6). No guarantees here, but hey you can always try it.


[http://ubuntuforums.org/showthread.php?t=771223](http://ubuntuforums.org/showthread.php?t=771223)

oh forgot to mention i have a nvidia go 7900 (toshiba satellite p100-239)

---

### Post by wheels. on 2008-04-27
> **daimaru said:**
> I just posted a thread to fix the nvidia gpu on toshiba p100's not sure if this also helps with a HP laptop, but since it's a nvidia problem it might just work. You could give it a try but keep your original dsdt.dsl file (make a copy of it before editing) so you can undo the stuff by recompiling the old dsdt.dsl file (step 5 and 6). No guarantees here, but hey you can always try it.


[http://ubuntuforums.org/showthread.php?t=771223](http://ubuntuforums.org/showthread.php?t=771223)

oh forgot to mention i have a nvidia go 7900 (toshiba satellite p100-239)

*Edit*
Tried your suggestion and _T_0 among other things were not in the dsdt.dsl file, so I guess this fix will not help me.

---

### Post by daimaru on 2008-04-27
sry to hear. Guess it only works on toshiba laptops. Sorry I couldn't be of more help.

---

### Post by wheels. on 2008-04-27
Thanks for the suggestion but I am not willing to give up on this yet, I am positive there has to be a workaround, I just have to find one soon, Idle temp with nothing open is 60 +, any and all ideas are welcome!

---

### Post by huntwell on 2008-04-27
I have a vostro 1000 and mine seems to be running hot as well. I haven't checked the temp as you have, but the fan turns on much more frequently than when using windows or gutsy or mint daryna.

If someone has suggestions on how to fix this issue, I would really appreciate it. I would hate to consider going back to Windows full time. I have made an almost complete conversion to Linux and don't want to stall complete conversion any longer than I have to.

Thanks all,
Huntwell

---

### Post by wheels. on 2008-04-28
Care to install lm-sensors and report back your temperature, I wouldn't mind knowing what temps, other people are getting.

---

### Post by huntwell on 2008-04-28
how do I install those kinds of sensors? I would be happy to if it didn't involve anything too complicated.

Thanks

---

### Post by wheels. on 2008-04-28
sudo apt-get install lm-sensors sensor-applet

then you should be able to add it to your gnome panel right click add to panel hardware sensor applet. 

also as a side note, i just installed ubuntu-restricted-extras with absolutely no intention to fix this problem and for some reason temps are lower but still too hot 55+ 
I will have to see what changed when I installed that package to cause things to cool by 10 degrees.

---

### Post by Niniel on 2008-04-28
I don't know, that doesn't look that unusual.
I have an older HP with a P4M @ 2.4 Ghz, and according to the sensor, the temperature fluctuates widely even with "nothing" running. I think 35 C was the lowest I've ever seen, but it's also been 55. 
As for the computer getting hot, that's what laptops are supposed to be doing. :)

---

### Post by radiopirate on 2008-04-28
I would be interested in the resolving of this problem I have a new laptop currently running Vista which i want to wipe in favour of Ubuntu

---

### Post by adult swim on 2008-04-28
radio have you tried running ubuntu yet? what are your computer specs?
edit! i see you are from lancashire.  a day in the life is one of my favorite songs (i hope im not to old!)

---

### Post by wheels. on 2008-04-28
> **Niniel said:**
> I don't know, that doesn't look that unusual.
I have an older HP with a P4M @ 2.4 Ghz, and according to the sensor, the temperature fluctuates widely even with "nothing" running. I think 35 C was the lowest I've ever seen, but it's also been 55. 
As for the computer getting hot, that's what laptops are supposed to be doing. :)

Yes its going to get hot, but approaching 70 degrees at idle and nearing 80 under a load? thats a little extreme, never have had heat problems with windows like that, Its that the fans just never seem to really kick in.

---

### Post by huntwell on 2008-04-28
Hmmm... I don't know what the problem is, but when I use the terminal and type 'sudo apt-get install sensor-applet' or 'sudo aptitude install sensor-applet' I get this message "E: Couldn't find package sensor-applet" and "Couldn't find any package whose name or description matched "sensor-applet"

Any suggestions?

---

### Post by lswest on 2008-04-28
my laptop's CPU is generally around 45°, but i found using ```
sudo powernowd -m 2 -vv
``` is a useful way of setting up frequency scaling so that it keeps temps nice.  Also, try changing the settings of your cpu scaling (by default it's aggressive and puts wear and tear on your CPU)

---

### Post by wheels. on 2008-04-28
> **huntwell said:**
> Hmmm... I don't know what the problem is, but when I use the terminal and type 'sudo apt-get install sensor-applet' or 'sudo aptitude install sensor-applet' I get this message "E: Couldn't find package sensor-applet" and "Couldn't find any package whose name or description matched "sensor-applet"

Any suggestions?

sorry my fault its sensors-applet

---

### Post by huntwell on 2008-04-28
No worries,

I installed the sensors applet, and hate to sound like a dope, but what do I do now? 

Thanks,

---

### Post by grannyw on 2008-04-28
I would try this code,this shut down hard disk power manager,and keeps the temperature low. 

```
sudo hdparm -B 255 /dev/sda
```
or if this wont work,try this
```
sudo hdparm -B 254 /dev/sda
```
THIS HELPED ME.
Try this on your own risk

---

### Post by cmnorton on 2008-04-28
You might want to enter a new bug, or tack on to

[https://bugs.launchpad.net/ubuntu/+bug/210300](https://bugs.launchpad.net/ubuntu/+bug/210300)

There is also a similar discussion in 
[http://ubuntuforums.org/showthread.php?t=763450](http://ubuntuforums.org/showthread.php?t=763450)

---

### Post by grannyw on 2008-04-28
it is a known bug in ubuntu in laptops.

---

### Post by yamawho on 2008-04-28
I installed 8.04 over the weekend on my desktop and noticed that it seems to be running hotter than the Mint 4 it replaced. The cpu fan seems to be running faster than before ...

---

### Post by nutpants on 2008-04-28
my dell m1210 runs ab 45 C idle cpu and 52 C gpu

is there a way to increase the fan speed 10% faster than normal>?


nutz

---

### Post by huntwell on 2008-04-28
In case anyone is interested this is the output of sensors from the terminal on my computer:

Adapter: PCI adapter
Core0 Temp:  +44.0°C                                    
Core0 Temp:  +49.0°C                                    
Core1 Temp:  +45.0°C                                    
Core1 Temp:  +35.0°C

---

### Post by wheels. on 2008-04-30
is there a utility to control fan speed, and set which temperatures the fan comes on at?

---

### Post by Kristopher on 2008-05-20
HP Pavilion DV6000 Ubuntu 8.04, laptop is very hot and the fans seem to be always going fast to try and cool it down.

---

### Post by Jensss on 2008-05-31
> **Kristopher said:**
> HP Pavilion DV6000 Ubuntu 8.04, laptop is very hot and the fans seem to be always going fast to try and cool it down.

Same laptop, same problem.
Can someone help please?

---

### Post by sayakb on 2008-05-31
Sorry, didn't read the entire thread. 
What I've done is: Open gconf-editor (Press Alt+F2 and type: gconf-editor)
Goto /apps/gnome-power-manager/cpufreq and change the performance ac and battery valuws to lower values (perhaps <50)

---

### Post by Bataille23 on 2008-05-31
My output CURRENTLY is

```
Core0 Temp:  +53.0°C                                    
Core0 Temp:  +47.0°C                                    
Core1 Temp:  +45.0°C                                    
Core1 Temp:  +43.0°C 
```

However, it was once (or twice; maybe thrice) so hot that the vent almost burned my hand upon touching it.  I figured that wasn't a good sign, but then I realized I was running about 1,000 things at once.  :redface:

It has, however, run pretty hot when idle (couldn't tell you exactly HOW hot), but I AM using a laptop and that IS, of course, to be expected.

You think you're hot now, though, try running Vista.  Mine had to have been running at about 80 degrees, and that was only after the first five minutes!  (i.e., right before I wiped Vista and did a full Hardy install)  :guitar:

---

### Post by Jensss on 2008-05-31
I run vista and 8.04 as dualboot on my Pavilion dv6000
At normal use Vista runs at about 30-40 degrees.
But ubuntu is even when there is no program open >60 degrees.
And after 10 minutes the fans go crazy.

I don't think that it's very normal..

---

### Post by Roundel on 2008-05-31
I have a HP ZD7000 and my cpu temp is usually around 73-75C with Hardy (very hot).  This wasn't the case with Gutsy, so I have hope that someone will come up with a fix for this eventually.

For now my fans blast full speed all the time.  My friends have nicknamed my computer "the hovercraft".:roll:

---

### Post by starcannon on 2008-05-31
[LIST]
[*]R-click on your top or bottom panel
[*]click on Add to panel
[*]select and add CPU Frequency Scaling Monitor
[/LIST]

```
sudo dpkg-reconfigure gnome-applets
```

Answer YES to the "run as root" question.

Now you should be able to left click on the cpu frequency scaling monitor and set the speed of your cpu. There are some presets in there as well, I just set mine to "Ondemand" that keep's the fan quite and the performance acceptable

GL

---

### Post by Roundel on 2008-06-03
Thanks Starcannon, this seems like a good solution in the short term.  I tried it on my HP ZD7000 and I got the error message 

"CPU frequency scaling unsupported: You will not be able to modify the frequency of your machine.  Your machine may be misconfigured or not have hardware support for CPU frequency scaling."

Is there anything you know of that might resolve this problem?  I checked the repositories but couldn't find anything.  I think it might just be an issue with my laptop hardware that makes it impossible.

---

### Post by starcannon on 2008-06-03
@Roundel
[SIZE="4"]UPDATE[/SIZE]
What cpu is in that laptop?

I know on my old Dell Inspiron | 5100 I had to add the P4 module because I was getting that same error message, could be you have a cpu that requires an additional module.
I used the modconf tool
```
sudo apt-get install modconf
```

Then run it:
```
sudo modconf
```

The section that will contain what you need is likely in:
```
 Select kernel/arch/x86/kernel/cpu/cpufreq modules 
```

After looking your computer up on google it would appear that,
You need the P4 Clock Mod for that machine:
```
p4-clockmod
```

That should get it working for you.

GL you may have to google around a bit to find any other specific modules you need for your laptop.

---

### Post by noland on 2008-06-05
i had the same problem in gutsy (now upgraded to hardy)...  i had installed a program called "gkrellm"  in which you can control a bunch of parameters... and i dunno why but, without that prog running, temp is super hot, i start that and it seems to take control of the fan and bring it back to 50 or less... does the job for me and its a lot more comfortable for the hand cuz high temp can be a pain.. and the fan is always running slowly but enough.

---

### Post by Roundel on 2008-06-12
Thanks Starcannon!  I used your suggestion, and its been working great for the last week.  I wanted to give it some time to see if I ran into any problems before I posted.  Seems very stable and fixes the problem.  What a relief!

Do you know if there's a similar control I could add for my GPU (I'm pretty sure they're not integrated on a ZD7000)?  Maybe Hardy already controls this, I don't know.

---

### Post by sergiom99 on 2008-06-17
@starcannon
how would it be for Kubuntu? I'm not sure I wanna install all the Gnome packages requiered for gnome-applets.
Thanks!

---

### Post by Dawa on 2008-06-30
I'm having the same problems on my HP Pavilion dz6500z CTO.  It has dual AMD turion 64s, but i'm running Hardy 32.  Anyway, sorry to be critical, but this absolutely sucks.  7.10 had a couple of things I had to mess with after install, but nothing was potentially damaging my computer.  Seriously, I could heat soup on this thing.  Looks like I'm stranded in Vista until Ubuntu works like it used to.

---

### Post by MacMan on 2008-07-01
I've always had CPU temperature problems with Kubuntu on my HP Pavillion dv6000: CPU scaling wouldn't work, the CPU was always running at the highest frequency, and the temperature would grow.

I've solved the issue with two fixes:
first, I've installed the latest laptop BIOS: this one turns the fan on earlier so the temperature doesn't go so high;
second, I've added these two boot options:
```
noapictimer irqpoll
```

After adding them, CPU scaling started working correctly, and the temperature is under control (usually around 44 °C). Using Win Vista the temperature is even lower (39 °C), but I'm happy anyway. The change also fixed Suspend to RAM, which wouldn't work before.

I hope this info can be useful for someone else.

Ciao.

---

