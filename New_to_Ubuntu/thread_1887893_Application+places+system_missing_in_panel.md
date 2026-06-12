---
title: "Application+places+system missing in panel"
date: 2011-11-28
forum: New to Ubuntu
---

### Post by xptional on 2011-11-28
Hi :), 

     I have searched to resolve the subjected problem but could not find the solution. 
The problem is that on the top panel, Application, Places and System menu is missing, how to resolve it ? 

Anyhow, the googlechrome icon, and other menu like wifi, time and date, user name et power button at the right side of panel are always displayed. 

Could you know about this problem ? please suggest how to solve it ? 
Thanks !

---

### Post by crazy bird on 2011-11-28
At the top panel, right click on it and select add to panel. Then you see a windows in which you can find what you're looking for!

---

### Post by xptional on 2011-11-28
O yesss, 

I selected Menu Bar, and I got it :) , 

Thanks a lot !

---

### Post by crazy bird on 2011-11-28
Great! Can you mark this thread as solved then?

---

### Post by westie457 on 2011-11-28
Glad it is fixed.

For future use keep this in a safe place.```
gconftool --recursive-unset /apps/panel && killall gnome-panel

```

---

### Post by xptional on 2011-11-28
Thank you westie for the code :) 

I will keep it :)

Already I searched how to mark this thread solved, but I could not be able to do so , any help please ?

---

### Post by xptional on 2011-11-28
I found & I did it , :D

---

