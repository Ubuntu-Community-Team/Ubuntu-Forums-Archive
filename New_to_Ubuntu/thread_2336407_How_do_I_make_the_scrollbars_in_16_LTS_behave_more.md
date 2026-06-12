---
title: "How do I make the scrollbars in 16 LTS behave more like Windows?"
date: 2016-09-08
forum: New to Ubuntu
---

### Post by newnotice on 2016-09-08
I like Ubuntu but I cannot get used to the scrollbars. I am using Terminal a lot and the hidden scrollbar is driving me nuts. Also when I click in the scroll area above the bar it doesn't just go up a page like it does in Windows, instead it goes up many pages. It seems the area I click is the point in the buffer it goes to rather than just up a page.

On askubuntu there is an answer how to make the scrollbar wider but it didn't work for me
[URL="http://askubuntu.com/questions/775201/how-to-get-a-bigger-static-scrollbar-aka-normal-scrollbar"]16.04 - How to get a bigger static scrollbar (aka normal scrollbar)? - Ask Ubuntu

[/URL]I changed it to ```
-GtkRange-slider-width: 42;
``` and rebooted but the scrollbar does not seem any bigger.

So how can I make the scroll bar behave and look more like Windows?

---

### Post by wildmanne39 on 2016-09-08
You should be able to disable scroll bars by running:
```
echo "GTK_OVERLAY_SCROLLING=0" | sudo tee -a /etc/environment
```
[https://ubuntuforums.org/showthread.php?t=2323881](https://ubuntuforums.org/showthread.php?t=2323881)

---

### Post by vasa1 on 2016-09-08
> **newnotice said:**
> ... when I click in the scroll area above the bar it doesn't just go up a page like it does in Windows, instead it goes up many pages. ...
I don't know about Windows, but it seems you want legacy scrolling. Putting "gtk-primary-button-warps-slider=false" in your settings.ini should fix that.

---

### Post by newnotice on 2016-09-08
I think the legacy scrolling worked, I created ~/.config/gtk-3.0/settings.ini and added:

```
[Settings]
gtk-primary-button-warps-slider = false
```

So that seems to work so that when I click at the top it goes up a page instead of all the way up to the top.

GTK_OVERLAY_SCROLLING=0 I don't know what it's doing because the scrollbar looks the same, attached is a screenshot. Basically I want a scrollbar like the command prompt in Windows. Not exactly like it I just mean visible where there's a widget that I can easily drag up and down and if possible an arrow at the bottom and top.

---

### Post by newnotice on 2016-09-19
I tried again to make them wider but it doesn't work. Surely there must be a way to do this. Does anyone here use different style "always present" type scrollbars like in windows?

---

### Post by vasa1 on 2016-09-19
I didn't look at the imgur images you posted as so I didn't know you were referring to *gnome-terminal*. But, it seems that there are exceptions to the codes you've been provided with: some apps just don't follow them and *gnome-terminal*, IIRC, is one. Would you mind trying another terminal? *xfce4-terminal* may work just as well unless you have very specific needs.

And the arrows at the top and bottom ... that's probably a theme thing. It's now the fashion to not have the arrows. But if you try a variety of themes, some still have them.

You could also hack the theme itself where that's possible and change something like *has-backward-stepper* and *has-forward-stepper* to "true" or "1", depending on how your theme does things.

---

