---
title: "Skype"
date: 2013-01-16
forum: New to Ubuntu
---

### Post by Charlie24 on 2013-01-16
I have just built a pc running Ubuntu 12.10. I have been trying to set up Skype . The icon appears on the home screen but when I open it all contacts show as blocked and there appears no way to unblock them. I have tried to delete the application but can find no way to do so. When I try to open again I get the message" another instance of Skype is open". I am lost , can anyone help please.

---

### Post by d4m1r on 2013-01-16
Are you logging in through your Skype account or MSN account?

Do uninstall skype, go to the software centre, search for skype, and you can uninstall it from there. I also recommend deleting the .Skype folder inside your home users directory to fully remove it.

---

### Post by Charlie24 on 2013-01-16
Thanks I have tried both but it does not show up in the Software centre. I have searched in Installed software and every other way I know but nothing seems to work. I am logging in through my Skype account.

---

### Post by Jonathan Precise on 2013-08-26
Try:

```
sudo apt-get update
sudo apt-get remove --purge skype
sudo apt-get install skype
```

That should fix it.

---

