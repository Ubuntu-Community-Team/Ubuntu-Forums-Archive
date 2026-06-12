---
title: "Problem with cyrillic when paste from Chrome to Word 2007"
date: 2013-03-25
forum: New to Ubuntu
---

### Post by araks on 2013-03-25
Hi, everybody. I just started to use Ubuntu as my main OS instead of Windows 7. But,  for school I have to actively use Microsoft Office 2007 under Wine.
I'm from Ukraine, and I'm working with russian text.

**Problem:** 
1. When I copy-paste russian text from Google Chrome to Word 2007 I get something like this:
[IMG]http://storage9.static.itmages.ru/i/13/0325/h_1364209637_7933987_d41d8cd98f.png[/IMG]

2. When I copy-paste russian text from Google Chrome to LibreOffice or gedit everything is ok.
3. When I make copy-paste operation from Firefox to Word 2007 everything is ok.

[COLOR=#a9a9a9]Ubuntu 12.04 LTS + Wine 1.5.26 + Microsoft Office 2007 + Google Chrome [/COLOR][COLOR=#a9a9a9][FONT=Ubuntu]25.0.1364.172[/FONT][/COLOR]

How to fix this Google Chrome issue?

Thank you.

---

### Post by grahammechanical on 2013-03-25
May I suggest a way around this problem that may work? Use the same fonts in Libreoffice as you use in Word 2007. You have installed Wine? Yes? That may have installed Microsoft True Type core fonts. Did it? The Ubuntu Software Centre has an installer for installing MS true type core fonts. I cannot give you the exact name to search for as my Software Centre is crashing (I am using 13.04. These things happen on development releases).

Another thing that you can look for is the web page encoding. Is Chrome using the same encoding of the text on the page as MS Word 2007 is using. I am using Chromium. And In Chromium we go to Settings>Show Advanced Settings>Web Content and click Customize Fonts. At the bottom of the dialog you will see Encoding. In the drop down list you will find Western (windows-1252). That may be the setting you need. In Linux the setting is Unicode (UTF-8). There are other settings in that long list.

Regards.

---

### Post by schragge on 2013-03-25
> **grahammechanical said:**
> I cannot give you the exact name to search for I can
```
sudo apt-get install ttf-mscorefonts-installer
```

---

### Post by araks on 2013-03-25
Thank you for your aswers, guys, but:
1. Installer for Microsoft TrueType core fonts (ttf-mscorefonts-installer) already installed.
2. Played a lot with encoding in Chrome (with Western-1252 also).

These steps _do not_ solve the problem..
Are there any other tips?

---

