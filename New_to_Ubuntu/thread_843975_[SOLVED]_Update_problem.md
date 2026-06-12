---
title: "[SOLVED] Update problem"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by d4ng3r on 2008-06-29
Okay, so earlier I had a problem because my /boot partition is too small and when Ubuntu updated the boot there was enough space and I needed to manually delete the old boot files and manually configure the update using some command it gave me.  Recently though, all my updates have been failing, or being left "un-configured" because of dependency on kernel version 19 or something.  I think it is due to a similar problem, but this time is different, Linux did not give me the command to manually fix it, and the updater didn't stop functioning like it did last time, it keeps "installing" updates, but gives me dependency errors every time.  I don't know what to do at all, I don't want to risk deleting my old boot information without knowing it will update, and what of the recently installed updates, will they automatically fix themselves, or do I have a large mess on my hands.

Thanks
-Brian

---

### Post by svk on 2008-06-29
Ok, it does sound like something got messed up pretty badly.  Cleaning up is always a pain, but there is one last thing you could try.

Go into the terminal.  All of the following commands should be issued as root.

First, try **sudo apt-get check**.  Does it report any problems?

Next, try **sudo apt-get update && sudo apt-get -f upgrade**.  The -f option should cause apt-get to attempt to fix broken packages.

If these do not work, there are more dangerous things you could try (like force apt-get to ignore missing dependencies), but they're generally not a good idea.  Rather, tell us specifically which packages are missing.  Copy and paste the error messages.

---

### Post by d4ng3r on 2008-06-29
Thank you, the -f apt get fixed it.  I had to manually remove the old boot images first, hopefully everything else will fall into place

---

### Post by adobrakic on 2008-06-29
please mark the thread as solved, and give a thank you(please) :)

---

