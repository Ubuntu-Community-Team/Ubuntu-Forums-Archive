---
title: "start alternate program when ipod connected"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by steve_4802 on 2008-04-27
Hi team,
Using amarok instead of rhythmbox to manage the ipod. How do I make ubuntu 8.04 start amarok instead of rhythmbox whenever I connect the ipod?

I know with earlier versions of ubuntu you used to be able to just do it in system->preferences-?removable drives and media. However this doesn't seem to be the case anymore.

Thanks in advance.

Also, any help with the correct command to eject the ipod with amarok would be most helpful as well. Cheers!

---

### Post by ro314 on 2008-04-27
What about starting nautilus (Places -> Home Folder) --> Edit --> Preferences --> Media --> Music Player --> Choose your program.
greetings
robert

---

### Post by steve_4802 on 2008-04-28
Hi Robert,
Yes that would work, except, for some reason Amarok doesn't come up in that list as an option (at least for me?). This gets me half way there though as I can at least use this drop down to stop Rhythmbox from starting by default.

Do you know how to have Amarok appear as an option in that list?

Thanks

---

### Post by ro314 on 2008-04-28
hi steve,
ok - i have by now installed amarok - and amraok doesn't show up for me too. my next guess would have been to change the configuration using the command gconf-editor:
/desktop/gnome/volume_manager/autoipod
/desktop/gnome/volume_manager/autoipod_command

but that doesn't seem to work... strange.

---

### Post by fhmanas on 2008-04-29
trying as well to replace Rhythmbox with banshee but change in nautilus and preferred applications would not work, it would start banshee but ipod gets stuck with rhythmbox.  Banshee was not the problem, bec somehow I was able to connect my ipod to banshee once by clearing the preferred applications and setting to custom and blanking it.  But after a reboot it went back to Rhythmbox.

This was a lot easier in Gutsy.

---

