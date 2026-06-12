---
title: "Nvidia X-server settings help."
date: 2008-08-05
forum: New to Ubuntu
---

### Post by elise1030 on 2008-08-05
I've been trying to figure out how to get Nvidia X-server settings remember what image sharpening setting I use. When I log out or shut down, then boot back into Ubuntu, it defaults back to 0.00.

Is there a way to make X-server remember what image sharpening I use?

---

### Post by Presto123 on 2008-08-05
Make sure to save to "X Configuration File" before you exit. If it gives you an error stating that the file is not found, you can save it as a new file.

---

### Post by elise1030 on 2008-08-05
It tells me it's unable to remove the old Xconfig backup file. How do I fix that?

---

### Post by Nepherte on 2008-08-06
You probably don't have the rights to save the file. You should run the program with sudo privileges.

---

### Post by Troll_the_Great on 2008-08-06
Hit Alt F2 and type:
```
gksu nvidia-settings
```
Now you have administrator rights.Save your configuration and you're done.
Cheers!

---

### Post by fatality_uk on 2008-08-06
> **elise1030 said:**
> I've been trying to figure out how to get Nvidia X-server settings remember what image sharpening setting I use. When I log out or shut down, then boot back into Ubuntu, it defaults back to 0.00.

Is there a way to make X-server remember what image sharpening I use?

Start the nvidia-settings as sudo using this command:
> gksudo nvidia-settings

This will allow nvidia-settings to overwrite the config file when applying changes

---

### Post by kpkeerthi on 2008-08-06
> **elise1030 said:**
> I've been trying to figure out how to get Nvidia X-server settings remember what image sharpening setting I use. When I log out or shut down, then boot back into Ubuntu, it defaults back to 0.00.

Is there a way to make X-server remember what image sharpening I use?

No need to use gksudo to change the settings in the GUI. Just be sure to add ```
nvidia-settings -l
``` to the list of startup programs. Any changes you make in the GUI will be loaded at startup.

---

