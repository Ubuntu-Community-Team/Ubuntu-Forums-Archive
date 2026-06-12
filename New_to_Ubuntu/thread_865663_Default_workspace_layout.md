---
title: "Default workspace layout"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by mynot on 2008-07-20
I have 3 workspaces which I want to open exactly the same when I login as they were when I last shutdown. Same windows, same sizes same files, addresses etc open. How can I do this please?
Tony

---

### Post by ibuclaw on 2008-07-20
In Gnome?

Go into "System>Preferences>Sessions" in the menu.
Click the "Session Options" tab in the new window, and you'll see two items of interest.

1) A check box saying:
"Automatically remember running applications when logging out"

2) A command button:
"Remember Currently-Running Applications"

Regards
Iain

---

### Post by LMP900 on 2008-07-20
> **tinivole said:**
> In Gnome?

Go into "System>Preferences>Sessions" in the menu.
Click the "Session Options" tab in the new window, and you'll see two items of interest.

1) A check box saying:
"Automatically remember running applications when logging out"

2) A command button:
"Remember Currently-Running Applications"

Regards
Iain

Thanks Iain; I wasn't aware that these were options.

---

### Post by tjwoosta on 2008-07-20
is there any way to make them open on the same workspaces that they were on before?

---

### Post by ibuclaw on 2008-07-21
There may just be a way, oddly enough.

I haven't yet written anything to implement it, but I'll show my findings.

```
sudo apt-get install wmctrl
```

In Metacity (and most other window managers), to find out which desktop you are running on, run the below command:
```
wmctrl -d | sed '/*/s/..\*.*$//'
```
Try it out on each desktop, you'll see that the number increments or decrements as each one you passthrough.

To change desktops, you use the "**-s**" option.
```
wmctrl -s 0
```
If you are already on Desktop 1, then nothing will happen for you.
But, now everyone is on Desktop 1, run this command instead...
```
wmctrl -s 1
```
And you all have switched to Desktop 2.

So, what is the point of this?
Well, we can have one script to get the current Desktop you are on before you logout, and another to put you back on that Desktop as soon as you login again.

How to achieve this?
I am working on a HowTo right now, be sure to look out for it in the Ubuntuforums HowTo section sometime today or tomorrow :)

Regards
Iain

---

### Post by tjwoosta on 2008-07-21
**you are awesome**


i have been trying to figure out a way to do this for about 4 months now

---

### Post by drs305 on 2008-07-21
Oops, meant to post this in a concurrent thread, although it sort of has application here...

There is an app called *devilspie* that puts specific apps in specific locations on specific workspaces. But be warned: you will probably tear most of your hair out trying to set it up!

It's in the universe repository if you want to spend the time and effort to get it working. (Once you have it set up, you don't have to mess with it again).

---

