---
title: "Login screen returns to login screen?"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by Djanvk on 2008-09-05
I just installed Ubuntu 8.04 onto my compaq desktop computer.

The installation went great but when I restarted it after installation I get to the login screen, enter my login and password and it starts to go to the main GUI I'm assuming, BUT my monitor will flash the message that it was going to shutdown for energy saving mode, then my Login screen just starts back up again.

I've tried it a couple of times same thing.  It installed fine just cannot get into the main OS.

Thanks

I am a newbie to Ubuntu.

---

### Post by alienexplorers on 2008-09-06
Are you getting any type of message concerning not being able to find home directory, will reset in 10 seconds.

---

### Post by Djanvk on 2008-09-07
Nothing I notice really flashes up, I just put my login and password in and I get th Ubuntu startup music then it goes black and my monitor acts like it is going into powersaving mode, so I'm assuming it's actually shutting off my monitor maybe and then back to the login screen.

---

### Post by JumpForJoy on 2008-09-07
I have the same problem.  I can log in the fail safe mode but if I try to log into the normal mode my moniter shuts off and my commputer returns to the login screen.  I am also compleatly new at Ubuntu.

---

### Post by Djanvk on 2008-09-07
Thats exactly where I'm at, I can get into failsafe mode also.

---

### Post by sanemanmad on 2008-09-07
> **Djanvk said:**
> Nothing I notice really flashes up, I just put my login and password in and I get th Ubuntu startup music then it goes black and my monitor acts like it is going into powersaving mode, so I'm assuming it's actually shutting off my monitor maybe and then back to the login screen.

Hi Djanvk~

From you are describing it's sounds like there is an issue with your graphics card and the [COLOR="Red"]xorg.conf[/COLOR] file. 

I would suggest trying the following:

First login into terminal

[COLOR="Red"]Applications > Accessories > Terminal[/COLOR] 

@ the prompt type :
[I]
sudo cp /etc/X11/xorg.conf xorg.conf.bak[/I]

then *sudo rm /etc/X11/xorg.conf* 

now reboot. 

when you come to the login try it. 

There is actually another *troubleshooting* technique but I do not recall of the top of my head as am reeaallly sleeeppy.

Anyhow the above steps are simply copying the *static* settings for your display to xorg.conf.bak and then removing the *static* settings from boot. now when ubuntu tries to load your vid settings it may default to 800x600 or even better your *native* display.

---

### Post by Djanvk on 2008-09-07
Ok tried that and still having trys to start then back at login screen.  It's funny, I can get into failsafe gnome, but cannot get into the regular gnome.

Thanks

---

### Post by Djanvk on 2008-09-07
This is my video card:  ATI Technologies Inc RS480 [Radeon Xpress 200G Series]

Is there a problem with Linux and This?  Could that be the problem

---

### Post by sanemanmad on 2008-09-07
Can you attempt to login then post the results of '[COLOR="Red"]dmesg tail[/COLOR]' from the [COLOR="Red"]Terminal[/COLOR] also. This shoud capture any issues that may be going on.

Hopefully someone more senior will jump in here and add some suggestions.

Can I see your Xorg file? 

[I am running dualhead or else I would compare mine]

---

### Post by sanemanmad on 2008-09-07
> **Djanvk said:**
> This is my video card:  ATI Technologies Inc RS480 [Radeon Xpress 200G Series]

Is there a problem with Linux and This?  Could that be the problem

Not at all in fact I was using that same vidcard on my HP desktop, I have since installed ubuntu server edition on that so there is no xorg file to look at in this case. but lets see that xorg file...

---

### Post by buntu_hugenewbie11 on 2008-09-17
I am having the same problem and I am using a Nvidia Geoforce card.
Looking at forums this seems to have happened to a few people with no solution posted. Has anyone been able to find a fix from being stuck in the never ending login loop?

---

### Post by coffeepro on 2008-10-09
Hi everybody I just tried a clean install of 8.04.
I have the EXACT video card and am getting the same issue.

7.04 works perfectly. I reinstalled 8.04 again to be sure, same problem, infinite loop back to the log-in screen.

Is this because Compiz is on by default in 8.04? If so how do I turn it off? Obviously this is a serious bug in this release.

Thanks for any input or suggestions.

---

### Post by coffeepro on 2008-10-11
After three attempts I about gave up. Then tried Xubuntu 8.04 and it installed no problem. The original disk was from Canonical maybe it was faulty. Still seems odd everyone with the same vid card is having this issue.

---

### Post by U2010 on 2010-02-21
Hi,

had the same problem last month. In my case, there have been two files  in my home directory with root:root ownership (.ICEauthority and  .nvidia-settings-rc). Just changed ownership and everything is back to  normal.

Hope this helps and greetings.

---

### Post by amarjoshi88 on 2010-03-26
> **U2010 said:**
> Hi,

had the same problem last month. In my case, there have been two files  in my home directory with root:root ownership (.ICEauthority and  .nvidia-settings-rc). Just changed ownership and everything is back to  normal.

Hope this helps and greetings.
I too am having the same problem....
but I'm new to linux, and I cant see those two files in my home directory. Do you have to use 'sudo' or something to view those files?

---

### Post by cjazz on 2010-03-27
> **amarjoshi88 said:**
> I too am having the same problem....
but I'm new to linux, and I cant see those two files in my home directory. Do you have to use 'sudo' or something to view those files?

Nope. In Linux, files with a leading dot are "hidden" files. From a terminal, do:
```
ls -la
```

---

### Post by jeff35 on 2010-05-12
type your main id in as other user. worked for me:P

---

