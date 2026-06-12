---
title: "Unicode Input"
date: 2013-05-17
forum: New to Ubuntu
---

### Post by William D. on 2013-05-17
How do you input Unicode Characters (HEX) into Libre Office Documents (Ubuntu 13.04)?? I made up a word document in Windows 7 with the Characters I want and opened that document in Libre and can copy and paste. There must be a better way.   In Windows 7 MS Word you can use ALT +  Decminal number or the ALT + X (hex) method.  ALT + 0163 will give you the Britsh Pound symbol.

---

### Post by Irihapeti on 2013-05-17
You can use IBus (see input methods in the language settings dialogue) for this. Install ibus-m17n if it's not already installed, then choose Other->unicode(m17n) as the input method when you setup IBus.

Once it's configured, it can be used in other applications as well as LibreOffice. It's activated when needed with ctrl+space (and turned off the same way). The codes are entered by using ctrl+u, followed by the code.

---

### Post by William D. on 2013-05-18
I have Ibus already installed on Ubuntu However there is no place to enter the settings you talked about.  There is no  OTHER or anywhere else to select unicode.

---

### Post by Irihapeti on 2013-05-18
Have you installed ibus-m17n?

If you have, you need to click on the ibus notification icon, choose preferences, choose the input methods tab and click on the "customize active input methods" box. Then you can choose to activate an input method. If you just have m17n installed, Other is at the bottom of the list.

---

### Post by William D. on 2013-05-18
I found it -  had to do a install -   sudo apt-get install ibus ....etc...

Now I have a full list to pick from and  in OTHER is unicode.
Thanks.
Bill

---

### Post by Irihapeti on 2013-05-18
> I found it - had to do a install - sudo apt-get install ibus ....etc...

Right. I thought IBus was installed by default - apparently not in 13.04, anyway. Anyway, the main thing is that it's working now.

---

### Post by IsaacJGL on 2013-05-18
You can use the Character map in Accessories to choose hundreds of different characters and you can copy and paste them into your document.

---

### Post by CatKiller on 2013-05-18
If it's Unicode that you want, pressing Ctrl-Shift-U and then typing the number works, but most symbols you're likely to want have a Compose key shortcut, which is much neater.

---

### Post by William D. on 2013-05-18
I found it -&nbsp; had to do a install -&nbsp;&nbsp; sudo apt-get install ibus ....etc...<br><br>Now I have a full list to pick from and&nbsp; in OTHER is unicode.<br>Thanks.<br>Bill<br>

---

### Post by William D. on 2013-05-18
Thank you all for your replies.  I have a good start on Unicode input now and a lot more research to do.  Did not know there was a Character Map with Ubuntu.

---

