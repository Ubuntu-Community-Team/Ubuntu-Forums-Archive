---
title: "Adept Updater Not Notifying"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by ChompTheMan on 2008-05-15
Hello.  I'm using 8.04 and Adept updater is not notifying me of updates.  I see the green circle pop up in my system tray when I first log in, but the update manager never pops up I have to 'sudo apt-get update'.

I had uninstalled Adept earlier and installed Synaptic.  Synaptic didn't work  out for me so I uninstalled it and re-installed Adept.  How do I get the updater to notify me when updates are available rather than  manually doing it?

---

### Post by Xiong Chiamiov on 2008-05-17
If you get the green circle, it means it can't find any updates.  If there really are updates, perhaps you're not yet connected to the internet?

---

### Post by ChompTheMan on 2008-05-18
I am connected to the internet.  The green circle is very familiar to me.  It was there when I first logged in to Kubuntu Feisty and it always brought up adept-notifier if updates were available.  Now I have to type 'sudo apt-get update' in order for adept-notifier to pop up in my system tray.  It used to do this automatically.  Now it doesn't and I can't figure out why.

---

### Post by MickS on 2008-05-18
Mine doesn't work either, in fact it didn't when on Gutsy, just saying that to subscribe to the thread and give it a bump.

Mick

---

### Post by Nosferatu1 on 2008-05-22
I can confirm also that the notification mechanism is not working correctly. The adept-notifier icon always shows as green until I manually start up adept and do a "Fetch Updates", after which the icon changes and notifies me that there are updates. 

I would think that the notifier should do auto Fetch Updates, however this would require SU privileges or does it?

I'll have a look at the documentation for adept-notifier so I can figure out how the mechanism should work and what's going wrong with the process.

---

### Post by Nosferatu1 on 2008-06-02
Bump


Doesn't anyone have any input or ideas?
Is the synaptic version working as expected?
An update notifier is sort of an important thing to get working correctly, otherwise what's the use in having it?

---

