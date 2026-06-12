---
title: "firefox title bar and taskbar disappear"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by Matt26 on 2008-11-18
for some reason whenever i open firefox now (it didn't do this before) or open a link from an email, firefox will shift to a different view mode (like when you press the F11 key) and firefox's title bar (orange bar at the top of the firefox window) and the gnome task bar disappear, and i have to press F11 every time to get it back to normal view again- why does this keep happening and could someone please provide a way to fix this?

thanks.

---

### Post by asgard_command on 2008-11-18
You haven't recently made any changes in Compiz to do with window management have you.

I had this once when the title of my Firefox window was coincidently the same as a window title I had set up in Compiz to have special display behavior applied.

---

### Post by binbash on 2008-11-18
go to compizconfig settings manager, then go to workarounds plugin.Disable legacy fullscreen support

---

### Post by Matt26 on 2008-11-18
> **binbash said:**
> go to compizconfig settings manager, then go to workarounds plugin.Disable legacy fullscreen support

where exactly do i find the compiz settings dialog?  i have looked under System/Preferences and i only see the Appearance option- i just changed the visual effects to extra and it installed the restricted graphics drivers.

---

### Post by Crafty Kisses on 2008-11-18
I've had the same issue but I've solved it. What you need to do is for a temporary fix is press "F11" twice, or for the permanent fix, do the following, go into the Compiz Settings Manager, and find "Windows Decorations" add the following line to "Decoration Windows":
```
(any) | class=Firefox

```
Once you've done that, close out CCSM, then open CCSM back up again, then change that to:
```
any
```
Then that should solve the problem, it worked flawlessly. If that doesn't work you can always revert back to metacity:
```
metacity --replace
```
I've also found another fix, what you want do to is press F11 twice. Then once you've done that minimize it and resize the window then make it smaller, then close Firefox then reboot it, and it will be back to normal.

---

### Post by Matt26 on 2008-11-18
> **Codename said:**
> I've had the same issue but I've solved it. What you need to do is for a temporary fix is press "F11" twice, or for the permanent fix, do the following, go into the Compiz Settings Manager, and find "Windows Decorations" add the following line to "Decoration Windows":
```
(any) | class=Firefox

```
Once you've done that, close out CCSM, then open CCSM back up again, then change that to:
```
any
```
Then that should solve the problem, it worked flawlessly. If that doesn't work you can always revert back to metacity:
```
metacity --replace
```
I've also found another fix, what you want do to is press F11 twice. Then once you've done that minimize it and resize the window then make it smaller, then close Firefox then reboot it, and it will be back to normal.

thanks for the suggestions, however i am still trying to figure out how to locate the compiz settings- where can i find them?

---

### Post by Crafty Kisses on 2008-11-18
You have to install the following package:
```
sudo apt-get install compizconfig-settings-manager
```
Once you have done that, you can access it by running the following command:
```
ccsm
```

---

### Post by zika on 2008-12-26
> **binbash said:**
> go to compizconfig settings manager, then go to workarounds plugin.Disable legacy fullscreen support

I thought I messed up something with my FireFox and Ubuntu but Your hint made it dissappear. Thank You. There are lot of fellows with the same problem.

---

### Post by steveneddy on 2008-12-27
> **binbash said:**
> go to compizconfig settings manager, then go to workarounds plugin.Disable legacy fullscreen support

Thank you - works like a charm.

---

