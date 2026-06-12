---
title: "[SOLVED] Can't add anything to panels"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by captgadget on 2008-06-06
Like I used to have the weather report, but when I right click on the panel my only choices are help or about panels.

---

### Post by iaculallad on 2008-06-06
Try to restore your default Ubuntu Panel:

```
sudo gconftool-2 --shutdown
sudo rm -rf ~/.gconf/apps/panel
sudo pkill gnome-panel
```

---

### Post by jamieh on 2008-06-06
> **iaculallad said:**
> Try to restore your default Ubuntu Panel:

```
sudo gconftool-2 --shutdown
sudo rm -rf ~/.gconf/apps/panel
sudo pkill gnome-panel
```

[COLOR="Red"][SIZE="6"]WARNING!!![/SIZE][/COLOR]

Please forgive me if I'm wrong, but doesn't "sudo rm -rf" mean reformat the entire drive?

---

### Post by iaculallad on 2008-06-06
> **jamieh said:**
> [COLOR="Red"][SIZE="6"]WARNING!!![/SIZE][/COLOR]

Please forgive me if I'm wrong, but doesn't "sudo rm -rf" mean reformat the entire drive?

Do a little research first before posting warnings, not all "sudo rm -rf" files are meant to destroy drives/system, that command is use to delete the old ~/.gconf/apps/panel in order to restore the default gnome-panel.

---

### Post by drs305 on 2008-06-06
> **jamieh said:**
> 
Please forgive me if I'm wrong, but doesn't "sudo rm -rf" mean reformat the entire drive?

**sudo rm -rf ~/.gconf/apps/panel**

rm is remove
-r is recursive - it will remove subfolders
-f is force - "ignore nonexistent files, never prompt"

The command as written, begins in the user's .gconf/apps/panel folder and works down from there. It won't touch any folders above .gconf/apps/panel  

The command is safe as long as the **~/.gconf/apps/panel** is included.

In this case, however, the user will be deleting files and folders from his own .gconf so the use of the sudo command is not necessary and exposes some risk if the command isn't used completely.

---

### Post by linuxisfree on 2008-06-06
Sorry to hijack the thread. Thanks for the info, but it only seems to reset the top panel, how do i do that for the bottom panel? can it be done? Thanks!

---

### Post by iaculallad on 2008-06-06
> **linuxisfree said:**
> Sorry to hijack the thread. Thanks for the info, but it only seems to reset the top panel, how do i do that for the bottom panel? can it be done? Thanks!

Right-click on the top panel, select "New Panel", a new panel will emerge and you have to right click on the new panel,  select "Add to Panel", double click on "Window List".

---

### Post by linuxisfree on 2008-06-06
> **iaculallad said:**
> Right-click on the top panel, select "New Panel", a new panel will emerge and you have to right click on the new panel,  select "Add to Panel", double click on "Window List".

I see... so i have to make a new panel to replace the one in the bottom. Thanks for the help! Will try that. (all this just because i can't see my trash applet - its there when i right click, i just can't see it...:()

---

### Post by captgadget on 2008-06-06
It didn't work. I still have only help or about panels. Also I cannot remove anything from a panel.

---

### Post by iaculallad on 2008-06-06
> **captgadget said:**
> It didn't work. I still have only help or about panels. Also I cannot remove anything from a panel.

What about:

```
sudo debconf gnome-panel
```

---

### Post by iaculallad on 2008-06-06
> **linuxisfree said:**
> I see... so i have to make a new panel to replace the one in the bottom. Thanks for the help! Will try that. (all this just because i can't see my trash applet - its there when i right click, i just can't see it...:()

You could add the Trash icon by righ-clicking on your bottom panel. Select "Add to Panel" -> Double click on the Trash icon located under "Desktop and Windows".

---

### Post by captgadget on 2008-06-06
Now, I don't know why this worked. I created a new user, restarted, logged in as the new user and I could add to panel. So, I logged of, restarted and logged in as the original user and now I can use the panel. Magic maybe?

---

