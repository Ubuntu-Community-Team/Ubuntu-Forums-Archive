---
title: "remove &quot;Remove CD and Press enter to shutdown&quot; from liveCD shutdown process"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by brdohman on 2008-05-15
Currently when you shutdown a liveCD, it prompts you to remove the disc and then press enter to shutdown.  Is it possible to just have the cd shutdown the machine completely, removing the prompt to have the user press enter?

I've created a custom cd that is going to be used on public machines all the time.  The user gets 60mins on the machine, before it shuts down.  But then they have to wait around to press enter, or the next user has to press enter.  The cds stay in the machine and aren't removed.  So I would like for it to be able to just shutdown, with the extra user interaction.

Thanks

---

### Post by candtalan on 2008-05-16
the command
sudo /sbin/shutdown -h now
will simply shutdown (I believe), maybe you could link that in a small script file with the live cd shutdown menu item?

---

### Post by sirdan on 2009-06-03
I was wondering if there was any resolution to this question. I have the same scenario, except I want users to be able to select restart and not see the system prompt to remove the LiveCD (which really is a USB drive).

Any suggestions?

---

### Post by LewRockwell on 2009-06-03
[http://www.computing.net/answers/linux/one-click-shutdown-as-user/29097.html](http://www.computing.net/answers/linux/one-click-shutdown-as-user/29097.html)

---

