---
title: "How to Extend Monitor to Dual Monitor?"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by kolisikepu on 2008-07-04
Hi Community,

How do I extend Ubuntu desktop to my dual monitor?  It clones it with no problems, but I want to extend it so I have a split screens.

Regards,

Kepz

---

### Post by Frozsyn on 2008-07-04
I think you should drop an eye in the menu [System]/[Preferences]/[Screen Resolution]

---

### Post by Toshibawarrior on 2008-07-04
I have the exact same problem! I unchecked the "Clone Screens" checkbox and it still makes my laptop's screen and my TV look the same. Everything that happens on the laptop's screen happens on the TV...is there any way to fix this?...My stupid computer is cloning the displays anyway...:(

:popcorn:Thanks in advance!

---

### Post by pvella on 2008-07-04
If you have an nvidia card it is pretty straight forward.  Just follow this [http://ubuntuforums.org/showthread.php?p=1773584](http://ubuntuforums.org/showthread.php?p=1773584)

---

### Post by Toshibawarrior on 2008-07-04
Thanks for you quick reply, but I have an Intel Graphics "card"...since it's all a chipset as far as I know...Weird thing is that it worked perfectly in Vista...darn...:mad:

---

### Post by Paddy Landau on 2008-07-04
Don't use Screen Resolution. It doesn't work.

I struggled for a couple of weeks over this, until a kindly soul showed me the answer. You want to use RandR.

Here's the post:

[http://ubuntuforums.org/showthread.php?p=5296990#post5296990](http://ubuntuforums.org/showthread.php?p=5296990#post5296990)

I found it easy, but you do have to follow the instructions carefully.

---

### Post by Toshibawarrior on 2008-07-04
> **Paddy Landau said:**
> Don't use Screen Resolution. It doesn't work.

I struggled for a couple of weeks over this, until a kindly soul showed me the answer. You want to use RandR.

Here's the post:

[http://ubuntuforums.org/showthread.php?p=5296990#post5296990](http://ubuntuforums.org/showthread.php?p=5296990#post5296990)

I found it easy, but you do have to follow the instructions carefully.

I don't know...it looks dangerous...

I don't feel comfortable tampering with anything that says "conf" in it on Ubuntu...I don't want to have to play with advanced settings that might make my laptop's screen useless unless I specify the opposite...:(:(:(

This is distressing...

---

### Post by qrwe on 2008-07-04
Also, take look if there is any restricted driver that's not activated. My Nvidia card was not activated by default after Ubuntu install. I simply activated it in the driver manager, rebooted and voíla!

---

### Post by Toshibawarrior on 2008-07-04
No, I don't have restricted drivers, only the Atheros one (wi-fi card)...

:(

---

### Post by qrwe on 2008-07-04
Have you searched for Intel in 'Add/Remove'? Might be a manager there.

---

### Post by Toshibawarrior on 2008-07-04
Hmmm...now that i think of it no...that's a good idea! 

I saw the hidden menu inside Applications>Other that's called "Screens and Graphics"...But I read on another post that xorg configurations are needed for it to work :(...is that true?...

---

### Post by Paddy Landau on 2008-07-04
> **Toshibawarrior said:**
> I don't know...it looks dangerous...
You don't have any choice, if you want your dual screen.

Here... look at this post:

[http://ubuntuforums.org/showthread.php?p=1288786#post1288786](http://ubuntuforums.org/showthread.php?p=1288786#post1288786)

Do _**not**_ follow all the instructions in that post! (You'll spend days on something that's deprecated.) However...

Scroll down to the "Tips" section. Specifically, follow the instructions in the first four tips (in green, blue, purple and brown).

When I was attempting to extend my desktop, before I found out about RandR, I made lots of mistakes. Those four tips were all I needed to help me work faster... and recover my xorg.conf when it was a total hash.

Just follow the instructions; there's nothing dangerous. Unlike Windows, Ubuntu seems to be very reasonable and tolerant.

The very first step is to make a backup. Go to Accessories->Terminal and enter this command:
```
cp /etc/X11/xorg.conf ~/Desktop
```(That backs up your config file into your Desktop.)
If you have to restore the config file, this is how: Go to Accessories->Terminal again and enter:
```
sudo cp ~/Desktop/xorg.conf /etc/X11/xorg.conf
```You'll be safe with that.

---

### Post by Toshibawarrior on 2008-07-04
> **qrwe said:**
> Have you searched for Intel in 'Add/Remove'? Might be a manager there.

Thanks a lot, but it didn't work...there's only a 915resolution program that works with intel card's resolutions, but it has to be run each time you restart the computer and anyways it didn't say anything about options or settings...

> **Paddy Landau said:**
> You don't have any choice, if you want your dual screen.

Here... look at this post:

[http://ubuntuforums.org/showthread.php?p=1288786#post1288786](http://ubuntuforums.org/showthread.php?p=1288786#post1288786)

Do _**not**_ follow all the instructions in that post! (You'll spend days on something that's deprecated.) However...

Scroll down to the "Tips" section. Specifically, follow the instructions in the first four tips (in green, blue, purple and brown).

When I was attempting to extend my desktop, before I found out about RandR, I made lots of mistakes. Those four tips were all I needed to help me work faster... and recover my xorg.conf when it was a total hash.

Just follow the instructions; there's nothing dangerous. Unlike Windows, Ubuntu seems to be very reasonable and tolerant.

The very first step is to make a backup. Go to Accessories->Terminal and enter this command:
```
cp /etc/X11/xorg.conf ~/Desktop
```(That backs up your config file into your Desktop.)
If you have to restore the config file, this is how: Go to Accessories->Terminal again and enter:
```
sudo cp ~/Desktop/xorg.conf /etc/X11/xorg.conf
```You'll be safe with that.

Thanks man, I'll try this then. I hope i don't crash anything since I've been working on my "perfect system" for three months now...just to have just the way I like it! :)

---

### Post by Paddy Landau on 2008-07-04
> **Toshibawarrior said:**
> Thanks man, I'll try this then. I hope i don't crash anything since I've been working on my "perfect system" for three months now...just to have just the way I like it! :)
As far as I know, the *only* thing you change with this is xorg.conf. As long as you've made a backup, you won't have a problem.

BTW, I find that RandR forgets my changes when I reboot, so I've put a launcher on my panel with the (single) command that I need to make it work. I just press it each time I reboot; in about two seconds, the extended desktop is working.

If your system is "perfect", have you made a full backup?

---

### Post by Toshibawarrior on 2008-07-04
> **Paddy Landau said:**
> 

If your system is "perfect", have you made a full backup?

I'm still looking for a satisfactory way of backing up configurations and CLI-based settings...I've successfully backed up every package/app/program I have installed...

As far as configurations go, I haven't found a way...that's why I'm paranoid about this...I don't want to spend 3 more months reconfiguring everything...

It's "perfect" to me...I have everything working as i want it to, except the dual-monitors...

So I guess I'll proceed with caution anyways...

BTW, I should follow the tips on the last thread you quoted (the ones in colors) and follow the wiki that you posted earlier...where it explains a lot of dangerous-looking (to me) things about xorg.conf and stuff?...I just want to make 200% sure before proceeding...

;)

---

### Post by kolisikepu on 2008-07-04
Hi All,

Thank you for your suggestions.  I have heard of RandR, so I'll give that a go.  But... to the first reply to my post, that was the first place I checked.... THE MENU!  I'm not that much of a noob. lol

---

### Post by Paddy Landau on 2008-07-04
> **Toshibawarrior said:**
> I'm still looking for a satisfactory way of backing up configurations and CLI-based settings...I've successfully backed up every package/app/program I have installed...
Here we are:
[http://ubuntuforums.org/showthread.php?p=175981#post175981](http://ubuntuforums.org/showthread.php?p=175981#post175981)

> **Toshibawarrior said:**
> BTW, I should follow the tips on the last thread you quoted (the ones in colors) and follow the wiki that you posted earlier...where it explains a lot of dangerous-looking (to me) things about xorg.conf and stuff?...I just want to make 200% sure before proceeding...
200% sure? There's no way you'll ever get even 100% sure. Not on Linux, not on Windows, not on Mac, ...

---

### Post by Toshibawarrior on 2008-07-04
> **Paddy Landau said:**
> Here we are:
[http://ubuntuforums.org/showthread.php?p=175981#post175981](http://ubuntuforums.org/showthread.php?p=175981#post175981)




Thanks for that! Anyways, i still don't get how can I make the xorg configurations with the terminal text only console...:(

This is so confusing to me...I hate the terminal...:mad:

---

### Post by Toshibawarrior on 2008-09-01
I finally got around to this, and i managed to get a huge desktop between my tv and my laptop's screen...It's a mess...

This was so much easier in Windows...ugh!...

I followed another tutorial, and it helped me get the desktop extended...literally...

the gnome panel is on one screen, the icons on another, Cairo Dock is clipped in half between both screens, and the wallpaper is streched across both screens...this sucks!.

Can anyone help me on this?!...

I made some changes to xorg.conf and they're completely ignored by Ubuntu and xrandr...sometime my laptop's screen doesn't even turns on. 

Please help me!

---

