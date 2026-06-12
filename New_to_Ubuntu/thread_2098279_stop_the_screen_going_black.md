---
title: "stop the screen going black?"
date: 2012-12-26
forum: New to Ubuntu
---

### Post by Old-un on 2012-12-26
How can i stop the screen from going black every 10 minutes or so?

---

### Post by squakie on 2012-12-26
Click on the Unity home icon, then type "system settings".  As you are typing it will eventually show it in the selection area, so you don't have to type the entire string.

Click on the system settings icon that shows in the selection area.

Click "Brightness and Lock".

Change the time out on powering down the screen.

---

### Post by sahabcse on 2012-12-26
Run the below command in terminal

gsettings set org.gnome.desktop.screensaver idle-activation-enabled false

---

