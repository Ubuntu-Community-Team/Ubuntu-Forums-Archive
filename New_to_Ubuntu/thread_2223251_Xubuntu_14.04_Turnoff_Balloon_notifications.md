---
title: "Xubuntu 14.04 Turnoff Balloon notifications"
date: 2014-05-10
forum: New to Ubuntu
---

### Post by matt103 on 2014-05-10
Any suggestions how to turn of the balloon notifcations or popup ballons throughout Xubuntu 14.04. It does seem quite silly to have a large ballon tip that says   eg "rubbish bin" when you hover over the rubbish bin. Thks

---

### Post by matt103 on 2014-05-10
AND for the future mentally challenged folk amongst us..the answer is: Right click on your desktop - desktop settings - icons tab - disable "show icon tooltips" 
SO where do I collect my prize..

---

### Post by kc1di on 2014-05-10
One way is to run the following in a terminal.
```
sudo mv /usr/share/dbus-1/services/org.xfce.xfce4-notifyd.Notifications.service /usr/share/dbus-1/services/org.xfce.xfce4-notifyd.Notifications.service.disabled
```  
just copy and past it to avoid typos.
To reverse it type ```
sudo mv /usr/share/dbus-1/services/org.xfce.xfce4-notifyd.Notifications.service.disabled /usr/share/dbus-1/services/org.xfce.xfce4-notifyd.Notifications.service
```

---

### Post by kc1di on 2014-05-10
Glad you found it :)

---

### Post by bapoumba on 2014-05-10
> **matt103 said:**
> AND for the future mentally challenged folk amongst us..the answer is: Right click on your desktop - desktop settings - icons tab - disable "show icon tooltips" 
SO where do I collect my prize..

You won the prize indeed : you can now go to Thread Tools, and mark your thread as solved, congrats :tongue:

(and in the future, even if I understand it was a light or funny remark, please bear in mind that your first sentence can make some people uneasy. I'm sure my very nice neighbors would feel uncomfortable or sad reading this, they have a kid, you know..).

---

### Post by vasa1 on 2014-05-10
If you don't want to turn off the icon tooltip altogether but just make it less huge, look for:
```
XfdesktopIconView::tooltip-size = 32
```in your theme's gtkrc and change the value there.

---

### Post by vasa1 on 2014-05-10
[QUOTE=kc1di;13019519]One way is to run the following in a terminal.
...
What you describe is a way to turn off the notifications. As it turns out, OP wanted to prevent tooltips from appearing on the Xfce desktop.

---

### Post by matt103 on 2014-05-10
> **bapoumba said:**
> You won the prize indeed : you can now go to Thread Tools, and mark your thread as solved, congrats :tongue:

(and in the future, even if I understand it was a light or funny remark, please bear in mind that your first sentence can make some people uneasy. I'm sure my very nice neighbors would feel uncomfortable or sad reading this, they have a kid, you know..).

Thank you for the advice regarding closing the thread, I will do this now. 
Your additional politically corrective comments draw unnecessary attention to obvious humour.

---

