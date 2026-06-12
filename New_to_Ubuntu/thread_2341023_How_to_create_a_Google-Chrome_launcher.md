---
title: "How to create a Google-Chrome launcher"
date: 2016-10-24
forum: New to Ubuntu
---

### Post by swb_mct on 2016-10-24
I installed Google Chrome on Ubuntu 16.04.1 desktop.   How do I create an icon / launcher on the desktop for Google-Chrome ?

and

Is their a way to get it on the Cinnamon Start Menu ?     (I added Cinnamon to 16.04)

Thank You.

---

### Post by Tadaen_Sylvermane on 2016-10-24
Create a .desktop file and put it in either /usr/share/applications/ or ~/.local/share/applications/ 

That will put it on the cinnamon menus.

---

### Post by swb_mct on 2016-10-24
Sorry, but what goes in the file . . I am not a Linux expert - at all.

I tried putting     google-chrome   in a file named chrome.desktop  
It did show up the Cinnamon menu.
The same file sitting on the desktop, sayd  "Error launching application"

---

### Post by cmcanulty on 2016-10-24
Right click desktop and select create launcher. Put name as Google Chrome or Chrome as you wish

 Command is:

```
/usr/bin/google-chrome-stable %U
```

double click on icon box and then scroll down through icons to google-chrome

this is for xubuntu but should be similar for cinnamon

---

### Post by deadflowr on 2016-10-24
Something's wrong.
The launcher should have been added to any and all menus without having to do anything.

If you logout login, does it show then?

---

### Post by Geoffrey_Arndt on 2016-10-24
Or use the "main menu" program (can't recall if it was pre-installed, but if not, use Synaptic or other package manager to install it),    Use the command in post #4 in the appropriate field.    Of course, as you may or may not know, in Unity, all you do is use the dash - type in "main menu", or "Chrome", and then just drag it to the Launcher.

---

### Post by swb_mct on 2016-10-24
> **cmcanulty said:**
> Right click desktop and select create launcher. Put name as Google Chrome or Chrome as you wish

 Command is:

```
/usr/bin/google-chrome-stable %U
```



Thanks,  This worked

---

### Post by yetimon_64 on 2016-10-24
> **swb_mct said:**
> Thanks,  This worked
Can you mark the thread as [SOLVED], from the thread tools drop down menu in your browser window, please ?
[[COLOR=#0000ff]--Here--[/COLOR]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") is a link for how to do so, if needed (link in blue text). Regards, yeti

---

