---
title: "Touchpad likes to stop working"
date: 2011-12-12
forum: New to Ubuntu
---

### Post by juniord2016 on 2011-12-12
Dear Helpers
    I have experienced the most annoying problem in the entire world which is indeed, on the topic. After loging in to my laptop for around 1-5 minutes I will suddenly find out that my touchpad no longer works. When I say 'not work', I literally mean 'not work'. No clicks, no moves, cursor freezes, nothing.  I need this to be solved, I use it in school everyday and I can't wait for the ten times login process to run. I'm using the newest version of ubuntu and all programs are updated to their limits. I thank you in advance for those of you who are trying to help me. This must be fixed. My kernel is in the latest version as well. Mouse works fine, just the touchpad is not working. My laptop's old so if you think that is the reason please tell me so. Thank again

    Regards
    Junior

---

### Post by jonnyboysmithy on 2011-12-12
A bit off topic but if your running the latest ubuntu. That would mean 11.10, on my old laptop it goes slow. Doesn't it for you?

---

### Post by ptoche on 2011-12-12
You'll need to tell us more about your  system, i.e. version, touchapd type, etc.

I have the occasional freeze of the touchpad on my system, Kubuntu 11.10 with synaptics touchpad, clean install, it happens every time 1) I connect or disconnect the laptop on my HP but not on my Lenovo (not sure what the touchap model is, must look into it), 2) I launch gnome-commander or Krusader, no problem with Dolphin or midnight commander... I don't need to restart the computer, just logging out and in again "fixes" it.

---

### Post by juniord2016 on 2011-12-13
Hello
    My touchpad is a synaptics touchpad. I thought I mentioned before as well that I only need to logout. when I reach the login screen, it works again

---

### Post by pierreyy on 2011-12-13
hey

 you have a  bug thats pretty common in 11.10
 open the terminal and enter this code 

```
synclient TouchpadOff=0
``` 

enjoy and dont forget to mark as solved!

---

### Post by juniord2016 on 2011-12-14
Dear pierrey
    I thank you so much for helping me, I will try test it for a day and if it works well, I will mark it as solved.

    Regards
    Junior

---

### Post by Momof9Blessings on 2012-01-05
I had an update a few minutes ago and had to do this again.... will this be a regular occurance of having to fix after updates???

---

### Post by MarjaE on 2012-01-23
Also affects Alps touchpad with Alps patch in 11.04.

---

### Post by olamina on 2012-04-02
Thanks! This worked like a charm for me too!

---

### Post by ageofsteam on 2012-09-12
Thank you.  My new laptop has been having this problem, and I was on the verge of getting rid of it, thinking that it was broken.  :(  

After entering this code, it works like a charm!  No more desperately TAB + arrows navigating! ^_^

---

