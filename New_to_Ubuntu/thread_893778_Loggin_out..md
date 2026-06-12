---
title: "Loggin out."
date: 2008-08-18
forum: New to Ubuntu
---

### Post by ghostier on 2008-08-18
Hi. Whenever I try to log out it shows a terminal instead of the log in menu. by the way. My log in menu is that of xubuntu instead of ubuntu. I tried switching it back using login menu manager but it doesnt work.

---

### Post by boblemur on 2008-08-18
what do you mean by, wont work??

run:

```
gksudo gdmsetup
```

try and change it, and then tell me what the error is.

make sure that in gdmsetup you click the little radio button over the left hand side, i find that its a little misleading when you just click it and select it, because it hasn't actually changed it.

---

### Post by cariboo on 2008-08-18
Have you got xdm installed? If not it is available in the repositories. This should give a graphical login and logout. IF you just want to leave things the way the are, you  can type:

```
sudo halt
```

or

```
sudo shutdown -h now
```

To shut down the computer.

---

### Post by ghostier on 2008-08-20
boblemur- I get this error when i run that command:
You might be using a different display manager, such as KDM (KDE Display Manager), CDE login (dtlogin), or XDM. If you wish to use this feature, then your system will need to be configured to use GDM instead.

---

### Post by ghostier on 2008-08-21
same problem still occuring. loggin out doesnt give me graphical interface.

---

### Post by ghostier on 2008-08-21
bump... still having this problem. Its extremely annoying.

---

### Post by ghostier on 2008-09-04
bump..

---

### Post by SuperSonic4 on 2008-09-04
what does typing *startx* do once you've logged in terminal?

---

### Post by ghostier on 2008-09-04
Error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.

---

### Post by Cheesehead on 2008-09-04
By 'Terminal', you mean a text login prompt or '$'? Or do you mean you see all the boot messages again?

For *today*:
If you're only logging out, and intend to log back in - then log out normally, then restart your X-server session with CTRL-ALT-BACKSPACE. That should take you back to your login prompt.

If you're powering off, close your apps and then open a Terminal and use the command 'sudo poweroff'

If you really feel like trying to track down the problem, you can...but it's probably not worth the effort for a couple weeks.

8.10 is coming soon; the problem may disappear on it's own when you upgrade...or you might wind up doing a fresh install for unrelated reasons anyway. Only if you upgrade successfully *and* the problem doesn't go away do you really need to track it down.

---

