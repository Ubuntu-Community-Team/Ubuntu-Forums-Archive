---
title: "How to remove minimise / maximise buttons"
date: 2011-12-22
forum: New to Ubuntu
---

### Post by jermza on 2011-12-22
I actually find the Gnome Shell idea of ONLY a close button smart because I don't use the maxmise / minimise buttons. If I want to maximise / minimise, then I simply double-click the title bar. And I drag the windows to resize.

Plus, no buttons is cleaner and less busy.

In 10.10, I was able to use the Gnome-Tweak tool to remove the said buttons. Is there a way that I can remove them in 11.10?

---

### Post by benpack101 on 2011-12-23
You can find the settings for this in the gconf-tool.

Follow the directions on this page, 

[http://askubuntu.com/questions/78410/how-can-i-get-the-buttons-back-on-the-left-side](http://askubuntu.com/questions/78410/how-can-i-get-the-buttons-back-on-the-left-side)

Instead however just go ahead and remove minimize and maximize.

And remember the : represents which side of the window you want them on

---

### Post by Frogs Hair on 2011-12-23
Ubuntu Tweak would be another way to accomplish removing buttons .

---

### Post by jermza on 2011-12-23
My apologies. I should indicated that I am referring to Unity and not Gnome Shell.

I'd like to remove the minimise / maximise buttons from my 11.10 Unity desktop environment. DConf doesn't seem to have such settings.

---

### Post by jermza on 2011-12-28
So, can I assume that there is no way to remove them in 11.10? (Not even with Dconf-editor?)

---

### Post by benpack101 on 2011-12-28
I'm sure there is a way to do it just no one has done it yet, or at least, no one has said how s/he did it.

If you are up to the challenge, I'm sure it could be looked into, but for now, no news.

---

### Post by Kulgan on 2011-12-28
I'm on Unity:
gconf-editor
apps->metacity->general->button_layout

Just change it to :close

---

### Post by jermza on 2011-12-28
> **Kulgan said:**
> I'm on Unity:
gconf-editor
apps->metacity->general->button_layout

Just change it to :close

No Gconf in 11.10. Dconf is the one. And there is no "metacity" option.

---

### Post by Kulgan on 2011-12-28
How odd. Apologies for that. 

I am on 11.10 and have gconf. Can't remember whether it was from fresh install, but must not have been.

---

