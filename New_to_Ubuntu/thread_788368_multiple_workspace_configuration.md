---
title: "multiple workspace configuration"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by Matt26 on 2008-05-09
is there a way to have an rdesktop session automatically open within a specific workspace in ubuntu 8.04?  i would like to set this up if possible.  thanks.

---

### Post by scragar on 2008-05-09
a combo of sessions(System>Preferences>Sessions -- add startup program) and [devilspie](https://help.ubuntu.com/community/Devilspie) will let you do this.

---

### Post by Matt26 on 2008-05-27
thanks, but i'm having difficulty in figuring out how to locate the proper files for starting up certain programs- for example, i would like to have FireFox, Thunderbird, Pidgin and Nautilus (to my Home folder) to open automatically , but i'm not sure where to locate these items to add them to the startup list.

i noticed the last tab in the Sessions window allows you to have your current session 'remembered' which i assume means that it will open the same applications you currently have open when the system is loaded again.  am i understanding this function correctly?  i have tried using it but not all the applications i have opened when i click the 'remember current session' button will open the next time i start ubuntu, only some- i had FF, Thunderbird, Pidgin and Nautilus opened but when i restarted only the first 3 started.

thanks.

---

### Post by scragar on 2008-05-27
> **Matt26 said:**
> thanks, but i'm having difficulty in figuring out how to locate the proper files for starting up certain programs- for example, i would like to have FireFox, Thunderbird, Pidgin and Nautilus (to my Home folder) to open automatically , but i'm not sure where to locate these items to add them to the startup list.

i noticed the last tab in the Sessions window allows you to have your current session 'remembered' which i assume means that it will open the same applications you currently have open when the system is loaded again.  am i understanding this function correctly?  i have tried using it but not all the applications i have opened when i click the 'remember current session' button will open the next time i start ubuntu, only some- i had FF, Thunderbird, Pidgin and Nautilus opened but when i restarted only the first 3 started.

thanks.nautilus is always running as your desktop, which has been the cause of several problems for people using that feature.

just add the program name in the startup box for command(all lower case).```
nautilus
firefox
thunderbird
pidgin
```

---

### Post by Matt26 on 2008-05-27
> **scragar said:**
> nautilus is always running as your desktop, which has been the cause of several problems for people using that feature.

just add the program name in the startup box for command(all lower case).```
nautilus
firefox
thunderbird
pidgin
```

thanks... sorry i might not have been clear on the Nautilus item (still learning the linux/ubuntu lingo).. i want to have my Home folder open automatically with the other items- is there a way to be that specific?  thanks.

---

### Post by scragar on 2008-05-27
as I said, just add ```
nautilus
```as the command in a session ( system > prefferences > sessions > start up applications > add ) name it whatever you want(just name it something you'll know later, incase you want to remove it or whatever...)

---

