---
title: "3 Problems"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by TR13 on 2008-05-27
Hi,

Got a bunch of issues... 

1. I have an NVIDIA card and I got it to work at 1440x900. But after I restart the computer it goes back to 1024x768. I ran NVIDIA-settings and tried saving the changes to the xconfig file but it says that it cannot overwrite the xconf.backup file. 

2. I have a System info watermark screenlet running, but when I restart the computer the screenlet does not load I have to go back and restart it from the screenlet manager, the old screenlet i had before comes back. I even tried resetting the screen lets settings but it does not work.

3. Whenever I open a windows it goes behind the top taskbar, I have to Alt+space it and then move it. I tried changing the settings from gconf-editor, I went to app->desktop->natulis->preferences and changed the windows start up position from 1024x768+-75+80 to 1440x900+75+80. But then when I maximized the windows it started blinking.

Thanks...

---

### Post by sdennie on 2008-05-27
1) To save the X settings from nvidia-settings you'll need to start it from the command line:

```

sudo nvidia-settings

```

3) Are you using compiz?  If so:

```

sudo apt-get install compizconfig-settings-manager

```

Got to System->Preferences->Advanced Desktop Effects and make sure the "Place Windows" module is enabled (it will be towards the bottom.

---

