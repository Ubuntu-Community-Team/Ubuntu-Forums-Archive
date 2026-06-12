---
title: "Blank screen at startup after editing Sessions"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by force-abuser on 2008-08-04
Hi All,

I did a search for this, but couldn't find anything close.

In 8.04 I downloaded and installed emerald, and added a change in Sessions.

I mistakenly typed in "emerald" instead of "emerald --replace" in the command box.

Now when it starts, it doesn't show a login screen, just a blank screen.

Can anybody help? Hope there's a simple solution for this.

Thanks.

---

### Post by appi2012 on 2008-08-04
is the screen just white. If so, try typing your username and password as you normally would, and hit enter. That might get you logged in, and from there, you could try changing what you typed in sessions. Also, are you using CCSM? If so, to set up emerald to start by default, open CCSM. Click on window decoration, and then type emerald --replace in the textbox labeled "command"

---

### Post by tuxxy on 2008-08-04
The session you added called emerald, will have created a file in the directory **/home/username/.config/autostart** just delete the unwanted file if you can.

If you cant access GNOME try pressing CTRL + ALT +F1 to bring up a command line from here you can delete the session you added.

To check the files type;

```
ls /home/username/.config/autostart
```

then

```
sudo rm  /home/username/.config/autostart/filename
```

to delete the unwanted session file.  Becareful when executing the last command, double check you entered the correct path first.

---

### Post by force-abuser on 2008-08-04
Thanks for the quick replies.

Nope... I'm not using CCSM

The screen isn't white, just blank or black. The mouse cursor shows, and "wheel" spins for a few seconds and then the screen goes black. I tried typing in my username and password, but it doesn't do anything.

tuxxy, thanks for the suggestions, I'll give those a try when I can get to my linux box. :)

---

### Post by force-abuser on 2008-08-05
Thank you Tuxxy. 

Your solution was spot on. 

Mark this as problem solved.  :)

---

