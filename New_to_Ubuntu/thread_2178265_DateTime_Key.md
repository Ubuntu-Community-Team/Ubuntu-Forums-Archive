---
title: "Date/Time Key"
date: 2013-10-02
forum: New to Ubuntu
---

### Post by Kompftputer on 2013-10-02
I want to assign a custom keymap that inserts a Timestap as if I typed it out myself.

Under Unity Ubuntu 12.10 LTS, I type keyboard into the Dash, then I click on "Keyboard" app, not "Keyboard Layout" that one doesn't appear to do what I wanted it to do. Then I click on the "Shortcuts" tab, go down to "Custom Shortcuts" and then click on the + symbol to add the following.

Name: timestamp
Command: echo -n "`date`"

This didn't work for me, I don't know what command to put to make it work, please fix this problem for me it is quite an issue since I have no idea what command even means.

echo -n "`date`" works in the terminal for me but my key doesn't work, I set it to using Ctrl+Alt+Space.

---

### Post by grahammechanical on 2013-10-02
I do not have the answer but I have tried to do this myself just now and it is my guess that the command is incorrect. That command in a terminal will echo or print these characters on the terminal screen 'date'  The echo command put an echo or prints whatever characters we have between the quotation marks.

What particular application do you wish to do this with? In Libreoffice we go to Insert>Fields and select either Date or Time or both.

---

### Post by steeldriver on 2013-10-02
You could do something like this, I think

1. install xclip

2. set the shortcut command to generate the date and copy it into the clipboard
```
sh -c 'echo `date` | xclip -selection clipboard'
```

3. to insert the date into your current application, you can then press your shortcut key combo followed immediately by the application's paste shortcut e.g. Ctrl-v 

I just gave it a try and it seemed to work for me, at least into gedit and libreoffice writer

---

### Post by Kompftputer on 2013-10-02
Yes, thanksalot, that works very well for me! :guitar:
It is a little inconvenient to press both twice, do you know if I can make a command that includes keystrokes? Ctrl+Alt+SPACEBAR and then Ctrl+V.
But otherwise I am exeedingly happy with it, was looking for a while until I bothered to ask in here, everything I found was overcomplicated.
Thanks again! I'm unbelievably gratefull!

---

### Post by Vaphell on 2013-10-02
you can add **; xdotool key ctrl+v** inside the single quotes to automatically generate 'paste' signal. Alternatively if you used primary buffer with xclip you'd be able to paste with middle click (**xdotool click 2**).
Personally i use xsel instead of xclip, it's shorter :-)
xsel -pi (put into primary buffer of middleclick)
xsel -si (secondary)
xsel -bi (clipboard ctrl+v)

---

### Post by Kompftputer on 2013-10-02
Okay.
I have installed xdotool.
This is my code ```
sh -c 'echo `date --rfc-3339=seconds` | xclip -selection clipboard'
```
What do I do with it now? I don't understand anything else of what you posted, it's all alien to me.
Where do I put what where?
I have installed xsel now. I hope it's not just for office suites as in excell, I want to paste timestamps everywhere, all over the place, upside-down even. Web Browsers and Filenames, I dunno where else but just assume if it exists I want it timestamped on.

---

### Post by stinkeye on 2013-10-02
> **Kompftputer said:**
> Okay.
I have installed xdotool.
This is my code ```
sh -c 'echo `date --rfc-3339=seconds` | xclip -selection clipboard'
```
What do I do with it now? I don't understand anything else of what you posted, it's all alien to me.
Where do I put what where?
I have installed xsel now. I hope it's not just for office suites as in excell, I want to paste timestamps everywhere, all over the place, upside-down even. Web Browsers and Filenames, I dunno where else but just assume if it exists I want it timestamped on.

[COLOR="#696969"]I can't get anything to work with keyboard shortcuts whether I put in a command or the path to a script in unity 13.04.[/COLOR]
**[COLOR="#FF0000"]Edit:[/COLOR]** Found custom shortcuts had been disabled somehow.
Maybe through installing another desktop.
Check the output of this command...
```
gsettings get org.gnome.settings-daemon.plugins.media-keys active
```
If it returns false, set back to default(true) with this command....
```
gsettings reset org.gnome.settings-daemon.plugins.media-keys active
```
Should now be able to set a custom keyboard shortcut.
Use this as the command in the custom shortcut comand box
```
sh -c "sleep 1 && xdotool type $(date --rfc-3339=seconds)"
```
[ATTACH=CONFIG]246692[/ATTACH]
----------------------------------------------------------------------


This command works with easystroke(mouse gestures) though....
```
xdotool type $(date --rfc-3339=seconds)
```

...and the same command with a delay so your keypress doesn't interfere,  works with the compiz commands plugin (bound to ctrl+alt+d)...
```
sleep 1 && xdotool type $(date --rfc-3339=seconds)
```

---

