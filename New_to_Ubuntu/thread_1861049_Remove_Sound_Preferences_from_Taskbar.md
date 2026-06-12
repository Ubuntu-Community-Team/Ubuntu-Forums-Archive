---
title: "Remove Sound Preferences from Taskbar?"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by Greg Mueller on 2011-10-15
How do I remove the **Sound Preferences** Icon from the taskbar?

---

### Post by Lisiano on 2011-10-15
I haven't found a way to blacklist the default items from the taskbar, only how to whitelist stuff like Skype, Deluge, etc.
But if you remove the indicator then it should be removed for every user.
```
sudo apt-get remove indicator-sound
```
Relog and it should be gone (I think)

---

### Post by Greg Mueller on 2011-10-15
Now I am gun shy. 
Things are so screwed up I hate to experiment with terminal stuff. If I could just drag it away or throw a switch, I would do it because I could put it back. But terminal stuff seems very final.

---

### Post by Lisiano on 2011-10-15
If you are afraid of the terminal, please just click this link [Indicator-sound](apt://indicator-sound)
Ubuntu Software Center should open and just press Remove, if you wish to reinstall it again later, press that link again and pick Install.

---

### Post by Greg Mueller on 2011-10-15
I think I got it.

Here's what I did....

I created a "New Panel" and told it to be at the bottom. This was to be my new taskbar

Then I dragged everything I wanted to keep to the new panel using the <ALT> + <Right Click> and chose "Move"

Essentially I moved everything except the **Sound Preferences**.

It would not let me move the icon that shows the internet connection.

At first it did not display the Apps that were active. I did the "right click alt" thing on the new panel and chose "Add To Panel" and then chose "Window List".

It seems to work best if I put my commonly used App Icons over on the right side by the clock and the "Applications.....Places" on the left. It then shows the open apps in between those two.

Then I deleted the old task bar.
I have not rebooted yet so I don't know if this will stick

---

### Post by Lisiano on 2011-10-15
You should have just said you used Gnome Fallback. In older Ubuntus you could just drag it off the panel and it would disappear. Should be the same in Gnome Fallback I think. Or did a Alt+Right-click+Remove/Delete.

---

### Post by Greg Mueller on 2011-10-15
Tried it and it wouldn't budge

---

