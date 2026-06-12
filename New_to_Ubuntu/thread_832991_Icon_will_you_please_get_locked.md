---
title: "Icon: will you please get locked???"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by shoaibi on 2008-06-18
Okay, here, first see the screenshot...

And please dont ask why do i have so many things installed, or why i have all of them on my panel...


Problem is:
1. Whenever i run some full screen application, even though each and every icon is locked, and i have also placed multiple separators and locked those separators as well, the icons still mix up again, and i again wasted my time to sort them according to my flavour....

What should i do?

---

### Post by drs305 on 2008-06-18
Once I get my panel set up the way I want it, I run the following to save my settings. On my computer it mostly restores the original placement.

To save the panel settings (to a file on the Desktop called panel_settings):
```
gconftool-2 --dump /apps/panel > ~/Desktop/panel_settings
```

To restore the panel and refresh the Desktop:
```
gconftool-2 --load ~/Desktop/panel_settings && killall gnome-panel
```

You can even make a shortcut and put it on your panel so you can do this anytime you add, eliminate or move your panel settings. Of course, you probably don't have any room for another shortcut!  ;-)

---

### Post by yragrelluf on 2008-06-18
I like what you did with your panel. As far as your problem goes, id install ubuntu tweak, and check the complete lockdown of the panel box, located under system/gnome and see if that helps. It seems easier than the above suggestion.

---

### Post by shoaibi on 2008-06-18
@drs305:
that seem to work for some reason :P
naaahhhh, i have room for atleast 3 more icons :P :D

@yragrelluf
that didnt help, i tried that at first, but icons still moves, seems like they are quite some wanderers :P those little scoundrels :D
you can do it to, tell me, i will send you my settings :P :D

---

### Post by shoaibi on 2008-06-18
drs305:
i can not make a shortcut :(
i did:
Add to Panel > custom Application Launcher
Application in Terminal > Command 

But it didnt work, i even tried simple application, or doing it by sh "cmd"...

---

### Post by ibuclaw on 2008-06-18
I think you put the path in with the command too.

ie:
```
/home/name/script.sh
```
Also, make sure that the file is executable
```
chmod +x script.sh
```
Regards
Iain

---

### Post by kaibob on 2008-06-18
> **shoaibi said:**
> <snip>Problem is: 1. Whenever i run some full screen application, even though each and every icon is locked, and i have also placed multiple separators and locked those separators as well, the icons still mix up again, and i again wasted my time to sort them according to my flavour....<snip>

Perhaps you have (in effect) already done this, but I would put a check mark next to the following key in the gconf editor:

/apps/panel/global/locked_down

---

