---
title: "alert &quot;battery Running on Battery&quot;"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by sa-mejia on 2008-10-03
Whenever I unplugged my laptop, I received the alert: "Running on Battery" (or something of the sort).  

But recently, I accidentally pressed the button "don't ask me again" attached to such message.

I want the alert back, I want to know that my computer has been unplugged (for sometimes my kids do it and I don't realize it).  But I have not found a way to do so.

Thanks in advance for any suggestion.

---

### Post by jamesrl on 2008-10-03
The setting you are looking for is in the gnome configuration settings in
/apps/gnome-power-manager/notify/discharging
[Assuming you are running gnome, with gnome-power-manager (which are ubuntu defaults)]

So to change the setting run 
```
gconf-editor
```
Search (Ctrl-F) for notify, select /apps/gnome-power-manager/notify
and turn the check mark on for discharging.  You also could just run
```
gconftool-2 --set /apps/gnome-power-manager/notify/discharging --type=bool true
```
However seeing the gconf-editor is handy (as many gnome features that can't be set elsewhere can be found in there)

Cheers.

---

### Post by sa-mejia on 2008-10-09
Thanks a lot.  

Santiago.

---

