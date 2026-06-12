---
title: "Restoring the top panel"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by Kirjon on 2008-05-05
Hey guys

I'm new to linux and currently enjoying it :) However, in all my wisdom, I deleted the top panel of the desktop (The one with the menus, battery life, time etc) and I have no idea how to restore it. If anybody could tell me how, that would be greatly appreciated :)

Thanks, Kirjon

---

### Post by Oldsoldier2003 on 2008-05-05
> **Kirjon said:**
> Hey guys

I'm new to linux and currently enjoying it :) However, in all my wisdom, I deleted the top panel of the desktop (The one with the menus, battery life, time etc) and I have no idea how to restore it. If anybody could tell me how, that would be greatly appreciated :)

Thanks, Kirjon
right click your existing panel and select new panel
you can the change its properties and put it as a top panel
you'll have to rebuild it though.

the things you want for sure are menubar, quit and notifcation area. from there have fun customizing :)

---

### Post by tamoneya on 2008-05-05
What Oldsoldier2003 said should work out perfectly.
However, if you some how managed to delete both of them you can get them back but hitting alt-F2 and the typing ```
gnome-panel
```

---

### Post by Oldsoldier2003 on 2008-05-05
> **tamoneya said:**
> What Oldsoldier2003 said should work out perfectly.
However, if you some how managed to delete both of them you can get them back but hitting alt-F2 and the typing ```
gnome-panel
```

yep:) only reason i didnt mention gnome-panel is he still had a panel .

---

### Post by Spoken on 2008-05-05
> **tamoneya said:**
> What Oldsoldier2003 said should work out perfectly.
However, if you some how managed to delete both of them you can get them back but hitting alt-F2 and the typing ```
gnome-panel
```

yep

---

### Post by tamoneya on 2008-05-05
he never explicitly said if he still had a bottom panel and I wanted to make the post as complete as possivle incase someone else comes along who has deleted both.  Your way works fine 90% of the time.

---

### Post by Kirjon on 2008-05-05
Sorry I should have mentioned that I don't have a bottom panel. Typing in "gnome-panel" gives me this:
cannot open display:
Run 'gnome-panel --help' to see a full list of available command line options

Any ideas? Thanks :)

---

### Post by tamoneya on 2008-05-05
can you type gnome-panel into terminal instead of alt-F2 so that we can possibly get a little more of an error message.

---

### Post by Kirjon on 2008-05-05
> **tamoneya said:**
> can you type gnome-panel into terminal instead of alt-F2 so that we can possibly get a little more of an error message.

Could you please tell me how to access the terminal through my current options? I have a blank dektop with absolutely nothing on it. I can right click to create a folder and launcher, thats it.

---

### Post by Oldsoldier2003 on 2008-05-05
> **Kirjon said:**
> Could you please tell me how to access the terminal through my current options? I have a blank dektop with absolutely nothing on it. I can right click to create a folder and launcher, thats it.

Alt+F2 gnome-terminal or make a launcher for gnome-terminal

---

### Post by Helios38 on 2008-05-05
press ALT + F2



enter

```
xterm
```


you will have a terminal open. how this is just my guess. my complete random guess, but perhaps u could try

```
sudo apt-get install gnome-panel
```

---

### Post by Kirjon on 2008-05-05
Ok typing in "gnome-panel" worked flawlessy this time, restoring both my panels to default. Thanks so much guys :)

---

