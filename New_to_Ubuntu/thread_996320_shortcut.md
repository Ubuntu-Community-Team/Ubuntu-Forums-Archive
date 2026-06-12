---
title: "shortcut"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by ibbill on 2008-11-28
Have tried to drag the url icon from the address bar to the desk top with no luck tried to right click on a page could not find create shortcut.

When I right click on the desktop nothing appears also.

Is this possible with xubuntu as I can do that in ubuntu 8.10

---

### Post by scragar on 2008-11-28
The desktop doesn't react the same way in XFCE as it does in gnome, you can do it by opening 2 copies of the file manager, then right click/drag works as you expect.

---

### Post by Bölvaður on 2008-11-28
I guess the most solid way to do that which works in all distros is making an empty file and make it contain

```
firefox www.ubuntuforums.org
```

and then make the file executable.


That would work as a shortcut which you can bring along with you like luggage :P you can always use it as long as you have firefox the command for firing up your browser

---

### Post by ibbill on 2008-11-28
Okay thanks for the quick reply. Just odd you cant have short cuts on your  desktop.Going to just add them to favorites and click on it there. Only wanted shortcuts for about7 sites that I visit a lot. Thanks again.

When I right click on the desktop nothing shows should there be something. Such a newbie to this.

Bill

---

### Post by scragar on 2008-11-28
XFCE has a few options for what should happen when you right click, I'm sure do nothing is one of them.

Open the settings manager, choose desktop, and look in the behaviour tab.

Oh, if that's right open a run box(ALT+F2) and copy paste:
```
xfdesktop
```
to restart the desktop process, I think that should fix it.

---

