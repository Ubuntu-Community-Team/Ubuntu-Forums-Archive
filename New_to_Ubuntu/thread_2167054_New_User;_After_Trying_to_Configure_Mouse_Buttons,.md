---
title: "New User; After Trying to Configure Mouse Buttons, Ubuntu 12.04 Fails to Boot"
date: 2013-08-12
forum: New to Ubuntu
---

### Post by jaarli-1 on 2013-08-12
I very recently (last Friday) installed Ubuntu 12.04 from a USB drive onto my new computer. It is currently the only OS on the computer; I am writing this from my older laptop.
I had a Logitech G300 mouse ([http://gaming.logitech.com/en-us/product/g300-optical-gaming-mouse](http://gaming.logitech.com/en-us/product/g300-optical-gaming-mouse)) that I had used before, and I wanted to program its buttons to change weapons in Team Fortress 2.
However, my computer did not seem to recognize the "G6" and "G7" buttons of the mouse, at least when I ran xev. The other buttons were recognized.

I then found this thread: [http://ubuntuforums.org/showthread.php?t=65471](http://ubuntuforums.org/showthread.php?t=65471)

I followed the outlined instructions up to phase 3, where the post says: 
[U]
"Warning![/U]
[COLOR=#000000]Don't restart X yet! Just before we do I have to warn you if you made a mistake in the xorg file X will not restart. But don't worry that's why we only commented out the previous settings and didn't delete them. If X fails to restart then you will end up in a text console. Log in and type the following to edit the xorg file:

[/COLOR][COLOR=#000000]Code:[/COLOR]
sudo nano /etc/X11/xorg.conf"

and instructions on how to get back to what you had before. I wrote down the instructions and restarted X using sudo restart lightdm.

My monitor went black, but did not display anything even after I had waited for five minutes. I shut down the computer using the power button, waited for a while, and then turned on the computer.
It now gets stuck in the Ubuntu loading screen, where it stops animating after it has filled the five orange dots.

---

### Post by grahammechanical on 2013-08-12
Do you agree that the best thing to do is to edit the xorg.conf file and commnet out the chnages that you made and to remove the comment marks (#) against the previous settings?

Reboot Ubuntu and at the Grub screen select Recovery mode. At the Recovery menu screen select Network. That will set up an internet connection. Which you may not need but it will also put the file system into read/write mode, which you do need because you are going to edit a file and you want to save it.

You should now be back at the Recovery menu. Select Root. That will give you a root prompt where you can run

```
nano /etc/X11/xorg.conf
```

You will not need sudo as it is a root prompt. The Nano text editor will open and display xorg.conf. Make the edits. At the bottom of the text editor you will see some Ctrl key combinations that will allow you to save the editted file and exit the editor.

^O = Ctrl+O = writout = save
^X = ctrl+X = Exit.

You should not need more than that. Oh, when back at the Recovery menu select Resume. You may find that you are in a lower video mode then usually. That is what Resume does. So, log out and log in or reboot and things should be back to where they were.

Regards.

---

### Post by jaarli-1 on 2013-08-12
When I open /etc/x11/xorg.conf in nano, the text area is blank. After a short wait (30s-ish) it tries to restart, forcing me to go back to the recovery menu and and do the network-root thing again.

---

