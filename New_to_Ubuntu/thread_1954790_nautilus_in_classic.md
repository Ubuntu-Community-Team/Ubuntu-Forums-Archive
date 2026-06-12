---
title: "nautilus in classic"
date: 2012-04-08
forum: New to Ubuntu
---

### Post by rosswmcgee on 2012-04-08
I got so far as to enable alt f2, but when I enter gconf-editor

I do not see how to get to apps/nautilus/desktop/

---

### Post by kazztan0325 on 2012-04-09
> **rosswmcgee said:**
> I do not see how to get to apps/nautilus/desktop/

Hi rosswmcgee,

You have only to click on the **triangle mark** which is at the head of each item in the left pane of 'gconf-editor' window to get to the key.

1. Click on the _triangle mark_ which is at the head of the item **apps**.
2. Items which are in the item **apps** will be expanded.
3. Then click on the _triangle mark_ which is at the head of the item **nautilus**.
4. Items which are in the item **nautilus** will be expanded.
5. You will find 4 items (compact_view, desktop, list_view, preferences) there.
6. Then click on the item **desktop**.
7. You will find 5 keys (computer_icon_visible, home_icon_visible, network_icon_visible, trash_icon_visible, volumes_icon_visible) in the right pane of 'gconf-editor' window.
8. You will be able to make the key enable/disable by Ticking ON/OFF against each key's check box in the Value column.

Hope this helps.

---

### Post by rosswmcgee on 2012-04-09
That I understand, but when I go  gconf-editor run with file I get to rosswmcgee

or if I select Run  I get
Could not open location 'file:///home/rosswmcgee/gconf-editor'

---

### Post by kazztan0325 on 2012-04-09
I do not well understand what you would like to do...

Have you tried to run 'gconf-editor' with Terminal?

1. Open up Terminal.
2. Type **gconf-editor**, and then Hit Enter key.
3. 'gconf-editor' window will open.

---

### Post by rosswmcgee on 2012-04-09
I would like to get where you see the triangle. Can't get to apps

---

### Post by rosswmcgee on 2012-04-09
OK now  I see from terminal that gconf-editor was not installed. Installed it

then followed your directions, how ever in desktop, trash visible is not an option, nor are there any others.

---

### Post by kazztan0325 on 2012-04-10
> **rosswmcgee said:**
> how ever in desktop, trash visible is not an option.

Oh, really?
What version of Ubuntu are you using?

---

### Post by rosswmcgee on 2012-04-10
Ubuntu 11.10

---

### Post by kazztan0325 on 2012-04-10
Sorry, I carelessly confused you.

A little while ago, I have confirmed there are 2 items ('desktop' and 'preferences') in /apps/nautilus/, and there is only 1 key ('volumes_visible') in 'desktop' on my 11.10 machine.

By the way, what would you like to do on /apps/nautilus/desktop/ in 'gconf-editor'?

---

### Post by rosswmcgee on 2012-04-11
I was going to make the trash can visable.

---

### Post by kazztan0325 on 2012-04-11
> **rosswmcgee said:**
> I was going to make the trash can visable.

Then I think it would be better for you if you used "**Advanced Settings** (its package name is '**gnome-tweak-tool**')".

Please install 'gnome-tweak-tool' with Synaptic Package Manager or Software Center, if you have not installed it yet.

---

### Post by rosswmcgee on 2012-04-12
Well now that did the trick. What other tweaks do  you like. For me I would like to move my panel icons exactly where I want them. alt right click moves them but really no way to adjust them personally.


OK now I have to undo the trash can visible because if I go back to the Ubuntu desk top I have two trash cans one in the panel and one on the desk top. No big deal I am getting more used to Ubuntu and the panel trash is fine with me, but in 

classic I would rather have it on the desk top. Bottom line, I am planing upgrade to  Ubuntu 12.04 when the beta is finished.

Then I am planning to do a 12.04 clean install on my wife's Mint 9 machine 100%. I gave up keeping bacon fat in the fridge

years ago. Progress is progress. I will keep on computer as Debian, just to see what they do and value for what it is

a very stable distro. So actually I see few reasons to use classic at this point.

---

