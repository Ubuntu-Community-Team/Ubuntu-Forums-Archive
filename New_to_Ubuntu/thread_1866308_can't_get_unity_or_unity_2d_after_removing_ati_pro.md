---
title: "can't get unity or unity 2d after removing ati properity drivers"
date: 2011-10-21
forum: New to Ubuntu
---

### Post by Najmudin on 2011-10-21
Hi 
I installed ubuntu 11.10 in my friend laptop which have ati graphic card and installed the ati proprietary drivers after few hours he send me a message saying that he got laggy video experience when playing any video file, so he removed the proprietary drivers ,after rebooting he was not able to get the top panel or the unity launcher in both unity and unity 2d.
when loging in he just gets (file,edit,view,go,bookmarks & help) in the top panel.
I was intending to try to make a recovery to the default driver using the grub menu so i can install the ati driver again and try some workaround for the laggy video.
I tried to hold the shift key or space key while booting but couldn't get the grub menu.
any help will be appreciated.

---

### Post by searchfgold6789 on 2011-10-21
Are you trying to access the Recovery console?
If so, you don't have to get to Grub 2 at all. At the login screen, choose "Recovery" as your session type.

---

### Post by lovinglinux on 2011-10-21
No need to recover. Try CTRL+ALT+F1, login and run these commands:

```

rm -fr ~/.compiz-1/session
rm -f ~/.config/compiz-1/compizconfig/config
sudo reboot
```

If you can't do CTRL+ALT+F1, then just boot from LiveCD and delete **~/.compiz-1/session** and **~/.config/compiz-1/compizconfig/config** from your user home, then reboot.

---

### Post by ArgusVision on 2011-10-21
This may not be a popular answer, but you could re-install the proprietary drivers.

In terminal:```
jockey-gtk
```
You should see a splash screen that says "Searching for Drivers"
Then in the window that follows, you should be able to select the proper driver.

You should also have to enter your password. 

Hope this helps.

---

### Post by waba on 2011-10-23
the same thing just happened to me as the ati drivers were not working well, so i uninstalled the driver.

just tried the second response (rm ~./compiz...) but it didnt seem to work. i will try reinstalling the ati driver as the last post suggests, but ultimately i would like to remove it as it causes my mouse to freeze in one of the corners, as well as not supporting dual screens!

Unfortunatly i cant open a terminal as i only have the top bar, cant find a way to open programs. i tried to type jockey-gtk after pressing ctrl+alt+F1, but ut says gtk cannot be initialised

please help! :D

---

