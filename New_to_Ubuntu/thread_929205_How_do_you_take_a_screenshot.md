---
title: "How do you take a screenshot?"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by Sarah L on 2008-09-24
In KDE, when you press the PrintScreen key, the application "ksnapshot" is launched, opening up a little window with a preview of your screenshot and the option to save to a file or copy to the clipboard.

Using the combination Alt-PrintScreen puts a screenshot of the focused window in the clipboard.
Using the combination Control-Printscreen puts a screenshot of the entire screen into the clipboard.

I find that launching KSnapshot every time I want to take a quick screenshot is very frustrating. I would prefer that hitting the PrintScreen button takes a full screen screenshot and saves it to the clipboard.

How can I switch PrintScreen to saving a full screen screenshot and Control-Printscreen to launching KSnapshot? (Simply swap these two hotkeys.)

Any help is appreciated! :)

---

### Post by philinux on 2008-09-24
Kmenu> system settings> keyboard and mouse 

choose keyboard then from the pulldown select khotkeys.

---

### Post by nowshining on 2008-09-24
it's already save to a clipboard :) the hotkeys quit working for me sooo....

open up the run dialog box in the menu and enter kcontrol, from there press enter, regional and accessibility - input actions - preset actions - on the right side after highlight preset actions check disable - click apply..

---

### Post by Sarah L on 2008-09-24
> **philinux said:**
> Kmenu> system settings> keyboard and mouse 

choose keyboard then from the pulldown select khotkeys.

Sorry philinux, but I cannot find the "pulldown" that has the option "khotkeys" in KDE System Settings.

Nowshining, your method disables KSnapshot but now pressing PrintScreen does nothing. No screenshot is saved to the clipboard.

Could anyone clarify on their methods?

---

### Post by nowshining on 2008-09-24
> **Sarah L said:**
> Sorry philinux, but I cannot find the "pulldown" that has the option "khotkeys" in KDE System Settings.

Nowshining, your method disables KSnapshot but now pressing PrintScreen does nothing. No screenshot is saved to the clipboard.

Could anyone clarify on their methods?

it's saved to the clipboard, open up gimp or another photo program and paste...

---

### Post by Sarah L on 2008-09-25
I pressed the PrintScreen key.
I opened up Gimp and pasted.
I got the following message:

   There is no image data in the clipboard to paste.

---

### Post by Ryadt on 2008-09-25
You can try by using the command-line.
Install scrot
```
sudo apt-get install scrot
```
Take a screen shot by doing
```
scrot MyScreenshot.png
```

---

