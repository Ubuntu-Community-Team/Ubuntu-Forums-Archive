---
title: "Lubunutu - Restore the 'power' icon on the panel"
date: 2013-11-15
forum: New to Ubuntu
---

### Post by Gregg_Coleshill on 2013-11-15
Hi,

I have been fiddling with my fathers lubuntu box out of curiosity and managed to remove the 'power' icon from the right of the panel. As far as I can tell this is the only graphical way of shutting the machine down and I don't fancy trying to explain to my 75 yr old computer illiterate father how to use cli so does anyone know how to bring it back, I have searched and searched through all the menus and dialogs I can find and have so far come up with nothing!!

Thanks.

---

### Post by Rex Bouwense on 2013-11-15
Boy are you in trouble.  However, there is another way to graphically shut down the computer.  You can always go to main menu->Logout and then choose Shutdown.
Also have you tried to relaunch the LXPanel?
Just put ```
lxpanelctl restart
``` in the terminal.
If that doesn't work create a new user.  That should give you a new LXPanel.  You can move any data that he has created to the new user.

Hold the presses.
I knew I had saved this somewhere.  Look here.
[https://help.ubuntu.com/community/Lubuntu/Boot_Install_Login#Shutdown_Button_is_missing_from_LXPanel.2C_how_can_I_add_it.3F](https://help.ubuntu.com/community/Lubuntu/Boot_Install_Login#Shutdown_Button_is_missing_from_LXPanel.2C_how_can_I_add_it.3F)
That should solve your problem.

---

### Post by Gregg_Coleshill on 2013-11-15
Rex you have just saved me a serious amount of time in teaching him 'new fangled things' thankyou sooooo much, that link is perfect. Happy days :)

---

### Post by Rex Bouwense on 2013-11-15
You are welcome.  Us old guys have to stick together.

---

