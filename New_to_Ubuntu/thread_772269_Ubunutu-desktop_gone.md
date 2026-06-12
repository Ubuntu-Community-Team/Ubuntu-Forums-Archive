---
title: "Ubunutu-desktop gone"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by anuban on 2008-04-28
I was running Evolution and suddenly my machine stopped responding.  I did a hard reset.  After that I don't see anything on my desktop.  Desktop wallpaper is intact, besides that I don't see the two bars, any icon, nothing.  I don't see anything except a wallpaper.
When I run in Failsafe mode, everything works fine.
I am not sure what I need to do run my machine as usual.
I am running a clean install Hardy with dual boot Vista on a Dell Inspiron 1505.
Please help.

---

### Post by elpichi on 2008-04-28
This old trick should do the trick if you didn't uninstall your desktop environment.

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

warning This resets all your settings to default

but before you do this give it a restart to the computer and see if it fixes itself.

---

### Post by Ub1476 on 2008-04-28
I believe that hard freeze is due to a kernel bug..

Press alt+f2 and run "gnome-panel".

---

### Post by Google Spider on 2008-04-28
<want to delete this post>

---

### Post by redbob on 2008-04-28
Anuban, your diagnostic is not so clear. Since you can't get anything in GUI, I recommend you to log by line-command (Ctrl-Alt-F1) and take a look in you syslog> nano /var/log/syslog. This already happened to me, it was DNS name issue, but I don't believe it's the same on you.

---

### Post by anuban on 2008-04-28
> **elpichi said:**
> This old trick should do the trick if you didn't uninstall your desktop environment.

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```warning This resets all your settings to default

but before you do this give it a restart to the computer and see if it fixes itself.


I have done restart several times.
I tried solving the issues using Recovery mode but that didn't help.
I tried changing the session, but only Failsafe mode works.

One more thing might help, my keyboard shortcuts are working, e.g. CTRL+ALT+DEL bring the quit menu and let me shutdown/restart the machine.  Except that nothing works unless I know how to access terminal and run the application with command line.

I will try using the above command you mentioned.

Thanks

---

### Post by anuban on 2008-04-28
Got the trick:

[LIST]
[*] Press CTRL+ALT+F2
[*] Login and password
[*] sudo apt-get remove gnome-panel
[*] sudo apt-get install gnome-panel
[*] sudo apt-get install ubuntu-desktop.
[*] Restart...
[/LIST]
 everything should be fine.:)

---

### Post by joshzam on 2008-08-09
> **anuban said:**
> Got the trick:

[LIST]
[*] Press CTRL+ALT+F2
[*] Login and password
[*] sudo apt-get remove gnome-panel
[*] sudo apt-get install gnome-panel
[*] sudo apt-get install ubuntu-desktop.
[*] Restart...
[/LIST]
 everything should be fine.:)

I was very eager to try this as NOTHING else I have found on these forums have helped and I have the same problem as the original poster... and I'm sorry to say that this didn't work for me either :(

Thanks for the suggestion and now let's see if anyone else can help us out. There appear to be a lot of people with this same problem...

---

### Post by anuban on 2008-08-10
> **joshzam said:**
> I was very eager to try this as NOTHING else I have found on these forums have helped and I have the same problem as the original poster... and I'm sorry to say that this didn't work for me either :(

Thanks for the suggestion and now let's see if anyone else can help us out. There appear to be a lot of people with this same problem...

I think I got a better way of resolving this problem.
Login with GNOME Ubuntu Desktop (3rd or 4th option) when you boot.
Go to your Home folder.
Delete 'gnome2' and 'gnome-private' folders.
Reboot your system with default settings on.

You should be all set.

Hope it works for you.
Thanks
Anurag Bansal

---

