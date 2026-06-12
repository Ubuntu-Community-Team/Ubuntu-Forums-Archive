---
title: "apache notify script"
date: 2008-05-10
forum: Programming Talk
---

### Post by tronica on 2008-05-10
Im pretty new to the bash scripting scene, but willing to learn, one thing that has been presented to me for a project is to have popups for data that enters into the apache access log and error log. I though i might be able to use it for this and use like zenity or notify-send. Im just not sure on how to have zenity or the other one poll the logs. any ideas? i just need a starting point. Thanks.

---

### Post by tronica on 2008-05-10
heres what i come up with but not really what im after, im using zenity for now:

```
tail -f /var/log/apache2/access.log & tail -f /var/log/apache2/access.log | zenity --title "Apache Log Viewer" --text-info --width 1024 --height 800 
```

is there a way to replace zenity with notify-send so i could have popups instead?

---

