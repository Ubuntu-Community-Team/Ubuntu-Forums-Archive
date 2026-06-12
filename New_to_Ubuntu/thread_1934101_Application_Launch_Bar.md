---
title: "Application Launch Bar"
date: 2012-03-01
forum: New to Ubuntu
---

### Post by cheatos on 2012-03-01
Hi,

I'm running lubuntu 11.04 on my desktop and there's this panel on the bottom of the screen (looks like in windows) and on the right corner there was a tiny little button to shutdown and logout and whatever the computer, but I was so stupid to remove the application launch bar from the panel and now I can't get my shutdown button back to the bottom right corner of the screen as this command is not shown in the available applets list... What can I do about this?
Is there a way of getting the shutdown button back to the corner of the screen?

---

### Post by SteveDee on 2012-03-02
> **cheatos said:**
> ...I was so stupid... What can I do about this?

No you're not stupid, you must experiment if you want to move forward with Linux!

Navigate to /home/cheatos/.config/lxpanel/Lubuntu/panels/panel
You may like to make a copy of this and save (say) to your desktop.

Now open /home/cheatos/.config/lxpanel/Lubuntu/panels/panel in a text editor and paste this:-
```

Plugin {
  type = launchbar
  Config {
   Button {
     id = lubuntu-logout.desktop
   }
  }
}

```
...at the very end of the panel file.

Once you are happy that it is working, you can delete the copy you saved on the desktop.

Note: the panel config file does not exist until a user has edited the lower panel for the first time. If you create more panels they will have config files called "top", "left" & so on.

---

### Post by cheatos on 2012-03-02
Thanks! Ill try thus but looks good so far.

---

### Post by cheatos on 2012-03-02
Thank you again,I tried it and it worked (desptie the shutdown button being black instead of red what it was before, but that's no problem)

Another question, is there a way to restart the x-server or how the desktop environment is called?
Because I had to restart my computer before it worked properly, it would be pretty cool if this was possible without a restart.

---

### Post by SteveDee on 2012-03-02
> **cheatos said:**
> ...it worked (desptie the shutdown button being black instead of red...

I was curious about the red icon. I couldn't find it, so I opened lubuntu-logout.desktop in text editor and found the icon used is:-
 /usr/share/icons/lubuntu/panel/22/system-shutdown-panel.svg

Using Inkscape I made a copy and coloured it red...I now have a red power button.

---

### Post by cheatos on 2012-03-02
Oh, ok, thanks for that.
Do you know something about restarting the x-server?
I think I have seen someone doing this on KDE, it was some really weird combination of keystrokes but the whole screen went blank and when it was reloaded it was just like a new login, but it was the desktop which has been reset, not the user session

---

### Post by SteveDee on 2012-03-03
> **cheatos said:**
> ...Do you know something about restarting the x-server?...

I didn't know, but a quick search via googlubuntu reveals that you hold down 2 keys:-

<Alt Gr> + <Prnt Scrn> then press k

...where <Alt Gr> is the right Alt button.

---

### Post by cheatos on 2012-03-03
Yes, that's it, thank you very much!

---

