---
title: "lack of concatination"
date: 2010-07-25
forum: Programming Talk
---

### Post by JohnnyC35 on 2010-07-25
I've been trying to write a small script to change wallpaper randomly, I'll prolly put it in cron so it happens every x minutes. I tried not to re-invent the wheel but drapes, wallpaper-tray, and wally seem to have an issue with either Peppermint One, or Openbox.
My end result I am hoping for is something like feh --bg-scale && echo /home/john/Wallpaper/ && (ls |grep .*.* -n | grep $[($RANDOM % ($[$(ls|grep .*.* -c)-1]+1))+1]\: | sed -e 's/^.:/ /' | sed -e 's/^..:/ /'| sed -e 's/^...://')

the issue I am having atm is:
> 
echo /home/john/Wallpaper/ && (ls |grep .*.* -n | grep $[($RANDOM % ($[$(ls|grep .*.* -c)-1]+1))+1]\: | sed -e 's/^.:/ /' | sed -e 's/^..:/ /'| sed -e 's/^...://')


right now I am getting
> 
/home/john/Wallpaper/
345427168.jpg

as the output. In my world I would have thought that the && would have stuck /home/... and the jpg output together but newline is getting in the way and I haven't Googled the right answer.

Anyone have thoughts how I can remove the newline from this?
After that I will have it out with feh :)

Thanks in advance :KS

---

### Post by Noccy on 2010-07-25
It will if you change it to "echo -n" to avoid the newline :)

Also, on a side note, if you just collect a list of files you can use the sort command with the -R switch to sort it in a random order:

```
find /home/user/wallpapers -iname "*.jpg" | sort -R | tail -n 1
```

Cheers,
Chris

---

### Post by JohnnyC35 on 2010-07-25
> **Noccy said:**
> It will if you change it to "echo -n" to avoid the newline :)

Also, on a side note, if you just collect a list of files you can use the sort command with the -R switch to sort it in a random order:

```
find /home/user/wallpapers -iname "*.jpg" | sort -R | tail -n 1
```Cheers,
Chris


haha I love how that nice simple line was just thrown out there :)
I've been trying to figure this out for over an hour :)  now to marry it to feh 

Thanks alot Chris :D

---

### Post by JohnnyC35 on 2010-07-25
ya! so now
find /home/john/Wallpaper -iname "*.jpg" | sort -R | tail -n 1 | xargs feh --bg-scale
will let me randomly throw a wallpaper up
I tried cron. it didn't work. so I looked up sleep and found this script

> 
#!/bin/sh
while true;
do
 find /home/john/Wallpaper -iname "*.jpg" | sort -R | tail -n 1 | xargs feh --bg-scale
 sleep 1m
done &
[http://wiki.archlinux.org/index.php/Feh#Random_background_image](http://wiki.archlinux.org/index.php/Feh#Random_background_image)

everything seem to be fine. thanks again.
tying to get it to run automatically. cron doesn't seem to work for me. init.d doesn't either and xinit did't. hmmm
and I can't seem to add automatic services in Peppermint like you can in Gnome Ubuntu...hmm...

---

### Post by Noccy on 2010-07-26
No worries, glad to help :D

What if you change your cron line to something like this:
```
*/5 * * * * DISPLAY=:0.0 /home/john/wallpaperchanger.sh
```

You can also use GConf to set the Gnome wallpaper from the command line :) Take a look at [http://library.gnome.org/admin/system-admin-guide/stable/gconf-9.html.en](http://library.gnome.org/admin/system-admin-guide/stable/gconf-9.html.en). Whatever solution you go for tho, I think you need to specify the display number when it's called from outside your active session (such as from cron which doesn't have the display variable set) :)

---

### Post by JohnnyC35 on 2010-07-26
> **Noccy said:**
> No worries, glad to help :D

What if you change your cron line to something like this:
```
*/5 * * * * DISPLAY=:0.0 /home/john/wallpaperchanger.sh
```You can also use GConf to set the Gnome wallpaper from the command line :) Take a look at [http://library.gnome.org/admin/system-admin-guide/stable/gconf-9.html.en](http://library.gnome.org/admin/system-admin-guide/stable/gconf-9.html.en). Whatever solution you go for tho, I think you need to specify the display number when it's called from outside your active session (such as from cron which doesn't have the display variable set) :)

ah ha! that was the issue. I didn't have the display. I don't think GConf was an issue as I have lxde/openbox but cron works now :) sweet!

---

### Post by Noccy on 2010-07-26
> **JohnnyC35 said:**
> ah ha! that was the issue. I didn't have the display.

Excellent, glad you got it working :D

Good luck with your future scripting adventures :)

---

### Post by ironwolfe on 2010-08-05
I tried the script but I get an error 
xargs: feh: no such file or directory

any ideas?

---

### Post by JohnnyC35 on 2010-08-05
did you change the directory?

find <insert directory here> -iname "*.jpg" | sort -R | tail -n 1 | xargs feh --bg-scale

---

### Post by linux18 on 2010-08-06
sudo apt-get install feh

---

