---
title: "Network Manager ticked in Add/Remove but not in tray?"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by spocksbeard on 2008-10-24
I recently installed Hardy and managed to delete what I'm pretty sure was Network Manager from the tray (next to the clock) although I still have something in there which the tool-tip tells me is called "Manual network configuration". 

I went to add/remove in the Applications menu and found network manager but it is still ticked, meaning it is installed already(?). Is there a way to get it back to the tray? 

I am still connected to my wireless network but would like to use network manager to connect automatically to my university network as I'm not too familiar with networking or Ubuntu yet.

Thanks in advance

---

### Post by mike555 on 2008-10-24
Just click an empty spot by where you want it and add it , just like you would any launcher ........

---

### Post by marco123 on 2008-10-24
There are 2 things you could do.

1.  Try logging out and logging back in again see if that solves it.

2. Right click on an empty section of the panel and select "Add to Panel..." then select "Network Monitor".

---

### Post by kpkeerthi on 2008-10-24
Go to System -> Preferences -> Sessions -> Startup Programs and add **nm-applet** under Command

Reboot.

---

