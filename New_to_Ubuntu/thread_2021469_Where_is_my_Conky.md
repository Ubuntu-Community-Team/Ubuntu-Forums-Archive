---
title: "Where is my Conky ?"
date: 2012-07-09
forum: New to Ubuntu
---

### Post by czgirb on 2012-07-09
I used Ubuntu 12.04 in Gnome Classic
I installed Conky from Ubuntu Software Center
But I found no conky on my menu.
My conky will show up only if I open it from Terminal.
Why?

Is it able to have conky as one of my startup application ?

---

### Post by Donjr on 2012-07-09
To run conky at startup, you have to do more than just run the conky command, because conky needs to be started after the desktop shows up, so that conky appears on top. So to do that, create an empty file in your home folder, let's call it .conky-startup.sh, make it executable and put this in it:

#!/bin/bash
sleep 30 && conky ;
Save the file and go to System > Preferences > Startup Applications, click "Add" and add the path to the .conky-startup.sh file, for instance /home/.conky-startup.sh


Found in Unixmen forums

---

### Post by QIII on 2012-07-09
Conky depends on a configuration file typically called /home/username/.conky/conkyrc.

If that does not exist, a very basic default conky is used.  It is nearly useless.

You have to construct conkyrc, which is too much to go in to here.

The command to launch it is typically

```
conky -c /home/username/.conky/conkyrc
```

The launch script would need to use that.

Designing and implementing your conkyrc for the first time can be intimidating.  I would suggest googling some fairly simple examples and building from there.

You will probably also want to install something like lm-sensors, then detect your sensors.  hddtemp will be necessary to monitor your hdd temps, and it will have to be configured with dpkg-reconfigure so that it will run without sudo.

All of this is too much to go in to here.

I'm on my cell phone so I can't add a link.  I'll try to get back to this to add some.

---

### Post by GreatDanton on 2012-07-09
Well, maybe that's right for previous versions of conky. I am using 1.9 and so called .conkyrc is now placed in home/etc/conky/conky.conf.

Maybe take a look at my thread where I posted the instructions for conky (in case anyone is interested post #48 ):
[http://ubuntuforums.org/showthread.php?t=2013848&page=5](http://ubuntuforums.org/showthread.php?t=2013848&page=5)


@Donjr: I don't have this command in my conky and everything works fine (conky shows on desktop), but that script is very good if you don't want to have any problems.

---

### Post by QIII on 2012-07-09
I believe conky.conf is the default one that is useless to begin with.

If you look at the thread you posted, people are referring to conkyrc.

If you log out with the option to save the session, conky will run at the next login.  If not, you have to start it.  Some prefer to sleep it and start it with a script to make sure everything else is running first on the first conky draw.

---

### Post by GreatDanton on 2012-07-09
> **QIII said:**
> I believe conky.conf is the default one that is useless to begin with.

Creating a conkyrc in your /home allows you to have one tailored by user.

True, but for beginners, is in my opinion, better to start with.

---

### Post by Kopkins on 2012-07-09
The conky config file can be specified as whatever you want. I use /home/user/.conkyrc. I start it with a simple bash script. 

```
#!/bin/bash

sleep 5

conky -c ~/.conkyrc

exit
```I've attached my conky config file for you to do anything with. It's fairly simple. Look up other threads to learn how to configure conky. It's fun to mess with. 

Good luck!

Kopkins

---

### Post by Frogs Hair on 2012-07-09
For manual startup and shutdown Alt + F2 
```
conky
```
```
killall conky
```
Dash will store these commands if using Unity.

---

### Post by QIII on 2012-07-09
> **Kopkins said:**
> The conky config file can be specified as whatever you want.

Which is why, of course, I said "typically".  ;)

---

### Post by stinkeye on 2012-07-09
Conky looks for a config @ **~/.conkyrc**
If the file doesn't exist it will load the default config @ **/etc/conky/conky.conf**

So if your only running 1 conky you just save your config to **~/.conkyrc**
and run with just **conky**

If you want to run more than one conky or like to test 
different configs, save your configs anywhere and
name them anything you want and use the -c option to specify a config.
eg
```
*conky -c /path/to/my/config*
```

Add to startup using the conky delay option -p (may need to increase delay)
eg
```
conky -p 10 -c */path/to/my/config*
```
or
```
conky -p 10
```

---

### Post by czgirb on 2012-07-10
I have **.conkyrc** file, which download from **devianart** ... and I placed in: **/home/***/****.conkyrc**

> **stinkeye said:**
> 
Add to startup using the conky delay option -p (may need to increase delay)
eg
```
conky -p 10 -c */path/to/my/config*
```or
```
conky -p 10
```

Oh! Please use simple word ... my knowledge to Ubuntu is very very unsufficient and now still in the LEARN level.

---

### Post by Kopkins on 2012-07-10
> **czgirb said:**
> 
Oh! Please use simple word ... my knowledge to Ubuntu is very very unsufficient and now still in the LEARN level.

He posted the commands that you need to use to run conky. In linux, several programs run from the command line. Opening a terminal will give you a command line, or you can use 'alt+f2' to pass a command to the system. 

So, if you want to use conky, you need to use the commands he gave you. It's not that he was being unclear. 

To test out your conky, press 'alt+f2' and type:
```

conky

```And you should get a conky window as long as the config file is good.

Best of luck,

Kopkins

---

### Post by stinkeye on 2012-07-10
> **czgirb said:**
> I have **.conkyrc** file, which download from **devianart** ... and I placed in: **/home/***/****.conkyrc**



Oh! Please use simple word ... my knowledge to Ubuntu is very very unsufficient and now still in the LEARN level.

If you have your config @ **/home/***/****.conkyrc**
then just running **conky** will load that config.

At this stage it's best to run in terminal as it will show any config errors. 
Hit the Super (windows) key and search for and open **terminal**
Type in **conky** in the terminal and press Enter.
[ATTACH]220998[/ATTACH]


If your config is ok you will have whatever is determined by the config displayed on the desktop.

Then to start conky automatically on boot, 
add to startup applications(top right in the panel)
using as the command
```
conky -p 10
```
[ATTACH]220999[/ATTACH]


The **-p 10** is an inbuilt conky option which will pause the starting of conky the number of secs specified.
This is needed when booting so conky doesn't run before the desktop is fully loaded.

---

### Post by czgirb on 2012-07-10
> **stinkeye said:**
> If you have your config @ **/home/***/****.conkyrc**
then just running **conky** will load that config.

At this stage it's best to run in terminal as it will show any config errors. 
Hit the Super (windows) key and search for and open **terminal**
Type in **conky** in the terminal and press Enter.
[ATTACH]220998[/ATTACH]


If your config is ok you will have whatever is determined by the config displayed on the desktop.

Then to start conky automatically on boot, 
add to startup applications(top right in the panel)
using as the command
```
conky -p 10
```[ATTACH]220999[/ATTACH]


The **-p 10** is an inbuilt conky option which will pause the starting of conky the number of secs specified.
This is needed when booting so conky doesn't run before the desktop is fully loaded.

Got it! Done. Thank you very very much!

---

