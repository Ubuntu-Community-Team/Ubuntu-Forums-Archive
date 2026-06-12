---
title: "Gnome 3 Wallpaper Changer"
date: 2011-12-06
forum: Programming Talk
---

### Post by mareser on 2011-12-06
Hi everybody,

I'd like to share with you a small bash script that sets a random picture as your background in Gnome 3.
You'll want to set the wallpaper_dir variable after the license to the directory containing your wallpapers.

I let cron execute this script every thirty minutes; you might add a line to your crontab to do the same by issuing this command in a terminal (after editing the path to the script):
```
sudo sh -c "echo \*/30 \* \* \* \* $USER bash $HOME/edit/this/path/change_wallpaper_gnome3.sh >> /etc/crontab"
```I'm happy to hear your feedback. :)

---

### Post by lisati on 2011-12-06
Thread closed, duplicate of [http://ubuntuforums.org/showthread.php?t=1891780](http://ubuntuforums.org/showthread.php?t=1891780)

---

