---
title: "Gnome 3 Wallpaper Changer"
date: 2011-12-06
forum: Programming Talk
---

### Post by mareser on 2011-12-06
Hi everybody,

I wanted to share with you a small bash script that sets a random picture as your background in Gnome 3.
You'll want to set the wallpaper_dir variable after the license to the directory containing your wallpapers.

I let cron execute this script every thirty minutes; you might add a line to your crontab to do the same by issuing this command in a terminal (after editing the path to the script):
```
sudo sh -c "echo \*/30 \* \* \* \* $USER bash $HOME/edit/this/path/change_wallpaper_gnome3.sh >> /etc/crontab"
```I'm happy to hear your feedback. :)

---

### Post by malspa on 2011-12-06
Thanks very much; I'll try this later, as soon as I get a chance!

---

### Post by malspa on 2011-12-19
Thanks for this script, mareser. I got it to work in GNOME Shell in Fedora 16. Here's what I did:

First, dropped some wallpapers in ~/wallpapers. Then, extracted the script to my home directory.

Within the script, edited this line to read:

```
wallpaper_dir="/home/steve/wallpapers/"
```

For the cron job, I used su - to get root access instead of sudo; I set it for 10 minutes instead of 30 minutes; instead of "$USER," I typed "steve," and I used the direct path to my wallpapers directory. So the command I used to add the cron job looked like this:

```
# sh -c "echo \*/10 \* \* \* \* steve bash /home/steve/change_wallpaper_gnome3.sh >> /etc/crontab"
```

---

### Post by mareser on 2011-12-20
Good stuff, malspa. Thanks for testing my script. :)
Not sure why the command for editing crontab didn't work for you (maybe Fedora uses a different version of sudo?) but thanks for posting your solution.

I might point out that one advantage of this script is that it doesn't care if the contents of your wallpaper directory change. So you can add or remove pictures in your wallpaper dir to your heart's content.

---

### Post by malspa on 2011-12-20
> **mareser said:**
> Not sure why the command for editing crontab didn't work for you (maybe Fedora uses a different version of sudo?) but thanks for posting your solution.

Well I'm not sure about the details of sudo in Fedora but the only distros I've used sudo in are Ubuntu (and Kubuntu) and Linux Mint. Otherwise I always use su, so that's what I do when I see commands originally meant for Ubuntu that I want to use on another distro, I use su instead of sudo. For all I know, the command might have worked in Fedora as written, but I didn't try it.

---

### Post by malspa on 2011-12-20
I also edited /etc/crontab as follows (to keep /var/log/cron from filling up):

```
*/10 * * * * steve bash /home/steve/change_wallpaper_gnome3.sh >> /home/steve/change_wallpaper_output.log
```

Not sure if that was the best solution, but I guess it'll do.

Edit: No, I guess that didn't work.

---

