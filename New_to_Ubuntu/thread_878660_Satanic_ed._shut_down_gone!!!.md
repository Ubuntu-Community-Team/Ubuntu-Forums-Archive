---
title: "Satanic ed. shut down gone!!!"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by Gaudentius on 2008-08-03
I don't know the the heck I did, but I've lost the shut down option.  I have log out, hibernate, suspend, switch user and lock screen.

Any ideas?

I'm pretty sure it's a simple fix, but I'm a n00b.

GD

---

### Post by billgoldberg on 2008-08-03
I presume you mean the log out button in the top panel.

Right-click the panel and pick "add xxx".

Then look for the shutdown button.

I can't be more specific as I'm in fluxbox right now.

You can also open a terminal and enter

```
sudo shutdown
```

That will bring down the system for you.

---

### Post by adobrakic on 2008-08-03
Did you try right clicking on the panel and going to Add To Panel, and then in the search box type in "Quit" and add to your panel

---

### Post by fatality_uk on 2008-08-03
I think the OP is talking about the dialog that appears after the logout button is clicked. It happened to me once and was ok after reboot.

---

### Post by Gaudentius on 2008-08-04
What I mean is when the quit button is selected, all other options are available but the shutdown button.

The "sudo shutdown" option blanks the screen, but it's more like a logout than a shutdown.

GD

---

### Post by Gaudentius on 2008-08-04
And wow, I just noticed that I don't even have a restart option either.

GD

p.s.
Is it ok to be doing hard shutdowns?

---

### Post by bpowell2005 on 2008-08-04
Ha! Where's your dark lord now?! :lolflag:

My Christian edition shuts down just fine thank you very much!
\:)

---

### Post by bpowell2005 on 2008-08-04
> **Gaudentius said:**
> And wow, I just noticed that I don't even have a restart option either.

GD

p.s.
Is it ok to be doing hard shutdowns?

Does your computers power button start a graceful Ubuntu shutdown? That's how mine was configured by default...I try to avoid the RESET button at all costs, but a quick tap of the power button almost always starts the Ubuntu shutdown process.

---

### Post by kansasnoob on 2008-08-04
> **bpowell2005 said:**
> Ha! Where's your dark lord now?! :lolflag:

My Christian edition shuts down just fine thank you very much!
\:)

What's the point of a post like this?

---

### Post by kansasnoob on 2008-08-04
I had to check some of my notes, but I knew that happened to me once.

I'd changed "Log-in" themes and needed to go System > Administration > Login Window:

[ATTACH]80138[/ATTACH]

You see at the bottom where it says "Show Actions Menu". Make sure that's "ticked".

Otherwise I'm clueless.

---

### Post by Gaudentius on 2008-08-04
> **kansasnoob said:**
> I had to check some of my notes, but I knew that happened to me once.

I'd changed "Log-in" themes and needed to go System > Administration > Login Window:

[ATTACH]80138[/ATTACH]

You see at the bottom where it says "Show Actions Menu". Make sure that's "ticked".

Otherwise I'm clueless.

Thank you Kansasnoob!  You are a godsend!  I wonder how I unchecked that.

And BPowell'05, I must've pissed him off for some reason.#-o 
I guess I redeemed myself because the dark lord sent me Kansasnoob!

Thanks to all who offered help.  Gotta love the Ubuntu community!

GD

---

### Post by bodhi.zazen on 2008-08-04
Satanic edition, I thought, was "just" a set of themes, no ?

Are there actual packages installed or specific configurations (outside of themes ?)

> It includes the complete Ubuntu 8.04.1 operating system plus the dark and brooding Satanic theme. There is also a 30 minute EP of creative commons licensed music from the likes of StabWounD, Auvernia, Frontside, Skaut, Taste of Hell, Scape.Goat and Holy Pain.OK, so some themes and some music, fairly basic ...

All I am saying is that the satanic edition is fairly close to a default Ubuntu installation.

Edit :

Ah, I see they have removed some things as well (for the live CD)

> A number of applications have been removed from the standard Ubuntu CD to make space for our theme and music. This includes the OpenOffice productivity suite comprising of a word processor, spreadsheet and presentation software. It also includes the Evolution email client, the F-spot photo photo management application, the Tomboy desktop note taking program and some games.

always nice to get an update from the variants of Ubuntu. I believe the Satanic Edition, like the CE, is "official" and therefore supported on these forums, although requests for support seem fairly minimal, :lolflag:

---

### Post by bodhi.zazen on 2008-08-04
> **bpowell2005 said:**
> Ha! Where's your dark lord now?! :lolflag:

My Christian edition shuts down just fine thank you very much!
\:)

Just a heads up, for better or worse the satanic edition is an "official" Ubuntu release, as is the CE.

As such both are supported on the forums.

I thought your post was funny, but I would appreciate it if we take care and not start flame wars ...

If you wish to discuss the issue please use OPP (OMG Purple Ponies) and keep these kind on comments out of the support forums.

No flame wars or Jihads here please :lolflag:

---

### Post by Gaudentius on 2008-08-04
As the OP, I didn't take it as a flame.  It was more of a ribbing.

BPowell'05 did offer a suggestion to try.

GD :popcorn:

---

### Post by bodhi.zazen on 2008-08-04
> **Gaudentius said:**
> As the OP, I didn't take it as a flame.  It was more of a ribbing.

BPowell'05 did offer a suggestion to try.

GD :popcorn:


Yes, I understand this, but the discussion can obviously get out of hand quickly and the comments, although funny, are not needed.

---

### Post by Oldsoldier2003 on 2008-08-04
> **bodhi.zazen said:**
> Yes, I understand this, but the discussion can obviously get out of hand quickly and the comments, although funny, are not needed.

It's a sad but true fact of forum life. People get offended over just about anything. In fact I find it offensive that I posted what I just did...

---

### Post by bpowell2005 on 2008-08-04
> **Gaudentius said:**
> As the OP, I didn't take it as a flame.  It was more of a ribbing.

BPowell'05 did offer a suggestion to try.

GD :popcorn:

Gaudentius,

I only meant humor, not a flame or insult. I'm glad you took it as it was intended! 

Also glad to hear your problem is fixed...what made the actions go away? Did you change themes or install a program that changed your shutdown options?

---

### Post by Gaudentius on 2008-08-04
> **bpowell2005 said:**
> ...what made the actions go away? Did you change themes or install a program that changed your shutdown options?

Kansasnoob suggested I check in **System > Administration > Login Window** and see if I had unchecked **Show Actions Menu** which I apparently had:confused:.

Anyway, I now have back both RESTART and SHUT DOWN. Woo hoo! \\:D/

GD

---

### Post by Lachinchon on 2008-09-15
Thanks Kansasnoob. I was in a panic when my shutdown and restart buttons disappeared. I finally shutdown using terminal commands, hoping the buttons would reappear on reboot. They didn't. Your observation about the setting in the login window manager worked like a charm. I had been changing my login screen before the calamity. My guess is that the "show actions menu" box is automatically unchecked when a different screen is selected. It will behoove me to be careful next time.

---

