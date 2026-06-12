---
title: "Basic Questions"
date: 2011-10-08
forum: New to Ubuntu
---

### Post by Radical_Dreamer on 2011-10-08
As a newbie to ubuntu, there are a couple of things that I'm having trouble with.

1.  Is there a way to permanently turn 'show hidden folders'? Because I know you can use control h to show them but i can't turn it on permanently.

2.  When it comes to things like internet, sometimes I want to open two browsers but I don't know hot to do that.  LIke, I can't just click the icon again to make another browser open.

3. In my many failures to install baldur's gate 2 (I got it working eventually).  Unfortunately, now i have like 3 apps of baldur's gate 2 throne of bhaal and the config and none of them work (and I don't even think they exist anymore because I deleted playonlinux).  So what should I do?

---

### Post by papibe on 2011-10-08
> **Radical_Dreamer said:**
> 1.  Is there a way to permanently turn 'show hidden folders'? Because I know you can use control h to show them but i can't turn it on permanently.

Open nautilus, Go to Edit -> Preferences, there check the box 'Show hidden and backup files'

> **Radical_Dreamer said:**
> 
2.  When it comes to things like internet, sometimes I want to open two browsers but I don't know hot to do that.  LIke, I can't just click the icon again to make another browser open.
With a regular mouse: click with the middle button (the wheel).

With a laptop: if your mouse pad is working OK with the driver, you can tap on the upper right corner.

Another method: launch another instance in the dashboard (tap the super key, type Firefox, click on the found app).

I hope that helps.
Regards.

---

### Post by raja.genupula on 2011-10-08
these gonna delete all configurations you made for playonlinux 

sudo apt-get remove --purge PlayOnLinux

sudo apt-get autoremove

sudo apt-get clean

---

### Post by Radical_Dreamer on 2011-10-09
I don't know, the apps still show up on applications thing in the launcher but I guess that's alright.

Anyway, how do I close the thread?

---

### Post by papibe on 2011-10-09
Go to the top of the page. Click on 'Thread Tools', and then select 'Mark this thread as solved'.

Regards.

---

### Post by 3rdalbum on 2011-10-09
> **papibe said:**
> With a laptop: if your mouse pad is working OK with the driver, you can tap on the upper right corner.

Or press the left and right mouse buttons together.

---

### Post by huggs on 2011-10-09
> **papibe said:**
> Open nautilus, Go to Edit -> Preferences, there check the box 'Show hidden and backup files'

Regards.

This will only show hidden files/directories for the current instance of Nautilus.
You can, however, permanently show hidden files and directories by going into Configuration Editor/Apps/Nautilus, and ticking the box labeled 'Show Hidden Files'

The exact location and name of the entry in gconf editor may not match exactly with what I put here, but it's close enough to be able to find what I'm talking about and make it happen8)

Now every time you open Nautilus, you can see your hidden files and directories

---

### Post by papibe on 2011-10-09
Hey huggs, I think your confusing it with  View -> Show Hidden Files, which is equivalent to Ctrl+H, and it is just for the current instance.

But if you go into Edit -> Preferences, which opens a new window, set the behavior for the application.

Regards.

---

### Post by huggs on 2011-10-09
Dang you're right. Shoulda read more carefully. My fault

---

