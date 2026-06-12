---
title: "Question about the chrono command"
date: 2011-12-19
forum: New to Ubuntu
---

### Post by Dan_o on 2011-12-19
Hello,
I've just started playing with Ubuntu as a second boot option, and I've found that I enjoy how much I can do with it. 
Most things I've been able to work out through the Ubuntu documentations and google, but this one's got me. 
I'd like to set ubuntu to automatically start Firefox on Pandora weekday mornings as my alarm. I've found the gnome-open command, and I've found a page describing cron, and I tried to follow it, but got a series of errors that I don't know how to prevent. 
I'd appreciate any help, as I still don't entirely understand Ubuntu. 
Thanks,
Dan

---

### Post by MartijnNL on 2011-12-19
You seem to be using cron as root, where you want to use it as your own user (after all you want Firefox to start at your desktop). You can use the following command for that:

```
crontab -e
```

This opens your personal crontab file in a text-mode text editor (may ask you to select an editor first). Note that using such an editor take some getting used too. You might want to run one (like nano) from the command-line first to get familiar with it first.

You could then add something to the (probably newly created) crontab file like: 

```
00 7 * * 1,2,3,4,5 export DISPLAY=:0 && firefox "www.pandora.com"
```

This will start firefox at 7:00 (00 7) on Monday to Friday (1,2,3,4,5) using [www.pandora.com](www.pandora.com) as the url.

You should preferably not use /etc/crontab for this purpose. (If you do, you should add your username between 1,2,3,4,5 and export.)

---

### Post by Dan_o on 2011-12-22
Thanks MartijnNL,
I got the text editor open, and was able to put in the times, but I can't seem to exit out without deleting the entry. (this is absolute beginner talk, right?)
Also, while I was reading, I came across the "at" command. I got it to accept the commands and list them as jobs, but it's not performing the command on my desktop. how do I tell it that is what I want?
Thanks again,
Dan

---

### Post by Dan_o on 2011-12-22
Ok, I just got the "at" command to work using the export command you typed above. Thanks again MartijnNL!

---

### Post by MartijnNL on 2011-12-22
> **Dan_o said:**
> Thanks MartijnNL,
I got the text editor open, and was able to put in the times, but I can't seem to exit out without deleting the entry. (this is absolute beginner talk, right?)
Also, while I was reading, I came across the "at" command. I got it to accept the commands and list them as jobs, but it's not performing the command on my desktop. how do I tell it that is what I want?
Thanks again,
Dan

You probably need to save before editing. Which editor did you choose?

And as far as I know an 'at' job runs only once, and not every week at the specified time. To get it to do so, you would have to add the 'at' command to a startup script (for your user) or something like that. It might work to put it in 'startup applications' but I'm not sure.

Cron on the other hand does repeat.

---

### Post by Dan_o on 2012-01-10
when I type crontab -e , a screen comes up that allows me to type new commands in. I believe it to be a part of the terminal.
Originally, I didn't understand that "^X" means to type control x to exit. I was looking for a way to save in the terminal menus, but since I didn't find it, started to read the documentation again, and got quite sidetracked. 
So, I eventually came back to try this again, and found that I could exit, but I was getting an error after exiting and saving. Here's another screencap.
Thanks in advance for the continued help.

---

### Post by Dan_o on 2012-01-10
here's the screen where I can edit the crontab.

---

