---
title: "Lost desktop"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by philk949 on 2008-07-31
Hi
After re-installing alsa sound modules, I have lost my desktop and now have only a black and white command line screen, even after running: sudo apt-get install gdm ubuntu-desktop.
Does anyone have any suggestions please?

Phil

---

### Post by eightmillion on 2008-07-31
Let's make sure everything still works first. Run this command at the terminal.
> sudo /etc/init.d/gdm restart

---

### Post by hyper_ch on 2008-07-31
if that doesn't work, you could move your gnome settings to another folder and then login again and things should be restored to default...

---

### Post by rockerphil on 2008-07-31
simply run this command

startx

that should start your X server, but preffereabely if you're accustomed to the graphical login, then i'd go with:

sudo /etc/init.d/gdm start

as suggested

Phil

---

### Post by philk949 on 2008-07-31
Thank you all for your replies and, doubtless, workable solutions. But I'm afraid (this is embarrassing) I lost patience with the spare computer I was using to post to the forum - constant freezes when it wasn't crawling along at glacial speed, and re-installed Ubuntu (with 248 updates!).

At least I have some very useful, helpful codes for future use. Thanks again.

Phil

---

