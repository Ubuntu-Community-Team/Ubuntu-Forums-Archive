---
title: "How to change the console font and resolution?"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by Jonathan Lahav on 2008-05-24
Hello.
When I had the 8.04 beta installed, the console at boot time, and the alternate consoles had a very nice sharp font with high resolution.
Now, in the final release I have a thin big weird font that starts to appear in the _middle_ of the boot and serves also the alternate consoles.
How can I change the resolution and font back to the beautiful and useful one?

Thanks!

---

### Post by Sarah L on 2008-05-24
Under Kubuntu, if you open up the console and go to Tools -> Configure -> Schema, you'll find a bunch of configuration options for your console's appearance.

I'm not sure what the differences between konsole and gnome-terminal are, but both programs should have a similar set of options.

---

### Post by Vicfred on 2008-05-24
```
sudo gedit /usr/share/vte/termcap/xterm
```

Just a few lines from the top will be the line reading:

 :co#80:it#8:li#24:\

Change the number right after co# to change the width. Change the number right after li# to change the height

to change the font/appearance go to

edit> current profile on the terminal

---

### Post by j1mc on 2008-06-07
Jonathan, did any of the comments below work for you?  I was having the same issue.  Please let me know.  Thanks!

---

### Post by Jonathan Lahav on 2008-06-10
Thank you for the replies but I'm not talking about the gnome-terminal.
I'm asking about the consoles that you get when pressing alt+ctrl+F1.

The gnome terminal is simple enough. These consoles are beyond by knowledge.

---

### Post by Jonathan Lahav on 2008-06-10
This is the way to go:
* open the terminal
* paste this command
    sudo dpkg-reconfigure console-setup
* press enter until you get to a dialog where you have to choose between vga and fixed.
* choose vga and then 16
* you're all done!

---

### Post by robertyou on 2008-11-20
use startupmanager, it has more than just changing the resolution. Try it out :)

---

