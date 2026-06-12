---
title: "No sound"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by kayfes on 2008-06-13
I have disabled my onboard sound via bios.  I have a sound blaster card that I want to use and am plugged into how do I get it to play sound?

---

### Post by iaculallad on 2008-06-13
You don't have to disable the built-in sound card through your BIOS, you can just change the sound card priority in your Ubuntu box.

-Enable first your internal sound card through your BIOS

-On your terminal:

```
asoundconf list
```

-Select your external sound card name

```
asoundconf set-default-card external_sound_card_name_from_asoundconf_list
```

That could do the trick.

---

### Post by kayfes on 2008-06-13
No luck.  I didn't enable the onboard card again don't know if that makes a difference but I don't see why I would enable it if im not using it.

---

### Post by iaculallad on 2008-06-13
What about just running the command **asoundconf list** on your terminal and taking note of the value. Run:

```
asoundconf set-default-card external_sound_card_name_from_asoundconf_list
```

even without enabling you on-board sound. Still the same?

---

### Post by kayfes on 2008-06-13
No sound.  

I found this and from what i can tell since I have a sound blaster audigy se I am not going to get sound.

[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)

Oh well back to crappy sound with onboard.

---

### Post by kayfes on 2008-06-13
this is what i get running as sudo 

steven@steven-desktop:~$ sudo asoundconf set-default-card external_sound_card_name_from_asoundconf_list
[sudo] password for steven: 
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

steven@steven-desktop:~$

---

### Post by iaculallad on 2008-06-13
Before going back to you on-board sound, Had you seen this Ubuntu [SoundBlaster]("https://help.ubuntu.com/community/HowToConfigureSoundBlasterAudigySEinBreezy") page?

---

### Post by Chr0mis on 2008-06-13
Have you tried using Pavucontrol? 
Run: 
sudo apt-get install pavucontrol

And then press alt+F2 and type: 
pavucontrol


Go to output devices
Locate your soundcard and right-click on it to set it as default. :)

---

