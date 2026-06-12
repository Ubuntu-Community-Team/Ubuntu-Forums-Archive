---
title: "Remove drum noise on system Startup"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by Palu on 2008-10-13
Hi

I am trying to get rid of the bum-bum (drum sound) at system startup (when you type in username--not the longer sound called "login sound"). I can't find a setting for it, and it is frustrating.

Current Settings...
System > Pref > Sound: Sounds Tab, all sounds set to "No Sound"; There is no setting for startup sound (only login sound).

I found the sound file (usr/share/sounds/question.wav) but it said I needed to be root to destroy / rename it. I wasn't sure what to do to do that either, but I'd love to find a way to do this in the GUI.

Thanks! :popcorn:

---

### Post by jemate18 on 2008-10-13
> **Palu said:**
> Hi

I am trying to get rid of the bum-bum (drum sound) at system startup (when you type in username--not the longer sound called "login sound"). I can't find a setting for it, and it is frustrating.

Current Settings...
System > Pref > Sound: Sounds Tab, all sounds set to "No Sound"; There is no setting for startup sound (only login sound).

I found the sound file (usr/share/sounds/question.wav) but it said I needed to be root to destroy / rename it. I wasn't sure what to do to do that either, but I'd love to find a way to do this in the GUI.

Thanks! :popcorn:


gO TO 
System -> Preference -> Sound

Once there, click the sound tab (Next to devices)

then on the last entry, (Log In) select No SOund.

That should do it and remove the drum sound

---

### Post by jemate18 on 2008-10-13
don't delete the file........

---

### Post by drs305 on 2008-10-13
> **Palu said:**
> I found the sound file (usr/share/sounds/question.wav) but it said I needed to be root to destroy / rename it. I wasn't sure what to do to do that either, but I'd love to find a way to do this in the GUI.

Thanks! :popcorn:

I can't access my notes at the moment, but if you are sure that is the sound file you want to stop playing, and you have turned off all sounds in the sounds tabs mentioned above, you can run this command:
```
sudo mv /usr/share/sounds/question.wav /usr/share/sounds/question.wav.original
```

To restore:
```
sudo mv /usr/share/sounds/question.wav.original /usr/share/sounds/question.wav
```

When you run a 'sudo' command you will be asked for your password. You will not see it as you type. Hit ENTER when you have input your password.

---

### Post by kukibird1 on 2008-10-14
> **Palu said:**
> Hi

I am trying to get rid of the bum-bum (drum sound) at system startup (when you type in username--not the longer sound called "login sound"). I can't find a setting for it, and it is frustrating.

Current Settings...
System > Pref > Sound: Sounds Tab, all sounds set to "No Sound"; There is no setting for startup sound (only login sound).

I found the sound file (usr/share/sounds/question.wav) but it said I needed to be root to destroy / rename it. I wasn't sure what to do to do that either, but I'd love to find a way to do this in the GUI.

Thanks! :popcorn:
Go to System > Administration > Login Window > Accessibility and uncheck Login screen ready.

---

