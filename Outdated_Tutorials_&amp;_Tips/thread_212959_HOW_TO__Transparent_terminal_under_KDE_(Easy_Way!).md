---
title: "HOW TO:  Transparent terminal under KDE (Easy Way!)"
date: 2006-07-10
forum: Outdated Tutorials &amp; Tips
---

### Post by d351GuJu on 2006-07-10
For those who like to achieve a quick and easy transparent terminal on their desktop, this is the way I found to be a lot easier.

**Step 1**:  sudo apt-get install gnome-terminal

**Step 2**:  Open Gnome-terminal, and create a new profile called "tterm".  Change the profile by going into *Terminal* **>** *Change Profile* **>** *tterm*.  Once that's done, right click and select "Edit Current Profile...".  Under the _General_ tab, unselect *"cursor blinks"*, *"Show menubar..."*, and *"Terminal Bell"*.  Go under _"Effects"_ and select **"Transparent background** and move it to **none**.  Go under _Scrolling_, and under **"Scrollbar is"** select **Disabled**.  Now click **Done**.

**Step 3**:  Move the terminal and set it to your preference, see screenshot I attached for more info.  Once you have done that, hit ALT+F3 while the terminal is active, and go down to **Advanced** > **"Special Window Settings..."**.  Under "_Geometry_" tab, select **Position**, and Force it.  Now go to "Preferences", and select "No border", "Skip taskbar", "Skip Pager".  And make sure to Force them and select the checkbox next to each.  Click Ok and you are done!!!

Everytime you reboot or logoff, it will start automatically!

Enjoy,

d351GuJu  :cool:

**UPDATE:**  For some reason, my newly installed kubuntu on my laptop doesn't start terminal automatically but my desktop does.

---

