---
title: "Set Default Font for Arabic Language (System-Wide)?"
date: 2016-01-14
forum: New to Ubuntu
---

### Post by miso77 on 2016-01-14
Hi,

Newbie Ubuntu 15.10 user here (Linux in general). The default Arabic font that is being rendered is not good looking.

I installed the new Ubuntu Arabic.TTF (copied from 16.04) and created a [COLOR=#000000][FONT=Courier New]~/.fonts.conf and placed this in it:

[/FONT][/COLOR][COLOR=#000000][FONT=Courier New]
[/FONT][/COLOR]```
<?xml version='1.0'?>
<!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
<fontconfig>
<match target="pattern">
<test name="lang" qual="any">
<string>ar</string>
</test>
<edit name="family" mode="assign" binding="same">
<string>Ubuntu Arabic</string>
</edit>
</match>
</fontconfig>[COLOR=#000000][FONT=Courier New]
[/FONT][/COLOR]
```[COLOR=#000000][FONT=Courier New]
[/FONT][/COLOR][COLOR=#000000][FONT=Courier New]
[/FONT][/COLOR][COLOR=#000000][FONT=Courier New]Firefox now displayed Arabic texts well, but not Chromium. Also, LibreOffice is not defaulting to this for Arabic text (I have to choose the font from list).

How Can I make Ubuntu Arabic.TTF the default Arabic font for everything (Browsers, programs, etc.)[/FONT][/COLOR][COLOR=#000000][FONT=Courier New]


[/FONT][/COLOR]

---

### Post by amirmasoud on 2016-01-27
To change font of the window title bars and some tightly integrated apps, you can install Unity Tweak Tool from the Ubuntu Software Center. Run it, go to "Fonts" section, and set the default font to whatever you like. However, this does not affect all desktop programs, notably, LibreOffice.

For LibreOffice, you need to change the default LibreOffice template. I have once explained this process on this page: [https://goo.gl/MxocRZ](https://goo.gl/MxocRZ) Although the page is written loooong ago, I think the process is still more or less the same. (Sorry, the page is in Persian, but I think the pictures are clear, and you can always use some online translator).

Hope this helps.

---

