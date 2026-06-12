---
title: "Keyboard Shortcut Keys"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by RealG187 on 2008-07-25
Okay on my laptop I have 4 buttons, one with an "e" (Acer laptop, in windows it would start Acer Empowering Technology), one with an envelop (in windows it started outlook express, or uTorrent after I configured it), and a globe (in windows started browser) and a "p" (in windows started the program to assign these buttons.)

The Envelop opens "Evolution Mail" in Gnome and Kmail in KDE.

Before the globe opened Firefox, but I removed Firefox 3 Beta 5 and put back on Firefox 2. Now it says "Couldn't execute the command Firefox/verify that this is a valid command"

I know to open Firefox 2 the command is "firefox2" so how can I make that button do that command instead? And since I dont use any email clients (I use webmail) I wanna make the envelop button do something else too. And the E and P.

---

### Post by ajmorris on 2008-07-27
> **RealG187 said:**
> Okay on my laptop I have 4 buttons, one with an "e" (Acer laptop, in windows it would start Acer Empowering Technology), one with an envelop (in windows it started outlook express, or uTorrent after I configured it), and a globe (in windows started browser) and a "p" (in windows started the program to assign these buttons.)

The Envelop opens "Evolution Mail" in Gnome and Kmail in KDE.

Before the globe opened Firefox, but I removed Firefox 3 Beta 5 and put back on Firefox 2. Now it says "Couldn't execute the command Firefox/verify that this is a valid command"

I know to open Firefox 2 the command is "firefox2" so how can I make that button do that command instead? And since I dont use any email clients (I use webmail) I wanna make the envelop button do something else too. And the E and P.

hi there,
this can probably be done through some configuration options in gnome, or kde. However, if you cannot find the option, you could temporarilly, open a terminal, and do ```
sudo ln -s /usr/bin/firefox2 /usr/bin/firefox
``` This will create a symbolic link 'firefox' pointing to firefox2, making your button work. However, if you upgrade to firefox 3 again (it is no longer a beta) be sure to remove this symlink first.

AJ

---

### Post by RealG187 on 2008-07-28
How would that work? Would it make the command firefox link to the command firefox2?

---

### Post by cdtech on 2008-07-30
Restructuring the keycodes can be done with "lineakd" but there is a lot of reading and understanding how the kernel detects the scancodes of each key pressed.

Some keys just work, because their hardwired (Fn+F4, Fn+F6, Fn+F7, Fn+Arrow left, Fn+Arrow right); you can leave those alone. The other keys can be devided into 2 categories: the keys that are recognized by the kernel, and those that are not.

To be able to program the keys, they must be recognized by the kernel. Using "xve" will tell you which keys are recognized.

Hope this gets you started..........

---

### Post by RealG187 on 2008-07-31
I think I figuured it out.

UNder System --> Preferences --> Keyboard Shortcuts I can configure "XF86WWW" to run the internet browser. This was setup right, it told the OS to start the browser. The problem was that the OS ran the command "firefox" when it should have ran "firefox-2:

when I went to system --> preferences --> preferred applications I changed the command it ran.

So what was funny is I thought the key was programmed wrong, when it was programmed right (to run the browser), but the system tried to run the wrong browser (that no longer existed).

In short, I changed my default browser and they key works!

---

