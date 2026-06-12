---
title: "Remembering default browser - asks me every time I login"
date: 2014-06-16
forum: New to Ubuntu
---

### Post by PeterRJG on 2014-06-16
Title says it all really. 

But...when I click on the Browser icon in the menu, I get presented with a dropdown of choices - despite having set Chromium as my default in Preferred Applications. Further, Chromium throws up that dialogue that it's not the default browser even though I set it to yes every time.

I'm sure it's just a simple config file issue but I've no idea which one to edit. There's nothing I can see under ~/.config that deals with this. 

It's not mission critical - it's just annoying but I'd like to get rid of it.

Thanks in advance.

---

### Post by LastDino on 2014-06-16
Which version of Ubuntu? 

There is generally option to edit default applications in settings.

---

### Post by PeterRJG on 2014-06-16
> **LastDino said:**
> Which version of Ubuntu? 


Xubuntu 14.04

> 
There is generally option to edit default applications in settings.

Yes, already said I've done that. What's happening is that it's not taking heed of the preferred application setting. I'm getting the dropdown dialogue when I click on browser - rather than open Chromium which I was what I've set it to as my preferred application.

---

### Post by LastDino on 2014-06-16
Try it once again following this method by accessing GUI with privileges;
```

sudo bash
xfce4-settings-manager

```[COLOR=#333333][FONT=UbuntuRegular]
[FONT=arial]or
[/FONT][/FONT][/COLOR]```

gksu xfce4-settings-manager

```[COLOR=#333333][FONT=UbuntuRegular]
[FONT=arial]then select preferred apps, and under browsers select other then paste:

[/FONT][/FONT][/COLOR]```

/usr/bin/chromium-browser

```[COLOR=#333333][FONT=UbuntuRegular]


[/FONT][/COLOR]

---

### Post by PeterRJG on 2014-06-16
Hmm, tried the gksu route. Did what you suggested but it's still presenting me with the dropdown box when I click on Browser - and Chromium still isn't remembering the default browser setting. I logged out and back in again to test the changes.

Edit - I just added the Chromium shortcut to the panel, but it's still asking me about the default browser setting.

---

### Post by LastDino on 2014-06-16
> **PeterRJG said:**
> Hmm, tried the gksu route. Did what you suggested but it's still presenting me with the dropdown box when I click on Browser - and Chromium still isn't remembering the default browser setting. I logged out and back in again to test the changes.

Edit - I just added the Chromium shortcut to the panel, but it's still asking me about the default browser setting.

hmm try

```
[FONT=Ubuntu Mono]sudo update-alternatives --set x-www-browser /usr/bin/chromium[/FONT]


```

---

### Post by slickymaster on 2014-06-16
If by any chance LastDino solution doesn't work, you can try to set it using the **update-alternatives** command. In a terminal command run:```
~$ sudo update-alternatives --config x-www-browser
There are 2 choices for the alternative x-www-browser (providing /usr/bin/x-www-browser).

  Selection    Path                       Priority   Status
------------------------------------------------------------
* 0            /usr/bin/firefox            40        auto mode
  1            /usr/bin/chromium-browser   40        manual mode
  2            /usr/bin/firefox            40        manual mode

Press enter to keep the current choice
[*], or type selection number:
```
You'll have to enter the selection number for the desired browser.

---

### Post by PeterRJG on 2014-06-16
Yes, that fixed it. Thank you very much.

---

### Post by greenjumper on 2014-07-02
Slickymaster's tip seems to have worked for me too - thanks!!

---

