---
title: "HOWTO: Software mixing with JACK and oss2jack"
date: 2006-07-03
forum: Outdated Tutorials &amp; Tips
---

### Post by joft on 2006-07-03
**[SIZE="4"]HOWTO: Sound mixing in software with JACK and oss2jack[/SIZE]** :guitar: :-({|= :-\" 

I originally wrote this HOWTO for Breezy some months ago. Then I wrote an updated and cleaned up version for Dapper and I also updated my packages used by this HOWTO. Lately I update all stuff to be used on **Feisty [COLOR="Red"](NEW)[/COLOR]**, too. *The **old** one for Breezy is still around: [http://www.ubuntuforums.org/showpost.php?p=695990&postcount=6](http://www.ubuntuforums.org/showpost.php?p=695990&postcount=6)*

**Problem:** ALSA supports **software mixing** by its dmix plugin (for sound cards which do not support that in hardware). dmix is working with most ALSA applications. But, there are some ALSA applications which do not work with dmix, they just block the whole ALSA device (as if dmix wasn't there).
Furthermore OSS apps which are forced to use ALSA OSS emulation can't be dmix'd, they also block the whole sound device.
[B]So, this HOWTO is for those of you who use OSS only applications and want them to be able to play sound at the same time, without using wrappers for sound servers or general ones (e.g. aoss).
Examples of OSS only applications are: Skype (< 1.3.x), TeamSpeak2, Audacity, ET, ...[/B]

[COLOR="Red"]**PROBLEM: this HOWTO & TeamSpeak2**
Some months ago it was discovered and confirmed by several people that **TeamSpeak2 doesn't work with the software used in this HOWTO** any more (crash, "Runtime error ...", "Segmentation fault"), although it used to work with the old HOWTO on Breezy. I still don't have any glue why. It's very very strange. As with Dapper, this **problem also exists on Feisty** - sorry.[/COLOR] :(

[COLOR="Red"]**PROBLEM 2: this HOWTO & Feisty & Audacity**
Till now, I couldn't convince Audacity to work through it's OSS output feature - neither playing nor recording works for me. **This hasn't been confirmed by others yet, so if you try it, tell me about your findings!**[/COLOR] :( 

**Solution:** Sound servers: artsd (KDE), esd, polyp (GNOME), ... others. Sound applications have to have special output drivers to use them and most have. 
But some applications don't have such drivers. Then you would have to use wrappers (artsdsp, esdsp) which "try" to catch the calls of the applications (in userspace) and reroute them to their sound servers.
These wrappers sometimes work great (artsdsp/KDE) or bad (esddsp/GNOME) (at least on my computer).

**Solution described here:** Use of JACK as sound server (although JACK is more than a sound server, I know ...) and oss2jack, a special tool which emulates an OSS device and reroutes the data to JACK.
Then all OSS only application will be able to open the sound device at the same time and play at the same time.
For other applications (all _true_ ALSA applications) there **two alternatives** now, which depend on how jackd is started (commandline arguments):

**(jack-only-alternative)** This is the original one, used in this HOWTO till now. jackd blocks the whole ALSA sound device and all other sound applications will have to use application specific jackd output drivers/plugins (like xmms, mplayer, ... have) and play through jackd.

**[COLOR="Red"](NEW)[/COLOR]** **(jack-as-dmix/dsnoop-client-alternative)** This is the second, the new one. Here jackd is started with the commandline arguments "-P dmix -C dsnoop" and therefore jackd will act as a dmix/dsnoop client, which means that ALSA applications which also use dmix/dsnoop can still use the sound device and play at the same time. This means, that _you don't have to reconfigure any of your ALSA applications_ (esd, totem, xmms, mplayer ...) - they just play their sound as usual (through dmix/dsnoop).
_The drawback is_, that you cannot use the commandline argument "-p 256" anymore and therefore _you might get latency problems_ (default is a value of 1024 (frames per period), which may be too much)!

The steps (1. to 10.) you see below, are marked with the **bold** words from above if they only apply to one specific alternative. You will see, that the second alternative effectivly uses steps 1 to 3, 5, 6.B and 7. only!



**Important assumptions made in this HOWTO: You are using Ubuntu 6.06 (Dapper) or Ubuntu 7.04 (Feisty) with GNOME and ALSA. Your sound card (hardware) basically works.**

**Note 1**: I'm neither an expert in sound stuff nor an ubuntu developer, so tell me, if I'm saying something wrong.

**Note 2**: If you really need *perfect* sound mixing, IMO you will still have to buy a "real" sound card with a sound chip which is able to do it in hardware.
Back then, when I started to write this HOWTO, I tested this solution with xmms, mplayer playing files and talking to somebody in skype at the same time. I also tested it with TS2 and ET at the same time.


**Installing needed packages:**

**1.** [COLOR="Red"]Add[/COLOR] the following (my) [COLOR="Red"]repository[/COLOR] to your /etc/apt/sources.list file:
[INDENT]
**Dapper**[/INDENT]
```
deb http://neogate.homelinux.org/debian/ dapper sound
```
[INDENT]
**Feisty**[/INDENT]
```
deb http://neogate.homelinux.org/debian/ feisty sound
```

Don't forget to update your package system. To do this you can do:

```
sudo apt-get update
```

**2.A** Then [COLOR="Red"]install jackd[/COLOR] from dapper and [COLOR="Red"]oss2jack[/COLOR]
from the repository given above by typing:

```
sudo apt-get install jackd oss2jack
```

**NOTE:** During the installation of the package "oss2jack" you'll get asked 2 questions.
The first one says *"Do you want to disable the ALSA OSS modules?"*. For this HOWTO to work, you have to choose "Yes".
The second question says: *"Do you want to unload the ALSA OSS modules now?"*. You may choose "Yes" here, too. You could do that manually, too (see step 7), but it won't hurt to let the installation try to unload them.

*_Now do step 2.B **OR** step 2.C, **NOT BOTH**, only one of them depending on the kernel you have installed:_*
**2.B** In my repository are pre-build kernel modules for **dapper kernel 2.6.15-23, 2.6.15-25, 2.6.15-26, 2.6.15-28, 2.6.15-29 and feisty kernel 2.6.20-15, 2.6.20-16**. If you have installed one of these kernels, do:

```
sudo apt-get install fusd-kor-module-`uname -r` fusd-kor
```

**2.C** **If** you have an **other dapper/feisty kernel** or a **selfmade one**, you will have to [COLOR="Red"]install fusd-kor-source instead[/COLOR] of the pre-build module and build your own fusd-kor-module package.
So, first you have to prepare your system for module compilation. To do that, install module-assistant:

```
sudo apt-get install module-assistant
sudo m-a prepare
sudo apt-get install gcc-`grep LINUX_COMPILER /usr/src/linux/include/linux/compile.h | sed 's/.* \([0-9]\+\.[0-9]\+\).*/\1/'`

```

The second command will make module-assitant (m-a) install the needed linux-headers packages. [SIZE=1](If you have a selfmade linux-kernel package, you (probably) will have to manually install your own linux-headers package.)[/SIZE] The last command here, makes sure that you have got installed the right version of gcc (GNU C Compiler).

Then, install fusd-kor-source and build your own fusd-kor-module packages:

```
sudo apt-get install fusd-kor-source
sudo m-a a-i fusd-kor
sudo apt-get install fusd-kor
```

In the second command m-a will do all the stuff needed to configure, build and install your own fusd-kor-module package automatically. The last command installs the package "fusd-kor".

**NOTE on step 2.B and 2.C:** During the installation of the package "fusd-kor" you'll get asked 2 questions.
The first one says *"Do you want the fusd-kor kernel module to be loaded during the boot process?"*. For this HOWTO to work, you have to choose "Yes".
The second question says: *"If needed, you can specify commandline parameters ..."*. Do not enter anything there, leave it blank.

*_Now do step 3.A **OR** step 3.B, **NOT BOTH**, only one of them depending on the kernel you have installed:_*
**3.A** I also [COLOR="Red"]installed the realtime kernel module[/COLOR], so that jackd and oss2jack are able to run with a higher priority. In my repository are pre-build kernel modules for **dapper kernel 2.6.15-23, 2.6.15-25, 2.6.15-26, 2.6.15-28, 2.6.15-29 and feisty kernel 2.6.20-15, 2.6.20-16**. If you have installed one of these kernels, do first:

```
sudo apt-get install realtime-lsm-module-`uname -r`
```
then
```
sudo apt-get install realtime-lsm
```

**3.B** **If** you have an **other dapper/feisty kernel** or a **selfmade one**, you will have to [COLOR="Red"]install realtime-lsm-source instead[/COLOR] of the pre-build module and build your own realtime-lsm-module package.
So, first you have to prepare your system for module compilation. To do that, install module-assistant:

```
sudo apt-get install module-assistant
sudo m-a prepare
sudo apt-get install gcc-`grep LINUX_COMPILER /usr/src/linux/include/linux/compile.h | sed 's/.* \([0-9]\+\.[0-9]\+\).*/\1/'`

```

The second command will make module-assitant (m-a) install the needed linux-headers packages. [SIZE=1](If you have a selfmade linux-kernel package, you (probably) will have to manually install your own linux-headers package.)[/SIZE] The last command here, makes sure that you have got installed the right version of gcc (GNU C Compiler).

Then, install realtime-lsm-source and build your own realtime-lsm-module packages:

```
sudo apt-get install realtime-lsm-source realtime-lsm
sudo m-a a-i realtime-lsm
```

In the last command m-a will do all the stuff needed to configure, build and install your own realtime-lsm-module package automatically.

[I]**4.** **(jackd-only-alternative)** Usually the package "libesd-alsa0" is installed to allow esd to output to ALSA. But since we are going to use JACK (and jackd blocks the ALSA sound device by default), you need to [COLOR="Red"]replace "libesd-alsa0" with "libesd0"[/COLOR], which enables esd to output to OSS devices.

   ```
sudo apt-get install libesd0
```

   This way, esd (which is responsible for all "GNOME desktop sounds") will output its stuff to our emulated OSS device by oss2jack.[/I]

**5.** To be able to run jackd and oss2jack with a higher priority, you have to [COLOR="Red"]make sure that you are a member of the "audio" group[/COLOR]. This is also needed due to the owner/group settings of the device files of the kfusd kernel module. If in doubt, do:

   ```
sudo adduser <your_username> audio
```


**Start jackd and oss2jack after login (automatically)**

[I]**6.A** **(jackd-only-alternative)** GNOME automatically starts its esd (GNOME's sound server) after login, so that you can hear the login sound etc. In the first section you configured esd to output to OSS devices (step 4.).
So we need to [COLOR="Red"]start our jackd/oss2jack combination before esd gets started[/COLOR].   To do that we use the ~/.gnomerc file, which is executed before any GNOME stuff gets started after login. You will find the script I use in /usr/share/doc/oss2jack/examples/.gnomerc , so copy it over to your home directory:

   ```
cp /usr/share/doc/oss2jack/examples/.gnomerc ~/.gnomerc
```

   I admit, that my script is some kind of a (dirty) hack ... just in case you wonder about the loop at the end for example.
[SIZE=1]Note that this script assumes, that you followed step 3. That means: in theory you could do without step 3, but that's not recommended. You would have to edit the script and remove the "nice" adjustments and run jackd/oss2jack without higher (realtime) priority.[/SIZE][/I]

**6.B** **(jackd-as-dmix/dsnoop-client-alternative)** We need to start our jackd/oss2jack combination after login. To do that we use the ~/.gnomerc file, which is executed before any GNOME stuff gets started. You will find the script I use in /usr/share/doc/oss2jack/examples/.gnomerc-dmixsnoop , so copy it over to your home directory:
[INDENT][B]
Dapper/Feisty[/B][/INDENT]
   ```
cp /usr/share/doc/oss2jack/examples/.gnomerc-dmixsnoop ~/.gnomerc
```

   I admit, that my script is some kind of a (dirty) hack ... just in case you wonder about the loop at the end for example.
[SIZE=1]Note that this script assumes, that you followed step 3. That means: in theory you could do without step 3, but that's not recommended. You would have to edit the script and remove the "nice" adjustments and run jackd/oss2jack without higher (realtime) priority.[/SIZE]

If you are using **Feisty** you may also copy the example file /usr/share/doc/oss2jack/examples/.asoundrc to your home directory:

[INDENT]**Feisty**[/INDENT]
   ```
cp /usr/share/doc/oss2jack/examples/.asoundrc ~/.asoundrc
```

It contains a configuration item which creates a mixer element named "dmix". If this is not there, jackd complains about not being able to open a mixer device.


**It's nearly done :D**

**7. Only needed if you don't want to reboot now.** You will have to load the realtime module manually. Next time you do a reboot it will get loaded automatically (step 3). Furthermore you have to unload the ALSA OSS emulation modules. If you choose to unload them during the installtion of the package oss2jack (step 2.A), they shouldn't be there anymore, but it doesn't hurt to "rmmod" them again (so there might appear an error message saying "ERROR: Module XXXX does not exist ..." - just ignore it). On future reboots they will be prevented from being loaded automatically, too (step 2.A).

```

sudo /etc/init.d/realtime start

sudo /etc/init.d/fusd-kor start
sudo rmmod snd-pcm-oss
sudo rmmod snd-mixer-oss
```

So, the first command should suffice here, the other three are just there to really make sure that nothing bad happened during the steps above while loading and unloading.

**NOTE:** If your are using **Feisty**, this step 7 shouldn't be necessary at all. But again: it can't hurt.

**8.** If you didn't reboot in step 7, now at least you have to logout and login again, so that your ~/.gnomerc script gets executed.


**Configuring software**

[I]**9.** **(jackd-only-alternative)** Usually [COLOR="Red"]gstreamer[/COLOR] is installed and configured to autodetect and chose one output "method". But - same reason as with esd (step 4.) - we need it to [COLOR="Red"]output to our emulated OSS device[/COLOR] by oss2jack. Go to:

   System -> Preferences -> Multimedia Systems Selector

and chose OSS (output and input). If this menuitem does not exist, start the Multimedia Systems Selector by this command:

```
gstreamer-properties
```

and chose OSS (output and input).

In **Feisty** there is another dialog, which _might need_ some changes:

System -> Preferences -> Sound

In tab "Devices" you _might have to_ chose "OSS" explicitly - but ATM I'm _not sure_ about "for what" these configuration items are really good for. The default, called "Autodetect", just works in my case.[/I]


[I]**10.A** **(jackd-only-alternative)** **Configuring (other) sound applications**

In general, it is a good idea to leave the configuration of your applications alone - at least at the beginning. Try them, if they still work and if not, change teir configuration.

Here is a list of applications and with which output driver I used them:

- esd ... oss	(configured above, step 4.)
- gstreamer ... oss	(configured above, step 9.)

- xmms ... jack
- mplayer ... jack in Dapper, oss in Feisty
- vlc ... oss
- gxine/xine ... oss
- licq ... use "esdplay" in Licq Menu -> Options -> OnEvent: Command
- wine ... oss (wine might need a patch, not sure at the moment, see the resources section below)

Note that the tool "esdplay" mentioned above is contained in the package "esound-clients". If you need "esdplay" (e.g. if you use licq) you have to install it:

```
sudo apt-get install esound-clients
```[/I]

**10.B** **(jackd-as-dmix/dsnoop-client-alternative)** **Configuring (other) sound applications**

As already mentioned, using jackd as a simple dmix/dsnoop client has the **advantage of not having to reconfigure any ALSA application**. jackd is just one more client to the ALSA library's software mixing feature (dmix/dsnoop) - like all other ALSA applications are (esd, xmms, mplayer, totem, vlc, ...).


**NOTE on step 10.A and 10.B :** Applications like Audacity, Skype, ET, ... can use OSS only, so they will use our emulated OSS device by oss2jack.


[INDENT]**(Other) resources around this HOWTO**

- Little (external) "homepage" of this HOWTO [http://neogate.homelinux.org/howto-oss2jack/]("http://neogate.homelinux.org/howto-oss2jack")

- oss2jack: [http://fort.xdas.com/~kor/oss2jack/]("http://fort.xdas.com/~kor/oss2jack/")

- JACK: [http://jackit.sourceforge.net/]("http://jackit.sourceforge.net/")
[/INDENT]

[COLOR="Red"][B]=====================================================================
END OF HOWTO
=====================================================================[/B][/COLOR]

[INDENT][INDENT]If you don't like the result of this HOWTO or if you have to reverse the whole thing because of some other reason, here's a **list**, what you have to do to **switch back to ALSA/dmix**. I used the same step numbers as in my HOWTO:

**6.** Remove ~/.gnomerc, ~/.asoundrc and terminate the tools:

```
rm ~/.gnomerc ~/.asoundrc
killall esd
killall oss2jack
killall jackd
```

[I]**9.** **(jackd-only-alternative)** Go to

System -> Preferences -> Multimedia Systems Selector

and select Autodetect for input and ALSA for output. If this menuitem does not exist, start the Multimedia Systems Selector by this command:

```
gstreamer-properties
```

and select Autodetect for input and ALSA for output.

**4.** **(jackd-only-alternative)** Replace the package "libesd0" with "libesd-alsa0", by doing:

```
sudo apt-get install libesd-alsa0
```
[/I]
**2.A(B|C) + 3.** Now uninstall the rest of the software packages installed by the HOWTO:

```
sudo apt-get remove --purge oss2jack fusd-kor* jackd realtime-lsm* 
```

**2.A** If you don't want to reboot now, you have to load the ALSA OSS emulation modules again:

```
sudo modprobe snd-mixer-oss
sudo modprobe snd-pcm-oss
```

**8.** Now at least you have to logout and login again, so that esd is getting started again by GNOME.
[/INDENT][/INDENT]

---

### Post by raid_ox on 2006-07-05
thanks, it works ^^

---

### Post by mmaura on 2006-07-09
Not working for me.

Before:

cedega wow : sound ok but not width Teamspeak (this is my probleme)

After:

cedega wow :  no sound
Teamspeak  : crash on starting


i ve do some test to see if process is load, everythings like to be good.


The procedure to go back work fine.

thank for howto.

---

### Post by joft on 2006-07-09
Hi mmaura,

> **mmaura said:**
> Not working for me.

Before:

cedega wow : sound ok but not width Teamspeak (this is my probleme)

After:

cedega wow :  no sound
Teamspeak  : crash on starting


i ve do some test to see if process is load, everythings like to be good.


hmmm, the first step for finding out what's going wrong probably would be to look for the **output** of jackd and oss2jack. For this you would have to remove your .gnomerc and start jackd and oss2jack by hand (after login, in terminal).

In one terminal:
```
jackd -R -d alsa -p 256
```

and in another one:
```
oss2jack
```

Ah, another idea: does esd (Desktop sounds, ...) work after such a TS crash? If not, this may indicate a crash of oss2jack/jackd. So you most probably will see something in the output of them.

> **mmaura said:**
> 
The procedure to go back work fine.


Thanks for your feedback.

---

### Post by linuxfan128 on 2006-07-09
Will this fix flash randomly having no sound for me?

---

### Post by schang on 2006-07-10
it's not really working for me ... 

using your script, i got system sounds, but oss2jack did not work. after removing your script and starting jackd and oss2jack in terminals, i get the following: 

```
delay of 6561.000 usecs exceeds estimated spare time of 5224.000; restart ...
delay of 6565.000 usecs exceeds estimated spare time of 5224.000; restart ...
delay of 6573.000 usecs exceeds estimated spare time of 5224.000; restart ...
delay of 6556.000 usecs exceeds estimated spare time of 5224.000; restart ...
delay of 6521.000 usecs exceeds estimated spare time of 5224.000; restart ...
delay of 6567.000 usecs exceeds estimated spare time of 5224.000; restart ...
delay of 6565.000 usecs exceeds estimated spare time of 5224.000; restart ...
delay of 6564.000 usecs exceeds estimated spare time of 5224.000; restart ...
delay of 6517.000 usecs exceeds estimated spare time of 5224.000; restart ...
delay of 6569.000 usecs exceeds estimated spare time of 5224.000; restart ...
delay of 6565.000 usecs exceeds estimated spare time of 5224.000; restart ...
delay of 6568.000 usecs exceeds estimated spare time of 5224.000; restart ...
delay of 6571.000 usecs exceeds estimated spare time of 5224.000; restart ...
delay of 6554.000 usecs exceeds estimated spare time of 5224.000; restart ...
delay of 6567.000 usecs exceeds estimated spare time of 5224.000; restart ...
delay of 6568.000 usecs exceeds estimated spare time of 5224.000; restart ...
```

in the jackd terminal, and oss2jack returns a nice 

```
Hello from the restart thread
```

have you got any idea what went wrong? :confused:

---

### Post by joft on 2006-07-10
Hi,

> **linuxfan128 said:**
> Will this fix flash randomly having no sound for me?

Oh, I am not an flash expert .... but I heard about the "flash problem". If the third-party-binary-only flash plugin uses OSS and is NOT able to use ALSA, then you will certainly have sound problems with flash - simply because if you have another sound application running/has opened a sound device, that application will block flash.

Keep in mind: This and and the whole **HOWTO is only true** for sound cards/chips which **don't support hardware mixing**. So if you have a sound card which does support hw mixing and flash does not work, this HOWTO won't help.


> **schang said:**
> it's not really working for me ... 

using your script, i got system sounds, but oss2jack did not work.


That doesn't make sense as long as you mean the "GNOME Desktop sounds" by "system sounds". In step 4 of the HOWTO we instruct esd to use OSS instead of ALSA by replacing esd's library. And OSS is provided by oss2jack.
So, "system sounds work" means esd works - which means that oss2jack and thus jackd is working, too.

> **schang said:**
> 
after removing your script and starting jackd and oss2jack in terminals, i get the following: 

<....>

in the jackd terminal, and oss2jack returns a nice 

```
Hello from the restart thread
```

have you got any idea what went wrong? :confused:

The message you received from oss2jack is ok. And in general messages by jackd are ok, too. At least I cannot see anything bad in your messages.

Can you check sound with XMMS (with JACK output plugin) for example? So we can see if jackd really works. Then you could check if oss2jack creates the device  (/dev/dsp and /dev/mixer). They have to exist - otherwise there really is something wrong with oss2jack (while oss2jack is running - check with "ps fx" - once started (e.g. in a termnial) oss2jack shouldn't stop!).

---

### Post by schang on 2006-07-11
well, oss2jack is now working properly. clearly a user problem on this one. ;)

but now i've got exactly the same problem as mmaura. TS crashes on start, with runtime errors and a segfault. it seems like it's a problem with the latest TS release... could you please check your TS version?

---

### Post by joft on 2006-07-11
Hi,

> **schang said:**
> but now i've got exactly the same problem as mmaura. TS crashes on start, with runtime errors and a segfault. it seems like it's a problem with the latest TS release... could you please check your TS version?

```

-rwxr-xr-x root/root   1641148 2003-08-29 16:20:22 usr/local/TeamSpeak2RC2/TeamSpeak.bin

```

Bad news ... TS does not work any more here, too. At the moment I'm a bit clueless, because TS did work under breezy and as I said in my HOWTO, I just update the HOWTO and the packages (for dapper). Therefore I used new upstream versions of oss2jack and fusd-kor in contrast to the versions I used in the HOWTO for breezy.

Perhaps these new versions have a bug - but, since the errors are segfaults, I think there is a bug in TS, too.

I am sorry - I will check the whole situation by using my old packages - just give me some time.

---

### Post by mathieujohnson on 2006-07-11
THANK YOU SO MUCH!!!!

seriously, I've been looking for this exact thing for months!

I have always wanted to run everything audio related through jack.
I run a studio based on linux so jack is a spectacular tool and now not having to close my music to open ardour or hydrogent or wathever app I feel like using, its just great!

I knew there was a way to go!

thanx again!

Mathieu

---

### Post by joft on 2006-07-17
Hi schang, hi mmaura

during the last few days, I tried to find out why TS is crashing.

- I took the old versions of fusd-kor and oss2jack used in my old HOWTO for Breezy (TS did work on Breezy) and recompiled them for Dapper - no luck.
- Then I tried several new-old combination (new fusd-kor 1.10.11, old oss2jack 0.24) - no luck.
- Then, this morning, I recompiled packages jackd and libjack0.80.0-0 from Breezy for Dapper, to make sure that jackd is ok - still no luck.

TS keeps crashing evertime, whatever I do and the basic error message I get is:

```

Runtime error 231 at 0806A7E9
/usr/local/TeamSpeak2RC2/TeamSpeak: line 8: 8469 Segmentation fault /usr/local/TeamSpeak2RC2/TeamSpeak.bin $*

```

Sometimes the first message occurs twice. Another rarely occuring message is (mixed with the one from above):

```

*** glibc detected *** corrupted double-linked list: 0x0871cc08 ***

```

For me **this is a clear sign for a really bad bug in TeamSpeak2**, which unfortunately occurs in combination with oss2jack and jackd .

So I added a red warning text at the beginning of my HOWTO, to warn people reading the HOWTO. For you, who are using it already, I am very sorry, but at the moment I have no solution.

---

### Post by yibble on 2006-07-18
I was wondering if anyone knew if this how-to (at least the oss2jack part) would be the correct way to be able to 'Skype' users into a Shoutcast stream, via a jack interface?

For my show, I use the configuration that is detailed at: [https://wiki.ubuntu.com/DJPlayWithShoutcastHowto](https://wiki.ubuntu.com/DJPlayWithShoutcastHowto)

---

### Post by joft on 2006-07-19
Hi,

> **yibble said:**
> I was wondering if anyone knew if this how-to (at least the oss2jack part) would be the correct way to be able to 'Skype' users into a Shoutcast stream, via a jack interface?

For my show, I use the configuration that is detailed at: [https://wiki.ubuntu.com/DJPlayWithShoutcastHowto](https://wiki.ubuntu.com/DJPlayWithShoutcastHowto)

I didn't read through the whole article. And I'm not sure I understand you right, but I can tell you what "the oss2jack part" does:

oss2jack is a program, which "provides" an OSS sound device (/dev/dspX). As soon as a sound program opens such a device, oss2jack does some processing on the data it receives from that sound program and then oss2jack forwards the data to jackd. What jackd does with this data is up to you - depends an your configuration of jackd.
The point now is: the sound program doesn't know about oss2jack, it thinks, it just opened an OSS sound device and thus simply starts to output data to this device.

---

### Post by Sidhy on 2006-07-21
The how to looks nice but it is kind of useless atm for me missing the GPG. Would be nice if you add a link to the gpg key file :)

---

### Post by TheSandman on 2006-08-09
> **Sidhy said:**
> The how to looks nice but it is kind of useless atm for me missing the GPG. Would be nice if you add a link to the gpg key file :)


Mmmhmm.
Same here.

I used this to get "duplex" working on Breezy, oss2jack opening on demand porting to jackd managed this nicely.
When i updated to Dapper a number of things broke (why's it getting more and more like Windows, i even got an ugly graphic init screen...why? :-#  ), including this jackd/oss2jack setup.
Jackd works fine with the old package but oss2jack is clearly broken since the old package seems to be incompatible even when i rewrote the missing config file it was whining about by hand. Never mind that the new kernel doesn't load the modules i need by default anymore :evil: 

I also tried to DL the GPG key but it just says that my request is denied, also getting no ping reply.

From the look of this post i'm guessing it's been like this for weeks.

So, as is this guide is utterly useless unless you're able to find the jackd and oss2jack packages elsewhere.
Which is what i'll be doing just the same.


This used to work just dandy!
What gives?

---

### Post by Acker on 2006-10-13
Hi There!

This Howto worked well for me in Dapper. Is there a chance to bring it to edgy? 

I found already a patch for fusd to work with kernel 2.6.17 - but i wasnt able to load the kfusd module.

Anyone tried it?

Regards,
Acker

---

### Post by originof on 2006-10-13
when i do ```
sudo m-a a-i fusd-kor
```

i have this :

> 
# build
/usr/bin/make -C kfusd KDIR=/lib/modules/2.6.17-10-386/build
make[2]: Entering directory `/usr/src/modules/fusd-kor/kfusd'
echo EXTRA_CFLAGS=-I/usr/src/modules/fusd-kor/kfusd/../include
EXTRA_CFLAGS=-I/usr/src/modules/fusd-kor/kfusd/../include
/usr/bin/make -C /lib/modules/2.6.17-10-386/build SUBDIRS=/usr/src/modules/fusd-kor/kfusd EXTRA_CFLAGS=-I/usr/src/modules/fusd-kor/kfusd/../include modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.17-10-386'
  CC [M]  /usr/src/modules/fusd-kor/kfusd/kfusd.o
/usr/src/modules/fusd-kor/kfusd/kfusd.c:181: error: expected ‘)’ before string constant
/usr/src/modules/fusd-kor/kfusd/kfusd.c: In function ‘fusd_register_device’:
/usr/src/modules/fusd-kor/kfusd/kfusd.c:2036: warning: label ‘register_failed2’ defined but not used
/usr/src/modules/fusd-kor/kfusd/kfusd.c: In function ‘init_fusd’:
/usr/src/modules/fusd-kor/kfusd/kfusd.c:2941: warning: label ‘fail2’ defined but not used
/usr/src/modules/fusd-kor/kfusd/kfusd.c:2929: warning: label ‘fail7’ defined but not used
make[4]: *** [/usr/src/modules/fusd-kor/kfusd/kfusd.o] Error 1
make[3]: *** [_module_/usr/src/modules/fusd-kor/kfusd] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.17-10-386'
make[2]: *** [default] Error 2
make[2]: Leaving directory `/usr/src/modules/fusd-kor/kfusd'
make[1]: *** [binary-modules] Error 2
make[1]: Leaving directory `/usr/src/modules/fusd-kor'
make: *** [kdist_build] Error 2
any ideas ?

---

### Post by Acker on 2006-10-13
Hi!

Please excuse my bad english :)

I think i'll have found a solution for edgy (using 2.6.17-10-generic:

1. Do step 1. , 2A and 2C from the Howto.
2. sudo apt-get install fusd-kor-source
3. Replace the fusd-kor.tar.bz2 in /usr/src with the one attached here!! (the file kfusd/kfusd.c is patched with this tutorial -> [http://www.nabble.com/-PATCH--oss2jack-for-kernel-%3D%3E-2.6.17-(with-patch)-t2335368.html]("http://www.nabble.com/-PATCH--oss2jack-for-kernel-%3D%3E-2.6.17-(with-patch)-t2335368.html") )

4. sudo m-a a-i fusd-kor
5. sudo apt-get install fusd-kor

6. I didn't try to use the realtime module. so the next step is the startup script. I modified it to a small one - working for me:


```
# Start jackd
jackd -R -d alsa -p 256 > /dev/null 2>&1 & sleep 4
# Starting oss2jack
oss2jack > /dev/null 2>&1 &
```

put this one in an executable file and put it into Settings -> Session

7. Restart your system

I additional put the line kfusd at the end of /etc/modules, but i don't know if that is necessary.

Regards,
Acker

---

### Post by originof on 2006-10-13
ok, thanks....
it working fine.... :-D

---

### Post by whyameye on 2006-10-14
This is fantastic! It works great! I'm a little concerned that I might have to repeat these steps though when ubuntu updates their kernel? Is this true?

---

### Post by gershon on 2006-10-14
hi, i'm having problems compiling oss2jack (0.25).

./configure fails even though kfusd is installed (using the patch for edgy)
"checking for main in -lfusd... no"

i've installed the oss2jack binary but i get a:
"oss2jack: error while loading shared libraries: libjack-0.100.0.so.0: cannot open shared object file: No such file or directory"

im guessing its a config problem in my system somewhere, but i'd rather like to compile from source.

i also tried a checkinstall on kfusd, hoping to help this theard, which also failed :( 

any help on this or other software mixing through jack would be great.

---

### Post by Acker on 2006-10-15
@gershon

Have you tried the oss2jack package from the repository?

---

@whyameye

Yes: I Think we'll have to recompile the module when a new kernel version is released.

---

### Post by Fab on 2006-10-26
any chance this will be updated for edgy? I just tried to follow the compile instructions, but it doesn't seem to work out :/

---

### Post by Svictor on 2006-11-01
Thank you very much Acker ! :D
I've been missing this feature since update to edgy ! I just followed your howto (posted some 2 weeks ago), and everything worked fine.

---

### Post by Europeen on 2006-11-02
Hi world, 

Tutorial failed with 2.6.15-**27** kernel under Dapper.

---

### Post by Europeen on 2006-11-02
Re hello,

I always have this problem with oss2jack configuration (kernel 2.6.15-26) :

```
Not replacing deleted config file /etc/modprobe.d/oss2jack
chmod: cannot access `/etc/modprobe.d/oss2jack': No such file or directory
dpkg: error processing oss2jack (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 oss2jack
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I copied the oss2jack file in modprobe.d & install oss2jack, but it's changed anything. Thanks for your help !

---

### Post by Rob_Frohne on 2007-04-18
I'm running Edgy, and today I rebooted.  I found that I couldn't login under gnome unless I moved .gnomerc to somewhere else.  All my .gnomerc had in it were the stuff described above.  This is as of 4/18/2007.

Rob

---

### Post by joft on 2007-04-20
> **Rob_Frohne said:**
> I'm running Edgy, and today I rebooted.  I found that I couldn't login under gnome unless I moved .gnomerc to somewhere else.  All my .gnomerc had in it were the stuff described above.  This is as of 4/18/2007.

In this post [http://ubuntuforums.org/showpost.php?p=1233894&postcount=4]("http://ubuntuforums.org/showpost.php?p=1233894&postcount=4") I described I way to start the daemons usually started in ~/.gnomerc by hand.

So move/rename your .gnomerc, start by hand and look for the output of the daemons. What do they say?

---

### Post by k-o-x on 2007-04-22
Hello

I'm having problems with the neogate.homelinux.org repository, I get a NO_PUBKEY 411D6DA82E2FBFA5 when updating apt-get after having added neogate to my sources.list. Unfortunately  gpg --keyserver pgpkeys.mit.edu --recv-key 411D6DA82E2FBFA5 returns :
```
gpg: failed to create temporary file `/home/niko/.gnupg/.#lk0x811d2c8.vaio-niko.12999': Not a directory
gpg: key block resource `/home/niko/.gnupg/secring.gpg': general error
gpg: failed to create temporary file `/home/niko/.gnupg/.#lk0x811e0e8.vaio-niko.12999': Not a directory
gpg: key block resource `/home/niko/.gnupg/pubring.gpg': general error
gpg: request key 2E2FBFA5 from server hkp pgpkeys.mit.edu
gpgkeys: key 411D6DA82E2FBFA5 not found on keyserver
gpg: no valid OpenPGP data has been found.
gpg: Total processed: 0

```
(this was partly translated by hand to English, sorry if I didn't get the exact messages)

Any idea how to authenticate the repository ?

Thanks

Nicolas

---

### Post by joft on 2007-04-23
> **k-o-x said:**
> Any idea how to authenticate the repository ?

Well, just bypass authentication, usually aptitude asks if you want to continue, if the key is not available.

But, due to the fact, that you are the third or forth one, who asks for the key, I finally uploaded the public key to pgp.net just a few minutes ago (Fingerprint=CCF1 C83A 879C 89D7 4D87  D85B 411D 6DA8 2E2F BFA5).

---

### Post by motin on 2008-07-22
Thanks man I used parts of your guide to write the updated [HOWTO: Install oss2jack on Ubuntu Hardy]("http://ubuntuforums.org/showthread.php?p=5438615#post5438615")

Cheers!

---

