---
title: "Controlling fan speeds?"
date: 2011-11-29
forum: New to Ubuntu
---

### Post by James.A.Parnell on 2011-11-29
How can i control/slow down the cpu fan on 11.10? using some form of GUI if possible. thanks :)

---

### Post by wolfen69 on 2011-11-29
Try the *Thinkfan* app.

---

### Post by Mark Phelps on 2011-11-30
> **James.A.Parnell said:**
> How can i control/slow down the cpu fan on 11.10? using some form of GUI if possible. thanks :)

Basically -- you DON'T -- that is, unless you want to burn out your CPU.  The fan is running because the CPU is HOT.  IF you use some utility to slow down the fan, the CPU will burn out.

This overheating is a common problem on 11.10 -- one that does not currently have a solution.

---

### Post by khelben1979 on 2011-11-30
> **Mark Phelps said:**
> Basically -- you DON'T -- that is, unless you want to burn out your CPU.  The fan is running because the CPU is HOT.  IF you use some utility to slow down the fan, the CPU will burn out.

This overheating is a common problem on 11.10 -- one that does not currently have a solution.

That is assuming he's using a standard cpu cooler. And if that is so, changing to a more quiet and yet efficient [Noctua cpu fan]("http://www.noctua.at/main.php?show=produkte&lng=en#cpu_retail") would solve the noise issue.

---

### Post by Mark Phelps on 2011-11-30
> **khelben1979 said:**
> ... changing to a more quiet and yet efficient Noctua cpu fan would solve the noise issue.

Agreed ... and there are other after-market coolers as well.  First thing I do when I buy or build a new PC is get a good after-market fan (because I usually overclock the processor).

But the OP's original question was about how to slow down the fan, not replace it with a quieter one.

---

### Post by jesse_A on 2011-12-06
Hi, I have a similar desire to quieten my computer - why should the fans be at full speed when browsing the web, for example?  I haven't been 100% successful in understanding how it works so some of my descriptions may not be technically correct, and it requires a bit of tinkering to get the fans to the speeds you want but I'll try and explain what I know and maybe someone else can come along and share their knowledge with us.  I've been using the program "fancontrol" which I setup thus;

This installs the sensors required to detect temperature
```
sudo apt-get install lm-sensors
```

This installs the fancontrol program
```
sudo apt-get install fancontrol
```

This detects which on board sensors your computer has
```
sudo sensors-detect
```

In the output of the last command there will be a line like this:

-----cut here-----
it87
-----cut here-----

There may well be others depending on your computer.  Each line between the 'cut here' sections should be appended to the modules file, I use gedit thus;
```
sudo gedit /etc/modules
```

Then add the cut section to it and save.

These modules then need to be installed, in my case I only have the it87 module but the modprobe command should be run for every one of your modules, thus;
```
sudo modprobe it87
```

Then you need to run the pulse width modulation (PWM) configuration which basically controls the voltages sent to each fan which thus defines its speed.
```
sudo pwmconfig
``` 

The defaults all the way through the setup process are generally fine, and then at the end (when you have 5 or so options depending on how many fans you have) if you select the fan to control you can define what speed the fan spins at below a minimum temp, at normal operating temp (between min and max) and above a maximum temperature.  I should warn you not to use 0 as a value as when you restart the computer you'll have a stopped fan and your computer should be buzzing to warn you you have a problem.  If this happens, quickly flash up a terminal and throw in the command;

```
sudo gedit /etc/fancontrol
```

and amend the two fan speed options **minstart **and **minstop **to numbers higher than 100, save and then restart your computer as fast as possible.

Currently I only know how to activate the changes by restarting the computer, but I'm sure some clever person knows how to do it more quickly.

I hope this helps.

---

### Post by Enginirical on 2011-12-06
Grrreat post Jesse! 

Its about time somebody began to consolidate the information on fan control. So many of us want a simple way to control pc noise and temperature through fan (and pump) speed control. I can't believe there is no simple GUI for this yet! 

If anyone out there knows anything more please contribute :)

So far my fan control is limited to the master fan on the mobo, controlled via the bios settings, the fan ramps up and down depending on CPU temp. I have 3 fans and a closed circuit water cooled system with quiet pump and rad. I want to see if this can be applied to ALL my fans AND the pump speed also, I'll let you know how things progress.

---

### Post by bknecht on 2011-12-12
I hope it's okay if I post my quite related question here. My desktop has some very strong fans, which are only needed when I play games under Windows (dual boot). SpeedFan in Windows regulates the fans, if not they show the same behavior under Ubuntu 11.10 (fresh install): Full power, then a slow down, full power etc.

Now I found out about fancontrol, sensors, sensor-detect and I've been running pwmconfig.

First my sensors weren't showing, so I installed a driver that should be included in the kernel :confused:

Then my sensors were showing, but pwmconfig would crash when checking the third fan (the first two seemed to slow down okay). The error message doesn't yield anything useful when I Google it: "Error on line 474, too many recursions."

pwmconfig continues after the error (so "crash" is probably over-exaggerated), but then it will create an empty config file for fancontrol.

So my guesses are to either use a different version of pwmconfig or write the fancontrol file without the help of pwmconfig. Can anybody help me with that (either the first or the second approach) or do you know a better solution to that problem?

---

### Post by cheway on 2011-12-15
Apologies in advance for not answering your question, bknecht, but I felt I should comment on this generally.

As has already been explained, slowing down your fans without any real feedback (closed-loop control), temperature in this case, is not a good idea.

That said, implementing closed-loop control in software is not a good idea either - there are many reasons as to why this could fall over and not work. It is far more robust to have this controlled in the hardware. For instance, if you were in an industrial environment and you needed to limit some heavy machinary from moving too far, proper hard-wired kill switches are always used as a last line of defence (even if software stops are present as well).

Same goes here. I understand the need to quieten noisy fans to a level that is appropriate. If you have a look around, you can buy units that mount in your PC that control your fans AND include temperature probes. This can then be programmed to spin the fans at the appropriate speed. Or, buy some decent fans and spin them at near full speed.

If you have a laptop, then stay away from all of this altogether, you want as much cooling as you can get.

Cheers,
Matt.

---

### Post by MG2R on 2011-12-17
> **cheway said:**
> If you have a look around, you can buy units that mount in your PC that control your fans AND include temperature probes. This can then be programmed to spin the fans at the appropriate speed.

Those add-in "hardware" units use software just as well to keep your fans running at a low speed and thus are just as well capable of crashing...

---

### Post by Ms. Daisy on 2011-12-17
For the average user, I would determine what process is eating up the CPU thus requiring high fan speeds before I messed around with fan control.  For instance, if it's the browser then maybe I could use adblocker & noscript to keep some of the stuff from loading in the first place.

Obviously people like Enginirical may have that already under control.  But seeing as how this thread is in "absolute beginners" we don't want to encourage newbies to overheat their machines.

---

### Post by amjjawad on 2011-12-17
> **James.A.Parnell said:**
> How can i control/slow down the cpu fan on 11.10? using some form of GUI if possible. thanks :)

You did not mention whether it's a PC or a Laptop?
As far as I know (I'm talking from experience here - happened with me), Controlling the FAN speed is done by BIOS. We have HP Pavilion DV6 at home and it was overheating big time. With a BIOS update (thanks to HP Customer Service over here), everything is OK now.

As Mark said, please don't do that.

---

### Post by amjjawad on 2011-12-17
> **mark phelps said:**
> basically -- you don't -- that is, unless you want to burn out your cpu.  The fan is running because the cpu is hot.  If you use some utility to slow down the fan, the cpu will burn out.

This overheating is a common problem on 11.10 -- one that does not currently have a solution.

+1

---

### Post by cheway on 2011-12-18
> **MG2R said:**
> Those add-in "hardware" units use software just as well to keep your fans running at a low speed and thus are just as well capable of crashing...

Well yes they must have software of some description in them, they don't run on witchcraft, but as it's software that runs independently of the OS in a ROM chip, and can't be altered/changed unless you actively try to hack it, it is somewhat safer.

Cheers,
Matt.

---

### Post by I2k4 on 2011-12-18
I'm pretty new to Ubuntu but have been experimenting with alternative versions for some time, looking to eventually replace XP.  

The original poster didn't mention his hardware configuration.  I have to say, after a fair amount of trial and error, that every version of 11.x on my little Acer netbook was too slow and too demanding of CPU and memory, and required more fan activity, as compared with 10.x versions.  

These demands caused me to stick to 10.x for my netbook and even my main Dell laptop, since the difference seems to be with the GUI and not with available software applications or other functionality - I seem to be able to do all the same stuff on my 10.x operating systems, but on the simpler and lighter weight old interface.

Not knowing the original poster's system, I'd only suggest that if it's an older or weaker one, he should consider using an older or lighter-weight Linux version instead of going nuts.  The 11.x Ubuntu really seems to be designed for newer systems with 4 or more GB RAM and powerful CPU chips.

---

### Post by amjjawad on 2011-12-21
> **I2k4 said:**
> I'm pretty new to Ubuntu but have been experimenting with alternative versions for some time, looking to eventually replace XP.  

The original poster didn't mention his hardware configuration.  I have to say, after a fair amount of trial and error, that every version of 11.x on my little Acer netbook was too slow and too demanding of CPU and memory, and required more fan activity, as compared with 10.x versions.  

These demands caused me to stick to 10.x for my netbook and even my main Dell laptop, since the difference seems to be with the GUI and not with available software applications or other functionality - I seem to be able to do all the same stuff on my 10.x operating systems, but on the simpler and lighter weight old interface.

Not knowing the original poster's system, I'd only suggest that if it's an older or weaker one, he should consider using an older or lighter-weight Linux version instead of going nuts.  The 11.x Ubuntu really seems to be designed for newer systems with 4 or more GB RAM and powerful CPU chips.

I've done some tests recently and I was surprised that Ubuntu 10.04 was running better than Xubuntu 11.04 and Mint LXDE 11. It was running as fast as Lubuntu 11.10 which made me really surprised. I didn't know that until I tested it myself. Perhaps it because Ubuntu 10.04 is an LTS and they did their best to make it as solid as rock, yet as fast as Lubuntu. This is as per my tests.

Please note the test I'm referring to has been done on a PC not a Laptop.

---

