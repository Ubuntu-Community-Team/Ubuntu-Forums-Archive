---
title: "Ubuntu 12.10 crashing on Standby"
date: 2013-04-15
forum: New to Ubuntu
---

### Post by Vontech615 on 2013-04-15
Hello all, 
This is my first post.  I guess you could call me a new user as I don't have skills with Linux like I do with Windows.  I've dabbled with Linux for about 3 years but never really delved in to far.  Anyway, to get to my question...   I have an Acer with an i5 and Nvidia Geforce 420m.  I've got it setup dual booting Windows 7 and Ubuntu.

  It all works fine until I close the lid, engaging standby or manually sending it to standby.  When I wake it back up, it's crashing.  It gives me a white screen with just the password asterisks.  I type password in and hit enter and it just sits at a black screen.  

Like Xorg is totally misbehaving afterwards, then I have to shutdown and start back up.  It acts ok as long as it doesn't go to standby.  It's using the Nouveau driver in place of anything proprietary.  This is what Ubuntu chose by default.  Thanks for any and all helpful suggestions.

Also, just to note I have run all available updates.

---

### Post by sp-1070 on 2013-04-15
Hi

Try to boot the computer and put it to standby then open the lid and try to hit the cntrl+alt f6 button to enter a terminal there.
See if that works and if it does try to kill the xorg process using ```
killall -9 xorg
```

And then hit cntrl alt f7 to take you back it should restart the window manager if it doesn switch back to f6 and use startx

Go see if that works !

SeeYa

---

### Post by Vontech615 on 2013-04-15
K, thanks.  I'll try this when I get back to the house.  Just curious, in essence your killing xorg and restarting, correct?  So what's that going to tell me, again just curious.

---

### Post by grahammechanical on 2013-04-15
What is the size of your swap partition? With hibernation and suspend the contents of system memory has to be stored somewhere and swap is the place. So, the swap partition has to be as large as system memory (RAM).

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Oh, by the way, Windows has a swap file. Yes? Ubuntu has a swap partition. So, it is not dynamically expandable. The size is fixed.

Regards.

---

### Post by Vontech615 on 2013-04-15
Good question.  I'll check and get back to you.  I allocated 100GB for my Ubuntu partition so I would think unless something went wrong with the install, then it should be adequate.  I've installed twice with same issue.  What's the best way to find the swap partition size?

---

### Post by sp-1070 on 2013-04-15
hi so this will show us if the problem is purely in xorg or that the whole system just crashes

---

### Post by Vontech615 on 2013-04-15
Gotcha, thanks.  I'll get post back when I've done this.

---

### Post by Vontech615 on 2013-04-15
> **grahammechanical said:**
> What is the size of your swap partition? With hibernation and suspend the contents of system memory has to be stored somewhere and swap is the place. So, the swap partition has to be as large as system memory (RAM).

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Oh, by the way, Windows has a swap file. Yes? Ubuntu has a swap partition. So, it is not dynamically expandable. The size is fixed.

Regards.

The swap size is 4.1 GB.  This should be adequate as I have 4 GB of ram.

---

### Post by Vontech615 on 2013-04-15
Ok, so I sent it to standby and it crashed when waking back up.  I ctrl alt f6 and then f7 which didn't fix anything.  The screen was still white and I could see the asterisks for the password.  I typed command: startx and it did start back up but just the background, then crashed again.

---

### Post by sp-1070 on 2013-04-16
At this point you might try reinstalling gnome but i'm not sure if that will solve annything but you might try it. Im using the gnome-shell since 13.04 and its working so yo might even consider upgrading to that. hope this helps. 

sudo apt-get purge gnome
sudo apt-get install gnome

or sudo apt-get install gnome-shell and then at login choose gnome instead of ubuntu

---

### Post by Vontech615 on 2013-04-16
Well, I can shutdown and restart and it comes back up.  I'm not an expert at reading Linux logs but I've found some evidence of graphic driver failure.  I wonder if 12.04 would be something to try? It may be more stable with my hardware.

---

