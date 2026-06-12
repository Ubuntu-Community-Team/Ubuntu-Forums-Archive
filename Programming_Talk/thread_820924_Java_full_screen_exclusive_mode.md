---
title: "Java full screen exclusive mode"
date: 2008-06-06
forum: Programming Talk
---

### Post by Jimmay on 2008-06-06
I'm trying to make a game in java, but despite all efforts I can't find out how to get full screen exclusive mode working in java. I managed it in Gutsy - simply not checking that FSEM was enabled and just using it worked fine, but that doesn't seem to work with hardy.
What gets me is that JDarkroom CAN use FSEM but I can't! I've searched everywhere, and all I get is reams of pages ranting about sun not supporting FSEM in Linux (apparently this isn't limited to ubuntu).

So, does anyone know how to get FSEM to work in hardy heron with java?

---

### Post by Jimmay on 2008-06-07
Anyone? :(

---

### Post by Lau_of_DK on 2008-06-07
Sorry, no.

But maybe its time you wrote Suns support? If you find a solution, please post it here, I'd be most interested.

/Lau

---

### Post by Jimmay on 2008-06-07
I've managed it! No-one would ever guess what the cause of the problem was though: calling setResizable(false) on the window to be made full screen caused the window to be displayed below the gnome taskbars. ](*,)](*,)](*,). Removing the call makes the window completely full screen. Of all things!

---

### Post by Lau_of_DK on 2008-06-07
Haha, sweet! :)

Thanks for the warning.

/Lau

---

### Post by moosejc on 2008-06-26
Unfortunately, I am having the same problem with creating a full screen game in Java. I found a bug report on the matter here: [https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/154613]("https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/154613") I am still a noob to ubuntu (and linux in general), and I can't figure out how to fix it. If you figure any thing out, let me know.

---

