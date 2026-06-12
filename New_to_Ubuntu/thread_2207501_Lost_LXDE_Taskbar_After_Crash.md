---
title: "Lost LXDE Taskbar After Crash"
date: 2014-02-23
forum: New to Ubuntu
---

### Post by zxasqw12 on 2014-02-23
Migrating from XP, very new user, less than a month.

Installed Lubuntu 13.10 from live CD, no problems

Attempted to customize the menu ["start button"] with a different image. System subsequently crashed and I received crash dialog box.

System hung following crash and did not restore. Restarted; system booted normally, proceeded through splash screen, but displayed background (wallpaper) only

Can right click and bring up desktop preferences dialog but nothing else. Keyboard/mouse function normally; I suspect that the system is fully functional except for this one issue

Any possible recovery options short of reinstalling? Appreciate any assistance, can attempt to provide additional info if necessary for a fix- thanks very much

---

### Post by llamabr on 2014-02-23
Sorry -- I'm not sure what you're asking.  What is it that you're trying to recover?

---

### Post by zxasqw12 on 2014-02-24
Thanks for the reply

After boot completes, I am presented with wallpaper only- no taskbar, menu, digital clock, or anything else. There is no GUI at all.

---

### Post by Rex Bouwense on 2014-02-24
Can you re-launch the panel by entering
```
lxpanelctl restart
```
into the terminal?
Alternatively, can you re-boot and log-in as a guest?  Is the LXPanel there?

---

### Post by zxasqw12 on 2014-02-24
Thanks for the reply Rex- really appreciate the assistance

 After reading your post I realized that there must be some sort of Ubuntu equivalent of "safe mode" and a little Googling quickly turned it up. After booting into recovery mode, I chose "drop to to shell prompt" and entered [HTML]lxpanelctl restart[/HTML] as you suggested. That returned the following: [HTML]Cant connect to display (null)[/HTML]

I set the system to autologin at bootup so I am not presented with a guest login unless I can do so via a terminal. I will investigate further. In the meantime, does that spark any further ideas/suggestions? Thanks

---

### Post by zxasqw12 on 2014-02-24
Edit: ```
lxpanel config
``` returns ```
Gtk - WARNING **: cannot open display
```

---

### Post by Rex Bouwense on 2014-02-24
Try
```
killall lxpanel && lxpanel --profile Lubuntu
```
Did you attempt to modify 
.config/lxpanel/Lubuntu/panels
at any time?  I believe that is the file that controls the LXPanel.  It should not be manually editted unless you are sure you know what you are doing.  Grave results can occur.

---

### Post by Rex Bouwense on 2014-02-24
I found this on Ask Ubuntu
[http://askubuntu.com/questions/64631/how-to-restore-the-default-lubuntu-panel/64664#64664](http://askubuntu.com/questions/64631/how-to-restore-the-default-lubuntu-panel/64664#64664)
Not sure if it is still valid since it appears to be for 12.04.
Another thought has crossed my mind while I was doing some research.  Have you minimized the panel (even by accident)?  Place the cursor over the bottom of your screen and see if the panel appears.

---

### Post by zxasqw12 on 2014-02-24
The "killall" command returned:

```
lxpanel: no process found
```

I can assure you that no manual editing was involved- I just wanted to see a different image on the LXDE menu button. My entire Linux experience totals about three weeks of trying out different distros and I generally like to try and gain some remote degree of familiarity with the OS before I start mucking about and making life difficult for myself :)

---

### Post by Rex Bouwense on 2014-02-24
I can screw up a distro in less than 30 minutes if I work really hard at it.  If you haven't got anything important on the computer, you could always re-install.  That takes 20-30 minutes plus whatever updates are out there and I imagine there are quite a few since the new version (which is the first and only LTS for Lubuntu) comes out in April of this year.
Alternatively you can use Synaptic Package Manager to re-install LXPanel.  Just open it up and search for LXPanel.  Mark the installed versions for re-installation and then apply.

---

### Post by zxasqw12 on 2014-02-24
Yeah, I thought that perhaps I minimized a panel (I'm only running one) but no such luck. Unfortunately, the string at the link you mentioned also threw an error.

 It wouldn't be the end of the world if I had to reinstall and booting off the live CD works fine so I wouldn't expect to have any further problems.

But before I throw in the towel, I'd like to try your suggestion to use Synaptic Package Manager to re-install LXPanel. Here's the problem- I have virtually no command line experience except for the tutorials I've just started reading (where I've learned pwd and such). The only similar frame of reference I have for this is my limited experience working in DOS which was a long, looong time ago. Could I possibly impose on you to point me in a direction where I could get some help running Synaptic in a terminal? 

 I want you to know that I really appreciate the time you've spent helping me work through this

---

### Post by Rex Bouwense on 2014-02-24
Ctrl + Alt + t will give you a terminal.  Once it appears, enter
```
sudo synaptic
```
You will be asked for your password.  Enter it.  The curser will not move as you enter your password.  Once you have done that hit enter.  That should launch the Synaptic Package Manager.

---

### Post by zxasqw12 on 2014-02-25
You know, I must have screwed this up amazingly well. 

Ctrl + Alt + t refused to bring up a terminal. I switched to recovery mode and got the shell prompt. Running sudo synaptic from there returned a Gtk - WARNING **: message.

 So I went back to the live CD. I was happy to find a partial reinstall option on the live CD so I ran it. Unfortunately, I received a "some packages did not install properly" message upon completion. Rebooted and got the same thing again- no GUI at all. So now I'm back to a complete reinstall.

We can file this under "good learning experience." Thanks again for all your efforts

---

### Post by Rex Bouwense on 2014-02-25
Sorry it didn't work out for you but glad that you are up and running.  I would like to invite you to drop by the LXDE Forum
[http://forum.lxde.org/index.php](http://forum.lxde.org/index.php)
Lubuntu uses LXDE.
I have screwed up distros so badly that I have had to re-install.  You are correct in that it is a learning experience.

---

