---
title: "HOWTO: Email Placemarks, Images, and View from Google Earth"
date: 2007-05-16
forum: Outdated Tutorials &amp; Tips
---

### Post by fakie_flip on 2007-05-16
If you have [Google Earth]("http://earth.google.com/") running under Linux, you may want to show your friends/family something that you find. In GE, you can go to File>Email> and click on "Email Placemark", "Email View", or "Email Image." GE will try to send an email with your web browser (probably Firefox). That will not work. However you can get Evolution email client to work. First setup Evolution to work if you have not already. Now open up a gnome-terminal and type this command.

```
export BROWSER=evolution
```

After doing that, GE will send emails with Evolution. However this is not permanent. As soon as you log out and reboot, this won't work anymore. To make it permanent. you must add something to your user's .bashrc. First create a backup of the .bashrc.

```
cp -v ~/.bashrc ~/.bashrc_backup
echo 'BROWSER=evolution' | tee -a ~/.bashrc
```

---

