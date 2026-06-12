---
title: "Alt+Tab - navigate switcher with the mouse?"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by grundunkus on 2008-11-20
I'm trying to make the switch from Vista to Ubuntu because I really hate Vista. The switch is going very well, except for one extreme annoyance I can't seem to find a way around: Is there a way to navigate the application switcher with the mouse? XP didn't have this feature and it drove me mad, but it was about the only thing about Vista that *didn't* drive me mad.

I've switched Preferences > Appearance > Desktop Effects between the three settings and the application switcher changes, but neither of them offers the ability to select an item with the mouse.

Is there a way to do this, or an alternative? I usually have a lot of windows open and having to hit tab thirty times when I could just click it with the mouse is a pain. Is there a command, or a shortcut key combination that I'm missing that can make this switching faster?

---

### Post by epitaph on 2008-11-20
You can do it while using the ring switcher in compiz.

Install CCSM:

```
sudo apt-get install compizconfig-settings-manager
```

After installed, go to System > Preferences > Advanced Appearance Preferences and open it.

Once in the CCSM, find "Ring Switcher". It is under the Window Management category.

Set the next window keybind to ALT+TAB. (Click on the button to the left of the notepad and say "grab new key combo" and press ALT+TAB)

Go to the "Misc. Options" tab and check the last radio box titled "Allow Mouse Selection".

Now, when you ALT+TAB you can click on any of the windows that are on the ring switcher.

You may want to customize the ring appearance a bit, I like mine a bit flatter.

Hopefully this helps.

---

### Post by crazyness003 on 2008-11-20
A better effect would be 'scale'. Like in mac, when you activate a shortcut combo, mouse combo or desktop hotspot, all the open windows get a little smaller can easily see what you need and just click it to give it focus. Its my fav for quick app switching. The cover-switcher is an alternative to the ring-switcher.

Believe me, once you start playing around with compiz, you'll never stop tweaking it.

---

### Post by epitaph on 2008-11-20
That's a great suggestion too. Compiz never ceases to provide! And yes, you will continually tweak and change things. At least I can't help it.

---

### Post by grundunkus on 2008-11-20
Thanks for all of the suggestions!

The Compiz settings manager is fantastic and addictive. I've tweaked everything to within an inch of its life.

The ring switcher does let me click on items, but it can be a bit hard to get at things when there are heaps of windows open. It's nice and I'll probably stick with it for the time being.

I'd prefer the scale switcher but I can't seem to find out how to make it show minimised windows, or at least icons for them.

Also, I can't seem to work out in compiz config how to change the application switcher back to gnome's default.The static application switcher plugin gives me some bizarre artefacts when I use it.

Thanks again for all the help.

---

### Post by crazyness003 on 2008-11-22
i dont think the scale plugin can show minimized windows (i could be wrong). If there is a way, id like to know about it. but since i never minimize my windows (no need to), it works flawlessly for me.

as for the appswitcher... cant help you there, sorry.

---

