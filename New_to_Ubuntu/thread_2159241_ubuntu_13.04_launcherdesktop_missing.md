---
title: "ubuntu 13.04 launcher/desktop missing"
date: 2013-07-02
forum: New to Ubuntu
---

### Post by okkie on 2013-07-02
I have nothing on my desktop 13.04 and can not get to the launcher or any menue. I get firefox using 'sudo firefox' in terminal.
Can someone please tell me how to get my launcher back on the desktop

---

### Post by grahammechanical on 2013-07-02
To reset Compiz use
```
dconf reset -f /org/compiz/
```
to reset Unity use
```
setsid unity
```
To change to another video driver - right click the desktop and select Change Desktop Background. That will get you to a link to System Settings. Open Software & Updates and open the Additional Drivers tab. Give the utility time to find some drivers for and then experiment.

Regards.

---

