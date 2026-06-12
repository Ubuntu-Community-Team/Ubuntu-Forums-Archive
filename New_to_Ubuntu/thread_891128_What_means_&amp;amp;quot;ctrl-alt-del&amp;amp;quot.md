---
title: "What means &amp;amp;quot;ctrl-alt-del&amp;amp;quot; in Ubuntu-speak?"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by Auspicious on 2008-08-15
I put in the live CD for the first time, got online, looked at a couple of websites, then closed the Firefox window.  It closed just fine, then the computer froze... the same situation when, in Windows, I'd hit ctrl-alt-del.  Does that do the same thing in Ubuntu?  Is there an equivalent operation to try?

---

### Post by dje on 2008-08-15
Ctrl + Alt + Backspace restarts the graphical interface (X)
Ctrl + Alt + F 1-7 switches to a terminal so you can kill non responding programs:
```
killall *program name*
```
or (get the PID, process id, from the first command in the second column of the output)
```
ps -ef | grep *program name*
kill *pid*
```
Ctrl + Alt + PrntScrn + REISUB reboots the computer

dje

---

### Post by Auspicious on 2008-08-15
What's REISUB?

---

### Post by Auspicious on 2008-08-15
ctrl + alt + backspace didn't do anything, and I don't know what program is causing a problem (or if it's a program thing at all, I sort of just assumed I overwhelmed the computer with the CD)

Of course, my baby just woke up, so right now my goal is just to safely get the CD out and the computer off.

---

### Post by Auspicious on 2008-08-15
Hmm... ctrl+alt+F1 didn't do anything, either.

---

### Post by dje on 2008-08-15
press the keys R E I S U B in that order while holding Ctrl Alt and PrntScrn
also how much ram and what processor do you have

dje

---

### Post by tahina on 2008-08-15
Wow, I didn't know there was anything to do if ctrl-alt-backspace and ctrl-alt-F1 failed...

---

### Post by Auspicious on 2008-08-15
Right, that worked!  (And my son's back to sleep, whew...)

The front of the computer says:
"Intel Pentium 4 processor 641" and "512 MB DDR2"

I hope those are the answers to your questions, I'm sooo used to looking this stuff up in Vista and don't know how to check it in Ubuntu (yet.)

---

### Post by dje on 2008-08-15
strange it shouldnt keep freezing as your computer is powerful enough to run the live cd. you know you get a menu just before booting the live cd with the ubuntu logo with options to install and try ubuntu without installing etc ? when you get to that select the option to check the cd for errors and see if it is ok

dje

---

### Post by Auspicious on 2008-08-15
I just restarted again to doublecheck... I never see an option to check the CD.  There's a screen for selecting a language with a countdown to the side and menu options for F1-6 at the bottom, then it loads the linux kernel, then Ubuntu, then I'm at the desktop.

If it matters, I have the 8.04.1 LTS Desktop Edition

---

### Post by HittingSmoke on 2008-08-15
> **dje said:**
> Ctrl + Alt + Backspace restarts the graphical interface (X)
Ctrl + Alt + F 1-7 switches to a terminal so you can kill non responding programs:
```
killall *program name*
```
or (get the PID, process id, from the first command in the second column of the output)
```
ps -ef | grep *program name*
kill *pid*
```
Ctrl + Alt + PrntScrn + REISUB reboots the computer

dje

Questions, how to you get back to KDE from the terminal or launch KDE from a terminal when it isnt running?

---

### Post by dje on 2008-08-15
> **HittingSmoke said:**
> Questions, how to you get back to KDE from the terminal or launch KDE from a terminal when it isnt running?

Ctrl + Alt + F7 if its running

```
startx
```
or
```
sudo /etc/init.d/kdm start
```
if it isn't

dje

---

### Post by dje on 2008-08-15
> **Auspicious said:**
> I just restarted again to doublecheck... I never see an option to check the CD.  There's a screen for selecting a language with a countdown to the side and menu options for F1-6 at the bottom, then it loads the linux kernel, then Ubuntu, then I'm at the desktop.

If it matters, I have the 8.04.1 LTS Desktop Edition

try pressing f4 at the menu (i cant remember the precise location of it but it is there somewhere, have a dig around that cd boot menu ;) )

dje

---

### Post by picpak on 2008-08-15
If you go to Accessories > Terminal and run

```
gconftool-2 --type string --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"

gconftool-2 --type string --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"
```

it will set the System Monitor to load when you run Ctrl-Alt-Del.

---

### Post by Sef on 2008-08-15
>  Originally Posted by Auspicious  View Post
I just restarted again to doublecheck... I never see an option to check the CD. There's a screen for selecting a language with a countdown to the side and menu options for F1-6 at the bottom, then it loads the linux kernel, then Ubuntu, then I'm at the desktop.

If it matters, I have the 8.04.1 LTS Desktop Edition

It is in the list of options (boot into live cd, install, mem86 test.)  It is 'Check disk for defects', if I remember correctly.

---

### Post by dje on 2008-08-15
> **picpak said:**
> If you go to Accessories > Terminal and run

```
gconftool-2 --type string --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"

gconftool-2 --type string --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"
```

it will set the System Monitor to load when you run Ctrl-Alt-Delete.

but not if the whole system freezes as is happening (restarting x or switching to tty will not work) ;)

dje

---

### Post by Auspicious on 2008-08-15
I did find the CD check, it was under F6.  : )

If anyone else is reading this thread for help:  I had to hit "enter" to select English before I could pick F6 to get into the menu where the CD check is.

---

### Post by picpak on 2008-08-15
> **dje said:**
> but not if the whole system freezes as is happening (restarting x or switching to tty will not work) ;)

dje

True, but this is great for a single-window crash. :) In the event of a full system freeze where neither Ctrl-Alt-BackSpace or Ctrl-Alt-F1 thru F6 works, I just hit the reset button on my computer. Bad style, I know, but it works.

---

### Post by dje on 2008-08-15
> **picpak said:**
> True, but this is great for a single-window crash. :) In the event of a full system freeze where neither Ctrl-Alt-BackSpace or Ctrl-Alt-F1 thru F6 works, I just hit the reset button on my computer. Bad style, I know, but it works.

i dont have one so i use Ctrl + Alt + PrntScrn + R E I S U B :D

dje

---

### Post by tech0007 on 2008-08-15
Is Ctrl + Alt + PrntScrn + R E I S U B the same as Alt + SysRq + R E I S U B ?

---

### Post by dje on 2008-08-15
> **tech0007 said:**
> Is Ctrl + Alt + PrntScrn + R E I S U B the same as Alt + SysRq + R E I S U B ?

not sure, i've never heard of that one before. if theyre not the same i'm sure they do much the same job :D

dje

---

### Post by picpak on 2008-08-15
> **dje said:**
> i dont have one so i use Ctrl + Alt + PrntScrn + R E I S U B :D

dje

That's probably better. :) I'm scared of mine; it's sensitive. :lolflag:

---

### Post by dje on 2008-08-15
> **picpak said:**
> That's probably better. :) I'm scared of mine; it's sensitive. :lolflag:

poor thing it probably hates being used, think of your reset button and use those keystrokes!! :lolflag:

---

