---
title: "usplash distorted on shutdown"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by mudrain911 on 2008-07-30
Everything is great when I boot up my computer, Xubuntu boots up very quickly with the correct splash image and everything. However, when I shut down my computer, all of the colors are inverted and distorted. 

When I first shut down the screen is black with a dark green text scrolling down it that I cannot really make out. After a few seconds, that goes away and the splash screen comes up, with its colors inverted and distorted badly. So far I have tried editing menu.lst, but nothing changed. If you have any ideas, please let me know.

Thanks in advance!

---

### Post by gvartser on 2008-07-30
Remove "splash" from the menu.lst files menu options.

/g

---

### Post by mudrain911 on 2008-07-30
you mean remove it fron the line starting with kernel? Im a bit new so you have to bear with me...

---

### Post by mudrain911 on 2008-07-30
Well, after I typed that last reply, I rebooted my computer and the colors were normal! I (played around with where 'vga=792' was in menu.lst). Now i have another problem. Now the text that scrolls down is white with a black background, and it stays up for the entire shutdown. I only get the splash screen for less than a second now, right before the computer cuts off. Does anyone know how to get rid of that text?

---

### Post by Dr Small on 2008-07-30
> **mudrain911 said:**
> Well, after I typed that last reply, I rebooted my computer and the colors were normal! I (played around with where 'vga=792' was in menu.lst). Now i have another problem. Now the text that scrolls down is white with a black background, and it stays up for the entire shutdown. I only get the splash screen for less than a second now, right before the computer cuts off. Does anyone know how to get rid of that text?
Did you add quiet back to the kernel line?

---

### Post by coffeecat on 2008-07-30
> **mudrain911 said:**
> Now the text that scrolls down is white with a black background, and it stays up for the entire shutdown. I only get the splash screen for less than a second now, right before the computer cuts off. Does anyone know how to get rid of that text?

I know of a fix that works in Ubuntu, because it's a gdm related problem - gdm being the gnome log in manager. I don't know whether this will work in Xubuntu, because I don't think Xubuntu uses gdm, but I could be wrong. I'll post it anyway. Have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=865670](http://ubuntuforums.org/showthread.php?t=865670)

The fix is in my post which I copied and pasted from the launchpad bugzilla thread I linked to there.

By the way, if you remove the word 'splash' from the kernel line in your menu.lst, you won't get any usplash at all. I guess that was not what you were after.

---

### Post by Dr Small on 2008-07-30
> **coffeecat said:**
> I know of a fix that works in Ubuntu, because it's a gdm related problem - gdm being the gnome log in manager. I don't know whether this will work in Xubuntu, because I don't think Xubuntu uses gdm, but I could be wrong. I'll post it anyway. Have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=865670](http://ubuntuforums.org/showthread.php?t=865670)

The fix is in my post which I copied and pasted from the launchpad bugzilla thread I linked to there.

By the way, if you remove the word 'splash' from the kernel line in your menu.lst, you won't get any usplash at all. I guess that was not what you were after.
Xubuntu probably uses GDM, since the three biggest Login Managers are GDM (Ubuntu), KDM (Kubuntu) and XDM (Xorg Login Manager).

---

### Post by mudrain911 on 2008-07-30
I tried the solution on the link that coffeecat posted, but so far that hasn't worked. actually the whole idea doesn't seem to accomplish anything....but thats just me. I have seen a post saying that this is just because Daemons are shutting down in different orders. Is that the only workaround found so far or are there others?

---

### Post by coffeecat on 2008-07-30
> **mudrain911 said:**
> ...is there anything wrong with that

Absolutely nothing. Except for the UUID, it's the same as mine, and >90% of the people of this forum I should think. :)

I don't believe the kernel line options were relevant to your problem.

---

### Post by mudrain911 on 2008-07-30
ok thanks...I just wanted to check on it. I edited my last reply rather than posting a new one. That is just habit because a lot of forums really don't like people double posting...

By the way, I noticed that all of the text scrolling down the screen has something to do with the Network Manager. I tried unplugging my ethernet cord before I shutdown, but that didn't do anything.

---

### Post by coffeecat on 2008-07-30
> **mudrain911 said:**
> I tried the solution on the link that coffeecat posted, but so far that hasn't worked.

It won't work until the second shutdown. Have you tried that yet?

> **mudrain911 said:**
> By the way, I noticed that all of the text scrolling down the screen has something to do with the Network Manager.

That's what I get, and I think that's what everyone gets.

---

### Post by mudrain911 on 2008-07-30
Ive rebooted like 4 times since then. Im trying everything I can think of... Im not really worried about the text, it's just kinda ugly you know what I mean?

---

### Post by mudrain911 on 2008-07-30
Does anyone know how to change the order in which the programs end on shutdown? Maybe if I could make the Network Manager close earlier than other it is the scrolling text won't show.

---

### Post by philinux on 2008-07-30
According to the official guide this should do it.

[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Fix_the_shutdown_.22Network_Error.22_display_.28restore_shutdown_splash_screen.29](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Fix_the_shutdown_.22Network_Error.22_display_.28restore_shutdown_splash_screen.29)

---

### Post by mudrain911 on 2008-07-30
Would that work on Xubuntu though? It says to use the Human login so Im guessing I would just use the Xubuntu Login Screen. Is there even an Xubuntu login manager or does it use the same one as Ubuntu?

---

### Post by philinux on 2008-07-30
I guess whatever the default xubuntu theme is. :)

---

### Post by mudrain911 on 2008-07-30
I tried that and did it as many different ways that I could. The white text is still coming up the exact same. Does anyone have any different solutions? I've tried everything posted here and nothing seems to work. (except that I got the colors back right)

---

### Post by mudrain911 on 2008-07-31
Just trying something new but I noticed that when i reboot or shutdown from the login screen the splash works perfectly fine, no white text. Are there different configurations for how this shutdown is done or are they the same? Maybe that could help in finding the problem.

---

### Post by mudrain911 on 2008-07-31
bump... :)

---

