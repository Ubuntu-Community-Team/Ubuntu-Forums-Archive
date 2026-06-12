---
title: "[SOLVED] Hardy Update (nvidia driver works but screen res is RESetted each time I log"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by maramot on 2008-05-12
After I finally managed to install my proprietary nvidia drivers (turned out I just had to use the newer hardy kernel in menu.lst and suddenly configuration through nvidia-settings became available) on the hardy upgraded from gutsy, I now have a problem with my profile's resolution being reset every time I log into my profile.

I open nvidia-settings and change the resolution to 1680x1050. I write the settings to xorg.conf. Everything is great until I restart or log out and log in again -> my resolution is always returned to 800x600. It's not a horrible pain but it gets very irritating to set up your resolution every time, especially when you know it shouldn't be like that.

A friend of mine who tried ubuntu told me that he had the same problem with hardy on his own laptop. He ended up returning to windows, so he doesn't have a solution either.

What's interesting and may be of help in solving this is that when I created a new profile to use for playing music in a party (I wanted to restrict access to some directories so I didn't want to use my profile that evening), it was created with a 1680x1050 resolution from the very start, and it didn't need resetting every time I logged on. It had other problems though - like inability to install more keyboard layouts but that's a different subject...

Hell, I ran away from XP exactly to avoid crap like that.. I wonder if anyone actually tested this release or one day they just renamed the beta to TLS and declared we're good to go.

---

### Post by alienexplorers on 2008-05-12
when you use nvidia-settings do you start it with gksudo, If not nvidia-settings will not save your settings.

---

### Post by sailor2001 on 2008-05-12
go direct to the files.    /usr/share/applications/screen & graffics

---

### Post by maramot on 2008-05-12
> **alienexplorers said:**
> when you use nvidia-settings do you start it with gksudo, If not nvidia-settings will not save your settings.

I know, I know. I start nvidia-settings through terminal with sudo nvidia-settings. Otheriwse it just says it can't write to the file. What's the difference between sudo and gksudo by the way?

[quote=sailor2001]go direct to the files. /usr/share/applications/screen & graffics[/quote]
Thanks, I'll try this when I get back home.

---

### Post by dublued on 2008-05-12
gksudo is used for gui apps ... i think.

i had the same problem.  i realized that there is a button next to where you change the screen resolution in nvidia-settings.  it says "write to xorg"  or something like that.

so basically make sure you start with gksudo and then once you change to desired settings... write it to xorg.  it should be there next time you restart

---

### Post by hufferd on 2008-05-12
> **dublued said:**
> gksudo is used for gui apps ... i think.

i had the same problem.  i realized that there is a button next to where you change the screen resolution in nvidia-settings.  it says "write to xorg"  or something like that.

so basically make sure you start with gksudo and then once you change to desired settings... write it to xorg.  it should be there next time you restart

Interesting I have had this VERY same issue.  and swept it under the carpet for now.  But I'm going to try this when I get home today 

Thanks
D :)

---

### Post by maramot on 2008-05-12
> **sailor2001 said:**
> go direct to the files.    /usr/share/applications/screen & graffics

if screen & graffics is supposed to be a dir's name I don't have such a dir. In /usr/share/applications/ I only have a bunch of files with .desktop extension and a couple of directories. If there's somewhere where I can edit this, please tell me where. I just lost my wireless today, and I'm on the way to also losing my patience with this whole misunderstanding called "hardy"

---

### Post by Aearenda on 2008-05-12
Take a look at system->preferences->screen resolution - Have you set a lower resolution in there at some stage in the past?

BTW, this is used so that an individual user can change resolution to his/her preference on a system meant for multiple users.

---

### Post by letubenaiah on 2008-05-12
Here is something that talks about the difference between sudo and gksudo:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

> **maramot said:**
>  What's the difference between sudo and gksudo by the way?

---

### Post by sonoma_jack on 2008-05-12
I'm having a similar problem, maybe you guys (and girls) can help me in this thread.

I updated to hardy(8.04) and started getting a crash when loading WoW.  I called in the callstack and they said it had to do with drivers.  I have an nVidia card that came stock with the computer (Dell - Ubuntu ready).  

I'm still new to linux and ubuntu, did the sync or swim thing, had it with mainstream media distro and production, work in the video game industry, and thought this would be the best thing for me to learn and use for future projects. 

Any help?  Been awhile since I got under the hood on this thing, so please type slow...

...thanks!

---

### Post by Aearenda on 2008-05-12
sonoma_jack: that's a bit off-topic for this thread, which is to do with screen resolution changing on login. However, I recommend you take a look here: [https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting)

---

### Post by alienexplorers on 2008-05-12
Can you please list your xorg.conf file here.  Exactly what resolution are you trying to get?

---

### Post by Aearenda on 2008-05-12
I don't think it's an xorg.conf problem, since the extra 'party' user gets the right resolution all the time.

BTW, 'screens & graphics' was the name of a Gutsy config tool for xorg.conf, but it is deprecated in Hardy as the new Xorg has changed and the tool can produce invalid configurations.

---

### Post by maramot on 2008-05-12
> **Aearenda said:**
> Take a look at system->preferences->screen resolution - Have you set a lower resolution in there at some stage in the past?

BTW, this is used so that an individual user can change resolution to his/her preference on a system meant for multiple users.

You absolutely nailed it here. I just went to the applet and set the resolution from 800x600 to 1680x1050 and it survived an x server restart, then a reboot without a hint of the previous problem. I guess sometimes you forget the obvious things. But who would suppose that changes made by nvidia-settings won't affect the other applet. Shouldn't they both read their settings from the same place? Drats!

Anyway, my thanks for helping me with this. Now I have the wireless to get operational again...  By the way, something I just noticed -- the hardware information applet crashes every time I try to start it. I can't get any info from it neither can I report it because, well I have no internet connection while in ubuntu.

---

### Post by alienexplorers on 2008-05-12
Please mark your thread as solved if everything is working OK.

---

### Post by sonoma_jack on 2008-05-12
> **Aearenda said:**
> sonoma_jack: that's a bit off-topic for this thread, which is to do with screen resolution changing on login. However, I recommend you take a look here: [https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting)

Aearenda, I'm having a problem starting a new thread.  I grabbed EnvyNG, installed the driver and still getting the same problem.

---

### Post by Aearenda on 2008-05-12
Sonoma_jack: To start a new thread, you go to the forum level (eg [http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326) for this forum, or click on the forum name near the top of this page) and open the 'Thread Tools' menu in red on the right, and choose 'Post a new thread'. That should get you going.

You need to get help from someone with WoW experience and Nvidia -  I have Nvidia but not WoW. Make the thread title meaningful, such as 'Need help with NVIDIA and WoW crashing' so that someone who has had that problem thinks 'I can help this guy'.

The 'Multimedia & Video' forum ([http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334)) or the 'Wine' forum ([http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)) might be helpful.

---

