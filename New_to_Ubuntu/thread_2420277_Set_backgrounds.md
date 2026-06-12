---
title: "Set backgrounds"
date: 2019-06-02
forum: New to Ubuntu
---

### Post by hateregistering on 2019-06-02
Seems to be simple to set background of the working desktop and also for the lock screen. But the login screen and the screen where you enter the password seems to be a whole lot more difficult. I have tried solutions like the one described here: [https://vitux.com/8-ways-to-customize-your-ubuntu-desktop/](https://vitux.com/8-ways-to-customize-your-ubuntu-desktop/). But that is not working. I have been googling for over an hour to try to find a solution to this problem, which I think should be rather simple. How can I solve this problem?

---

### Post by kc1di on 2019-06-02
don't know if you saw [this page ]("https://vitux.com/how-to-change-login-lock-screen-background-in-ubuntu/")but it works for me.
Note the file address has changed in 19.04 it's in the gnome-shell.css file now. so the address looks like this ```
 gedit admin:///usr/share/gnome-shell/theme/gnome-shell.css
```

---

### Post by corradoventu on 2019-06-02
```
gedit admin:/etc/alternatives/gdm3.css
``` you will find: ```
#lockDialogGroup {
  background-color: #2C001E; }
```
I changed to ```
#lockDialogGroup {
  background: #2c001e url(file:///home/corrado/Pictures/LockScreen.png);
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center; }
```
so I have my picture in the screen where i enter the password.
the picture is a .png or a .jpg of the size of your screen

---

### Post by deadflowr on 2019-06-02
Easier way is to just edit the /etc/alternatives/gdm3.css file as that will apply to whatever the linked file actually is.
Mine isn't either the ubuntu.css nor the gnome-shell.css files posted/linked, but rather a file in the theme/Yaru directory.
Running
```
ls -l /etc/alternatives/gdm3.css
```
will give a definitive answer.

I find it's also good to make copies of both the original and my edited versions in case I
1)mess up the edit and break the login screen.
2)the theme gets an update the reverts my changes back to the original.

I keep the backup/edits in a Documents sub folders in my home directory.
that way I can revert them in a console session or recovery mode with a simple copy command.

---

### Post by corradoventu on 2019-06-02
fot the splash screen (ubuntu with dots) in ```
/usr/share/plymouth/themes/ubuntu-logo/ubuntu-logo.script
```
change dark grey to dark grey:
```
Window.SetBackgroundTopColor (0.16, 0.00, 0.12);     # Nice colour on top of the screen fading to
Window.SetBackgroundBottomColor (0.16, 0.00, 0.12);  # an equally nice colour on the bottom

```
to red to blue
```
Window.SetBackgroundTopColor (0.90, 0.00, 0.12);     # Nice colour on top of the screen fading to
Window.SetBackgroundBottomColor (0.16, 0.00, 0.90);  # an equally nice colour on the bottom
```

---

