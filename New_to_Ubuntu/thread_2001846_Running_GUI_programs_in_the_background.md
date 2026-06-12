---
title: "Running GUI programs in the background"
date: 2012-06-11
forum: New to Ubuntu
---

### Post by joetait on 2012-06-11
Hi

I know that there are various ways of running programs from the terminal "in the background" - i.e. so that they never notify of what they are doing, only notify you in case of an error, only give you the output etc.

I was wondering if there was a way to do such things with a program that is operated via a GUI. My understanding is that it won't be, but I thought I would check in case.

In particular, I have a program to change wallpapers, and ideally I would have it start at login, and never see it unless it is doing stuff, in which case a notification is fine. So it would operate exactly as Ubuntu One, for example, can/does do for me.

Thanks :)

---

### Post by spikoley on 2012-06-11
Which program are you trying to run?

---

### Post by deadflowr on 2012-06-11
Well, whenever you add a program to the startup applications list, it creates a .desktop file in the folder /home/username/.config/autostart.
You can gedit the file, and usually the file has a line that say nodisplay=false(meaning, yes display), try changing it to true and see what happens.

---

### Post by joetait on 2012-06-12
> **spikoley said:**
> Which program are you trying to run?

The program is called wallch. 

I have changed to autostart file, will report back when it has been restarted

Thanks

---

### Post by spikoley on 2012-06-13
I was thinking on the same lines of deadflowr, but I wanted to try it before suggesting it.  Well... I tried it and it works.  It looks like the *Hidden=true* is the mime type that controls the display of an application.  I tested it with NoDisplay=true and it did not work.  

Just change it to *Hidden=true* and you should be good to go!

/home/*UserName*/.config/autostart/wallch.desktop

```

[Desktop Entry]
Type=Application
Exec=/usr/bin/wallch
Hidden=true
NoDisplay=true
X-GNOME-Autostart-enabled=true
Name[en_US]=Wallch
Name=Wallch
Comment[en_US]=Wallch Wallpaper Changer
Comment=Wallch Wallpaper Changer


```

---

### Post by joetait on 2012-06-14
> **spikoley said:**
> I was thinking on the same lines of deadflowr, but I wanted to try it before suggesting it.  Well... I tried it and it works.  It looks like the *Hidden=true* is the mime type that controls the display of an application.  I tested it with NoDisplay=true and it did not work.  

Just change it to *Hidden=true* and you should be good to go!

/home/*UserName*/.config/autostart/wallch.desktop

```

[Desktop Entry]
Type=Application
Exec=/usr/bin/wallch
Hidden=true
NoDisplay=true
X-GNOME-Autostart-enabled=true
Name[en_US]=Wallch
Name=Wallch
Comment[en_US]=Wallch Wallpaper Changer
Comment=Wallch Wallpaper Changer


```


Brilliant, thank you very much :)

Do you know/think that this would be the case for most programs?

---

### Post by spikoley on 2012-06-14
> **joetait said:**
> Brilliant, thank you very much :)

Do you know/think that this would be the case for most programs?

I do not know, but I think this will work with most programs.  It is the first time I have ever messed with it.

Make sure you go to Thread Tools and mark this thread as Solved.

---

### Post by hakermania on 2012-06-16
Hey! Hold on a minute :P
Wallch, on its Preferences window, under Startup, has options so as to start on startup without showing up!

I can help, just make it a bit clear what you need to do (i am one of the developers) :)

---

### Post by joetait on 2012-06-29
Thanks very much - I don't know why I missed this before. Should the time lapse before changing be the same as whatever it was left as last log in?

---

### Post by hakermania on 2012-06-29
> **joetait said:**
> Thanks very much - I don't know why I missed this before. Should the time lapse before changing be the same as whatever it was left as last log in?

The timeout will be the same as the last time you closed wallch!

---

