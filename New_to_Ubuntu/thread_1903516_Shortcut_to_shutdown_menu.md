---
title: "Shortcut to shutdown menu"
date: 2012-01-02
forum: New to Ubuntu
---

### Post by jermza on 2012-01-02
Can't seem to find this in the forums, but, is there a keyboard shortcut to the shutdown menu? 

CTRL-ALT-DEL takes me to the logout menu.

I'd like a shortcut to the shutdown menu so that I don't have to click on the top right icon every time. Is it possible?

---

### Post by spiky001 on 2012-01-02
Have a look at the keyboard shortcuts and remap a key

---

### Post by spacecheck on 2012-01-02
Try this:

Ctrl+Alt+T

sudo init 0

You could also write an executable for that, save it and create a link to it or assign it a hotkey. Have to enter a password each time though, unless you store it in the file.

You could also try the solution(s) listed here:

[http://askubuntu.com/questions/66723/how-do-i-set-the-power-button-to-shutdown-instantly-instead-of-opening-a-dialog](http://askubuntu.com/questions/66723/how-do-i-set-the-power-button-to-shutdown-instantly-instead-of-opening-a-dialog)

Good luck!

---

### Post by I_can_see_the_light on 2012-01-02
In older versions the command was (I think) **gnome-session-save**.

In 11.10 you can press alt + F2 and enter ```
gedit /usr/share/applications/indicator-session-shutdown.desktop
```

Inside it there should be a line that begins with **Exec=**
Copy/Paste the command that follows ([FONT="Courier New"]/usr/lib/indicator-session/gtk-logout-helper --shutdown[/FONT]) in an alt + F2 dialog and press <enter> and see what happens. I'm not logged in to Ubuntu now so I can't test to see if it will work.

If it does the trick you can go to Keyboard shortcuts and create a new mapping.

---

