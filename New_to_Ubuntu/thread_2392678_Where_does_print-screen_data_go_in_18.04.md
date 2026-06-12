---
title: "Where does print-screen data go in 18.04?"
date: 2018-05-23
forum: New to Ubuntu
---

### Post by wrongusername2 on 2018-05-23
In case of 16.04, when I press 'Print Srcn' an application used to **capture** the *view* and show it in a separate dialog box. That dialog box had "Copy to clipboard' or 'Save' buttons. In case of 18.04 the behavior is different.
In case of 18.04, when I press 'Prny Sscrn', I hear the sound but no application seems to capture the data. 
Please help me make 18.04 behave like 16.04.

This is a fresh install of 18.04


Thanks

---

### Post by mc4man on 2018-05-23
Take a look in your Pictures folder

---

### Post by wrongusername2 on 2018-06-02
Thanks I will check it.

---

### Post by wrongusername2 on 2018-06-09
[COLOR=#000000][FONT=Arial]I did some research on this, and here is the solution.  Solution is when user presses PRINT, output goes to Clipboard instead of File. Since the data is in Clipboard, user can paste it anywhere.

 There  are settings in **Settings** to control the destination of screen capture output.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
 Most likely current state will be [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]      
          "PrntScr" =>  "Save a screenshot to Pictures"[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]          "Ctrl + PrntScr" =>  "Save a screenshot to Clipboard"[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]    
You may want it to be** reverse**           [/FONT][/COLOR]
```
[COLOR=#000000][FONT=Arial]           "PrntScr" =>  "Save a screenshot to Clipboard"[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]          "Ctrl + PrntScr" =>  "Save a screenshot to Pictures"[/FONT][/COLOR]

```[COLOR=#000000][FONT=Arial]    
Steps to do this[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]-High light "Save a screenshot to Pictures" and press "CTRL + Print"[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]-High light "Save a screenshot to Clipboard" and press "Print"[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Now onwards when you press PRINT, data will go to Clipboard, so that you paste it where ever you want.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]

---

### Post by lamino144 on 2018-09-19
Could you explain how to change the destination in **Settings?** I couldn't find anything related to screenshots.

---

### Post by jasomux on 2018-09-21
The settings for screenshots are in the keyboard shortcuts. Go to **Settings** => **Devices** => **Keyboard** and scroll down to the "Screenshots" section. There you can click on the action you want and enter the new key press you want to take that action, as well as review the current shortcut settings.

---

