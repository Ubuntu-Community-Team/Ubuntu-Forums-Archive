---
title: "[SOLVED] I do not want to upgrade to Hardy yet"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by Homosuperior on 2008-06-06
Okay, so I've been dual-booting for several months now, and decided to upgrade to Hardy a couple months ago and everything started crashing on me constantly. I can handle a lot when it comes to dealing with beta programs, but my wife and kids can't, and I'm having a hard enough time integrating linux into our lives without the extra stress, so I decided to revert to Gutsy which has worked fantastically for us. But when I finished re-installing today, and went through all of the updates, now it appears to be holding my updates hostage and wants to do a "partial upgrade" and tries to upgrade to 8.04 every time I try to do a software upgrade. I have no interest in upgrading my OS at this time, but I do want to make sure everything is updated otherwise. HELP!!! I can't find anything anywhere on this, and I don't know if I can just not do upgrades for the time being and as software upgrades come up, will I be able to upgrade them without upgrading to Hardy? Any help would be appreciated as I really enjoy Ubuntu, but I'm still trying to get my family into it. Thanks in advance.

---

### Post by sayakb on 2008-06-06
System->Administration->Software sources
Click on Updates tab. **Uncheck **pre-relesed and unsupported updates.
Also, under release upgrade, set *Show new distribution releases* to Never .
Close the window and press Reload button when asked to.

---

### Post by Homosuperior on 2008-06-06
Okay, I got the first part, but I couldn't find "release upgrade, set Show new distribution releases to Never". Am I missing something? I'm still not really familiar with linux yet, so I don't know if I need to use some sort of sudo command, or use root or if I'm just missing it. Thank you for your rapid response!

---

### Post by sayakb on 2008-06-06
Under the Updates tab, at is at the bottom of the window. Expand the drop menu and select **Never** from there.

[ATTACH]73120[/ATTACH]

---

### Post by Homosuperior on 2008-06-06
My frame doesn't have that option at the bottom, but I am signed in under the administrator account. ??

---

### Post by sayakb on 2008-06-06
Okay fine.. lets try something else then :)
Press Alt+F2
Type in **gconf-editor** and press Enter
Now navigate to apps->update-manager
There on the right panel, **uncheck **check_dist_upgrades
Close the gconf-editor window, and open the update manager and press Check/Reload.
The notification should go away (or maybe it might need a reboot)

---

### Post by Homosuperior on 2008-06-06
You are my HERO!!! Thank you!

---

### Post by sayakb on 2008-06-06
Lol.. Glad I could help :)

---

