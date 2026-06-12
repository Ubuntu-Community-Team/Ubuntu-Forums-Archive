---
title: "Super dog slow boot-up like XP for past 2 days"
date: 2011-09-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ventrical on 2011-09-10
All of a sudden it seems that the Oneiric boot up is very , very slow .. stalling somewhat at the Ubuntu splash, almost like windows XP. And this came with the last update.Anyone else ?

---

### Post by fjgaude on 2011-09-10
Well, Unity is slow to boot to a usable desktop but also to get out to a new startup.

I would hope this is part of the debug code, converting to gtk3 not complete, or what have you during the Betas.

---

### Post by ventrical on 2011-09-10
> **fjgaude said:**
> Well, Unity is slow to boot to a usable desktop but also to get out to a new startup.

I would hope this is part of the debug code, converting to gtk3 not complete, or what have you during the Betas.

It's not Unity I'm talking about. Unity works just great (believe it or not). I'm talking about a cold boot to the LightDM screen where we choose the DE. It's dog slow. It was really zippy there for the past week, but now it acts like XP.

---

### Post by QCompson on 2011-09-10
Same issue here... after an update last night bootup is incredibly slow (hangs?) at the loading screen. For ~2-3 minutes.

I've tried turning off some startup apps to no effect. What is an easy way to start diagnosing this problem? 

Thanks.

---

### Post by fjgaude on 2011-09-10
> **ventrical said:**
> It's not Unity I'm talking about. Unity works just great (believe it or not). I'm talking about a cold boot to the LightDM screen where we choose the DE. It's dog slow. It was really zippy there for the past week, but now it acts like XP.

Okay, then it's Ubuntu 11.10 Beta.

---

### Post by ventrical on 2011-09-10
Are you propounding that Unity and Oneiric Ubuntu are one and the same?

I don't understand you logic here.

---

### Post by fjgaude on 2011-09-10
No, no... Unity is a shell, Ubuntu the OS. The general slowness of both booting and shut down is the issue, and likely caused by the whole project is not released yet.

---

### Post by ventrical on 2011-09-10
> **fjgaude said:**
> No, no... Unity is a shell, Ubuntu the OS. The general slowness of both booting and shut down is the issue, and likely caused by the whole project is not released yet.

Yes.. very well .. and thanks for that clarification.. however I find that Unity 3D loads rather quickly (and superfast in alpha 3).

  I understand also that this is beta and lots of testing still to be done.

:)

---

### Post by cariboo on 2011-09-10
According to bootchart, my crufty old install averages about 1:03 to boot to a usable desktop.

---

### Post by choel on 2011-09-11
Same problem after last update, looks like it's looking for network drivers in the start up. That's where my start up halts for a long long time and then continues. 
Haven't figured out how to disable the search for network drivers at start up, anyone? 

Then lighdm crashes after start up.

---

### Post by VinDSL on 2011-09-11
> **cariboo907 said:**
> According to bootchart, my crufty old install averages about 1:03 to boot to a usable desktop.
Bootchart!  Thank you!!

I was sitting here, bored out of my mind (now that my install is stable).

I'll go install bootchart, restart, and report back.

Heh!  I love that proggie...  :D

**EDIT**

Whoa!  1:03, same as yours.

I've never had a boot that slow.

Kind of odd that we charted the exact same time, no?

This machine boots in the 20-ish range, normally.

Hrm...

---

### Post by cariboo on 2011-09-11
In Natty, this system boots in 20 -26 seconds, I have another system with a slower processor (AMD 3800+) that seems to boot faster with a fresh beta 1 install, I haven't installed bootchart to see yet, but I'll do so next week, when I replace the power supply fan. I've had 2 Coolermaster P/S fans die in the last couple of weeks, even though they are both over 5 years old, I'm still disappointed at the fact.

---

### Post by VinDSL on 2011-09-11
> **cariboo907 said:**
> In Natty, this system boots in 20 -26 seconds[...]

I've had 2 Coolermaster P/S fans die in the last couple of weeks[...]
We must be twins, separated at birth.  LoL!

Natty booted in the mid-20s too - Maverick in the low 20s and occasionally the high-teens.

And, I lost an Ultra X-Connect PSU a couple of weeks ago.  Luckily I had a new Corsair PSU sitting in the closet.

Anyway, I guess UbuOO is indeed slow to boot-up.

---

### Post by 3rdalbum on 2011-09-11
Now you mention it, I've been getting slow startups. I assumed it was just because of debugging symbols and things that had been enabled for testing, but then I've never had slow startups before during development versions.

---

### Post by ventrical on 2011-09-11
I downloaded the bootchart program through terminal , but can't find the icon anywhere.

---

### Post by ventrical on 2011-09-11
> **VinDSL said:**
> We must be twins, separated at birth.  LoL!

Natty booted in the mid-20s too - Maverick in the low 20s and occasionally the high-teens.

And, I lost an Ultra X-Connect PSU a couple of weeks ago.  Luckily I had a new Corsair PSU sitting in the closet.

Anyway, I guess UbuOO is indeed slow to boot-up.


Same here !! Delta Power FRU PO0400. I rebuilt this one from scrap. It is one of those funny clamp P4 processors. The pin grid is attached by a pressure-clamp and not a PGA.

 Good thing about  a lot of those4 p4s is that they have a thermal shutoff. All need be done is just clean out the heatsync, new fan , voila'  :)

---

### Post by VinDSL on 2011-09-11
> **ventrical said:**
> I downloaded the bootchart program through terminal , but can't find the icon anywhere.
Bootchart runs automagically at boot.

Results are in stored in /var/log/bootchart  ;)

**EDIT**

BTW, make sure to install pybootchartgui.  It renders the charts for bootchart.

I always install bootchart using Synaptic - and Synaptic includes pybootchartgui in the install.

I'm not sure if pybootchartgui gets included when installing bootchart from a terminal...

---

### Post by ventrical on 2011-09-11
Ok . .thanks. My bootchart .png reads 1:07 but that is false because it only took 10 seconds to boot  from a hard boot. This happening just after I installed bootchart.

So yet another strange anomoly. :)

More anomolies :)

---

### Post by VinDSL on 2011-09-11
> **ventrical said:**
> Ok . .thanks. My bootchart .png reads 1:07 but that is false because it only took 10 seconds to boot  from a hard boot. This happening just after I installed bootchart.

So yet another strange anomoly. :)

More anomolies :)
That's encouraging!

I couldn't imagine it taking 1:03 to boot this machine, but...

I'll research the topic.

---

### Post by ventrical on 2011-09-11
I hand measured the boot time - that being the time it takes from the GruB Menu to the LightDM.

  I now count 25 seconds and Unity only takes about 6 seconds to load - but I do not include the POST and this machine has it's own Firmware bootmanager .. so I have to exclude those times from boot.

So I think my next question would be :" what is the interval of thime that the 'bootchart_program' is measuring: from:To:?

---

### Post by ventrical on 2011-09-11
> **VinDSL said:**
> Bootchart runs automagically at boot.

Results are in stored in /var/log/bootchart  ;)

**EDIT**

BTW, make sure to install pybootchartgui.  It renders the charts for bootchart.

I always install bootchart using Synaptic - and Synaptic includes pybootchartgui in the install.

I'm not sure if pybootchartgui gets included when installing bootchart from a terminal...

Yes .. the GUI was included but I have to read the .png file manually with a photo-editor. Kind of dicey :)

Something I did or did not do again :)

---

### Post by ventrical on 2011-09-11
it's installed. I can't find an icon though.

Is this a terminal app?

---

### Post by VinDSL on 2011-09-11
> **ventrical said:**
> So I think my next question would be :" what is the interval of time that the 'bootchart_program' is measuring: from:To:?
The kernel executes the bootchart script after /proc is mounted.  It temporarily stores the data in memory, then writes it to a file when the boot process is complete.

I found plenty of bug reports, but they mostly had to do with bootchart not running, or it not being able to write the results to a file.  

I didn't read anything about it being inaccurate, so...

Maybe it does take 1:03 for this machine to boot.

Wishful thinking on my part - hoping bootchart is producing bogus stats.  LoL!  :D

---

### Post by VinDSL on 2011-09-11
> **ventrical said:**
> it's installed. I can't find an icon though.

Is this a terminal app?
It's activated by the kernel command line in GRUB, AFAIK.  

Anyway, no it isn't a terminal app...  ;)

**EDIT**

Nope!  Not in GRUB.

I don't know where it's hiding.

**EDIT2**

00:42.54 on the last boot.

It's getting better...  :)

---

### Post by QCompson on 2011-09-11
I win!

[SIZE="2"][B]3:32.06
[/B][/SIZE]

It's a long time. Was fine before I updated friday.

---

### Post by ronacc on 2011-09-11
with gnome shell on my 64bit install I am getting 1.12.21  ( 72 sec ) slow but atleast not 3 + min . What seems really clogging up the works for me seems to be udisks-helper is very slow to start , about 20 secs after everything else is finished , but then it finishes in 1 sec .

---

### Post by ventrical on 2011-09-11
> **QCompson said:**
> I win!

[SIZE=2][B]3:32.06
[/B][/SIZE]

It's a long time. Was fine before I updated friday.


 I'm up in the 3 minute range now too.

---

### Post by VinDSL on 2011-09-11
Ran across an interesting video in the FOSDEM 2010 dev rooms...

Michael Meeks discussing Bootchart (24 min):  [http://ftp.heanet.ie/mirrors/fosdem-video/2010/devrooms/distributions/bootchart2.ogv](http://ftp.heanet.ie/mirrors/fosdem-video/2010/devrooms/distributions/bootchart2.ogv)

It'll give you some insights, as to what you're looking at...

**EDIT**

w00t!

And, here's the slide presentation (PDF):  [http://people.gnome.org/~michael/data/2010-02-09-bootchart2.pdf](http://people.gnome.org/~michael/data/2010-02-09-bootchart2.pdf)

---

### Post by ronacc on 2011-09-11
pybootchartgui seems to have a problem reading the bootchart . It looks for a file named /var/log/bootchart/bootchart.tgz but bootchart actually writes a file named /var/log/bootchart/<name of my box>.tgz  but even if I rename the file to what its looking for it don't find it . the file is ok because I can extract it and view it with any image viewer .

---

### Post by VinDSL on 2011-09-11
> **ronacc said:**
> pybootchartgui seems to have a problem reading the bootchart . It looks for a file named /var/log/bootchart/bootchart.tgz but bootchart actually writes a file named /var/log/bootchart/<name of my box>.tgz  but even if I rename the file to what its looking for it don't find it . the file is ok because I can extract it and view it with any image viewer .
Yep!  I ran across many posts, on Google Search, concerning this bug.

It's a common complaint, and I don't know if there is a fix.  :(

---

### Post by ventrical on 2011-09-11
Not a bad lecture. I guess the theme there is that there are 'serious bug' that still have to be worked on and that Xfce is the way of the future :)

---

### Post by ventrical on 2011-09-11
Here is a snap from my Acer Aspire Oneiric Install.!!

---

### Post by ventrical on 2011-09-11
Here is that same machine with an already installed Alpha3 Oneiric.

---

### Post by ronacc on 2011-09-11
> **ventrical said:**
> Here is a snap from my Acer Aspire Oneiric Install.!!

can you identify what seems to be causing the slowdown ?

---

### Post by ventrical on 2011-09-11
> **ronacc said:**
> can you identify what seems to be causing the slowdown ?

  There are quite a few programs running or loading up in paralell to each other and for some reason there seems to be an I/O wait.

  In older PC science we used to call these <traffic cops>. I cannot identify the exact program but <dbus> and <init> are high on the list of throughput programs.

  I am declaring the assumption that, because of the beta testing and problems with wireless and graphic responses , an added wait state has been added throughout the boot sequence so that perhaps older hardware cards can catch up to modprobe queries and the like. In many cases a system may have a really fast processor but no enough other resources , ie:(graphical accelerators) and so it may be that some of the older cards, which are in effect graphically capable, need more time to respond to modprobe and so the developers are casting a broader net (so-to-speak) so as everybody has a chance to be included in the beta testing.

  A lot of users are using dual procesors wirth hyoer threading capabilites and so there is this <readahead>program with tries to have to data ready at the <bottom-up> of the bootstrap loader sequence - which could include post boot loadings also. I am not saying that bootchart is giving a false reading  but during a beta testing, then all programs have to be monitored , even the monitoring programs.


 Also plymouth runs along the sequence from beggining to end along with <rsyslog>, <upstart-socket>, dbus daemon>, <polkitd>, <wpa_supplicant>, <modem manager> etc...

Therefore if there is a fast processor, medium speed graphical accelerator and slower IDE HDD with a slow bus then the properties and state of the hardware become a different dynamic while attempting to service the software and vis a versa. And hence this may be a global temporary traffic cop .. 

  This is just my preliminary veiw.

---

### Post by ronacc on 2011-09-11
I have had boot times around 30 sec in lucid and maveric on this same box so I doubt it is a hardware problem also with many people reporting the same thing I don't believe they all have slow boxes . People running unity seem to have it much worse than those running other de's so probably some of it lies there but even though I don't even have unity installed I am seeing boot times with gnome-shell more than twice what I am used to , I'll check my lubuntu installs when I get my box back . tight now its doing a massive update of my sabayon install through a slow mirror antipodal to me 1 1/2 hrs and only 43% done so it will probably be tomorrow before I get around to it .

---

### Post by choel on 2011-09-11
Think I found what causes the slow boot after last update. 
Found this bug report. 
[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/845914](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/845914)

As described in the bug report have a look in "/etc/init/failsafe.conf"
If you have "sleep 120" as shown below change it to "sleep 1"

```

# failsafe

description "Failsafe Boot Delay"
author "Clint Byrum <clint@ubuntu.com>"

start on filesystem and net-device-up IFACE=lo
stop on runlevel

pre-start exec sleep 120

```

```

# failsafe

description "Failsafe Boot Delay"
author "Clint Byrum <clint@ubuntu.com>"

start on filesystem and net-device-up IFACE=lo
stop on runlevel

pre-start exec sleep 1

```

That fixed my slow boot. Still just a workaround, don't know what caused the problem.


[EDIT]
Just found another fix for the problem. As described in this bug report.
[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/839595](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/839595)

Changing in "/etc/network/interfaces" also works. 

As described in the bug report by Scott Moser (smoser)>  
I suspect that you have a interface listed there as 'auto' that is not
plugged in. If that is the case, the correct solution for you is to
remove that line or comment it out. To be clear, I suspect you have
something like:
  auto eth0
  iface eth0 inet dhcp

but your eth0 is not plugged in.

---

### Post by QCompson on 2011-09-11
> **choel said:**
> 
Changing in "/etc/network/interfaces" also works. 

Excellent! That worked for me.

After commenting out auto eth0 in interfaces, my boot time went to 00:47.00. :D

Thanks.

---

### Post by VinDSL on 2011-09-11
> **QCompson said:**
> Excellent! That worked for me.[...]
Worked for me, too.

**00:41.36**

I'm still getting a large dip in CPU activity around the 25s mark, but it's better than it was!

If that wasn't there, I'd probably be booting in the mid-30s.

---

### Post by cariboo on 2011-09-12
The devs should start removing the debugging bits fairly soon, so boot times should be getting better the closer we get to final release

---

### Post by ventrical on 2011-09-12
Nice fix indeed.

---

### Post by ronacc on 2011-09-12
just for info the fix does not have any effect on my non unity installs , lubuntu 32bit  66 sec , lubuntu 64bit 62 sec  , ubuntu gnome-shell 64bit 73 sec  before and after . interestingly the fix seems to bring people with unity into the same range as non unity installs .

---

### Post by ventrical on 2011-09-12
Thank you for your observations. Beta testing is a great learning experience. it seems , here , is where the brightest minds gather.

I hope I am staying on topic , as I wrote a message in one of the Fedora forums  about GNOME3.0 and how it was the 'master of suspence' taking only 4 seconds to suspend and 4 seconds to bring the end_user right back to where they left off .

Now that's a fast boot for what it's worth.

---

### Post by VinDSL on 2011-09-15
Heh!  I'm actually in the middle of an update, right now, but I stopped by to document this patch:

```

--- /etc/init/failsafe.conf	2011-09-11 19:47:29.440708465 -0700
+++ /etc/init/failsafe.conf.dpkg-new	2011-09-14 19:02:17.000000000 -0700
@@ -6,4 +6,36 @@
 start on filesystem and net-device-up IFACE=lo
 stop on runlevel
 
-pre-start exec sleep 1
+console output
+
+pre-start script
+	# Determine if plymouth is available
+	if [ -x /bin/plymouth ] && /bin/plymouth --ping ; then
+		PLYMOUTH=/bin/plymouth
+	else
+		PLYMOUTH=":"
+	fi
+
+    # The point here is to wait for 2 minutes before forcibly booting 
+    # the system. Anything that is in an "or" condition with 'started 
+    # failsafe' in rc-sysinit deserves consideration for mentioning in
+    # these messages. currently only static-network-up counts for that.
+
+	sleep 20
+
+    # Plymouth errors should not stop the script because we *must* reach
+    # the end of this script to avoid letting the system spin forever
+    # waiting on it to start.
+	$PLYMOUTH message --text="Waiting for network configuration..." || :
+	sleep 40
+
+	$PLYMOUTH message --text="Waiting up to 60 more seconds for network configuration..." || :
+	sleep 59
+	$PLYMOUTH message --text="Booting system without full network configuration..." || :
+
+    # give user 1 second to see this message since plymouth will go
+    # away as soon as failsafe starts.
+	sleep 1
+end script
+
+post-start exec	logger -t 'failsafe' -p daemon.warning "Failsafe of 120 seconds reached."

```

Okay, carry on.  See ya on the next boot...  :D

---

### Post by VinDSL on 2011-09-15
Smooth, baby!

Like driving' in a Cadillac.

**00:41.15**

And, there's only a 2-3 sec dip in CPU activity now.  The rest of it pegs the chart.

They're getting there...  ;)

---

### Post by ventrical on 2011-09-15
Good eye , Vin ! :)

---

