---
title: "Laptop fan control"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by r5gtt2k3 on 2008-11-22
Is there such thing on Ubuntu ? There was only one application that would let me adjust my fan speed in windows. It runs a little to hot (70c when I'm watching video) before the thermostat kicks in on the laptop, yet I'm unable to change it within the bios 

It's a Dell Latitude D830, I hope I can do something as i really don't like high temps on the cpu :( 

Thanks

---

### Post by mbsullivan on 2008-11-22
> Is there such thing on Ubuntu ?

As far as a general solution, I believe that installing lm-sensors and pwmconfig might work for your laptop, but it doesn't look like a trivial install.

See [here]("http://ubuntuforums.org/showthread.php?t=42737") and [here]("http://wiki.archlinux.org/index.php/Fan_speed_control") for some tutorials. I'm sure there are more out there.

For a laptop, 70 degrees Centigrade is not too hot (for the CPU, anyway). Mobile CPUs are built to withstand higher temperatures than their desktop counterparts.

Mike

---

### Post by adult swim on 2008-11-22
you can use gkrellm to control your fans.  to install it, from a terminal run ```
sudo apt-get install i8kutils gkrellm gkrellm-i8k
```
when its installed we need to run a few more commands.
```
sudo modprobe i8k force=1
```
then ```
gksudo gedit /etc/modules
```a file will open up, at the end of the file make a new line and paste in ```
i8k force=1
```save the file and close it.  now you can run gkrellm by hitting alt+f2 and typing in ```
gkrellm
```  to set the temperatures you want your fans to come on at, right click the gkrellm window and select configuration.  then go to plugins and enable the dell i8k plugin.  click the plugins drop down menu and select dell i8k plugin. now you can go to the temps tab and set up the temperatures that you want your fans to come on.

---

### Post by frankleeee on 2008-11-22
Install i8k and GKrellM in synaptic and you can set auto or manual controls with a temp adjustment in gkrellm. You can also set gkrellm to do a auto start when you turn your computer on from the sessions area by add it to startup if you need more info just ask.
[http://www.diefer.de/i8kfan/index.html](http://www.diefer.de/i8kfan/index.html)

---

### Post by r5gtt2k3 on 2008-11-23
Wow, Thanks for the reply guys, I will Take a look :) 

And i know laptop cpu's run hotter i just don't like it at 70c hehe, Under load with the fan on slow it was just hitting 45c under vista

---

### Post by frankleeee on 2008-11-23
> **r5gtt2k3 said:**
> Wow, Thanks for the reply guys, I will Take a look :) 

And i know laptop cpu's run hotter i just don't like it at 70c hehe, Under load with the fan on slow it was just hitting 45c under vista

As the other poster suggested, (beat me to it by seconds) the i8k and GKrellM work great I have set up GKrellM to start at boot and adjusted the fan speeds per the temps, so my dell inspiron 4100 never goes above 40 c now.

---

### Post by motoperpetuo on 2008-11-23
> **adult swim said:**
> you can use gkrellm to control your fans.  to install it, from a terminal run ```
sudo apt-get install i8kutils gkrellm gkrellm-i8k
```
when its installed we need to run a few more commands.
```
sudo modprobe i8k force=1
```
then ```
gksudo gedit /etc/modules
```a file will open up, at the end of the file make a new line and paste in ```
i8k force=1
```save the file and close it.  now you can run gkrellm by hitting alt+f2 and typing in ```
gkrellm
```  to set the temperatures you want your fans to come on at, right click the gkrellm window and select configuration.  then go to plugins and enable the dell i8k plugin.  click the plugins drop down menu and select dell i8k plugin. now you can go to the temps tab and set up the temperatures that you want your fans to come on.

is there anything like this that might work on a gateway solo 1450 running itrepid? i tried it, but my fan is still not switching on. could that be because i haven't run updates after installing intrepid? or because i'm on a gateway, not a dell? i'm a bit afraid to run updates...who knows how hot my cpu will get?

---

### Post by motoperpetuo on 2008-11-25
> **motoperpetuo said:**
> is there anything like this that might work on a gateway solo 1450 running itrepid? i tried it, but my fan is still not switching on. could that be because i haven't run updates after installing intrepid? or because i'm on a gateway, not a dell? i'm a bit afraid to run updates...who knows how hot my cpu will get?

well, fan control started working somehow, using the same script and cronjob i was using when i had fedora on this laptop. if anyone wants the script (for a gateway solo 1450), feel free to IM me.

---

### Post by bobnutfield on 2008-11-25
CPU frquency scaling is normally enabled in Ubuntu by default.  But 70C is pretty hot, even for a laptop.  Mine never goes above 50C, even when doing heavy graphical stuff like videos.  I would make sure that it is in fact enabled.

---

### Post by angus_young on 2008-12-06
Sorry a noob question, do i have to have gkrellm running all the time, on screen for the fan to be controlled?

Thanks

---

### Post by LudaChr1s7 on 2008-12-15
Hi guys,
I am a fairly new Linux user.  I have tried many different fan control programs now including nclock, dellfand and now gkrollm.  While gkrollm seems to work, when set on automatic the fan goes on high (which is expected because my laptop is hot and over the degree) but every like 5 seconds or 10 seconds it pulses going to a lower speed and then back up, its not going completely off though just lower and starting up again.  I worry this is wearing out the fan.  I would also like to know how stop all these programs and just go back to the default Ubuntu fan settings as if I had never tweaked them.
Any help is greatly appreciated.
Thanks

---

### Post by jerrynewt on 2008-12-15
I am also having temp problems on my Toshiba Satellite Pro 6100. "sudo toshset -fan 6" which worked just fine in 8.04 gives a "kernel support not enabled" in 8.10 and 9.04. Any suggestions for a workaround on this ?? Thanks and Merry Christmas !!

---

### Post by SSdio on 2009-02-23
Hello, is there a script that works for acer aspire 1690 for gkrellm?  I tried installing lm-sensor but it's not picking anything at all when I use sensor-detect.

---

### Post by quirijnquintus on 2009-03-12
Same problem here, no sensors detected. My laptop is steaming up to 95 degrees! It's painfully slow too. Is there any other way to manage fan control then lm-sensor?

[SIZE="2"]edit: I'm running a FujitsuSiemens laptop, 512MB DDR Ram, 1.60 Ghz Celeron[/SIZE]

---

### Post by Hachi-Roku on 2009-09-03
hey guys. 

Any luck with the fan tweaks?

im on a toshi satellite. 

under hardy; the fan comes on then never goes off.
under jaunty: the fan doesnt seem to come on!

man, talk about strange. 

Done the lm sensors and i see that when both cpu's are at 71 deg the fans are still not on.

So i reboot and they come on straight away at the bios screen.
AND DONT TURN OFF.

I havent really been game enough to see how high they will go before the fan comes on. If it does.

Also, i did the gkrellm thing, and of course im not on a dell so that plugin doesnt do much. Tweaking the settings doesnt seem to make a difference either.

Not sure which way to go next... Any help appreciated!

J

---

### Post by Daedalus Fly on 2009-10-08
Hi There. This is my first post. As much as I really like Ubuntu, this fan issue is driving me nuts. I notice a great deal of the posts are related to fan problems. I'm surprised there are no official solutions. I swear every response is a link to another post, which in turn is a link to another post, ad infinitum.
I have a Thinkpad T42 and recently installed Jaunty on it. All I want to do is control the temperature at which the fans go on... and if I can stop the fans from pulsing, all the better. It seems my saviour may lie in the [ThinkPad Fan Control daemon]("http://www.surban.net/mediawiki/index.php/ThinkPad_Fan_Control"). But, being an Ubuntu rookie, I have no idea how to install it. The read me states:

1. Adjust src/tpfand/build.py to your needs. (This makes sense.)
2. Run make install (This doesn't make sense.)
3,4,5 ETC...

I don't understand how to run make install. There is a file called Makefile. But, when I double click on it, it opens it in a text editor. There is no info on how to run it, and there is no executable-like file. Can anyone offer up some advice? I've already installed i8k (or some name like that), which gives me temperatures. But, fan tweeks don't work. I also checked my bios, but can't find anything about fans there. I've spent a long time on this problem because I think Ubuntu has a lot to offer. Though, I fear I may have to switch back to Windows if I can't get this issue sorted.

---

### Post by Daedalus Fly on 2009-10-08
I assume I have to play around in the terminal. I just don't know what commands to use and what file to use them on. Hope you can help.

---

### Post by lochii on 2009-11-28
start the terminal, 

$ cd <path to your diretory>
$ make install

The Makefile is a file which is processed by a utility called GNU "make" which can be found in the "make" package.

---

