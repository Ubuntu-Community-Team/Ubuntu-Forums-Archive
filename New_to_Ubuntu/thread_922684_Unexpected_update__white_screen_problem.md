---
title: "Unexpected update / white screen problem"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by MightyFrog on 2008-09-17
I wasn't expecting this level of problem today. :( Opened Update Manager to do some routine updates to Hardy Heron, Nothing showed up. I clicked Check and updates appeared in the screen. I got a message asking if I wanted to do a partial update and I clicked OK or Yes, whatever the right command was. Update Manager started to download over a hundred updates! The computer was updated just a couple of days ago, so I wondered if the system got confused about what updates it actually needed. I rebooted when asked to, got to the login screen, logged in OK, and then the screen went white and I could see nothing but the mouse cursor. I hadn't done anything special to configure the UI, I haven't been running dual monitors. I see this referred to as "White Screen of Death," but I'm not sure what steps to take next.

---

### Post by Sealbhach on 2008-09-17
This command reconfigures the GUI.

See here:

[http://ubuntuforums.org/showthread.php?t=759309](http://ubuntuforums.org/showthread.php?t=759309)

```
dpkg-reconfigure -phigh xserver-xorg
```

Then restart.

```
sudo /etc/init.d/gdm restart
```

Wait for other suggestions if you're not sure - I've never ran it myself.


.

---

### Post by MightyFrog on 2008-09-17
Erm, how do I enter a command? I'm looking at a white screen here. I've tried to see if the command would work by hitting ESC on boot and typing the command at the grub command line, but it's an unrecognized command.

---

### Post by MightyFrog on 2008-09-17
OK, figured out how to enter failsafe terminal mode. Tried the command, got the message "Package xsession-xorg is not installed and no information is available."

---

### Post by karlr42 on 2008-09-17
I was playing with the virtual terminals (ctrl-alt f1-f6) to try and answer your question about how to enter commands, and I got the white screen too when I tried to return to X. I just hit crt-alt-backspace on the white screen and gnome started up again! Try it!

---

### Post by MightyFrog on 2008-09-17
Ctrl-Alt-Bksp logs me out just fine and takes me back to the login screen, but doesn't fix the graphic problem. Logging in on either computer account brings up the white screen.

---

### Post by Sealbhach on 2008-09-17
If you're connected to the internet, try these:

```
sudo apt-get update
sudo apt-get install ubuntu-desktop

```

Also, try the "fix broken packages" option when booting in recovery mode.


.

---

### Post by MightyFrog on 2008-09-17
Yay, i discovered failsafe GNOME mode! When I went to upgrade, I was told that it could only do a partial upgrade. I selected Partial Upgrade and got this message:

```
An upgrade from 'intrepid' to 'hardy' is not supported with this tool.
```

I don't remember approving any upgrade to a new version. Any advice on what to do next?

---

### Post by Sealbhach on 2008-09-17
I don't know. Anyone else know?

(sorry):(

.

---

