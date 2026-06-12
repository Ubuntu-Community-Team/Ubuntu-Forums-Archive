---
title: "Which flavour and settings for an elderly person"
date: 2021-09-08
forum: New to Ubuntu
---

### Post by Nina_W on 2021-09-08
I want to install Ubuntu on my Mum's laptop, she had it on a previous laptop and preferred it to MS Windows.
The snag is, she's in her 80's her eyesight is reasonably good but not perfect and she has arthritis in her hands. Functionally she uses it for internet, mostly online shopping, facebook etc. word processing and arranging and printing photos (sometimes with captions).

Most operating systems now like to have everything looking smooth and sleek which is the exact opposite of what someone with poor eyesight needs. She needs something more bold and clunky looking. I have Kubuntu on a memory stick but everything I have found about how to customize it is very much about how to make it look more smooth and sleek. I need the opposite.

The arthritis in her hands makes it a bit difficult to get the cursor (she uses a tracker ball) exactly where she wants it and this has been a problem with skinny scroll bars, also scroll bars that vanish when you're not on them are troublesome and confusing.

So can anyone suggest a flavour and style or tweeks that can get me what I need? I'm happy editing code if that is necessary.

---

### Post by ajgreeny on 2021-09-08
I use Xubuntu with the Xfce desktop which can be configured to use desktop icons if that is how your mother likes it, and 5hose icons can be easily enlarged to a size of her preference.  The window scrollbars can also be made wider with the stepper buttons top and bottom, not normally used in modern themes, by creating a simple text file in the user's home, details of which i can give you when on the correct machine.

Some users suggest the desktop is very old fashioned looking but that is a very subjective comment; to my mind it just works better for me than anything else I've tried.

More detail when on my Xubuntu box but search around and you may find other users who feel the same as I do.

---

### Post by mastablasta on 2021-09-08
KDE is fully customiseable. most option can be done through menues, but some might require editing config files.

i think oyu are after system that has Accessibility settings. then just set it as you would like to have it.

---

### Post by monkeybrain20122 on 2021-09-08
Everything would look big if you set a low screen resolution.

---

### Post by grahammechanical on 2021-09-08
Ubuntu has accessibility settings. At the login screen click the icon of the human. These are the settings that are by default disabled: High Contrast: Zoom; Large text; Screen reader; Screen keyboard; Visual alerts; Sticky keys; Slow keys; Bounce keys; Mouse keys.

In System Settings>Universal Access we find similar options but also Cursor Size. There is also a Track pad & Mouse setting dialog. I have yet to find anything about changing the width of the scroll bars.

I am also confident that accessibility options are available in other desktop environments. Has your mother considered using a mouse rather than the track pad?

Regards

---

### Post by kurt18947 on 2021-09-08
Your mother sounds much like my wife. Poor vision, some dexterity degradation. Mainline Ubuntu has some accessibility tweaks. Click the upper right corner of the screen then Settings -> Universal Access. A larger cursor is a benefit and there are various screen zoom settings. If her track ball has a scroll device scroll bars don't seem like too much of an issue. I've told SWMBO she doesn't have to have the cursor over the scroll bar in order to scroll the page. She still doesn't believe me :). We also bought her a larger monitor, 32" in her case. The resolution is 1920 X 1080 I think. A higher resolution would be better, icons and text can get a little jagged.

---

### Post by Holger_Gehrke on 2021-09-08
+1 to ajgreeny's recommendation of XUbuntu. Three features which - to me - make XFCE very nice:
[LIST]
[*] You can set a keyboard shortcut for finding the mouse cursor. Hit that key and concentric rings spread out around the pointer. Setting this up is a bit fiddly: you have to turn it on in Settings->Accessibility **and** define a key for xfce-find-cursor in Settings->Keyboard.
[*]Hold the "Alt" key and drag with the right mouse button to resize a window. No need to position the pointer exactly near some very thin window border.
[*]Built in screen enlargement. Hold "Alt" and turn the mouse wheel - or perform whatever gesture you've configured on your trackpad for scrolling - up to zoom in and down to zoom out.
[/LIST]

Holger

---

### Post by monkeybrain20122 on 2021-09-08
> **Holger_Gehrke said:**
> +1 to ajgreeny's recommendation of XUbuntu. Three features which - to me - make XFCE very nice:
[LIST]
[*] You can set a keyboard shortcut for finding the mouse cursor. Hit that key and concentric rings spread out around the pointer. Setting this up is a bit fiddly: you have to turn it on in Settings->Accessibility **and** define a key for xfce-find-cursor in Settings->Keyboard. 
[*]Hold the "Alt" key and drag with the right mouse button to resize a window. No need to position the pointer exactly near some very thin window border. 
[*]Built in screen enlargement. Hold "Alt" and turn the mouse wheel - or perform whatever gesture you've configured on your trackpad for scrolling - up to zoom in and down to zoom out. 
[/LIST]

Holger

I don't think holding this key and using that keyboard shortcut is quite as natural to someone used to point and click. I am quite experienced but I do have a hard time remembering a bunch of random key combinations which more geeky types are more comfortable (like with vi and emacs), especially with key combos with odd positions with respect to your fingers (check out some default key combos in compiz ccsm for example)

Like I said, and it was not meant to be a joke, if you set your screen resolution low then everything will be large. This dude with very poor eye sight got a reburbished laptop for $100 with Linux Mint on it from a local Linux computer shop, that was exactly what they did for him. Set the screen resolution low so everything appears big enough for him.

---

### Post by jim Kane on 2021-09-08
another +1 to ajgreeny's recommendation of XUbuntu.
im also quite old and eyesight is not what it was and i dont like change, i find it the easiest to use

---

### Post by mastablasta on 2021-09-09
> **monkeybrain20122 said:**
> 
Like I said, and it was not meant to be a joke, if you set your screen resolution low then everything will be large. This dude with very poor eye sight got a reburbished laptop for $100 with Linux Mint on it from a local Linux computer shop, that was exactly what they did for him. Set the screen resolution low so everything appears big enough for him.


yeah my grandfather used to have this large 1650x1050 monitor, but he used resolution 800x600 (stretched), so it was all big on windowsXP. it was easier for him to see like that.

linux can change DPI. i know my Kubuntu defaulted to 1280x1024, but everything was huge because of the DPI. so i had to change that first to get it all down to normal size.

---

### Post by Nina_W on 2021-09-09
Many thanks for all the replies, I think I'll try XUbuntu first and see what I can do with that.
Just to answer a few other points. I tried Kubuntu and just couldn't see how to do what I needed, it seems there are a whole host of different styles but it seemed like too much of very similar things and nothing like what I wanted. It is possibly there but a bit of a needle in a haystack type thing.
Just making screen resolution bigger doesn't necessarily help much, it would make the scroll bars bigger, so easier to roll over but also means needing to scroll more and some webpages become difficult to use. Also, seeing where the cursor is isn't the issue, it is getting it on the right place physically. She prefers a tracker ball so she can sit in a comfy chair with a small table pulled right up to her with the tracker ball on the side (unfortunately it doesn't have a scroll facility), back and shoulder issues make this essential for all but brief use.
Shortcut keys are a no no because she would probably struggle to remember them.

---

### Post by pantazi on 2021-09-09
I use a padded tray under my laptop (on my knees), this has enough room at the side to keep a permanent list of keyboard shortcuts in my line of sight. It has proved very useful.

---

### Post by Nina_W on 2021-09-10
> **ajgreeny said:**
> I use Xubuntu with the Xfce desktop which can be configured to use desktop icons if that is how your mother likes it, and 5hose icons can be easily enlarged to a size of her preference.  The window scrollbars can also be made wider with the stepper buttons top and bottom, not normally used in modern themes, by creating a simple text file in the user's home, details of which i can give you when on the correct machine.

Some users suggest the desktop is very old fashioned looking but that is a very subjective comment; to my mind it just works better for me than anything else I've tried.

More detail when on my Xubuntu box but search around and you may find other users who feel the same as I do.

I've got Xubuntu on a memory stick now and have booted from that and played around, seems to be just what we need. Can you give me the text file to widen the scroll bars please. No hurry for this.

Many thanks

---

### Post by ajgreeny on 2021-09-10
> **Nina_W said:**
> I've got Xubuntu on a memory stick now and have booted from that and played around, seems to be just what we need. Can you give me the text file to widen the scroll bars please. No hurry for this.

Many thanks
Sure can.
Create a simple text file with the content attached below and save it as /home/*user*/.config/gtk-3.0/gtk.css
```
/* Set thickness of scrollbars */
.scrollbar.vertical slider,
scrollbar.vertical slider {
    min-width: 12px;
    background-color: #34a853;
}

.scrollbar.horizontal.slider,
scrollbar.horizontal slider {
    min-height: 12px;
    background-color: #34a853;
}

.scrollbar.vertical.slider:hover,
scrollbar.vertical:hover slider {
    min-width: 12px;
}

.scrollbar.horizontal.slider:hover,
scrollbar.horizontal:hover slider {
    min-height: 12px;
}

/* Include scrollbar steppers */
.scrollbar,
scrollbar {
    -GtkScrollbar-has-backward-stepper: 1;
    -GtkScrollbar-has-forward-stepper: 1;
}

scrollbar button {
min-width: 20px;
min-height: 20px;
}

.xfce4-panel {
  -XfcePanelWindow-popup-delay: 10;
  -XfcePanelWindow-popdown-delay: 10;
}

```
This will also give you the little arrow icons at top and bottom of scrollbars that can be useful for stepping up and down but unfortunately it does not have any effect on firefox if that is the browser used though you can change that in the about:config page in firefox by changing the entry for ***widget.non-native-theme.scrollbar.size*** a size that fits your needs; mine is set to 24.

Good luck; I hope this is a help to you.

---

### Post by cmcanulty on 2021-09-13
I have poor eyesight and agree on xubuntu. In addition I like the chronos theme for firefox as it has colored buttons for max, min, and close.

---

