---
title: "How to make it so only 1 VLC can be opened?"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by alwiap on 2008-06-04
Hi,

I'm using VLC media player, and I would like only one to be open at a time, because when I click on an audio/video file it opens a new VLC, and I have to close the old VLC if something was playing, which was annoying.  I want the next audio/video files to open in the same one, it's fine if it interrupts what was playing.

Is there a setting in the preferences of VLC?  I've looked.

Thanks!

---

### Post by kamitsukai on 2008-06-04
id be interested if there is a way to do this :D

---

### Post by alwiap on 2008-06-04
> **kamitsukai said:**
> id be interested if there is a way to do this :D

I know!  I NEED to know how to do this! HALP!

---

### Post by kellemes on 2008-06-04
I'm using VLC 0.8.6f with the wxWidgets interface.
I'm using the Dutch version so I'm translating..

Select "preferences", tick the checkbox at the botomright of the prefences-dialog so advanced options are shown..
Select "advanced" from the treeview at the left of the dialog, there you have a checkbox named "only allow one running instance".

---

### Post by darkline on 2008-06-04
at the moment there is no setting in vlc, i believe there will be one available in 0.9.0.

Until then here is a way borrowed from another thread :

> 
This is possible using a shell script.

```
#! /bin/bash
# this script ensures that only 1 instance of vlc is running at a given time.
# It uses wmctrl. Make sure you have wmctrl installed, if not issue:
# sudo apt-get install wmctrl

WIN_ID_LINE=$(wmctrl -l | grep "VLC media player")
if [ -n "$WIN_ID_LINE" ]; then
	WIN_ID=${WIN_ID_LINE:0:10}
	wmctrl -i -c $WIN_ID	
fi
vlc $1

```

You need to save it where the system will find it (ie in your path); I just saved it to /usr/bin. Like this


```

gksu 'gedit /usr/bin/vlc-start'
```

<paste script text>
Now, make it executable

```

sudo chmod +x /usr/bin/vlc-start
```

Now, edit the vlc shortcut in your menus to use vlc-start as command instead of vlc.

Finally, as I wrote in the script, you need to install wmctrl:
Code:

```
sudo apt-get install wmctrl
```


Basically it closes the old instance and opens a new one.

---

### Post by alwiap on 2008-06-04
> **darkline said:**
> 
Now, edit the vlc shortcut in your menus to use vlc-start as command instead of vlc.


What do you mean by this?  Or rather, how do I do this exactly?  I put 'vlc-start' in my preferred applications, but it didn't work.

---

### Post by stchman on 2008-06-04
An awful lot of trouble to just get around hitting the little X in the upper right corner.

---

### Post by alwiap on 2008-06-04
> **stchman said:**
> An awful lot of trouble to just get around hitting the little X in the upper right corner.

yes it is :(

---

### Post by meborc on 2008-06-04
> **stchman said:**
> An awful lot of trouble to just get around hitting the little X in the upper right corner.

or alt+F4 ;)

---

### Post by darkline on 2008-06-04
> **alwiap said:**
> What do you mean by this?  Or rather, how do I do this exactly?  I put 'vlc-start' in my preferred applications, but it didn't work.

First try running "vlc-start" in your terminal to make sure it works.

Then hopefully it will work in your preffered applications, if not try right clicking on a multimedia file, properties > open with > add > custom > browse> find vlc-start in /usr/bin and add

hopefully then you will be able to use it with the files then!


just make sure you made it executable as well

"sudo chmod +x /usr/bin/vlc-start"

---

### Post by alwiap on 2008-06-04
> **darkline said:**
> First try running "vlc-start" in your terminal to make sure it works.

Then hopefully it will work in your preffered applications, if not try right clicking on a multimedia file, properties > open with > add > custom > browse> find vlc-start in /usr/bin and add

hopefully then you will be able to use it with the files then!


just make sure you made it executable as well

"sudo chmod +x /usr/bin/vlc-start"

ok got it! thanks.

---

### Post by kamitsukai on 2008-06-04
[FONT="Comic Sans MS"][SIZE="3"]I've just tried that script and it doesen't work for me it opens vlc but you get an error stating that vlc couldn't find the specified video file (and I've tried this with all my videos!)[/SIZE][/FONT]

---

