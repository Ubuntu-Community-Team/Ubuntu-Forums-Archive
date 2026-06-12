---
title: "[SOLVED] Can't add anything to panel"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by 71CH on 2008-07-19
Usually when I right click my panel I get options like "Add to panel".  Now for some reason I only get two options "Help" and "About panels".  Anybody know how to fix this?

---

### Post by iaculallad on 2008-07-19
What about restoring the default Ubuntu panel then try right-clicking if it pops the complete menu:

```
sudo gconftool-2 --shutdown
sudo rm -rf ~/.gconf/app/panel
sudo pkill gnome-panel
```

---

### Post by 71CH on 2008-07-19
Can you explain what those commands do before I try them?  Thanks.

---

### Post by pikabuntu on 2008-07-19
I think it deletes the panel's settings and restores it to the default.

---

### Post by iaculallad on 2008-07-19
```
sudo gconftool-2 --shutdown
```

This command shut down the gconfd daemon

```
 sudo rm -rf ~/.gconf/app/panel 
```

This command deletes the values of your Ubuntu panel

```
sudo pkill gnome-panel
```

This command terminates the GNOME panel and at the same time creates new default values.

---

### Post by 71CH on 2008-07-19
Thanks for your help but those commands didn't do anything.  :(

---

### Post by iaculallad on 2008-07-19
> **71CH said:**
> Thanks for your help but those commands didn't do anything.  :(

What about:

```
sudo debconf gnome-panel
```

---

### Post by pikabuntu on 2008-07-19
what does debconf do?

---

### Post by iaculallad on 2008-07-19
> **pikabuntu said:**
> what does debconf do?

Configuration application for Debian packages (i.e: gnome-panel at this point).

EDIT: For more details on debconf:

```
man debconf
```

---

### Post by 71CH on 2008-07-19
It seemed to do the trick but then when I close the terminal it goes back to normal.

---

### Post by iaculallad on 2008-07-19
What about: Run the sudo terminal command below then log-out off your account then log back in. Retry adding items to panel:

```
sudo debconf gnome-panel
```

---

### Post by dhughes on 2008-07-19
> **71CH said:**
> Can you explain what those commands do before I try them?  Thanks.

 A wise question, considering this: [http://ubuntuforums.org/announcement.php?f=336](http://ubuntuforums.org/announcement.php?f=336)

 That's always bugged me, no offense to you iaculallad, but I think many people here get in the habit of posting commands with no explanation, especially here in the Absolute Beginner Talk section.

 Sorry for the interruption continue on!

---

### Post by saratchandra on 2008-07-19
You locked down the panel completely. Install ubuntu-tweak and uncheck complete lockdown of the panel. You can also restoreusing gconf.

---

### Post by 71CH on 2008-07-19
> **saratchandra said:**
> You locked down the panel completely. Install ubuntu-tweak and uncheck complete lockdown of the panel. You can also restoreusing gconf.

Ahhh this did the trick.  Thank you very much.  Thanks also to iaculallad.

---

