---
title: "Preferred applications in Ubuntu 11.10"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by solongsoho on 2011-10-15
Where can i configure the preferred applications in 11.10? I want to enter on other programs then the one they offered me. For example Chromium instead of Firefox.

How can I do it?

---

### Post by will547_us on 2011-10-15
Click the Ubuntu symbol at the top of your Unity panel,
Click the Internet apps,
Click other, choose Chromium

---

### Post by bob53124 on 2011-10-15
Open Chromium then open settings/prefrences and then click make chromium my default browser you might have to change the icon on the side panel but it will appear above browse the web when the ubuntu button is clicked

---

### Post by solongsoho on 2011-10-15
I'm sorry if this sounds stupid but I really can't see that ubuntu sign there. The only one is the one I click to go to the menu.

---

### Post by will547_us on 2011-10-15
It's normally above your Home folder.

---

### Post by solongsoho on 2011-10-15
No, no. I actually wanted to use Rhytmbox instead of Banshee  (the one with Chromium was just and example). I tried to uninstall Banshee and I installed Rhytmbox but Movie player appears there as the first program.

---

### Post by like coffee on 2011-10-16
Need to know this to.
We need the use as default app dialog back.

---

### Post by smurf69 on 2011-10-16
What if you try to go System Settings>System info>Default Applications ?

---

### Post by like coffee on 2011-10-16
So thats where they hid it.
Thanks! 

But still this only covers the most usual filetypes.

---

### Post by mcduck on 2011-10-16
> **like coffee said:**
> So thats where they hid it.
Thanks! 

But still this only covers the most usual filetypes.

If you want to set the default application for an actual *filetype*, instead of a certain task (like audio player/video player/internet browser etc), it's done the same way as in previous Ubuntu version; right-click a file, select "Properties", go to "Open With"-tab, select the program you want and click the "Set as Default"-button.

---

### Post by like coffee on 2011-10-16
Thats what I wanted, thanks.
Can't believe I missed that, used to use the dialog in "open with>other applications" wich they removed.

Thanks again.

---

### Post by brylevdaniel on 2011-10-17
This can be done in System Settings -> System Info -> Default Applications.

But after I set default browser to Chromium, some applications (e.g. Pidgin) still used Firefox as default. The way I solve this:
```
sudo update-alternatives --config gnome-www-browser
sudo update-alternatives --config x-www-browser
```

---

### Post by curracruisers on 2011-11-09
I have a similar problem in that the app I want to set as default is not in the "Open with" list. there used to be a "run command" option for those apps but not anymore. The app appears in the launcher and menus ok. How do I make it appear in the "Open with" list?

---

