---
title: "Heron - Newbie upgrade issues"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by lambomania on 2008-05-04
Something went wrong when I ugpraded to Heron from Gutsy. 

I noticed something was wrong after I had to log on. The system had restarted after applying the updates, and I received two error messages:
[LIST=1]
[*]1 - Nautilus can't be used now due to an unexpected error from bonobo when attempting to register the file manager view server. error code: 3 and will exit it may be automatically restarted.
[*]2 - The panel has encountered a fatal error. The panel could not register with the bonobo activation server.
[/LIST]

I searched the forums for similar errors. Some users reset their system clocks or just did a killall for the bonobo activation server. These didn't seem to fix it for me...This is now less urgent to me since I can log on in the Gnome failsafe session, but I would like to try to resolve if anyone has a brilliant idea. Thanks in advance for your attention. :)

---

### Post by halloween2311 on 2008-05-06
Greetings Lambomania,

I am having the same issue.  I have not tried to kill bonobo but will give that a shot right now.

Anyone have any ideas?:confused:

Thanks as always!

---

### Post by halloween2311 on 2008-05-06
Greetings Lambomania,

Okay, I have it working for me now using the advice I found on this thread

[http://ubuntuforums.org/showthread.php?t=780412&highlight=nautilus+bonobo](http://ubuntuforums.org/showthread.php?t=780412&highlight=nautilus+bonobo)

Posted by SonicSteve(thanks again by the way)

Have you tried installing mono (moonlight, the open source version of microsoft silverlight)?  That was my problem and after I uninstalled it everything worked fine.

I hope his helps!:)

---

