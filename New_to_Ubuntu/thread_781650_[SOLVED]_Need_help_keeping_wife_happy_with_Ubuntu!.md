---
title: "[SOLVED] Need help keeping wife happy with Ubuntu!"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by yogo on 2008-05-04
There are a few annoying oddities that are going on with an Ubuntu install on my wife's pc.

Mainly when it rears it's ugly head, no program can be started. IE FF, terminal, system monitor,quit, etc. Nothing can be run. The cursor spins and then it disappears with nothing starting. 

I can use alt +F2 and that will pop up a window to run commands, but none work from there including running in terminal option.

* can do ctrl alt backspace but* that freezes up. The only option is to power off manually.

I would think it has something to do with sessions but she has almost nothing running in her default session, only four or five items and none that I thought would interfere.

So I am perplexed as to what to do especially since terminal does not work.

Help me keep my wife from asking for Windows back.

---

### Post by SunnyRabbiera on 2008-05-04
hmm, well maybe another distro is in your future.
try mandriva, Mint or mepis... my three M's!

---

### Post by PmDematagoda on 2008-05-04
Could you please post the specifications of your wife's PC.

---

### Post by neur0 on 2008-05-04
Try to reach the terminal with ctrl-alt f2 (ctrl-alt f7 to retun to GUI)

---

### Post by yogo on 2008-05-04
Her specs are not that good, using an old hp processor Celeron 800, with 368 mb of ram on Feisty but it runs well despite the low specs, it should be something else though.

I will try these [          Try to reach the terminal with ctrl-alt f2 (ctrl-alt f7 to retun to GUI)] next time it acts up to see if I can get a terminal.

Her Dell motherboard fried when trying to install Ubuntu but that is a whole nother story, probably my fault, hard to work on a PC with a two year old jumping on your back.

I just did try the ctrl-alt f7 to retun to GUI but it was not acting up so I will have to wait but that is a nice little trick I did not know.

Thanks

---

### Post by R6V2 on 2008-05-04
I want a kid. I'm 13.

Lol. Back on topic. These are some wierd problems your having. Anyway, try using the terminal etc, and getting it back.

---

### Post by nynoah on 2008-05-04
well, I would say first, get rid of fiesty and go to Hardy.  It is far more stable than Fiesty was.  Another thing to check is to see what is running that is taking up so much computer memory that it is bogging you system.  Sounds like a program is hogging something up.  If there is one in there that is pulling 80% of your processor, I bet killing that will free up the computer.

Go to System-Administrator-system monitor-processes

---

### Post by yogo on 2008-05-04
> **nynoah said:**
> .  If there is one in there that is pulling 80% of your processor, I bet killing that will free up the computer.

Go to System-Administrator-system monitor-processes
  Yeah but when that is happening I can not open anything let alone system monitor.

As for upgrading to Hardy, I am not sure if her Celeron would run well in Hardy, I will have to look at min. requirements.

---

### Post by nynoah on 2008-05-04
keep the system monitor running and just watch it too see what is going on.  Maybe you can catch a pattern and see that a certain program spikes before you lock.

---

### Post by nynoah on 2008-05-04
Also you may want to try a different distro like - Fluxbuntu or xubuntu.  They are lighter on system load.

---

### Post by Slim Odds on 2008-05-04
I'm running Hardy on an older machine and it works fine.

Pentium III  - 800MHz
Memory       - 384M

Sometimes my daughter is playing frozen bubble and I connect over the network with XDMCP, and it all works fine.

---

### Post by yogo on 2008-05-04
> **nynoah said:**
> keep the system monitor running 

Now why didn't I think of that!

---

### Post by xyphur on 2008-05-04
...could also be as simple as a clogged CPU heatsink/fan, not allowing the machine to get the fresh, cool air it requires to cool off after a little bit of CPU loading. I've seen this all too often; CPU fans that can't even spin anymore because there's so much caked-on dust...

Check it out. Use a little brush and a vacuum to clean the heatsink and fan separately. I use the little brush that came with an old electric razor, works great.

---

### Post by yogo on 2008-05-04
> **xyphur said:**
> ...could also be as simple as a clogged CPU heatsink/fan, not allowing the machine to get the fresh, cool air it requires to cool off after a little bit of CPU loading. I've seen this all too often; CPU fans that can't even spin anymore because there's so much caked-on dust...

Check it out. Use a little brush and a vacuum to clean the heatsink and fan separately. I use the little brush that came with an old electric razor, works great.


That could be true, I have not looked inside this machine for about two years.

The pc did just lock up on me with the system monitor running. It is not from a cpu overload, thats for sure, I was averaging between 4 and 18 % at the time it locked up.

Well now all I need to know are a few cli commands to run and a way to copy and paste output from these commands in terminal.

???

---

### Post by mbarak on 2008-05-04
An alternative to keeping the system monitor running is to use the program "top" from the terminal (ctrl+alt+f1) when it freezes. it's like a system monitor but for the terminal
some options to help you:
once inside "top" you can press "u" and type the user name to see processes only for that user name
press "O" (capital o) and you can choose how to sort the list of processes (by CPU usage or memory usage are the most helpful)

Edit: once you find the program responsible for the freeze, press "k" and type in the programs PID (the number on the left)

again, like mentioned earlier, press ctrl+alt+f7 to get back to your screen

if all else fails, restart gdm (the display manager) with 
```
sudo /etc/init.d/gdm restart
```to start over, and login again

---

### Post by yogo on 2008-05-04
Mbarak,

Not really familiar with top, I tried running it and was not sure by your once inside comment above, how long it is suppose to take to get inside.

All I had was the cursor blinking in the top left hand corner. I waited several times but it never went away, only with ctrl alt +F9.

I looked for top in synaptic, is it automatically installed?

TIA

---

### Post by mbarak on 2008-05-04
top is a terminal program like the system monitor in gnome
what i meant by once inside is, once you run it (i.e with the cursor blinking at the top left corner)
it's installed by default, you don't need to install it
those other suggestions were just to easier find the runaway process - they're optional

Edit: O, and i forgot - press "q" to quit :p

---

### Post by kansasnoob on 2008-05-04
I have Xubuntu 7.10 (Gutsy) running fairly well on an old PII 333mhz w/192 GB RAM, but I had to use the text (alternative) installation.

To watch for cpu temp I always install "computertemp" from synaptic and then right click on any "open" area of either panel and select "add". Then you can drop an applet in the panel that shows if you're getting too warm. I generally change it to Fahrenheit and just tell people to pay attention if it hits more than 20 degrees above room temp. Unless it's a laptop, then I actually set the alarm limits to match the BIOS.

---

### Post by yogo on 2008-05-04
[quote=kansasnoob;4880872]I have Xubuntu 7.10 (Gutsy) running fairly well on an old PII 333mhz w/192 GB RAM, /quote]


Ok from the Xubuntu site, it says if you already have Ubuntu installed you can install Xubuntu by using Synaptic.

Well I did just that but it does not appear that anything was installed, although it took a good twenty minutes plus to install.

The only change it appeared to make is a new splash screen, not really any different than Ubuntu was, is this just a ??? and not the real thing?

I would probably be better doing a fresh install of Xubuntu Gutsy via apt on CD.

---

### Post by mbarak on 2008-05-04
to use xubuntu you have to log out, and log back in but choose "xfce" as your session instead of gnome
when you log out before entering your username and password click options > select session > xfce
then, when you log in you should see the xfce desktop environment

---

### Post by yogo on 2008-05-04
> **mbarak said:**
> to use xubuntu you have to log out, and log back in but choose "xfce" as your session instead of gnome
when you log out before entering your username and password click options > select session > xfce
then, when you log in you should see the xfce desktop environment 

 Did that, it just did not seem like that much different. I  just did the top, there was absolutely nothing that was eating up resources at all.

Hmmm.

---

### Post by mbarak on 2008-05-04
You should use top after your computer seems to act like it did in your first post - so you can find out which process is causing all the trouble.
as for xubuntu, it is meant to look and funtion similarly to ubuntu, but using much less resources. it does this by using different programs (ex: different panel, desktop, window manager, etc.)
if you look in the applications menu you'll notice a bunch of new programs - those programs are like other programs you already had, but use less resources (ex: abiword for word processing).

---

### Post by hufferd on 2008-05-04
> **yogo said:**
> There are a few annoying oddities that are going on with an Ubuntu install on my wife's pc.

Mainly when it rears it's ugly head, no program can be started. IE FF, terminal, system monitor,quit, etc. Nothing can be run. The cursor spins and then it disappears with nothing starting. 

I can use alt +F2 and that will pop up a window to run commands, but none work from there including running in terminal option.

* can do ctrl alt backspace but* that freezes up. The only option is to power off manually.

I would think it has something to do with sessions but she has almost nothing running in her default session, only four or five items and none that I thought would interfere.

So I am perplexed as to what to do especially since terminal does not work.

Help me keep my wife from asking for Windows back.


This is very interesting I have been reading the other posts but I thought I would quote the first one here because.  I am new to ubuntu but I to have had this issue.  I am getting ready to build a new box but I wanted to try ubuntu out on an old machine... 

specs.  Dell 2.8 processor 1gig ram running 8.04 desktop ver. 

I have had this same thing happen many times I just thought seeing how my PC I was using with it was 5 years old..  I thought all would be fixed when I got my new machine built.  

maybe not I to have had to power down I get the very same thing at times when trying to fire up a program.  Maybe I should file a bug report??? 

Any way I will keep reading everyone have a good sunday whats left of it anyway!

~DH:lolflag:

---

### Post by yogo on 2008-05-04
> **mbarak said:**
> You should use top after your computer seems to act like it did in your first post - so you can find out which process is causing all the trouble.
.


That is ezactly how I used top, when her pc was acting up, but she only had about 14 things going and not one was using any resources, all were sleeping or less than 1%.

I started her running Xcfe, I remember using it before but has been a while, hopefully this will not happen. However it does not appear to be from running apps.

Must be something screwy somewheres and Xcfe will probably be clean whatever it is.

Fingers crossed, I just burned an app on cd of Xubuntu to install just in case.

---

### Post by mbarak on 2008-05-05
There are no processes taking up all the resources? then i'm sorry i don't know what the problem is, and i can't help you (i'm not experienced enough with linux)
the only other thing i can suggest is that perhaps one program is freezing (not necessarily taking up all resources) and causing everything else to lock up.
if you were using a program before it freezes, try closing that program and maybe everything else will start to run properly again.
you can do this by switching to a terminal and using these commands:
to list all running processes:
```
ps -u username
```
to force-kill the specific process:
```
kill -KILL processnumber
```
or to kill all occurrences of that process
```
killall program-name
```

the last one you should be able to run from alt+f2
ex: killall firefox

**also, just in general - if a program freezes you can run xkill (from alt+f2) and click the window of the frozen program

hope all of this helps

---

### Post by kwacka on 2008-05-05
Possible that its disk indexing by trackerd - to test go to System --> Administration --> Services and clear the 'Tracker' box, reboot

Another possibility see: [http://ubuntuforums.org/showthread.php?t=763450&highlight=hot+kernel+patch](http://ubuntuforums.org/showthread.php?t=763450&highlight=hot+kernel+patch)

---

### Post by Slim Odds on 2008-05-05
> **kwacka said:**
> Possible that its disk indexing by trackerd - to test go to System --> Administration --> Services and clear the 'Tracker' box, reboot

Another possibility see: [http://ubuntuforums.org/showthread.php?t=763450&highlight=hot+kernel+patch](http://ubuntuforums.org/showthread.php?t=763450&highlight=hot+kernel+patch)

For the Love of God, people, quit telling everyone to REBOOT linux. It's JUT NOT NEEDED. The **only** time to reboot linux is when there is a **kernel** update.

Just shut servers down or restart them.

UUUUUUUUUUUUGGGGGGGGG!!!!!!!!!!

---

### Post by Slim Odds on 2008-05-05
dup due to server error!

---

### Post by ant2ne on 2008-05-05
> **Slim Odds said:**
> For the Love of God, people, quit telling everyone to REBOOT linux. It's JUT NOT NEEDED. *Ahem* I can give you a list of reasons to restart linux. Granted, not NEARLY as frequently as a windows machine..

This problem sounds like a hardware issue. The OP did not mention how well the PC performed before installing ubuntu. Or if this is a dual boot machine.
My first instinct is that this is a bad sector on the HD, most likely where the swap space is located. In a windows machine I would tell you to run chkdsk c: /f/r I'm not sure what the equivalent linux command would be. My second guess is bad RAM, overheating RAM, or overheating CPU. Does this error seem more related to up time? Or random application memory usage?

---

### Post by Gregmond on 2008-05-05
> **ant2ne said:**
> 

This problem sounds like a hardware issue. The OP did not mention how well the PC performed before installing ubuntu. Or if this is a dual boot machine.


My first thought was its hardware, I also recall the opriginal entry saying he fried something ? or was that unrelated ?
Not sure about the HDD/Swap file eroor listed, but the type of thing you have described I have seen from a CPU/MotherMoard that was faulty - I swapped the M/B with an identical one and same result, got a different CPU (went from a 3.2Ghz to 3.4Ghz as I couldn't get an identical one) and the problem went away. :)

---

### Post by Slim Odds on 2008-05-06
> **ant2ne said:**
> *Ahem* I can give you a list of reasons to restart linux. Granted, not NEARLY as frequently as a windows machine..

***Ahem*  **He was talking about shutting down the tracker daemon, whence NO REASON TO REBOOT!!!!

And please, give us the list. It's pretty short.

1) New kernel
2) Major reconfiguration (usually kernel related)
3) New hardware (duh)

That's really about it.....

---

### Post by kwacka on 2008-05-08
> **Slim Odds said:**
> For the Love of God, people, quit telling everyone to REBOOT linux. It's JUT NOT NEEDED. The **only** time to reboot linux is when there is a **kernel** update.

Just shut servers down or restart them.

UUUUUUUUUUUUGGGGGGGGG!!!!!!!!!!

yes, my bad.

I should have ignored the title of the forum and instead of just saying remove tracker & rebooting I **should** have continued to mention stopping trackerd, etc.

Possibly I could also have mentioned the possibility of using upstart instead of cron to force trackerd to index at 4.00 am. 

please, please accept my apologies for this gross neglect.

---

### Post by yogo on 2008-05-13
Well it seems that it was a faulty theme engine that was causing all the troubles. I am going to have her stop using xcfe4 and back to her normal ubuntu desktop. Not that xcfe4 has any issues with it, the theme problem rose it's ugly head on both xcfe4 and gnome but I find editing the menu's on xcfe4 confusing and not straightforward, no items are listed to delete etc.

---

