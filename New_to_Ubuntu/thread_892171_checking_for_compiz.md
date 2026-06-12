---
title: "checking for compiz"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by firsttimeubuntero on 2008-08-16
[http://www.makeuseof.com/tag/check-if-compiz-will-run-well-on-your-linux-box-with-compiz-check/](http://www.makeuseof.com/tag/check-if-compiz-will-run-well-on-your-linux-box-with-compiz-check/)

I'm trying to use that link to check if my computer can run compiz, I'm just starting with Ubuntu so I was following the instructions on that link, but then I ran into a problem, it mentions to go to the terminal and type chmod +x compiz-check,I've done that and pressed enter, and I get an error message, then I tried typing chmod +x compiz-check and then ./compiz-check pressed enter but still nothing happens. Can anyone point me in the right direction as to how to enter these commands in the terminal? I'm not sure if they should be entered in 2 different lines or if just in one line.

---

### Post by tamoneya on 2008-08-16
can you type : "ls -l" for us

---

### Post by firsttimeubuntero on 2008-08-16
> **tamoneya said:**
> can you type : "ls -l" for us
I obtained a list, what exactly should I be looking for?

---

### Post by tamoneya on 2008-08-16
can we see the list.  Copy it with ctrl-alt-c and then paste into the forums with ctrl-v

---

### Post by ad_267 on 2008-08-16
You should be looking for that file called "compiz-check"

If it isn't in your home directory then you need to use "cd path/to/directory" to change into the directory where it is before running those commands.

---

### Post by firsttimeubuntero on 2008-08-16
> **tamoneya said:**
> can we see the list.  Copy it with ctrl-alt-c and then paste into the forums with ctrl-v

[IMG]http://i271.photobucket.com/albums/jj125/julio84photos/Screenshot-carloscarlos-laptop.png[/IMG]

---

### Post by ad_267 on 2008-08-16
Where did you download the script to? It isn't in your home directory obviously.

> (1) Download this file and put it in your home directory (ie, /home/username/).

If you have it in a different directory like in ~/Desktop, you can use "cd Desktop" to change to that directory.

---

### Post by tamoneya on 2008-08-16
ywah i see the problem.  type```
cd Desktop
```Then type the commands detailed in the howto

---

### Post by firsttimeubuntero on 2008-08-17
oh man it seems I can't run it :(

[IMG]http://i271.photobucket.com/albums/jj125/julio84photos/Screenshot-carloscarlos-laptop-Desk.png[/IMG]

what a shame

---

### Post by overdrank on 2008-08-17
You may have a look here
[http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

### Post by jualin on 2008-08-17
why don't you try running it either way. I have a laptop with an ATI chip and even though sometimes I get some weird screen errors, it runs pretty neat.

---

