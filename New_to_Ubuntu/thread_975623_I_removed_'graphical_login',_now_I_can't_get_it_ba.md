---
title: "I removed 'graphical login', now I can't get it back"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by BetterSense on 2008-11-08
I wanted to bypass the gnome graphical 'enter your password' screen on my laptop cause I thought it would be faster and in case I just wanted to boot and cp a file or listen to an mp3 I wouldn't have to start x. 

I went to System->Administration->Services and I unchecked 'graphical login'. But when I rebooted and startx'd, my user switcher applet is gone! So I can't have a guest account. So I guess, to get my user switcher and guest account back, I want the graphical login back, but there is no way to get it back because **both the Services window AND the 'Unlock' button are greyed out.** So there is no way I can unlock the Services dialog anymore. I tried using sudo and  gksudo to launch services-admin, and it prompts me for my password when I do that, but when the dialog launches it's still grey and the unlock button is still grey. Is this a bug?

My computer works and has no graphical welcome screen thing, but I no longer have a user switcher applet or guest account and I would like those things back.

---

### Post by fooman on 2008-11-08
when you reboot....instead of startx,  try:

```
sudo /etc/init.d/gdm start
```

see if that gets you to a normal login screen w/user switcher.

---

### Post by bodhi.zazen on 2008-11-08
How did you start X ?

exit your x session , back to the command line. Then start GDM

```
sudo /etc/init.d/gdm start
```

Log in and all should be well. Re-activate gdm in services :twisted:

---

### Post by hictio on 2008-11-08
Also, try this on a Terminal:
```

sudo update-rc.d -f gdm defaults

```

That's how I re-enable gdm, if I need it for something, I usually turn it off, and setup a [high resolution console as well](http://oesediez.blogspot.com/2008/09/ubuntu-high-resolution-console.html).

---

### Post by BetterSense on 2008-11-08
> **fooman said:**
> when you reboot....instead of startx,  try:

```
sudo /etc/init.d/gdm start
```

see if that gets you to a normal login screen w/user switcher.

The user switcher I'm talking about isn't really part of the login screen, but an applet on the gnome 'panel'. I don't know why getting rid of GDM killed it, but it must be part of gdm somehow. Is there any way I can get it back? I don't *want* a graphical login, but I do want my fast-user-switcher-applet.

---

### Post by fooman on 2008-11-08
after you login with

```
sudo /etc/init.d/gdm start
```

right click on the panel and choose "add to panel".  scroll down to "user switcher" highlight it and click the add button.

does that work?

---

### Post by BetterSense on 2008-11-08
Yes, now I have the guest session ability back. But am I forced to have the graphical login in order to have it? I shall try re-disabling graphical login, and try to add it to the panel then.


EDIT: I tried to add it to the panel with 'graphical login' unchecked, but it instantly warns me that it dies unexpectedly and asks if I want to reload it. Reloading it does nothing as it simply dies again. Very strange to me that I can't have one without the other.

---

### Post by bodhi.zazen on 2008-11-08
GDM is more then the graphical log in screen and switch user is a function of gdm.

So yes, if you want to use this feature you need to start GDM.

---

### Post by BetterSense on 2008-11-10
I guess I'll have to do without the user-switcher then. I really enjoy not having a graphical login because it's faster.

---

