---
title: "Boot up problem"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by dwally89 on 2008-05-27
Hi,

My computer is running fine, however at boot up, when the Ubuntu bar is loading, I'm presented with loads of text and [OK]'s.

How can I hide this?

Thanks

---

### Post by sayakb on 2008-05-27
Install via terminal:
```
sudo apt-get install startupmanager
```Goto System->Administration->Startup-manager and on the **Boot Options** tab under **Misc.** topic, uncheck **"Show text during boot"**

---

### Post by dwally89 on 2008-05-27
OK, I installed the program, and that box isn't ticked.

Any ideas why the text is still being shown?

Thanks

---

### Post by Duck2006 on 2008-05-27
In your menu.lst on the kernel line do you have "quiet splash". If you don't add it and it should hide the text.

---

### Post by dwally89 on 2008-05-27
Yeah it says quiet splash.

Any other reason why the text might be showing?

---

### Post by Majorix on 2008-05-27
By default, Ubuntu is set to show nothing if no service fails to start. I rarely get those Matrix-like text flowing through the screen, but when I look closely, it starts with one service failing to boot up.

---

### Post by sayakb on 2008-05-27
Do see only text or the logo + bar + text. If you see only text, press Ctrl+Alt+F7 and see if it hides the text.

---

### Post by dwally89 on 2008-05-28
I start off by seeing the Logo and bar, then very shortly after, it is all replaced by the text.

I tried Ctrl-Alt-F7 and nothing happened.

Is there a way I can find a log of that text that is appearing and post it on the forums to check if anything is wrong?

Thanks

---

### Post by sayakb on 2008-05-28
Seems like some error message is coming up and that is showing the tty text output..

---

### Post by dwally89 on 2008-05-28
Where can I find a log of all the text?

---

### Post by sayakb on 2008-05-28
System->Administration->System Log. Not sure which section..

---

### Post by dwally89 on 2008-05-28
Anyone know which section?

---

