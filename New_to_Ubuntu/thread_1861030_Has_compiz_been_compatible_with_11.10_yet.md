---
title: "Has compiz been compatible with 11.10 yet?"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by ngubk on 2011-10-15
I had tried 11.04 for a month and got disapointed because it is no longer 'infinite customizable' anymore. Compiz often makes the destop crash and many features can't be changed. I turned back to 10.10 and still hesitate whether to upgrade to 11.10. Please give me some good review and thought regarding the newest distribution of ubuntu

---

### Post by Meelad on 2011-10-15
Nope not yet.. Just broke my 11.10 with it.

---

### Post by Lisiano on 2011-10-15
How did you try using Compiz? Did you tell CCSM to load the Ubuntu Unity Plugin?

---

### Post by Meelad on 2011-10-15
> **Lisiano said:**
> How did you try using Compiz? Did you tell CCSM to load the Ubuntu Unity Plugin?

I just installed it, ran it, and was ONLY exploring the options (didn't change anything, didn't check or uncheck anything).. When I clicked the Preferences tab (below) Unity disappeared completely!

But thanks to this thread 

[http://ubuntuforums.org/showthread.php?p=11347705#post11347705](http://ubuntuforums.org/showthread.php?p=11347705#post11347705)

I got it back up and running in 10 minutes, but I didn't dare to play with Compiz again..

---

### Post by Lisiano on 2011-10-15
When you clicked the Preference tab, Compiz tried to apply the settings stored in the Default profile.
Please try using a short guide on how I got Compiz to play nicely with Unity.
[http://ubuntuforums.org/showpost.php?p=11347579&postcount=3](http://ubuntuforums.org/showpost.php?p=11347579&postcount=3)
You can always restore unity by using this command
```
unity --reset
```
If you login using a TTY (Ctrl+Alt+F1-F6) to reset unity, prepend DISPLAY=:0.0

---

### Post by lovinglinux on 2011-10-15
> **Meelad said:**
> I just installed it, ran it, and was ONLY exploring the options (didn't change anything, didn't check or uncheck anything).. When I clicked the Preferences tab (below) Unity disappeared completely!

But thanks to this thread 

[http://ubuntuforums.org/showthread.php?p=11347705#post11347705](http://ubuntuforums.org/showthread.php?p=11347705#post11347705)

I got it back up and running in 10 minutes, but I didn't dare to play with Compiz again..

I had a similar problem, but in my case, Unity 3D didn't work anymore. I ended up cleaning all my gnome and kde settings and now it is working properly. However, I am experiencing a weird issue with compiz. Sometimes it grabs the window on it's own, like if I am trying to move it and the window gets completely distorted.

---

### Post by Meelad on 2011-10-15
> **Lisiano said:**
> When you clicked the Preference tab, Compiz tried to apply the settings stored in the Default profile.
Please try using a short guide on how I got Compiz to play nicely with Unity.
[http://ubuntuforums.org/showpost.php?p=11347579&postcount=3](http://ubuntuforums.org/showpost.php?p=11347579&postcount=3)
You can always restore unity by using this command
```
unity --reset
```If you login using a TTY (Ctrl+Alt+F1-F6) to reset unity, prepend DISPLAY=:0.0

Ok, I won't click on the Preferences button again. (still this problem has to be solved imo)

I turned on the wobbly window effect now in Compiz, and changed the icon size of the launch bar, and the transparency of the menu bar. No crash so far, but I don't think I'm going any further..

Thanks for giving me some confidence to play with Compiz again, but these issues have to be addressed by the Ubuntu developers team..

---

### Post by wildmanne39 on 2011-10-15
Hi, I am using the cube and full effects in 11.10, you can not disable Opengl and you need to pay attention when changing things, it will disable the unity plug in but if you just put a check back by unity pluging it works.

Also the cube and effects worked in 11.04 they were just harder to setup that is why I wrote the guide that is in my signature.
Thank you

---

### Post by wildmanne39 on 2011-10-15
Hi lovinglinux, I believe what you are talking about in reference to the grabbing of the window is when you are moving the window and it touches the top panel, you can deactivate that by opening ccsm and uncheck enable grid, but it will mess up your desktop most likely and you will need to log out.

I have a menu bar at the bottom of my screen so logging out was easy for me but the log out icon in the top right corner did disappear when I unchecked enable grid.
Thank you

---

### Post by beew on 2011-10-15
It  works quite well for me. I have changed CCSM settings many times without things going crazy like in Natty.  For example, I enabled the desktop cube with just a few clicks (disable Unity -> disable desktop wall -> enable desktop cube, 3d windows and rotating cube -> enable Unity)  and it didn't crash and mess up my settings like in Natty. 

When fiddling with the options the screen went blank several times and I thought "****.." but it lasted only momentarily then it fixed itself again. I didn't even have to logout and log back in for the new settings to take hold.

---

### Post by beew on 2011-10-15
> **wildmanne39 said:**
> 
Also the cube and effects worked in 11.04 they were just harder to setup that is why I wrote the guide that is in my signature.
Thank you

I find it a lot easier to set up the cube and the effects in 11.10 then in 11.04. The cube was one of the first things I did, since I was expecting to reinstall I didn't even take any special precaution like I did in Natty, but everything worked out rather smoothly.

---

### Post by lovinglinux on 2011-10-15
> **wildmanne39 said:**
> Hi lovinglinux, I believe what you are talking about in reference to the grabbing of the window is when you are moving the window and it touches the top panel, you can deactivate that by opening ccsm and uncheck enable grid, but it will mess up your desktop most likely and you will need to log out.

I have a menu bar at the bottom of my screen so logging out was easy for me but the log out icon in the top right corner did disappear when I unchecked enable grid.
Thank you

The thing is I am not moving the window. It grabs the window by itself.

I disabled Unity MT Grab Handles and looks like it solved the problem. I will post gain if the problem persists.

---

### Post by wildmanne39 on 2011-10-15
Hi lovinglinux, I am not sure then.

---

### Post by lovinglinux on 2011-10-15
> **wildmanne39 said:**
> Hi lovinglinux, I am not sure then.

I disabled Unity MT Grab Handles and looks like it solved the problem. I will post again if the problem persists.

---

### Post by wildmanne39 on 2011-10-15
Hi, that is good, I am glad you have it working.

---

### Post by lovinglinux on 2011-10-15
> **wildmanne39 said:**
> Hi, that is good, I am glad you have it working.

It's been a long time since I used Compiz. I was using KDE for the past 3 releases. But I am getting acquainted with it again :-)

**EDIT:** Spoke too soon. Is doing it again.

---

### Post by ngubk on 2011-10-16
Can you change the workspace by clicking on the edge of the screen? Love that Compiz feature in 10.10 but it's impossible in 11.04

---

### Post by lovinglinux on 2011-10-17
> **wildmanne39 said:**
> Hi lovinglinux, I believe what you are talking about in reference to the grabbing of the window is when you are moving the window and it touches the top panel, you can deactivate that by opening ccsm and uncheck enable grid, but it will mess up your desktop most likely and you will need to log out.

I have a menu bar at the bottom of my screen so logging out was easy for me but the log out icon in the top right corner did disappear when I unchecked enable grid.
Thank you

I think the real culprit was Wobbly plugin.

---

### Post by wildmanne39 on 2011-10-17
Hi lovinglinux, that is strange I always use wobbly windows I have never had a problem with them but maybe I have just been lucky.

---

### Post by lovinglinux on 2011-10-17
> **wildmanne39 said:**
> Hi lovinglinux, that is strange I always use wobbly windows I have never had a problem with them but maybe I have just been lucky.

I was using Wobbly before, but now when I try to enable it Compiz crashes.

---

### Post by wildmanne39 on 2011-10-17
Hi, I do not remember for sure but with several changes in compiz the desktop and compiz went crazy but then they returned after about 30 seconds.

It could be an issue with just your compiz though.

I will try to test that issue later tonight, I have to download 11.10 again and install it in virtualbox.

I have to get off for a little while, I will be back as soon as I can.
Thank you

---

### Post by mc4man on 2011-10-17
> **wildmanne39 said:**
> I have to download 11.10 again and install it in virtualbox.

I have to get off for a little while, I will be back as soon as I can.
Thank you
When you do try cube again - at least here & for many others the 'flashing' makes unusable

---

### Post by wildmanne39 on 2011-10-17
Hi mc4man, I actually already had the cube setup and it is working good, I just wanted to experiment with it in virtualbox and not my production machine.

I have 11.10 installed in virtualbox now and almost were I can test it, but I am very busy in networking right now trying to help with wireless issues.

As you can see the only thing I have not had time to fix is my conky.

I hope to make an updated page for the cube guide I wrote for 11.04 to include 11.10, it is a lot easier to set up in 11.10, but there may be some bugs showing up for some people.
Thank you

---

### Post by PaulInBHC on 2011-10-18
I just had the same problem as the first page when clicking prefs in ccsm. Hope the fix works.

---

### Post by dFlyer on 2011-10-18
depends on how far you want to go. If you just want to work with the launch bar you may have some success, if your looking for the cube and other enhancements I really don't know.

---

### Post by wildmanne39 on 2011-10-18
Hi lovinglinux, ccsm was not as responsive as I would have liked, in virtualbox I enabled wobbly windows and then I had to log out and back in because compiz became slow.

Then I disabled grab handles and grid and everything seems to be working ok, like I said it all works on my production machine but many people are having mixed results.

I have a quad core with a nvidia card almost 4 years old now, that is just to give you an idea of what it is working on but I am like you I believe, there are some issue that still need to be worked out.
Thank you

---

### Post by lovinglinux on 2011-10-18
> **wildmanne39 said:**
> Hi lovinglinux, ccsm was not as responsive as I would have liked, in virtualbox I enabled wobbly windows and then I had to log out and back in because compiz became slow.

Then I disabled grab handles and grid and everything seems to be working ok, like I said it all works on my production machine but many people are having mixed results.

I have a quad core with a nvidia card almost 4 years old now, that is just to give you an idea of what it is working on but I am like you I believe, there are some issue that still need to be worked out.
Thank you

I have a dual core with nVidia 7300GT, which is a cheap card.

I have disabled gran handles, wobbly and snapping windows. Is working fine now. However, changing settings still cause troubles.

I tried to play a game using Steam and performance was poor compared to 11.04, except if I log in using Unity 2D.

---

### Post by lovinglinux on 2011-10-18
Just tried version 173 of nVidia driver and I was able to enable Wobbly. It also crashed compiz, but restored it much faster.

I don't know yet if the original problem is still present.

---

### Post by wildmanne39 on 2011-10-18
Hi
> Just tried version 173 of nVidia driver and I was able to enable Wobbly. It also crashed compiz, but restored it much faster.

I have to use the 173 driver anything else and mine is unresponsive.

Also with nvidia and ati cards you need to do this for better performance if Sync to Vblank is checked in the nvidia settings manager.

I get better performance by setting the refresh rate to 60 in ccsm.
[http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)
Thank you

---

### Post by lovinglinux on 2011-10-18
> **wildmanne39 said:**
> Hi


I have to use the 173 driver anything else and mine is unresponsive.

Also with nvidia and ati cards you need to do this for better performance if Sync to Vblank is checked in the nvidia settings manager.

I get better performance by setting the refresh rate to 60 in ccsm.
[http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)
Thank you

Thanks. That did the trick for Steam games performance. No need to log into Unity 2D anymore.

---

### Post by wildmanne39 on 2011-10-18
Hi lovinglinux, your welcome!

---

