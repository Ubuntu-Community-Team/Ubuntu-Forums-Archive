---
title: "I want to turn off my screen when I am not working on my computer."
date: 2013-05-24
forum: New to Ubuntu
---

### Post by gpucho on 2013-05-24
Hello,

I am absolutely new to Ubuntu, and I need someone's advice to solve a problem. 

I need to make sure that my screen turns off 10-20 seconds after I am done working with it. Now, I have tried xset s on > xset s 20 600 > xset dpms 0 0 20 and other combinations that I found throughout the forums. However, even though those parameters work fine for a couple of tries, when I reboot the system, the computer do not retain the settings. I do not watch movies on my computer - maybe I try that later - but at this time, I need to know how to _permanently_ have those values set all the time.

Thanks in advance :D

---

### Post by lethall1 on 2013-05-24
may be you can put those commands in a file, and make it executable on start?

---

### Post by gpucho on 2013-05-24
Thanks! How do I do that?

---

### Post by claracc on 2013-05-25
You can do it easily with the gui through system settings.

What ubuntu release are you running?

In my precise gnome-fallback desktop I go to system settings-->preferences -->control center, then I select brightness and block, and in this window you can select turn off screen when inactive for....and there you select the time, I think the minimum is 1 minute.

---

### Post by HiImTye on 2013-05-25
system > preferences > startup applications
(or in unity type startup intobthe dash and choose it)
then hit the + (or add, I'm not at my pc), then type your commsnd into the box for command, give it a name, viola!

---

### Post by gpucho on 2013-05-28
> **HiImTye said:**
> system > preferences > startup applications
(or in unity type startup intobthe dash and choose it)
then hit the + (or add, I'm not at my pc), then type your commsnd into the box for command, give it a name, viola!



Sorry for not writing any sooner. I had to take some vacations and unplug myself from everything.

I guess I should've written that I am not using any graphics, and that I have to do everything from the terminal. See, I am using this fan-less system that once it is started, I can not change any settings because they have been locked out from the company. And the reason I want to be able to turn the display off permanently, or at least until the touchscreen is touch again, is because the system would be running all the system, and it will end up blowing the board that powers the back-light. 

I've only started to work on it, and I know I could probably make it work, but I wanted to see what experienced Linux users had to say first. 

PS: The system uses Ubuntu 10.04 LTS
[ATTACH=CONFIG]243146[/ATTACH]

---

### Post by Nayab Basha Sayed on 2013-05-28
If you are using Ubuntu 12.04 LTS... then go to "system settings"(available on launcher). In that window under "Personal" Category select "Brightness and Lock". Double Click on that. An option says 'Turn Off Screen When Inactive for'. Selece the minimum time available (No option less than 1 minute).

---

