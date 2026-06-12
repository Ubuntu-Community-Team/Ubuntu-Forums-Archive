---
title: "My screen is showing grains"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by GoCool on 2008-05-01
Hi,
Today when I switched to my computer, it suddenly changed my display settings and now its just grains, nothing is clearly visible. I dont know why it occured.

1. Is there any way I can revert back to the old settings.

2. Or atleast get a decent display.

Any help on this would be highly appreciated.

---

### Post by phr0ze on 2008-05-01
What do you mean - 'Switched to my computer'

If the image on the screen is distorted it is usually the result of the monitor settings being wrong. This can happen if you switch from one monitor to another.

---

### Post by vmalep on 2008-05-01
I do not know if it is the same problem, but I shortly tried Kubuntu 8.04 and it happened sometimes that the screen was squared with small white rectangles. I just switch to the TTY1 terminal (ctrl+alt+1) and back to the graphical session (ctrl+alt+7) and the display was normal again.

Is this working for you (it is not a solution, but meanwhile...)?

---

### Post by GoCool on 2008-05-01
> **phr0ze said:**
> What do you mean - 'Switched to my computer'

I am sorry for not elaborating, I am using a KVM switch to switch between two computers (xp and ubuntu)

> **phr0ze said:**
> 
If the image on the screen is distorted it is usually the result of the monitor settings being wrong. This can happen if you switch from one monitor to another.

How do I go about fixing it?

> **vmalep said:**
> I do not know if it is the same problem, but I shortly tried Kubuntu 8.04 and it happened sometimes that the screen was squared with small white rectangles. I just switch to the TTY1 terminal (ctrl+alt+1) and back to the graphical session (ctrl+alt+7) and the display was normal again.

Is this working for you (it is not a solution, but meanwhile...)?

I think this is what the problem is. But I am using ubuntu, and here (ctrl+alt+1) and (ctrl+alt+7) is not working. But then I rebooted the machine, shouldnt it fix it??

---

### Post by Tiede on 2008-05-01
> **GoCool said:**
> Hi,
Today when I switched to my computer, it suddenly changed my display settings and now its just grains, nothing is clearly visible. I dont know why it occured.

Check your antenna and change the channel!!!:popcorn:
(sorry, I couldn't help it)

But seriously, do you mean you just switched it on, or was it on before and you just happened to pass by?

How old is your PC? My GF has a very old one that displays weird vertical lines on startup, but after flickering for about 5 to 15 seconds, the gdm comes up just fine...

You could try Alt+Ctrl+F1 to switch to a terminal and change your x settings from there... Can you at least switch to one?

---EDIT
sorry, I didn't get those last posts
You need to Ctl+Alt+**F**1. That's the *F1* key on your keyboard. That should work.

---

### Post by GoCool on 2008-05-01
> **Tiede said:**
> Check your antenna and change the channel!!!:popcorn:
(sorry, I couldn't help it)


Well I know no pun intended, I was using KVM switch. Sorry for not elaborating.

> **Tiede said:**
> But seriously, do you mean you just switched it on, or was it on before and you just happened to pass by?

I was switching between xp and ubuntu using the KVM.

> **Tiede said:**
> 
How old is your PC? My GF has a very old one that displays weird vertical lines on startup, but after flickering for about 5 to 15 seconds, the gdm comes up just fine...

You could try Alt+Ctrl+F1 to switch to a terminal and change your x settings from there... Can you at least switch to one?

I'll try and would let you know soon.

---

### Post by GoCool on 2008-05-01
> **Tiede said:**
> 
You could try Alt+Ctrl+F1 to switch to a terminal and change your x settings from there... Can you at least switch to one?

Well I could get on to the terminal by Alt+Ctrl+F1, but then how to change my x settings. I have absolutely no clue.

---

### Post by Tiede on 2008-05-01
Did you try the Ctrl+Alt+F1 followed by Ctrl+Alt+F7 workaround?
It should work... If for some reason it doesn't, here how to modify your X server conf in an interactive way. I'd personally try rebooting first, though...

```
sudo dpkg --reconfigure xserver-xorg
```
Make sure to **ONLY** change the relevant part of that. ie, leave your mouse and other settings alone.

---

### Post by GoCool on 2008-05-01
> **Tiede said:**
> Did you try the Ctrl+Alt+F1 followed by Ctrl+Alt+F7 workaround?

Yes but its the same.
> **Tiede said:**
> It should work... If for some reason it doesn't, here how to modify your X server conf in an interactive way. I'd personally try rebooting first, though...

I even rebooted, but nothing happened.

```
sudo dpkg --reconfigure xserver-xorg
```
This is giving me an error saying "dpkg: unknown option --reconfigure".

---

### Post by Tiede on 2008-05-03
oops, that was my bad. The right line is
```
sudo dpkg-reconfigure xserver-xorg
```
It should work now...

---

### Post by GoCool on 2008-05-05
> **Tiede said:**
> oops, that was my bad. The right line is
```
sudo dpkg-reconfigure xserver-xorg
```
It should work now...
Tiede...awesome, it did work like a charm. My thanks to you. You definitely make the Ubuntu world a lot sweeter than what it already is.

---

