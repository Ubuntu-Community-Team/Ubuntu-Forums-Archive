---
title: "Conky or something else?"
date: 2012-07-12
forum: New to Ubuntu
---

### Post by Penfold1971 on 2012-07-12
Still very new to Ubuntu (12.04), and am looking for recommendations.

I'd like to be able to monitor CPU temperature. I've read a bit about Conky, but it seems to offer a vast range of stats. If I downloaded it I suppose I could have it display only the single stat I want, but is there something simpler I could use instead?

---

### Post by puntigamer on 2012-07-12
You can try Screenlets, but a conky is a much more elegant solution! Search for some simple scripts, try them and modify them to your own needs, it's not to difficult ;)

---

### Post by GreatDanton on 2012-07-12
Only what you need is time. Play with Conky, and you will see how much fun Conky can produce. Oh and here is the screenshot.

P.S If you want to know how to build Conky, then here is the link for you:
[http://ubuntuforums.org/showthread.php?p=10879356#post10879356](http://ubuntuforums.org/showthread.php?p=10879356#post10879356)

[http://ubuntuforums.org/showthread.php?t=2013848&page=5](http://ubuntuforums.org/showthread.php?t=2013848&page=5)

---

### Post by jmfal on 2012-07-12
Conky is addictive, there is a humongous "post your conky" thread in the community cafe,
it will show you haw to set one up, if you want to go that route.

I use "psensors" also ,  from here:

[http://www.addictivetips.com/ubuntu-linux-tips/monitor-temperature-of-system-components-in-ubuntu-with-psensor/](http://www.addictivetips.com/ubuntu-linux-tips/monitor-temperature-of-system-components-in-ubuntu-with-psensor/)

---

### Post by NikTh on 2012-07-12
> **jmfal said:**
> 
I use "psensors" also ,  from here:

[http://www.addictivetips.com/ubuntu-linux-tips/monitor-temperature-of-system-components-in-ubuntu-with-psensor/](http://www.addictivetips.com/ubuntu-linux-tips/monitor-temperature-of-system-components-in-ubuntu-with-psensor/)

I use psensor too . Have in mind that psensor in 12.04 added to Ubuntu General repository so [U]you don't need to add an external repository of ppa:jfi/ppa 

[/U]You just run these commands 
```
sudo apt-get install lm-sensors
sudo sensors-detect **# answer with Enter to all questions**
sudo apt-get install psensor 
```and reboot your machine

---

### Post by jmfal on 2012-07-12
You are right Nik th

For some reason I couldn't get it to work from repos  so I added ppa

---

### Post by Penfold1971 on 2012-07-12
> **jmfal said:**
> I use "psensors" also ,  from here:

[http://www.addictivetips.com/ubuntu-linux-tips/monitor-temperature-of-system-components-in-ubuntu-with-psensor/](http://www.addictivetips.com/ubuntu-linux-tips/monitor-temperature-of-system-components-in-ubuntu-with-psensor/)

I've chosen your suggestion to use 'psensors'. It looks to be what I'm after - I only want temps.

I've run [FONT="Courier New"]sudo apt-get install lm-sensors[/FONT], and then
[FONT="Courier New"]sudo sensors-detect[/FONT] .

In Terminal I've now got to a point, after lots of probing and scanning where it says 

[FONT="Courier New"]Monitoring programs won't work until the needed modules are loaded. You may want to run 'service module-init-tools start' to load them.

Unloading i2c-dev... OK
Unloading i2c-i801... OK
Unloading cpuid... OK[/FONT]

This is then followed by the usual [FONT="Courier New"]name@name etc;~$[/FONT] prompt.

QUESTION :  Do I want to run 'service module-init-tools start' ? Or is that covered by the next step in your link : "Now install Psensor from PPA by entering the following Terminal commands:" ?

---

### Post by Penfold1971 on 2012-07-12
OOps. Just seen NikTh's post. 

Am I OK to continue with the instructions on the page you linked to ?  :

[http://www.addictivetips.com/ubuntu-linux-tips/monitor-temperature-of-system-components-in-ubuntu-with-psensor/](http://www.addictivetips.com/ubuntu-linux-tips/monitor-temperature-of-system-components-in-ubuntu-with-psensor/)

---

### Post by jmfal on 2012-07-12
You can do it either wa,y I just had problems with the repos at the time so I added the ppa', you can follow the setup instructions from the link

---

### Post by GreatDanton on 2012-07-12
Edit: post deleted

Do you want conky script for temperatures or you only want it to display it once in a while?

---

### Post by Penfold1971 on 2012-07-12
This is what I instinctively fear about using Terminal : (Maybe I'm just superstitious :) )

I went ahead and entered [FONT="Courier New"]service module-init-tools start[/FONT] after the prompt and got :

[FONT="Courier New"]start: Rejected send message, 1 matched rules; type="method_call", sender=":1.196" (uid=1000 pid=11993 comm="start module-init-tools ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")[/FONT]

followed by the prompt.

Can anybody explain this? I seem to have ground to a halt here.

---

### Post by Penfold1971 on 2012-07-12
> **jmfal said:**
> You can do it either wa,y I just had problems with the repos at the time so I added the ppa', you can follow the setup instructions from the link

Thanks for replying.

I'll follow the set up in your link then but first I'm stuck on the part in my last post. What should I do about that?

---

### Post by jmfal on 2012-07-12
If you are brought back to a prompt without a error message then you can continue with setup.

---

### Post by Penfold1971 on 2012-07-12
But there is an error mentioned :

[FONT="Courier New"]start: Rejected send message, 1 matched rules; type="method_call", sender=":1.196" (uid=1000 pid=11993 comm="start module-init-tools ") interface="com.ubuntu.Upstart0_6.Job" member="Start" [COLOR="Red"]**error**[/COLOR] name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")[/FONT]

---

### Post by NikTh on 2012-07-12
I think its not necessary to start init modules. The modules will be added to startup . Just reboot your system. 
Did you install psensor ? 
If you don't want psensor (as a graphical program) you can see temperatures from terminal giving this command 
```
sensors
``` 
But restart your PC.

---

### Post by Penfold1971 on 2012-07-12
> **NikTh said:**
> I think its not necessary to start init modules. The modules will be added to startup . Just reboot your system. 
Did you install psensor ? 
If you don't want psensor (as a graphical program) you can see temperatures from terminal giving this command 
```
sensors
``` 
But restart your PC.

OK thanks for that reply.  I installed simply with the command
[FONT="Courier New"]sudo apt-get install psensor[/FONT]
then I did a Restart.

It is working! The temperatures are high - I guess I'll have to connect up the two extra as-yet unconnected case fans (I have just the top case fan running just now). Maybe I'll connect them one at a time and monitor temps.

I use this machine (purpose-built for the task) to run Folding@home continuously. It is CPU intensive. CPU usage is shown as 100% on the psensor window.

Many thanks - I might start another thread if I have any more questions/observations.

---

### Post by Penfold1971 on 2012-07-12
My thanks to everyone who replied with advice and suggestions.

---

