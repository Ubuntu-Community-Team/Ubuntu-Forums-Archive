---
title: "wireless adapter is disabled and I need help"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by Jonesd22 on 2008-04-28
Ok so I am new to linux.  I have installed ubuntu 8.04 on a compaq laptop and everything so far is running fine.  Except for the wireless adapter.  I was able to get to ther terminal using commands found that it shows disabled.  How do you enable it?

---

### Post by hermes0710 on 2008-04-29
> **Jonesd22 said:**
> Ok so I am new to linux.  I have installed ubuntu 8.04 on a compaq laptop and everything so far is running fine.  Except for the wireless adapter.  I was able to get to ther terminal using commands found that it shows disabled.  How do you enable it?

You do have an icon indicating the connections on the system tray right? If yes right click on it and see if the popped menu gives you the ability to enable wireless

---

### Post by Khalis7 on 2008-04-29
> **Jonesd22 said:**
> Ok so I am new to linux.  I have installed ubuntu 8.04 on a compaq laptop and everything so far is running fine.  Except for the wireless adapter.  I was able to get to ther terminal using commands found that it shows disabled.  How do you enable it?

Hi. Make sure your wireless device switch is turned on if you have any.If it's already turned on but still nothing happens, you may restart the networking interfaces by typing this in terminal:
```
sudo /etc/init.d/networking restart
```

---

