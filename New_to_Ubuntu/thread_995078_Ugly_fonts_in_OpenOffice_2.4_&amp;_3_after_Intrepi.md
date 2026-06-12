---
title: "Ugly fonts in OpenOffice 2.4 &amp; 3 after Intrepid clean install"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by Proshka on 2008-11-27
Hi,

Every time I update Ubuntu I have the same annoying problem with OpenOffice: the menu fonts look absolutely ugly. I think I have tried all the suggestions I could find in the community fora since the old Dapper days with relative success. Unfortunately, once I find a more or less cosmetic solution after weeks of trial and error (and of course I do not remember all I did to get good results) I have to begin working again because the new upgrade or clean install has ruined it all as usual. I am currently using Intrepid with both OO 2.4.1 and 3 installed. I will welcome any help that may fix this issue.

---

### Post by OrangeCrate on 2008-11-27
I'm not sure which fonts you're looking for, to make OOo look better, but these things might help...

Have you installed the restricted extras, to get the MS TrueType fonts?

[http://packages.ubuntu.com/intrepid/ubuntu-restricted-extras](http://packages.ubuntu.com/intrepid/ubuntu-restricted-extras)

Or, if you just want the TrueType fonts, take a look here:

[http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/](http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/)

Hopefully, this is what you're looking for.

---

### Post by Proshka on 2008-11-27
Yes, I have already installed those fonts and extras with no avail. What I mean for "ugly fonts" is blurred egdes, no sharp contorns whatsoever.

---

### Post by OrangeCrate on 2008-11-27
> **Proshka said:**
> Yes, I have already installed those fonts and extras with no avail.

I'm currently using Xfce on Xubuntu, so I can't exactly remember how to do this on Ubuntu Gnome, which is what I'm assuming you're using, but go to System > Appearance > Fonts, and check your system settings for fonts. Frankly, I use Verdana for everything, and it picks it up for OOo. Change to what you like, and see if that picks up in the OOo menus.

---

### Post by OrangeCrate on 2008-11-27
You edited your post while I was replying, so here's an additional thought...

Under Fonts, check your font rendering. Change it to what you like. Personally, I use full hinting, and sub-pixel hinting for LCD screens. My OOo menus are crisp and clean.

If a combination of my suggestions don't work for you, I can't offer anything else. Sorry.

---

### Post by pablolie on 2008-11-27
> **Proshka said:**
> Hi,

Every time I update Ubuntu I have the same annoying problem with OpenOffice: the menu fonts look absolutely ugly. I think I have tried all the suggestions I could find in the community fora since the old Dapper days with relative success. Unfortunately, once I find a more or less cosmetic solution after weeks of trial and error (and of course I do not remember all I did to get good results) I have to begin working again because the new upgrade or clean install has ruined it all as usual. I am currently using Intrepid with both OO 2.4.1 and 3 installed. I will welcome any help that may fix this issue.

Do your preferences under "appearance" change? Personally, I find 8.10 had a cleaner interface with more readable fonts, I have only seen an improvement.

---

### Post by Proshka on 2008-11-27
Thanks Orange. Still blurry with Verdana and other fonts. I tried all possible combinations under font rendering too.
Pablolie, OO is the only application which causes me trouble. The other ones always look nice regardless the upgrades.

---

### Post by OrangeCrate on 2008-11-27
One last thought...

In OOo,

Go Tools > Options > OpenOffice.org > View, and make sure that the "Use system font for user interface" box is checked.

---

### Post by Proshka on 2008-11-27
> **OrangeCrate said:**
> One last thought...

In OOo,

Go Tools > Options > OpenOffice.org > View, and make sure that the "Use system font for user interface" box is checked.

It is.

---

### Post by peterhoeg on 2008-12-19
> **Proshka said:**
> It is.

Do you have openoffice.org-gtk and openoffice.org-gnome installed? I had exactly the same problem as you on one machine and it was caused by those two packages not being installed.

---

### Post by Proshka on 2008-12-19
Yes, both packages are installed but the situation is exactly the same. Since Feisty I could not have crispy fonts again.

---

### Post by yaztromo on 2009-01-16
Hi. Please see [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/271283/](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/271283/) for description of bug and workaround near bottom of page.

---

### Post by Proshka on 2009-01-16
> **yaztromo said:**
> Hi. Please see [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/271283/](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/271283/) for description of bug and workaround near bottom of page.

Thanks, I will try it.

---

### Post by jnewm on 2009-09-10
Possible Solution? - Ok, I'm really late to this thread, and maybe your problem isn't the same as mine...  BUT I figure I'd post what solved the problem for me, in case it helps you or anyone else.  Basically, I'd installed msttcorefonts and everything looked great, except on my OpenOffice menus, which had a blurry nasty font.  I tried searching for a solution but couldn't find anything.  Finally, I checked (probably for the 50th time) to make sure the "Use system font for user interface" box was checked.  Of course it was, BUT I also noticed the little "Screen font Antialiasing" setting underneath, which was set to "from _1_ Pixels."  A light bulb went off and I changed the setting to "from _100_ Pixels" (i.e. to do away with the antialiasing).  AND THAT WAS IT!!!  I guess the OpenOffice antialiasing just blurs the heck out of the msttcorefonts (I was using "Times New Roman").  Okay, that's it.  I hope this helps someone! :)

---

### Post by Proshka on 2009-09-11
Thanks jnewm, your message was very enlighting. I immediately tried your solution but it did not work (even more blurred fonts). Later on I checked the "User system..." and the "Screen font antialiasing" boxes again and begun playing with numbers. Oddly, the antialiasing set to 1 did the trick! Now I can type my document without crying anymore. Thanks!

---

### Post by jnewm on 2009-09-12
Awesome Proshka!  I'm so glad it helped!

---

