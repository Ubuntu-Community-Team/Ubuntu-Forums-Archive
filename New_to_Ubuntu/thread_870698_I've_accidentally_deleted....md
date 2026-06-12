---
title: "I've accidentally deleted..."
date: 2008-07-26
forum: New to Ubuntu
---

### Post by jozmoz on 2008-07-26
I've accidentally deleted my wireless network icon that sits on the top bar. I can't see it in the 'add' list to display it again. How do I get it back?

Please help. Thanks:)

---

### Post by iaculallad on 2008-07-26
> **jozmoz said:**
> I've accidentally deleted my wireless network icon that sits on the top bar. I can't see it in the 'add' list to display it again. How do I get it back?

Please help. Thanks:)

For the Network Manager:

Right-click on the top-panel and select "Add to Panel", under "Utilities" -> select "Notification Area" and click on Add button.

For the Network Monitor:

Right-click on the top-panel and select "Add to Panel", under "System and Hardware" -> select "Network Monitor" and click on Add button.

---

### Post by jozmoz on 2008-07-26
which one is the one that displays your wireless connections?

---

### Post by kunixos on 2008-07-26
They both do. Choose one and use the instructions to get it up and running.

---

### Post by jozmoz on 2008-07-26
which is the icon that when you install ubuntu, its sitting in the top bar and when you click on it it shows you the available wireless networks that you can connect to?

---

### Post by bhadotia on 2008-07-26
> **jozmoz said:**
> which is the icon that when you install ubuntu, its sitting in the top bar and when you click on it it shows you the available wireless networks that you can connect to?
The notification area.

---

### Post by jozmoz on 2008-07-26
when i right click top panel and choose 'add to panel' there is no 'utilities' option in my list?

---

### Post by jozmoz on 2008-07-26
there is no 'Utilities' or System & Hardware' in my 'add to panel' list? how do i get them in the list?

Please help.

---

### Post by iaculallad on 2008-07-26
> **jozmoz said:**
> when i right click top panel and choose 'add to panel' there is no 'utilities' option in my list?

Open your terminal and issue the following commands below:

```
sudo gnome-session-remove gnome-panel
sudo gconftool-2 --recursive-unset /apps/panel
sudo gnome-panel &
```

EDIT: corrected command

---

### Post by bhadotia on 2008-07-26
> **jozmoz said:**
> when i right click top panel and choose 'add to panel' there is no 'utilities' option in my list?
Can you post a snapshot of your panel list window?

---

### Post by jozmoz on 2008-07-26
sorry i'm an absolute beginner:) How do i open up the terminal and issue that command?

---

### Post by iaculallad on 2008-07-26
> **jozmoz said:**
> sorry i'm an absolute beginner:) How do i open up the terminal and issue that command?

Applications->Accessories->Terminal

---

### Post by jozmoz on 2008-07-26
thanks i'll give it a go:)

---

