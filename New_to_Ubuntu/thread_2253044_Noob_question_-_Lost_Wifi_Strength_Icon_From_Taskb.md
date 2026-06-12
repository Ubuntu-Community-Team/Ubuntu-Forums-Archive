---
title: "Noob question - Lost Wifi Strength Icon From Taskbar; How do I Bring it Back? (14.10)"
date: 2014-11-16
forum: New to Ubuntu
---

### Post by ktc2 on 2014-11-16
I clicked something wrong and lost my wifi strength indicator from the taskbar. I consulted google, and this is apparently a common problem. I've found instructions on how I'd fix it on previous versions of Ubuntu (something like system settings > preferences > sessions) but the options and menus don't seem to be the same in 14.10. Thank you for any help or advice! 

KTC

---

### Post by grahammechanical on 2014-11-16
Ubuntu has had the Unity user interface for more than 3 years. I have not seen menus in Ubuntu for all that time, especially System Settings>Preferences. Except the menus that drop down from an application indicator. I wonder if you are using Ubuntu or a flavour of Ubuntu that still uses menus.

If you are indeed using Ubuntu + Unity then this command might work for you

```
killall unity-panel-service
```

The unity panel service should restart automatically. If it does not then try this command

```
/usr/lib/unity/unity-panel-service
```

Of course, those commands are only useful if we are running Ubuntu + Unity.

Regards.

---

### Post by ktc2 on 2014-11-16
Menu was not the correct term for me to use (hey, I said I was a noob :-) ). I do not have a dropdown menu. I do have Unity user interface.

 I suppose my question should have been, how do I access the function I'm looking for (bring little wifi icon back to it's home at on the far upper right of the screen, on the far left of the other icons there) through Unity user interface? All the info I've been able to find through the forums and google, seem to give instructions for the old drop-down style menu (I suppose I was using the word "menu" in a more general sense, of any directory of any kind. Bad me.)

"System settings" doesn't appear to have the same options, as the old drop-down menus. What do?

---

