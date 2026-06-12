---
title: "HowTo: Switch Workspace or run commands by moving the mouse to the edge of the sceen"
date: 2005-12-16
forum: Outdated Tutorials &amp; Tips
---

### Post by frodon on 2005-12-16
Written originally by [**shakin**]("http://www.ubuntuforums.org/member.php?u=2332")

Brightside is a utility that allows you to switch to adjacent workspaces by moving your mouse cursor to the edges of the screen. Move your mouse left and you switch to the workspace to the left of your current one, move right to move to the workspace to the right, etc. You can also configure custom commands to run when you move to the corner of the screen, or set it to move to a diagonal workspace if you have a multi-row, multi-column layout.

Install Brightside : ```
sudo apt-get install brightside
```configure brightside using the GUI : ```
brightside-properties
```To run the daemon : ```
/usr/bin/brightside
```You should now be able to switch workspaces by moving your mouse to the edges of the screen.

Below are instructions to have brightside start when you login, otherwise you will need to run the /usr/bin/brightside command after each login.

- Menu: System -- Preferences -- Sessions.
- Go to the Startup Programs tab.
- Click Add.
- In the Startup Command text box type (without the quotes) '/usr/bin/brightside' and click OK.

---

### Post by juniah on 2007-11-03
I will be amused for hours on end.  Thanks!

---

