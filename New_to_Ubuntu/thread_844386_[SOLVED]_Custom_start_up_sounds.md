---
title: "[SOLVED] Custom start up sounds???"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by hvac3901 on 2008-06-29
Has anyone else tried to do this?

I tried to do it NOOB style, got a sound bite, dropped it in the folder /usr/share/sounds and selected it in; /system/administration/login window

And what do you know nothing, no sound. the file is of the same length 6 seconds give or take as the Ubuntu login sound clip, and the same file extension what gives, anyone know?

---

### Post by Bodsda on 2008-06-29
You may not have necessary permissions to play the file. in a terminal type

```
sudo chmod a+x /usr/share/sounds/YourFile
```

replacing 'YourFile' with the actual name of your sound file

---

### Post by sayakb on 2008-06-29
Since we run gdmsetup (Sys->Admin->Login Window) as superuser, there shouldn't be any permission issue I guess (or should there be?). Btw, why don't you just select the sound file from any alternate location (for example, put it in your home folder and select it from there?)

---

### Post by hvac3901 on 2008-06-29
Permission settings read the same, i used ,gksu nautilus to pull off the file move.

i must admit to not knowing what gdmsetup is. 

Humm thats embarrassing, i do now.

---

### Post by sayakb on 2008-06-29
gdmsetup is the Login Window settings prompt.. (System->Administration->Login Window)
Anyway, why do you want to keep the file within /usr/share/sounds?
Probably this is bad advise, but try:
```
sudo chown *yourusername* /usr/sounds
```If this fails, don't forget to revert this back to:
```
sudo chown root /usr/sounds
```

But shouldn't you just keep the file within the home folder or ny other folder of yours and selecting it at gdmsetup? Whats keeping you from doing that? ;)

---

### Post by billgoldberg on 2008-06-29
Simply to go to "system -> preferences -> sound" and in the drop down menu, you can select a different sound, or install your own sound (needs to be .wav).

If you need a converter, try "sound converter" in the repo's.

---

### Post by hvac3901 on 2008-06-29
> **LinuxIsInnovation said:**
> gdmsetup is the Login Window settings prompt.. (System->Administration->Login Window)
Anyway, why do you want to keep the file within /usr/share/sounds?
Probably this is bad advise, but try:
```
sudo chown *yourusername* /usr/sounds
```If this fails, don't forget to revert this back to:
```
sudo chown root /usr/sounds
```

But shouldn't you just keep the file within the home folder or ny other folder of yours and selecting it at gdmsetup? Whats keeping you from doing that? ;)

:oops: apparently nothing. but i cannot get this file to play. and because of my poor explanation i may have confused you all.

I want the UBUNTU drum beat, with the hyper cricket chips (the lion king intro) gone in exchange for one of my own. I don't think that there is a selection i gdmsetup for that.

Beginning to think i should rename a file as ubuntu.wav and drop it there to see if that works. I think i was obsessed with that folder because i assume it is where the OS looks for that sound clip. 

Did that make a bit more sense? sorry for the confusion and thank you all for the advice all of you.

---

### Post by ubername on 2008-06-29
Are you asking for the sound that Ubuntu makes when displaying the login screen ( a short 'pit a pat') or the longer sound when you have identified and authenticated your user ( the longer 'lion king' thing you describe) ?

/usr/share/sounds/question.wav is the default for the former in hardy heron, you can change it in Administration > Login Window > Accessibility tab, Login Screen Ready option.

Hope that helps but it sounds like you've had a good look around so sorry if this is teaching grandmothers to suck eggs.

---

### Post by hvac3901 on 2008-06-29
> **ubername said:**
> Are you asking for the sound that Ubuntu makes when displaying the login screen ( a short 'pit a pat') or the longer sound when you have identified and authenticated your user ( the longer 'lion king' thing you describe) ?

/usr/share/sounds/question.wav is the default for the former in hardy heron, you can change it in Administration > Login Window > Accessibility tab, Login Screen Ready option.

Hope that helps but it sounds like you've had a good look around so sorry if this is teaching grandmothers to suck eggs.

not the short pit pat, thanks for confirming where it was set at. I will keep at it, and come back if i have more trouble.

---

### Post by sayakb on 2008-06-29
> **hvac3901 said:**
> :oops: apparently nothing. but i cannot get this file to play. and because of my poor explanation i may have confused you all.

I want the UBUNTU drum beat, with the hyper cricket chips (the lion king intro) gone in exchange for one of my own. I don't think that there is a selection i gdmsetup for that.

Beginning to think i should rename a file as ubuntu.wav and drop it there to see if that works. I think i was obsessed with that folder because i assume it is where the OS looks for that sound clip. 

Did that make a bit more sense? sorry for the confusion and thank you all for the advice all of you.

Okay.. I though that you want to modify the drumbeat for "Login window ready" as ubername said. Anyway, then just goto System->Preferences->Sound and click on Sounds tab and expand the **Log in:** drop-menu and select **Select sound file...** option and point it to your sound file.

---

### Post by hvac3901 on 2008-06-29
LinuxIs...

yes that is the one i want to change, the long drum beat. I replaced the "login window is ready" default with my sound clip, and it didn't play :( so that motivated this thread. I tested the clip and it plays in a media player, and after some time (and without me changing the selection), Heron went ahead and played the "Lion King" anyway. So i began to think the file is being snatched from somewhere else, or is relevant to a name, and not a selection in GDM

Thanks

---

### Post by kender42 on 2008-07-26
I've been having the same sort of problem. I want to change the sound that happens after you authenticate, but no matter what I put as the sound, it will only allow me to play the login.wav sound even after I have changed it in System -> Preferences -> Sound. It also won't allow me to play the sound in the sounds tab to test it. However the sound I want will play in any of the media players. Yes, the sound I want to change it to is a .wav file

---

### Post by hvac3901 on 2008-07-26
> **kender42 said:**
> I've been having the same sort of problem. I want to change the sound that happens after you authenticate, but no matter what I put as the sound, it will only allow me to play the login.wav sound even after I have changed it in System -> Preferences -> Sound. It also won't allow me to play the sound in the sounds tab to test it. However the sound I want will play in any of the media players. Yes, the sound I want to change it to is a .wav file

I never was able to fix that thing. I made a switch to Xubuntu for a short while, found it to be very difficult to modify, and loaded back all the software i use, over the last few weeks. I may decide to attack this bothersome sound again semeday, if you figure out how to make it stop please lend me a clue i would be much appreciative of it. thanks

---

### Post by hvac3901 on 2008-07-30
> **kender42 said:**
> I've been having the same sort of problem. I want to change the sound that happens after you authenticate, but no matter what I put as the sound, it will only allow me to play the login.wav sound even after I have changed it in System -> Preferences -> Sound. It also won't allow me to play the sound in the sounds tab to test it. However the sound I want will play in any of the media players. Yes, the sound I want to change it to is a .wav file

Got mine working, i dont know why there are two places (aparently) for the same setting. but if you go to System - Preferences - Sounds. you will find the setting that makes the start-up sound change. :)

---

