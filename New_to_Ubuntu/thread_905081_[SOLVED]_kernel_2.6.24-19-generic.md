---
title: "[SOLVED] kernel 2.6.24-19-generic ???"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by anewguy on 2008-08-30
One of the updates that ran this week installed kernel 2.6.24-19 generic, but it never updated my menu.lst for grub.  Am I supposed to start using that kernel image?

Thanks in advance!

Dave :)

---

### Post by nicedude on 2008-08-30
Yes the kernel will update every so often, like I am using -21 right now. But your grub menu list should automatically add the new kernel to your boot choices, unless you have changed something to tell grub to not update it ( I forget what it is that can do that but I saw a thread where someone had the same problem the other day )


You could always change menu.lst by hand if you wanted as it shouldn't be too hard for you to do, but over a long period and many kernel updates that could get annoying so you might want to figure out how to fix it instead :-)

---

### Post by anewguy on 2008-08-30
> **nicedude said:**
> Yes the kernel will update every so often, like I am using -21 right now. But your grub menu list should automatically add the new kernel to your boot choices, unless you have changed something to tell grub to not update it ( I forget what it is that can do that but I saw a thread where someone had the same problem the other day )


You could always change menu.lst by hand if you wanted as it shouldn't be too hard for you to do, but over a long period and many kernel updates that could get annoying so you might want to figure out how to fix it instead :-)

Thanks for the reply!  It has always updated the grub menu for me in the past - the only difference this time is that I had to walk away from the PC for a few hours - maybe something timed out?

At any rate, I guess since your at -21 now it should be okay for me to use -19, so I'll make the change in the menu.

Thanks again!

Dave :)

---

### Post by Shazaam on 2008-08-30
If you look at the end of the new kernel it will be 2.6.24.19.41 so you may not see a change to menu.lst. 2.6.24.19.36 was what I had before and my menu.lst did not change. Menu.lst would change if the .19 went to .20.0 or higher.

---

### Post by anewguy on 2008-08-30
AHAAA - that's it!!  Never thought of that!

Thanks! 
Dave :)

---

