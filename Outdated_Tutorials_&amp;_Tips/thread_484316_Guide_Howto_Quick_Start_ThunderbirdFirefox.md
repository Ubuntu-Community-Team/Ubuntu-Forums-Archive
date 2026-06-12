---
title: "Guide: Howto Quick Start Thunderbird/Firefox"
date: 2007-06-25
forum: Outdated Tutorials &amp; Tips
---

### Post by IMELucky on 2007-06-25
This a step-by-step guide to have Firefox and Thunderbird start automatically in the background when you log into your session. I find it to be especially useful for Thunderbird, because that way it checks my email right away and I get a friendly notification if I have new mail.

Unless I am mistaken, there is no minimize-to-tray extension for Mozilla applications for Linux. However, we can use the program "Alltray" to mimic this feature. Heres how to do it:

Note: These directions are specificlly written for GNOME, but can be easily adapted for other desktops

1) Open your terminal window by pressing ALT-F2 and typing "gnome-terminal"

2) sudo apt-get install alltray

3) gedit .Mozilla_Start.sh

4) Now copy and paste this into your text editor

#!/bin/bash

alltray firefox &
alltray thunderbird &

5) Save and exit the text editor

6) Make the file executable

7) Go to System->Preferences->Sessions

8) Click on "New" and Type "Mozilla Start" in the Name section, and add the path to your .Mozilla_Start file

There you go, now when you start your session you will see a tray icon for both Firefox and Thunderbird. Other programs can be added by editing the script

A word about Firefox 2 restore feature....

You may find Firefox asking you if you want to restore the current session each time you log in. This feature can easily be disabled.

Open Firefox and type "about:config"
Right click and select New-Boolean

Type browser.sessionstore.enabled and set it to "false"

---

### Post by tak1150 on 2007-06-26
IMELucky,

Thank you! I've been looking for something like this. It works great!

---

### Post by forger on 2007-07-04
because i use gmail manager, it asks me for my master pass on start. that breaks my alltray and doesn't show firefox in tray after I type the pass

---

### Post by markusf21 on 2007-07-16
I tried this and it works for firefox but not thunderbird i just copy/pasted so im sure it got it right im using version 1.5

---

### Post by markusf21 on 2007-07-16
Never mind i figured it out 
#!/bin/bash

alltray mozilla-thunderbird &

---

### Post by Soarer on 2007-07-16
Well, that's just excellent!

Thanks, IMELucky :)

---

