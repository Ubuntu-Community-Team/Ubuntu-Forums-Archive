---
title: "Astronomy Photo of the Day Wallpaper"
date: 2008-01-26
forum: Programming Talk
---

### Post by acvwJosh on 2008-01-26
Hello!  I posted this in[ another thread]("http://ubuntuforums.org/showthread.php?t=459912"), but I thought that it was a lot more applicable to this forum.  The idea was to take the picture from [this website]("http://antwrp.gsfc.nasa.gov/apod/astropix.html"), download it automatically every day, and set it to my wallpaper.  I wrote a small shell script to do this, that I wanted to share.  It's my first script, so I'd definitely like criticism and suggestions.  I've got the script in a folder in my home folder called .wallpaper, and it runs every morning via a crontab entry.  Let me know what you think!

```
#!/bin/bash

# download image from apod site
wget -A.jpg -R.txt -r -l1 --no-parent -nH http://antwrp.gsfc.nasa.gov/apod/astropix.html

# move image from obscure folder to main folder, rename image
find ./apod -name "*.jpg" | while read line ; do
	mv "$line" "wallpaper.jpg"
done

# set image to wallpaper
gconftool-2 -t string -s /desktop/gnome/background/picture_filename "blank.jpg"
gconftool-2 -t string -s /desktop/gnome/background/picture_filename "/home/josh/.wallpaper/wallpaper.jpg"
gconftool-2 -t string -s /desktop/gnome/background/picture_options "zoom"
```

---

### Post by Peyton on 2008-01-26
Creative!

---

### Post by LaRoza on 2008-01-26
Neat. Although I never use wallpapers, that is very cool.

---

### Post by sisyphus1978 on 2009-11-01
Any idea why I can't get crontab to run this script? Works fine from terminal? I even tried gnome-scheduler (after trying really hard to get it working) but still. The script seems to download the image but doesn't change the backdrop.

---

### Post by diesch on 2009-11-01
A way to do the download without the need to move the file around:

```
wget -q -O ~/.wallpaper/wallpaper.jpg "http://antwrp.gsfc.nasa.gov/apod/$(wget -q -O- http://antwrp.gsfc.nasa.gov/apod/astropix.html|grep -B1 '^<IMG SRC'|awk -F\" '/^<a href/ {print $2}')"
```

---

### Post by diesch on 2009-11-01
> **sisyphus1978 said:**
> Any idea why I can't get crontab to run this script? Works fine from terminal? I even tried gnome-scheduler (after trying really hard to get it working) but still. The script seems to download the image but doesn't change the backdrop.

When started from cron it can not connect to you Gnome sessions's GConf server so it can't change the backdrop.

---

### Post by sisyphus1978 on 2009-11-01
So how do I solve this exactly?

/and here was me thinking I was a geek with conkyrc and nanorc...

---

### Post by diesch on 2009-11-01
One way is to use a script that periodically gets the new wallpaper and at that to your Gnome session:

```

#!/bin/sh

sleep_until(){
 s=$((`date +%s --date "$*"` - `date +%s`))
 if [ $s -ge 0 ]; then
   sleep $s;
 fi
}

FILE=~/.wallpaper/wallpaper.jpg

wget  -q -O "$FILE" "http://antwrp.gsfc.nasa.gov/apod/$(wget -q -O- http://antwrp.gsfc.nasa.gov/apod/astropix.html|grep -B1 '^<IMG SRC'|awk -F\" '/^<a href/ {print $2}')"

gconftool-2 -t string -s /desktop/gnome/background/picture_filename "$FILE"
gconftool-2 -t string -s /desktop/gnome/background/picture_options "zoom"

sleep_until tomorrow
exec $0

```

---

### Post by sisyphus1978 on 2009-11-01
Thanks for all the scripts, but I'd more like to understand why crontab doesn't finish what I can do in the terminal and how to fix it? I can run crontab -e and I understand the commands, but I don't get why it doesn't change the desktop picture.  The OP says they used the original script with a crontab entry. How does that work?

Am I missing something obvious here?

---

### Post by diesch on 2009-11-01
If  [FONT=monospace][/FONT]~/.wallpaper/wallpaper.jpg already is your current wallpaper it works with cron as Gnome reloads the wallpaper when then corresponding file is modified. You don't need the gconftool stuff in that case.

---

### Post by sisyphus1978 on 2009-11-02
> If ~/.wallpaper/wallpaper.jpg already is your current wallpaper it works with cron as Gnome reloads the wallpaper when then corresponding file is modified. You don't need the gconftool stuff in that case.

That helped. As the script was downloading the jpg, I just set it as my desktop and crontab updated it the next time. 

Phew, that was hard, but I've learnt some, so it's all good.

---

### Post by sisyphus1978 on 2009-11-06
Okay. I am just not succeeding with this, and since changing the desktop picture really shouldn't be hard (not compared to the raid, the networking, xbmc) I am frustrated that I can't get it to work.

It all works fine if I'm logged in. But when I log out it spazzs out and doesn't stick with the wallpaper set (which I guess is ~/wallpaper.jpg. Now if I set ~/wallpaper.jpg as the desktop, then crontab changes the picture fine. But like I say, when I logout and back in, it's not sticking and doesn't work.

h e l p :)

---

### Post by diesch on 2009-11-06
If the wallpaper gets set to something else after login you have some other software running that changes the wallpaper.

What does
```
gconftool-2 -g /desktop/gnome/background/picture_filename
```
print before logout and after login?

---

### Post by sisyphus1978 on 2009-11-06
Thanks for the command. It's hard for me to replicate the behaviour (since I try and get it working manually). I guess I'll see what happens tomorrow and investigate further if it continues to fail...(or I guess more correctly if I continue to fail)...

---

