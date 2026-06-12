---
title: "System problem with freezing"
date: 2015-12-09
forum: New to Ubuntu
---

### Post by Brian_Buck on 2015-12-09
I have an e-machines E510 laptop which I recently converted from Windows Vista to Ubuntu. This is working quite well for me apart from the fact that the image on the monitor continually changes to black and white and the system freezes for a few minutes before restarting with the image resuming its proper colour. Whilst the image is showing in black and white, the curser arrow can still be moved but is ineffective.

Can anyone suggest a way that I can correct this irritating problem please?

Many thanks

---

### Post by v3.xx on 2015-12-09
First tell us what your running.  Ubuntu, xubuntu;  15.10, 14.04 or something else?

You have a Celeron 560 single core processor and at best two gig of ram.  If your running Ubuntu then I would say your underpowered.  Ubuntu requires a lot of resources.

---

### Post by tdawgf on 2015-12-09
I have to second this. I think another problem might be the integrated GPU. I am not certain that GPU would have the umph (for lack of a better technical word jumping to mind), However, this is only assuming that the OP is using Ubuntu. Looking through the specs, I would highly recommend Lubuntu or Xubuntu for this machine.

---

### Post by Brian_Buck on 2015-12-10
I'm running Ubuntu 15.10

---

### Post by v3.xx on 2015-12-10
I would also suggest trying Lubuntu.

[http://lubuntu.net/](http://lubuntu.net/)

---

### Post by Brian_Buck on 2015-12-11
Many thanks for the suggestion. I have downloaded Lubuntu and this is now showing on my downloads file, but I haven't been able to fathom out how to install it from this point onwards. Could someone be kind enough to explain how this should be done - in simple terms please as I am very new to computers and find it difficult to understand much of the terminology. What I would like to do is completely replace the currently running UBUNTU system with LUBUNTU - not keep both of them.

Thanks again in anticipation.

---

### Post by v3.xx on 2015-12-11
I am uncertain if you still have windows installed.

If you have removed windows and have only ubuntu installed then just use the option to "use entire disk".  This will remove the current install.

If you have windows and ubuntu installed then I recommend to first use Gparted to remove the current ubuntu partition (you can leave the "swap" partition).  Gparted is on the Lubuntu live installer, look for it in the menu.

[http://www.dedoimedo.com/computers/gparted.html#mozTocId309606](http://www.dedoimedo.com/computers/gparted.html#mozTocId309606)

After you have deleted the ubuntu partition; close gparted and choose the install option from the desktop screen.

Now, when you get to this screen on the install

[ATTACH=CONFIG]266097[/ATTACH]

Check the box to install third party software.  Leaving "Download updates" unchecked (you can update later).

At this screen select "Something else".

[ATTACH=CONFIG]266098[/ATTACH]

And select the free space you created with Gparted.

[ATTACH=CONFIG]266099[/ATTACH]

Then create a mount point.

[ATTACH=CONFIG]266100[/ATTACH]

And finish the install.

If you have any questions, please ask.

---

### Post by Brian_Buck on 2015-12-13
Thank you for your suggestion, but I'm still struggling! I have downloaded Lubuntu and this now shows in my downloads folder. However, if I double click on it, the Archive Manager shows and I get the message "Reading Lubuntu 15.10" I then get an another message giving me the choice of 13 options, one of which is "install" but when I click on this, I get an error message.

I've obviously made a bit of a pig's ear of the whole operation, so I'd be grateful if you could set down the correct procedure step by step. My apologies if I come over as being a bit thick, but I am relatively new to computers and find much of the terminology a bit baffling.

Many thanks for your patience.

---

### Post by Vladlenin5000 on 2015-12-13
> **Brian_Buck said:**
> Thank you for your suggestion, but I'm still struggling!

Why??? Considering you *"recently converted from Windows Vista to Ubuntu"* what's keeping you from doing the same? It should be the exact same procedure...
I would also like to add that you used the wrong terms here: You can't convert Windows into Ubuntu. You actually installed Ubuntu using the default option thus removing any traces of the previous OS - it really doesn't matter which - in the process.

---

