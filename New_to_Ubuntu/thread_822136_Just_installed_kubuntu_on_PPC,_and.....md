---
title: "Just installed kubuntu on PPC, and...."
date: 2008-06-07
forum: New to Ubuntu
---

### Post by ivanpk on 2008-06-07
Hi,
I just installed Kubuntu, on my iBook G4 PPC
and I'm having some troubles. How do I get the trackpad to work faster? I edited a file in the Terminal like one thread said, yet this didn't help. Do I have to restart my computer first?
Is there any other thing to do? I would be able to explore lots more if I could actually navigate well :]


Thanks,
Ivan

---

### Post by avtolle on 2008-06-07
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328) is a link to the Apple Users Forum, where your question may receive more specialized attention. You will also need to provide the release of Kubuntu you are running as well.

Off the top of my head, it looks like you might need to edit the/etc/X11/xorg.conf file, and this is what you may be referring to in your post. However, before doing anything else, I'd get a copy of that existing file saved somewhere, as someone will want to look at it over on the Apple Users Forum, and it will save time if you have it ready to post. For example, at the terminal```
cat /etc/X11/xorg.conf > /home/<your user name>/Desktop/xorgconfig.txt
``` will create a text file you can post as an attachment. Hope this helps.

---

