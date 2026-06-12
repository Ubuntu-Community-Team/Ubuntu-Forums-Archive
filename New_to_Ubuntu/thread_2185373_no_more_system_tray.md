---
title: "no more system tray"
date: 2013-11-02
forum: New to Ubuntu
---

### Post by ornothaloapq on 2013-11-02
I just upgraded to 12.10 from 12.04 and when I boot up I get the error message: no system tray was found. All the icons on the left of the screen are not loading. I cannot open any files either. Has any one else had this happen?

---

### Post by whitesmith on 2013-11-02
Do you have an HP printer? If you do, the HP tray may be the system tray. I don't see a need for it unless you're into fancy footwork. You'll have to show us exactly what happens when you try to open a file.

---

### Post by ornothaloapq on 2013-11-02
I do have an HP printer but I can't click the any icons to open any programs because the system tray won't load. Files are opening now but they are missing the close/maximize/minimize buttons.I get the following error messages in this order:

No system tray detected in this system
Unable to start,exiting


One PDF fid open and then I got this:
The application compiz has closed unexpectedly

---

### Post by DuckHook on 2013-11-02
I don't do upgrades--just fresh installs--so may not be of much help here, but Unity may be on the fritz.

It's harder to reset Unity after 12.04, so try the following via either <Ctrl>+<Alt>+<F1> or <Ctrl>+<Alt>+<t>:```
sudo apt-get update
``````
sudo apt-get install dconf-tools
``````
dconf reset -f /org/compiz/
``````
setsid unity
```Let us know how it goes.

---

### Post by ornothaloapq on 2013-11-02
How should I go about opening the terminal? I tried Ctrl T but it didn't work

---

### Post by whitesmith on 2013-11-02
CTRL+Alt+T

---

### Post by ornothaloapq on 2013-11-02
Ok I put all that into the terminal. The reset dcof didn't do anything. The setsid unity turned up the following

Unity-panel-service: no process found
Compiz (core) - error: Another window manager is already running on screen: 0
Compiz (core) - info: stopping plugin: core
Compiz (core) - info: unloading plugin: core

---

### Post by ornothaloapq on 2013-11-02
I aslo can't switch to between windows (1-4) like before

---

### Post by ornothaloapq on 2013-11-02
i decided to switch to Gnome mode instead of unity at login. it works well enough but i still got that error message about no system tray found.

---

### Post by whitesmith on 2013-11-02
Somehow, as the installation progressed, some serious devilry hit the fan. See if you can back-rev to 12.04 LTS. It's good until 2017, whereas 1210 (a normal release) hits EOL in July, 2013. LTSes are much safer than their younger cousins. What they gain in glitter they lose in reliability and all-around quality. And quality is key, isn't it? Of what value is some hot new number with a gorgeous face if it doesn't work quite right? I'm a 12.04 LTS guy on my production machine--and will be until the next drop of an LTS. Yes, I know, you need my verbosity like a hole in your head, but I sincerely hope I've helped. Good luck to you.

---

### Post by DuckHook on 2013-11-02
> **whitesmith said:**
> See if you can back-rev to 12.04 LTS. It's good until 2017, whereas 1210 (a normal release) hits EOL in July, 2013. LTSes are much safer than their younger cousins. What they gain in glitter they lose in reliability and all-around quality. And quality is key, isn't it?I actually agree with this sentiment 99%. I run 12.04 on my production boxes too. But I do tinker with the newer stuff on experimental boxes out of curiosity, and I can see that some people need the latest and greatest to solve HW issues. 12.10 is actually EOL April 2014, but that's just 6 months away.

@ornothaloapq

You may want to try installing a pristine 13.04, since this should be where you are going anyway. 13.10 just came out and is too new and buggy, so I don't recommend it yet. 12.10 is already seeing it's due date around the corner. Or, you can follow whitesmith's recommendation and reinstall 12.04. Frankly, this last is what I would do, and then rest easy knowing that you have stability until 2017, or alternatively, wait for 14.04 which will also be LTS.

I'm out of ideas on getting Unity working for you unless someone else jumps in. I don't know enough about the newer ways of doing things because most of my knowledge is still based on 12.04.

---

