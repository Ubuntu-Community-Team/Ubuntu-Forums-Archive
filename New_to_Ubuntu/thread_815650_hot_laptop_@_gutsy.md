---
title: "hot laptop @ gutsy"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by adamogardner on 2008-06-01
laptop is getting hot to the touch compared to my windows partition which has been the only temperature I knew up until a few weeks ago when I began using ubuntu.  whats up with that?  i have gutsy by the way, and don't know why computers get hot under a different operating system.  Should I be concerned?

---

### Post by tamoneya on 2008-06-01
its probably because you are using compiz and everything.  Windows XP has fairly low graphics resources.  Compiz is probably having your graphics card work harder and generate more heat.  As for if it is something to worry about can you provide us with some more concrete details.  Install lm-sensors and conky and give us some temps.  Both the CPU and GPU temps would be nice.

---

### Post by Joeb454 on 2008-06-01
It could just be the design of your laptop, mine gets very hot sometimes.

Strangely it gets very hot in the early hours of the morning - which I'm beginning to see as a sign ;)

Check System > Administration > System Monitor, and what is your CPU running at (it will give a percentage).

---

### Post by spiderbatdad on 2008-06-01
You can install sensors-applet via synaptic package manager. This will create an option under "add to panel" for Hardware sensors, to give you some idea...it is configurable. Could be your wireless card getting hot...try disabling it when it is not in use by right clicking the network monitor.

---

### Post by adamogardner on 2008-06-01
well I tried to install conky but found a problem.  I'll go work on that and in a minute start a new thread on it.  Thanks for the advice, and reassurance.

---

### Post by Joeb454 on 2008-06-01
You should just be able to run ```
sudo apt-get install conky
``` from a terminal

---

### Post by adamogardner on 2008-06-01
that seemed to work easier than finding conky on my computer.  incidently, I am wondeering still how to find that application  i tried to execute it from the deskbar applet.  nothing happened. DOHT!

---

### Post by JoshuaRL on 2008-06-01
If it turns out your processor is running high for some reason, there are a few steps you can take to drop the system load on resources.  

I would suggest going into System->Preferences->Indexing Preferences and turn off indexing preferences.  On an older laptop that dropped the standard load on the processor from ~20% t0 ~5%.

Another idea is to run Startup Manager and turn off processes that you know you don't need (like Bluetooth and Laptop processes if you don't have those).  That can make it quicker to boot up too.

---

### Post by adamogardner on 2008-06-01
ok i tried to add my hardware sensor applet to my top panel but it displays that I don't have sensors.  but this can't be   my computers got everything.  any ideas?

---

### Post by tamoneya on 2008-06-01
you need to install lm-sensors as well.```
sudo apt-get install lm-sensors
```

---

### Post by spiderbatdad on 2008-06-01
maybe you have some hardware detection problems...IDK you can run ```
dmesg > dmesg.txt
```in your terminal. This will write a small file in your home directory. Look through it to see if the kernel is reporting hardware detection problems during boot. I don't believe the key to your heat problems lies in solving any possible hardware detection problems...but who knows, and it may get your system running more smoothly...or faster booting.

conky is a cool app, but of course it uses cpu. There is a great conky thread for copying or writing a .conkyrc file to display the info you want displayed: [http://ubuntuforums.org/showthread.php?t=281865&highlight=.conkyrc](http://ubuntuforums.org/showthread.php?t=281865&highlight=.conkyrc)

basically copy/paste one to a text file. Name it .conkyrc (note the dot) and put in in your home directory. Press Alt+F2 and type in conky. You can also make a conky launcher for your panel.

---

### Post by adamogardner on 2008-06-01
here's what i get back but again when I try to place the hardware sensors applet icon on the dock I get the same alert that "no sensors found!"  
  
adamogardner@CRONUS:~$ sudo apt-get install lm sensors
[sudo] password for adamogardner:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package lm is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  lmodern
E: Package lm has no installation candidate

---

### Post by Joeb454 on 2008-06-01
Copy and paste this command ```
sudo apt-get install lm-sensors
``` into the terminal, and enter your password if/when asked :)

---

### Post by tamoneya on 2008-06-01
> **adamogardner said:**
> here's what i get back but again when I try to place the hardware sensors applet icon on the dock I get the same alert that "no sensors found!"  
  
adamogardner@CRONUS:~$ sudo apt-get install lm sensors
[sudo] password for adamogardner:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package lm is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  lmodern
E: Package lm has no installation candidate

Note the dash: "-" between "lm" and "sensors"

---

### Post by Sim777 on 2008-06-01
> **JoshuaRL said:**
> If it turns out your processor is running high for some reason, there are a few steps you can take to drop the system load on resources.  

I would suggest going into System->Preferences->Indexing Preferences and turn off indexing preferences.  On an older laptop that dropped the standard load on the processor from ~20% t0 ~5%.

Another idea is to run Startup Manager and turn off processes that you know you don't need (like Bluetooth and Laptop processes if you don't have those).  That can make it quicker to boot up too.

is there man for indexing?

---

### Post by Joeb454 on 2008-06-01
I think so - you could try ```
man trackerd
``` Though I don't know if that's what you're looking for :)

---

### Post by adamogardner on 2008-06-01
sounds like you know your stuff.  I'll check all that out.  thankyou very much.

---

### Post by adamogardner on 2008-06-01
hmm  well after fixing my really stupid mistake I get the following which looks good to me but offers the same results when I try to add the sensor icon to the top panel:

E: Invalid operation lm-sensors
adamogardner@CRONUS:~$ sudo apt-get install lm-sensors
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  debhelper module-assistant intltool-debian xulrunner-1.9 kbuild po-debconf
  libxalan110 html2text libxerces27 dpatch
Use 'apt-get autoremove' to remove them.
Suggested packages:
  sensord read-edid
The following NEW packages will be installed:
  lm-sensors
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 509kB of archives.
After unpacking 1556kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main lm-sensors 1:2.10.4-1ubuntu1 [509kB]
Fetched 509kB in 3s (142kB/s)      
Selecting previously deselected package lm-sensors.
(Reading database ... 113594 files and directories currently installed.)
Unpacking lm-sensors (from .../lm-sensors_1%3a2.10.4-1ubuntu1_i386.deb) ...
Setting up lm-sensors (1:2.10.4-1ubuntu1) ...

Creating config file /etc/sensors.conf with new version

---

### Post by tamoneya on 2008-06-01
ive never had great results with the automatic configuration of lm-sensors.  Follow this thread:
[http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

---

### Post by adamogardner on 2008-06-01
if it's "man indexing"  then no  there is no manual.  and everything runs super well, I just noticed a difference in temperature.  I am going to explore that area that you mentioned, thankyou.

---

