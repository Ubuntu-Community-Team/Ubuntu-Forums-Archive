---
title: "When I start Ubuntu I get this message."
date: 2008-05-27
forum: New to Ubuntu
---

### Post by JohnPta on 2008-05-27
Internal error
failed to initialize HAL!

I never had that message till I upgraded to 8.04 Hardy Heron.

---

### Post by sayakb on 2008-05-27
Did the update wizard and freeze and exit by itself? I think it did. On facing the same problem, I backed up my data and went for a Hardy clean install.

---

### Post by cdtech on 2008-05-27
I've seen this with the upgrade. Most are uninstalling the hal and reinstalling with success.

You could try:
sudo /etc/init.d/hal restart (see if you get the hardware abst layer restart message)

You'll probably end up reinstalling hal anyway.

Hope this helps.......

---

### Post by iaculallad on 2008-05-27
Or before doing a clean install, you could at least browse this [link]("http://ubuntuforums.org/showthread.php?t=291130") for a solution regarding the Hardware Abstraction Layer error.

---

