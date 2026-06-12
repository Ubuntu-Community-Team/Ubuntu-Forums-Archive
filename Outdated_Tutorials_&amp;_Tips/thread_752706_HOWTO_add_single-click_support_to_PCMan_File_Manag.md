---
title: "HOWTO add single-click support to PCMan File Manager"
date: 2008-04-11
forum: Outdated Tutorials &amp; Tips
---

### Post by mrjnoobles on 2008-04-11
[B]PCMan File Manager is a fast, lightweight file manager by Hong Jen Yee.

[http://pcmanfm.sourceforge.net/](http://pcmanfm.sourceforge.net/)[/B]

[CENTER]Have you ever wished you could use single-click to open items in PCMan?

I did, so I made this patch and now you can!

[IMG]http://nuqlear.com/crap/prefdlg.png[/IMG][/CENTER]

This tutorial will show you how to patch PCMan 0.3.9.10 to support single-click opening of items.
> 
[SIZE="4"][COLOR="DarkRed"]Step 1[/COLOR][/SIZE]

You will need the source for PCMan version 0.3.9.10, get it here:

[http://sourceforge.net/project/showfiles.php?group_id=156956&package_id=265937&release_id=585699](http://sourceforge.net/project/showfiles.php?group_id=156956&package_id=265937&release_id=585699)

[SIZE="4"][COLOR="DarkRed"]Step 2[/COLOR][/SIZE]

Extract the archive somewhere, it should extract into a folder named "pcmanfm-0.3.9.10".

[SIZE="4"][COLOR="DarkRed"]Step 3[/COLOR][/SIZE]

Download my patch here:

[http://nuqlear.com/crap/pcmanpatch.zip](http://nuqlear.com/crap/pcmanpatch.zip)

[SIZE="4"][COLOR="DarkRed"]Step 4[/COLOR][/SIZE]

Extract the patch into your "pcmanfm-0.3.9.10" folder.

If it asks if you want to overwrite existing files say yes.

[SIZE="4"][COLOR="DarkRed"]Step 5[/COLOR][/SIZE]

Prerequisites for compiling PCMan: (taken from the PCMan site)

[QUOTE]automake
libgtk2.0-dev
libglib2.0-dev
libgamin-dev
libstartup-notification0-dev

If you are unsure if you have these packages try to install them using 'sudo apt-get install'.

For example, if you wanted to install libgtk2.0-dev you would enter the following into the terminal:

```
sudo apt-get install libgtk2.0-dev
```

[SIZE="4"][COLOR="DarkRed"]Step 6[/COLOR][/SIZE]

Open up a terminal and navigate to the "pcmanfm-0.3.9.10" folder, then enter the following:

```
./configure
make
sudo make install
```

[SIZE="4"][COLOR="DarkRed"]To uninstall PCMan:[/COLOR][/SIZE]

Open up a terminal and navigate to the "pcmanfm-0.3.9.10" folder, then enter the following:

```
sudo make uninstall
```

[SIZE="4"][COLOR="DarkRed"]To un-patch PCMan:[/COLOR][/SIZE]

First, uninstall PCMan using the previous instructions.

Delete the "pcmanfm-0.3.9.10" folder.

Extract the PCMan source.

Compile using the instructions from step 6.
[/QUOTE]

Thanks for looking!

If you find any bugs etc please reply and let me know what's up.

---

### Post by K.Mandla on 2008-04-12
Interesting. I'm not a single-click fan, but it's always good to see someone add features to a great little file manager.

Did you submit your patch to PCMan?

---

### Post by KongKNoob on 2008-05-19
Great!

But, like mrjnoobles said, you should get this in to source code. The PCMan FM project invites everyone to participate, and it would be great if "one-click" was supported by default.

---

### Post by TrD on 2008-06-28
Thank you. 

I think PCMan should make this an option on next versions.

---

### Post by PCMan on 2008-07-16
> **TrD said:**
> Thank you. 

I think PCMan should make this an option on next versions.

Please don't mix this patch with the latest version of PCManFM.
Since PCManFM 0.4.6, single-click is already well-supported.

---

