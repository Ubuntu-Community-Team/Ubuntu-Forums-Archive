---
title: "Keyboard shortcut to &quot;show desktop&quot;"
date: 2012-05-14
forum: New to Ubuntu
---

### Post by vasa1 on 2012-05-14
Xfce 4.10 has an icon in a panel that can be clicked to minimize all open windows and show the desktop. But I want a keyboard shortcut that will do the same thing. Is it possible?

---

### Post by brainwash on 2012-05-14
[Ctrl]+[Alt]+D

This is the default keyboard shortcut to show/hide the desktop. It affects all workspaces.

---

### Post by vasa1 on 2012-05-14
> **brainwash said:**
> [Ctrl]+[Alt]+D

This is the default keyboard shortcut to show/hide the desktop. It affects all workspaces.
Thank You :) <<< marking the thread Solved

---

### Post by Agent24 on 2012-06-06
Can you tell me how to *change* that shortcut?

---

### Post by vasa1 on 2012-06-06
> **Agent24 said:**
> Can you tell me how to *change* that shortcut?
You want to re-assign ctrl+alt+d to something else? Or you want to have some other shortcut to showing the desktop?
Either way, how exactly you go about it depends on which desktop environment (?) you are using.
But, basically, you'll be looking for something like Settings, Keyboard, Keyboard Shortcuts.
One restriction though is that there will be key combinations reserved by the system or otherwise so popular that you may not want to change those on a computer accessible to other people.

---

### Post by Agent24 on 2012-06-06
I want to change the "show desktop" shortcut from Ctrl+Alt+D to something else.

Sorry, I should have been more clear.

I am using Xubuntu 12.04. I have looked in the keyboard shortcuts but there is no "show desktop" item anywhere.

---

### Post by vasa1 on 2012-06-06
> **Agent24 said:**
> I want to change the "show desktop" shortcut from Ctrl+Alt+D to something else.

Sorry, I should have been more clear.

I am using Xubuntu 12.04. I have looked in the keyboard shortcuts but there is no "show desktop" item anywhere.
I'm on Xfce 4.10 installed on top of Ubuntu 12.04 and so what I see maybe different from what you see but try this command which should throw up a list of keyboard shortcuts and the technical terms for various things. (I'm not on my Linux box now.):
```
xfconf-query -c xfce4-keyboard-shortcuts -l -v
```

---

### Post by Agent24 on 2012-06-06
Thanks for your help, I found it in "Settings -> Window Manager -> Keyboard"

Must have skimmed right over it the first 10 times I looked there!

I've changed it to Super+d now, like in Windows... 

*runs and hides* :p

---

### Post by vasa1 on 2012-06-07
> **Agent24 said:**
> Thanks for your help, I found it in "Settings -> Window Manager -> Keyboard"

Must have skimmed right over it the first 10 times I looked there!

I've changed it to Super+d now, like in Windows... 

*runs and hides* :p
Great! I'm leaving things as they are because I don't want to get confused when I use Unity because then the "Super" key does special things ...

---

### Post by Agent24 on 2012-06-07
> **vasa1 said:**
> Great! I'm leaving things as they are because I don't want to get confused when I use Unity because then the "Super" key does special things ...

Didn't know that, but I don't like Unity (why I switched to Xubuntu) so I guess that won't be a problem.

---

