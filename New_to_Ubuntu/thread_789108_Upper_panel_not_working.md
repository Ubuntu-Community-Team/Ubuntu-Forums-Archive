---
title: "Upper panel not working"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by Accinson on 2008-05-10
Hi,
i'm having a weird problem...

My upper panel isnt working anymore....i mean:i can see the "Applications","Places" and "System" sections on the left,but,on the right,i can only see the shutdown button...Moreover,none of the visible ones is working.I cant see desktop contents as well..

I tried to boot in recovery mode and i tried to fix server,but this  produced an addictional problem:the screeen is flickering...

Can you please help?

---

### Post by Accinson on 2008-05-10
>  tried to fix server

I meant xserver :)

---

### Post by Accinson on 2008-05-10
Anyone?

---

### Post by SunnyRabbiera on 2008-05-10
did you try to turn off desktop effects?

---

### Post by N.N. on 2008-05-10
> **Accinson said:**
> Hi,
i'm having a weird problem...

My upper panel isnt working anymore....i mean:i can see the "Applications","Places" and "System" sections on the left,but,on the right,i can only see the shutdown button...Moreover,none of the visible ones is working.I cant see desktop contents as well..

I tried to boot in recovery mode and i tried to fix server,but this  produced an addictional problem:the screeen is flickering...

Can you please help?
You will have to supply some more information to be properly assisted. Do you have desktop effects enabled? Which items are missing from your panel? How did you try to fix xserver?

The screen flickering you have described is probably due to incorrect refresh rates in your /etc/X11/xorg.conf file caused by faulty hardware detection. To fix this issue, you might have to specify the horizontal and vertical sync frequencies of your monitor manually. The following wiki entry details how this is done:

[https://help.ubuntu.com/community/FixVideoResolutionHowto#head-e2249d4bcb9fe0dea110f9b82ec7a40716221541](https://help.ubuntu.com/community/FixVideoResolutionHowto#head-e2249d4bcb9fe0dea110f9b82ec7a40716221541)

---

### Post by Accinson on 2008-05-10
Thanks for your answers :)

[quote=SunnyRabbiera]did you try to turn off desktop effects?[/quote] 
I don't have desktop effects enabled: one of the issues i have since the Hardy upgrade is that i am not able to turn them on.

[quote=N.N.]Which items are missing from your panel?[/quote]
I apologize for the lack of detail:first of all,i'm running Hardy in an Acer 5720G laptop.
The icons i miss are those on the right side of the upper panel (clock,search,network,volume ...).The only one i can see is the "logout" one.Everything else looks fine,but none of the things i can see, seem to work, i.e. i cannot interact with the visible menus (i click on them,but nothing happens).

Moreover,when i log on,i can see the desktop folders and open them,but,after that,the pc starts to hung (so i can't continue to browse the file system).This happens also if i right click on the desktop:the pc hungs on the context menu.

[quote=N.N.]How did you try to fix xserver?[/quote]
I did it with the xfix utility when i booted in recovery mode.


Further detail...
Sometimes,after pressing CTRL+ALT+backspace the screen flickering  effect disappeared,but that was kinda erratic...after another reboot,it restarted to flicker..

---

### Post by N.N. on 2008-05-10
It seems like you have a more serious problem than just gnome-panel acting up. However, if you are lucky, you might be able to solve the problem by simply resetting your GNOME settings.

The easiest way to determine whether this will solve your problem is to add a new user and then log in with that user. If things are working properly when you are logged in as that user, that means that the problem lies in the GNOME settings of your original user. In that case you can solve your problem by reverting the user's GNOME settings to the default configuration by deleting (or renaming) the following hidden folders which are located in the user's home directory (press CTRL+H to reveal hidden folders):

[LIST]
[*].gnome
[*].gnome2
[*].gconf
[*].gconfd
[*].metacity
[/LIST]

EDIT: Also, did you try the fix I suggested for the screen flickering problem?

---

### Post by Accinson on 2008-05-11
Hi and thanks N.N. for your vey kind help :)

I did what you suggested (both for the flickering problems and the missing panel icons) and now the flickering disappeared and the icons came back,but...

It seems Nautilus has something wrong...i mean:i can now try to run the terminal by clicking "Applications>Accessories>Terminal" but after the click the terminal won't run.
Moreover,i can't explore the fyle system with nautilus:i tried to open a desktop folder,the contents were correctly displayed,but then,from that folder,tried to explore the filesystem and,after some time,it said the window browser was not responding.After that,i couldnt see the desktop icons anymore.

Any idea?

---

### Post by N.N. on 2008-05-11
Unfortunately I don't know how to solve that problem, Accinson. :(

The only advice I can give you is this: try starting a new thread about your problem and make sure it has a descriptive title detailing the terminal and nautilus problems. With luck, someone experienced will then drop by and help you with your problem.

---

### Post by Accinson on 2008-05-11
I'm gonna do that.

Again,thanks for your patient help,i do appreciate it :)

---

