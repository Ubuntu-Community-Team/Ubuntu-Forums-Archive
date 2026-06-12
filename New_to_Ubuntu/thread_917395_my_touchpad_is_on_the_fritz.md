---
title: "my touchpad is on the fritz"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-09-11
using ubuntu studio. my touchpad randomly clicks iten when i dont want it to this is incredibly annoying. im on a blog and every link is clicked for me even though i dont want to read it. anyone know how i can fix this or should i procure a mouse

---

### Post by PatrickMoore on 2008-09-11
anyone?

---

### Post by chidorex on 2008-09-22
I have the same issue with my mouse, but in my case this happens with all mouse inputs, that is, with the touchpad and with external usb mice. Basically the mouse left-clicks randomly, which is a nuisance mostly while typing. :mad:

Anybody have an idea on how to resolve this? I run 8.04 Hardy on a Dell Inspiron 1420.

Patrick, have you tried with an external mouse? Does it only happen with the touchpad?

Thanks in advance.

---

### Post by dorite on 2008-09-22
Fritzy touchpad?

Nearly drove me crazy.  I can't tell if you have the same problem that I did:  cursor jumps unpredictably -- be composing an e-mail, typing in word-processing -- any program that understands mice and all of a sudden the insertion point would be somewhere it wasn't supposed to be. Never had a problem typing in a terminal. 

To shorten a long story:  I used (Ubuntu 8.04; from the top panel) System -> Preferences -> Mouse to get to the "Mouse Preferences" window, moved to the Touchpad tab, then UNchecked the "Enable mouse clicks with touchpad" box.

My problems went away.  It seems that just brushing the touchpad was enough to move and click with it.

Hope this helps.

---

### Post by anotherdisciple on 2008-09-22
Try editing your Xorg instead of just turning off tap to click.

Make a backup of your Xorg just in case if you mess something up.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Then edit your Xorg with gedit:

```
gksudo gedit /etc/X11/xorg.conf
```

Find your touchpad device section and add this to a new line about "EndSection"

```
Option "MaxTapTime" "1"
```

Change 1 to whatever works for you. That is controlling your tap to click sensitivity.

---

### Post by chidorex on 2008-09-22
Both alternatives sound great. I probably will turn off the touchpad as Dorite suggests to find out if this fixes the problem. Once identified, I might go with your MaxTapTime solution.

Thanks for your help.

---

### Post by anotherdisciple on 2008-09-23
Good stuff... If either one works can you post which one did and mark this thread as solved please?

---

### Post by Potters Son on 2008-09-23
dorite says:> To shorten a long story: I used (Ubuntu 8.04; from the top panel) System -> Preferences -> Mouse to get to the "Mouse Preferences" window, moved to the Touchpad tab, then UNchecked the "Enable mouse clicks with touchpad" box

I have done that, and half the time I boot my computer, it ignores that command.

I'll try anotherdisciple's solution of editing xorg.conf. It's okay to add the code under the "Input Device" section, right? Under "synaptics touchpad?"

---

### Post by anotherdisciple on 2008-09-24
> **Potters Son said:**
> dorite says:

I have done that, and half the time I boot my computer, it ignores that command.

I'll try anotherdisciple's solution of editing xorg.conf. It's okay to add the code under the "Input Device" section, right? Under "synaptics touchpad?"

Yep, it's okay. That's why I had you make a backup though... if things get really messed up you can just use the old configuration like this:

```
sudo mv /etc/X11/xorg.conf.backup /etc/apt/sources.list
```

---

