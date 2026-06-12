---
title: "slight panel problem from 8.04 to 8.10"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by Dark006 on 2008-11-01
After upgrading from 8.04 to 8.10 I ran into a few problems (nVidia and wireless network problems mainly). I got those fixed and moved on to changing the theme to try out the new DarkRoom theme. I ended up changing it back to what I originally had and then tried to remove a separator from the panel.

When I did this it also got rid of the wireless status icon. Now every time I open a program that should have an icon appear (like pidgin, transmission, amarok, etc. etc.)in the top panel nothing shows up. 

Anyone know how to get those icons to appear again when the respective program is open?

---

### Post by fullmetalgerbil on 2008-11-01
I suppose you've tried right clicking on the panel and selecting "add to panel"? I'm not trying to be a smartass, that's just the only way I'd know how to fix it.

---

### Post by Dark006 on 2008-11-01
Yeah, I've tried that. I have firefox, pidgin, and a terminal icon in the top left so I can easily start them from the panel. But I'm talking about once a program is actually started then you'd be able to see it in the top right (usually, and for example, like when pidgin is running you can right click on the icon to change status etc. etc.).

---

### Post by Potters Son on 2008-11-01
The network icon is usually the first icon in the Notification Area panel applet. It's weird, but the wireless icon is not a standalone applet. It's part of the notification area (like the light blue box on the taskbar in WinXP), and the notification area is preceded by a separator.

In other words, if you want the network manager (and other things such as battery status), then you have to have the separator (unless someone clever finds a way around it).

---

### Post by Dark006 on 2008-11-01
I figured it out, I just had to add the Notification Area back to the panel and now every thing works fine.

---

