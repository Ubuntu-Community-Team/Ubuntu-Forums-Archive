---
title: "Ubuntu 11.10 - Clear Recent Files - Newbie"
date: 2011-10-22
forum: New to Ubuntu
---

### Post by shotgunxbaby3 on 2011-10-22
Just got the 11.10 upgrade a few days ago and I was wondering if there is an easy way to clear recent files and possibly prevent new ones from showing up. I found this piece of code for terminal to clear files: 

rm ~/.local/share/zeitgeist/activity.sqlite
zeitgeist-daemon --replace

And it works well enough, run it and then I log out and login and recent files are gone. Along with this I found this piece for terminal that is supposed to prevent more recent file posts:

echo -n > ~/.recently-used.xbel
sudo chattr +i .recently-used.xbel

Which did not work at all.

---

### Post by ShodanjoDM on 2011-10-22
Delete the recently-used.xbel file inside ~/.local/share folder.

```
rm ~/.local/share/recently-used.xbel
```

I'm using gnome-shell, btw, and it works wonder. Wish that there's another "gnome 2-ish" way to clear the recent files' list though...

---

### Post by shotgunxbaby3 on 2011-10-22
The gnome shell...that make it similar to 11.04? I have a desktop running 11.04 and it's so simple to clear recent files on that version.

---

### Post by philinux on 2011-10-22
For a gui install these two.

gnome-activity-journal

And the log manager from here.
 [http://www.webupd8.org/2011/05/zeitgeist-activity-log-manager-now.html](http://www.webupd8.org/2011/05/zeitgeist-activity-log-manager-now.html)

---

### Post by ShodanjoDM on 2011-10-22
> **shotgunxbaby3 said:**
> The gnome shell...that make it similar to 11.04? I have a desktop running 11.04 and it's so simple to clear recent files on that version.

Oh, sorry, I run 11.10 on my desktop. But I also used gnome-shell 3.0 in 11.04 though.

---

### Post by ShodanjoDM on 2011-10-22
> **philinux said:**
> For a gui install these two.

gnome-activity-journal

And the log manager from here.
 [http://www.webupd8.org/2011/05/zeitgeist-activity-log-manager-now.html](http://www.webupd8.org/2011/05/zeitgeist-activity-log-manager-now.html)

In my experience, both gnome-activity-journal and the log manager won't clear recent files so I still have to delete the recently-used.xbel file manually.

---

### Post by anjoze on 2012-03-16
Finaly!!

sudo apt-get install activity-log-manager

---

### Post by RicardoPiky on 2012-04-22
I can't be able to stop the recent items but when using

rm ~/.local/share/zeitgeist/activity.sqlite

it erase it for the moment, one way can be to take off the file section of the "Dash Home" 

go to /usr/share/unity/lenses folder and there you will see a folder called files i guess, for caution i move it to my home folder to keep it in case of need.

sudo mv /usr/share/unity/lenses/music /home/("me")/

after this the section is off, try it yourselves.

Thanks and pardon me for my poor english.

It works. and is for Ubuntu 11.10

---

### Post by dimamali on 2012-06-18
> **anjoze said:**
> Finaly!!

sudo apt-get install activity-log-manager


works in 12.04 too.
thummbs up

---

