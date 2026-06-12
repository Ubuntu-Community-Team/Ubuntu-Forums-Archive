---
title: "Script with location variable"
date: 2013-06-03
forum: New to Ubuntu
---

### Post by thesoundman20 on 2013-06-03
I am trying to edit a script so that you can execute it from your desktop but make it work for multiple users. here is my code: 

```

[Desktop Entry]Type=Application
Encoding=UTF-8
Version=1.0
Name=No Name
Name[en_US]=Rescapp
Comment[en_US]=Rescapp - Rescue Tool
Comment=Rescapp - Rescue Tool
Exec=gksu python /home/joshholmes/Desktop/rescapp/rescapp.py
X-GNOME-Autostart-enabled=true

```

which works for my user but what im trying to do is set the USER as a variable "/home/USER/Destkop/". how can i go about doing this? I have read about setting $PATH or $HOME. but considering that i am trying to set it up so that anyone can use it, i wont know what the users name will be i cant set $PATH. im a beginner when it comes to scripting, and im willing to learn.

---

### Post by ajgreeny on 2013-06-03
You're almost there.

The variable for a user is, perhaps not surprisingly, $USER, so I think /home/$USER/Desktop/ etc etc, should work for you.

---

### Post by thesoundman20 on 2013-06-03
i tried that. did not work unfortunately.

---

### Post by ajgreeny on 2013-06-06
I don't know if it is of any consequence, but the file you show is not strictly a script but a .desktop desktop-configuration file, or launcher.

If you wish to do the activity with a shell-script try something like ```
#!/bin/bash
<command to run>
```
I have no idea if it will work using the $USER variable, particularly if it requires root permissions as yours does, but it's worth a try.

I am also not sure if you need **gksu** or **sudo** for a python command; I do not use python other than in other scripts etc etc, that call for it, but I thought it was really a command-line utility, not a GUI, therefore should be **sudo**, not **gksu**.

---

### Post by monkeybrain2012 on 2013-06-06
> **ajgreeny said:**
> You're almost there.

The variable for a user is, perhaps not surprisingly, $USER, so I think /home/$USER/Desktop/ etc etc, should work for you.

Shouldn't it just be $HOME/Desktop?

---

### Post by deadflowr on 2013-06-06
What are the permissions for your home folder and the path to the file that will be executed?

---

