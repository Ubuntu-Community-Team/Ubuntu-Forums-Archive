---
title: "Fan Control for Dell XPS M1330?"
date: 2012-06-03
forum: New to Ubuntu
---

### Post by Sasakie on 2012-06-03
Hi,

I recently installed ubuntu on my dell xps m1330 and I was wondering if there is a good fan control program to use? I used to use i8kfangui on win7 but it doesn't seem to support linux.

Thanks

---

### Post by sam_delta on 2012-06-03
Ubuntu comes with 'fancontrol' which calculates and sets fan speeds depending on the current computer temperatures. Why would you change their speed manually? you might risk overheating your pc, just leave it automatically.

---

### Post by Sasakie on 2012-06-03
I want to set my fan speed to max all the time because my laptop will over heat on automatic settings.

---

### Post by sam_delta on 2012-06-03
you might give "i8kutils" a try, it claims to work for dell inspiron and latitude laptops.

if it doesnt work, you can try configuring fancontrol directly, here are 2 links on that:
[http://tuxtweaks.com/2008/08/how-to-control-fan-speeds-in-ubuntu/](http://tuxtweaks.com/2008/08/how-to-control-fan-speeds-in-ubuntu/)
[http://askubuntu.com/questions/22108/how-to-control-fan-speed](http://askubuntu.com/questions/22108/how-to-control-fan-speed)

I would also try cleaning your laptop fans, i stopped having overheating problems in my laptop after i cleaned my dusty fans, try a compressed air bottle to blow out all dust from the fans.

let us know if you still have problems.

---

### Post by Sasakie on 2012-06-03
I have tried both of your links and whenever I run sudo pwmconfig i get the message /usr/sbin/pwmconfig: there are no pwm-capable sensor modules installed.

I periodically clean my fans so I know that's not the issue.

---

### Post by Redblade20XX on 2012-06-03
My input : In today's age, usually fan control is dictated by the BIOs and software has a limited role due to potential volatility. Look for an advance BIOs menu if the basic menu doesn't have any for fan control. Also maybe its worth your time looking into updating your BIOs. Read the changelogs of your BIOs first to see if its worth it.

-Red

---

### Post by Sasakie on 2012-06-03
Hmm, it appears that i8kutil is installed. However, I'm not able to find/install gnome-swallow-applet as instructed here [http://ubuntuforums.org/showthread.php?t=842775](http://ubuntuforums.org/showthread.php?t=842775)

Also, when I run i8kmon without installing gnome, I get this popup window: [http://imgur.com/YgNQ9](http://imgur.com/YgNQ9)

Clicking on the lower button will turn my fans on, but only a few seconds. Also, having this running in the background appears to lock my terminal. (exiting with ctrl-c also closes the window)

Maybe this has something to do with the config file shown here: [http://ubuntuforums.org/showthread.php?t=842775](http://ubuntuforums.org/showthread.php?t=842775) but I have no idea what changing the values do.

Update: There was a typo in the original instructions. Instead of sudo gedit /etc/i8mon, it should have been sudo gedit /etc/i8kmon.conf. Problem is, running i8kmon still ends up locking my terminal and the fan seems to pulse between high and low every second or so. Terminal screenshot: [http://imgur.com/CCkhf](http://imgur.com/CCkhf)

---

### Post by Sasakie on 2012-06-05
Anyone have any ideas? =/

---

### Post by crowolf on 2012-06-30
Hi, 

I have the same problem with a fan on my XPS laptop. The only way to control it is i8k driver and i8kutils/i8kmon, so your are on the right way. It seems the problem is that XPS BIOS is too smart and tries to control the temperature by itself. You can turn on your fun by typing:

```
# i8kfan - 2
```

But in a few seconds or faster the hardware will set the previous speed. Unfortunately at the moment I don't have better solution then setting fan speed every second. Also I tuned nvidia card to change the frequency adaptively and it helps to keep a computer cool.

To tune i8kmon you need editing i8kmon.conf and change the following values:

```

# Run as daemon, override with --daemon option
set config(daemon)	1

# Automatic fan control, override with --auto option
set config(auto)	1

# Report status on stdout, override with --verbose option
set config(verbose)	0

# Status check timeout (seconds), override with --timeout option
set config(timeout)	1

# Temperature display unit (C/F), override with --unit option
set config(unit)	C

# {- -} means doesn't change fan speed, the following values mean that
# this setting should be used when temperature is up to 35 degrees in
# both cases: ac and battery mode.
# {- 2} means set maximum fan speed, the following values mean that
# this setting should be used when temperature is from 35 to 128 degrees.
set config(0)	{{- -}  -1  35  -1  35}
set config(1)	{{- 2}  35 128  35 128}

```

All other values you can leave as is.

Unfortunately with such settings fan will be turn on and off each few seconds.

---

### Post by crowolf on 2012-07-01
By the way there is great post about XPS M1330 and i8kmon:

[http://ubuntuforums.org/showthread.php?t=842775]("http://ubuntuforums.org/showthread.php?t=842775")

---

### Post by rv77 on 2012-07-16
Hi, 
I have started using Ubuntu recently and I am delighted to see postings which concern one of my minor problems today. I use Ubuntu 12.04 via an external hard disk on my dell XPS 1330. A problem that I have now is that, when I shut down, the fan keeps running. Yes, the fan seems to slow down, but it keeps running. The only way that I have found to solve this is to yank off the battery.

If, for example, I just boot up and then shut down without doing anything demanding, I am able to shut down normally. Probably, the fan does not get switched on in the first place.

Can I follow the routines suggested here to solve this problem? On receiving a positive answer, I will go through the material here to prepare a detailed step-by-step procedure for installing i8kmon and other utilities. The experts here can then suggest changes to my procedure. I hope that this is OK.
Right now, I would like to get some short tips to get me started.
Thanks,
rv77

---

