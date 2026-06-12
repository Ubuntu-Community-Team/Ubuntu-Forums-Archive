---
title: "Bar at the bottom"
date: 2024-10-17
forum: New to Ubuntu
---

### Post by dmraven on 2024-10-17
Hi All,

I have a gray bar at the bottom of the screen that shows running applications and off to the right hand side the four desktops(?).
How do I make this bar go away?

Thanks.

---

### Post by grahammechanical on 2024-10-17
We cannot help you unless you tell us what distribution of Linux you are using and what desktop environment and user interface it is using.

I am running Ubuntu 24.04 LTS that is using the Gnome 3 desktop environment and the Gnome 3 shell user interface. I do not have a bar at the bottom of the screen or four desktops on the right side of the screen.

Regards

---

### Post by dmraven on 2024-10-17
Thanks for the reply and that is totally fair.
OS: Ubuntu 24.04
echo #XDG_CURRENT_DESKTOP=GNOME-Classic:GNOME

---

### Post by ActionParsnip on 2024-10-17
Could you give a screenshot or find an example online.

---

### Post by dmraven on 2024-10-17
[IMG]https://imgur.com/a/ur0U9uO[/IMG][IMG]https://imgur.com/a/ur0U9uO[/IMG]Here you go: [https://imgur.com/a/ur0U9uO](https://imgur.com/a/ur0U9uO)

---

### Post by grahammechanical on 2024-10-17
Thank you.

I have a bar on the left side of the screen. It is called the Dock. Open System Settings. It is the cog icon in the panel that drops down when we click the small panel at the top right of the screen. When System Settings is open select Ubuntu Desktop and select Dock and look at Position on the screen. In your case it is ticked Bottom. You can choose Left or Right instead.

Regards

---

### Post by dmraven on 2024-10-17
Thanks for the reply!  :)
When I open settings I don't see one for Ubuntu Desktop.
Under Appearance I can choose "Default" or "Dark"
Displays relates directly to the monitor stuff.
[COLOR=#FFFFFF][FONT=&amp][https://imgur.com/MO11Mih](https://imgur.com/MO11Mih)


[/FONT][/COLOR]

---

### Post by ActionParsnip on 2024-10-17
If you right click the bar is there a preferences option?

---

### Post by dmraven on 2024-10-17
No, right clicking does not produce any menu at all.

---

### Post by davetheoldcoder on 2024-10-17
> **dmraven said:**
> When I open settings I don't see one for Ubuntu Desktop.

Are you sure that your Settings doesn't have this section, shown in the attached screenshot?

---

### Post by dmraven on 2024-10-17
I am 100% sure.  It goes from "Appearance" to "Apps"

---

### Post by dmraven on 2024-10-17
Not sure if this helps or matters, but I did have extensions turned on and because of the bar at the bottom which suddenly popped up I had to turn them off.
Now I am trying to get that bar removed so I can turn the extensions back on.
On the log-in screen I see the following desktop options:
GNOME
GNOME Classic (selected)
GNOME on Xorg
Plasma (X11)
Ubuntu
Ubuntu on Xorg

---

### Post by davetheoldcoder on 2024-10-17
Do you have Extension Manager (package name: gnome-shell-extension-manager) installed? If so, does it show the extension Ubuntu Dock?

---

### Post by dmraven on 2024-10-17
Yes that package is installed, but it is turned off.
Yes it does show the Ubuntu Dock Extension.

[edited for grammar and fixing a mistake ~ sorry]

---

### Post by davetheoldcoder on 2024-10-17
> **dmraven said:**
> On the log-in screen I see the following desktop options:...

You might try GNOME.

I think that's what I'm using:

```
$ echo $XDG_CURRENT_DESKTOP
ubuntu:GNOME

```

---

### Post by deadflowr on 2024-10-17
Do you want the whole bar to go away?
Then toggle "window list" to off in Extensions or Extensions manager if installed.
The Extensions app should be installed.

For what it's worth I think you might want a better alternative like gnome-flashback/gnome-panel,
gnome classic is weird.
This should still work: [https://help.ubuntu.com/community/GNOMESessionFlashback](https://help.ubuntu.com/community/GNOMESessionFlashback)

---

### Post by dmraven on 2024-10-17
In Settings I still do not have the Ubuntu Desktop option, but the bar at the bottom of the screen is gone now...

---

### Post by dmraven on 2024-10-17
Changing from GNOME-Classic to GNOME seems to have resolved the issue for now.
Thanks everyone!
I am grateful for all the help and advice!

---

