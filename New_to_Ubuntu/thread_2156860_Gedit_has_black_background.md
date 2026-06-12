---
title: "Gedit has black background"
date: 2013-06-23
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2013-06-23
Gedit opens with a black background. I've tried changing the color scheme in Preferences but -no go-. I've tried selecting differing "Themes" - desktop color schemes and that hasn't worked either.

See attached screenshot.

Can this be fixed?

---

### Post by sudodus on 2013-06-23
Which version and flavour are you running? (Is Xubuntu 12.04 Precise Pangolin correct or an outdated stationary text)

Do you have black foreground (text colour) and black background, or is there 'nothing' in the window?

Can you change colour in the preferences for either of foreground and background? Do you use colours from the system theme? Have you tried custom colours?

---

### Post by Mark_in_Hollywood on 2013-06-23
> **sudodus said:**
> Which version and flavour are you running? (Is Xubuntu 12.04 Precise Pangolin correct or an outdated stationary text)

[COLOR="#FF0000"]This is Xubuntu, Precise Pangolin, ver. 12.04 LTS. This is also in the right side of the post under: Distro - I have no idea what "stationary text" is and cannot respond.[/COLOR]

Do you have black foreground (text colour) and black background, or is there 'nothing' in the window?

[COLOR="#FF0000"]By opening a new text file, the background changes to white with black text. Yes I can see text typed.[/COLOR]

Can you change colour in the preferences for either of foreground and background? Do you use colours from the system theme? Have you tried custom colours?

[COLOR="#FF0000"]I cannot change this, as I said in my OP. I have used the Gedit Preferences Menu to change the Color & Fonts scheme. I have also tried to change the Xubuntu system color & font theme. No avail.[/COLOR] 

Could you explain "stationary" font?

---

### Post by vasa1 on 2013-06-23
Do you have something like this after clicking Edit, Preferences, Fonts & Colors?

---

### Post by sudodus on 2013-06-23
> **Mark_in_Hollywood said:**
> Could you explain "stationary" font?

I simply meant the text at the right side (many people forget to update it, so it may may be out-dated). Sorry, I did not mean to cause any confusion.

> [COLOR=#FF0000]By opening a new text file, the background changes to white with black text. Yes I can see text typed.[/COLOR]

So you can use the editor. Is the problem 'only' before you have any text in it? Then it might be caused by a problem with the art-work and themes (a bug in other words).

---

### Post by Mark_in_Hollywood on 2013-06-23
Yes, I have that. But changing from one theme to another does not fix the blackness.

---

### Post by Vormeph on 2013-06-23
Have you recently tampered with gedit source-wise? You should undo any changes made in that case. If it so satisfies, you should uninstall gedit and reinstall it to reset anything and everything pertaining thereof. If it so satisfies, perhaps installing dconf-tools through synaptic package manager is probably the safest way to modify gedit.

---

### Post by Mark_in_Hollywood on 2013-06-24
Now I am seeing this problem in another part of the OS. Please see attached screenshot.

---

### Post by Mark_in_Hollywood on 2013-06-25
This problem seems to be related to variances in Ubuntu/Gnome/Unity and Xubuntu Desktop "Themes" or color schemes for borders and icons. Case closed.

---

