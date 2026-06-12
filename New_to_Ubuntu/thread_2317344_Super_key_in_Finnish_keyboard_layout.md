---
title: "Super key in Finnish keyboard layout"
date: 2016-03-15
forum: New to Ubuntu
---

### Post by omcesa on 2016-03-15
Hello

I am new to Linux so do not judge me if my question is obvious.

I installed Ubuntu yesterday and I set Finnish for my keyboard layout. A moment after that I realized that my Windows key doesn't work as super key. I changed the layout to English with extended WinKeys and then it worked. I opened Keyboard Layout Chart and my Windows key was assigned to super key like it should. Then I changed my layout back to Finnish and opened the chart again. Now my Windows key was assigned to "Compose" key.

I have tried to find answer few hours and this is very frustrating. Do you have any ideas how to modify my Windows key to act as super key?

Thank you.

---

### Post by Edward_Fish on 2016-03-16
I don't own a Finnish keyboard. There are some things you could try. Read them all first, then decide which order you want to try them in.
1. Plug in another Finnish keyboard via USB, hit the Windows key, and see if it works. (This will almost definitely fail to work.)
2. Buy an Ubuntu keyboard (I think such a thing exists).
3. Press all the keys on the keyboard in turn, waiting a few seconds between each one, to see if any of them work. (Most likely none will.)
4. Click the cog in top right corner > System Settings > Keyboard > Shortcuts tab > Set "Open Dash" (or similar) to the Windows key. (I'm not sure if such an option exists.)
5. Try using one of these packages: gnome-tweak-tool or unity-tweak-tool or ubuntu-tweak and go through the menu options until you find the right setting. (That setting may not exist, I can't remember.)
6. Use a key remapper or similar tool. When asked which key you want to change, press the Windows key while in Finnish keyboard layout. When asked what you want to change it to, switch to the English layout and press the Windows key. (This one should work.)
8. Click the button on screen instead of using the keyboard. (This will work for sure!)

---

### Post by mcduck on 2016-03-16
Which variant of the Finnish layout are you using? I'm using the default one "Finnish", and my windows key is assigned to Super like expected, and the Menu key is set to Compose.

Maybe try one of the other variants? Try the "Finnish (winkeys)" one, or maybe the "Finnish (classic)".

Also, if you run this in a terminal, what does it return?
```
gsettings get org.gnome.desktop.input-sources xkb-options
```

Maybe try resetting it, or specifically setting it to empty (you shouldn't have anything set there by default):
```
gsettings reset org.gnome.desktop.input-sources xkb-options
gsettings set org.gnome.desktop.input-sources xkb-options []
```

---

### Post by omcesa on 2016-03-16
When I run that line, it returns ```
@as []
``` I have no idea what that means.

The problem isn't in my keyboard or other hardware, it's just Ubuntu's keyboard layout. The question is, how can I change Compose key to the Super key.

---

### Post by mcduck on 2016-03-16
That's odd, then, since I'm using exactly the same layout, and the windows key is bound to Super like it should be.

I was expecting you to have something in that dconf setting forcing a compose key, as that could have explained having a compose key where one shouldn't exist... But the "[]" means it's just an empty list with no options, like it should be. Either way it must be something specific to your keyboard or setup, as it's not how the Finnish layout usually works in Ubuntu. Something, somewhere, must be overriding the default layout.

Anyway, did you try the other Finnish layout variants like I suggested? Do they have the same problem?

edit: So, the question really isn't "how to change the compose key into super key" but instead "what's changing the super key into compose key"... ;)

---

### Post by mcduck on 2016-03-16
If you go to keyboard settings,Input tab, and the Typing section, do you have anything set on the Compose key option? It should be set to "disabled".

Also, do you have one or two windows keys on your keyboard? The default Finnish layout should have the *left windows key* as Super-L, and if you happen to have a right windows key as well, that would be set to Compose.

---

### Post by vasa1 on 2016-03-16
Is the compose key "normally" set to the Menu key? If so, what about something like *xmodmap -e "keysym Menu = Super_L"*?

---

### Post by mcduck on 2016-03-17
The normal Finnish layout has left windows key as Super-L, right windows key as Compose, and menu key as Menu. (So the Compose key is an optional thing you only get if you happen to have two windows keys on your keyboard, since the Finnish layout already supports typing fair amount of international characters by using AltGr as third-level chooser and ****+AltGr for fourth level, so a separate Compose isn't as necessary as with many other layouts).

---

### Post by vasa1 on 2016-03-17
Maybe OP has a laptop with fewer keys? My laptop has just one Super key.

---

### Post by mcduck on 2016-03-18
That could be the reason, assuming the laptop only has the right windows key, and is missing the left one. Although I don't think I've ever seen a keyboard like that, it seems to me you pretty much always have the left windows key if the keyboard only has one. But then again especially laptop manufacturers still seem to pull off odd layouts every now and then...

I only have one Windows key as well, and it's on the left side so it's assigned as Super by default.

---

### Post by vasa1 on 2016-03-18
> **mcduck said:**
> That could be the reason, assuming the laptop only has the right windows key, and is missing the left one. Although I don't think I've ever seen a keyboard like that, it seems to me you pretty much always have the left windows key if the keyboard only has one. But then again especially laptop manufacturers still seem to pull off odd layouts every now and then...

I only have one Windows key as well, and it's on the left side so it's assigned as Super by default.Yes, mine's on the left only as well.

---

