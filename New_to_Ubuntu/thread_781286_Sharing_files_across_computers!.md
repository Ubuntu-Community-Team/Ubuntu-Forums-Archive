---
title: "Sharing files across computers!"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by ashwin108 on 2008-05-04
Excuse me, 

I have installed Hardy Heron LTS on my computer and another computer of mine. They are both connected to a router, along with another computer running windows 2000. I can see the windows computer from both the Hardy computers. I want to share files between the two Ubuntu machines, but I couldn't find any up-to-date information on how to. It worked fine when the computers were running Windows XP.
 I have tried installing Samba and right clicking on the folder i want to share, but all I get is this error message:

> 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.

Please tell me how to share files between the ubuntu comps!

---

### Post by locky28 on 2008-05-04
Also needing help with this.

---

### Post by Qball2105 on 2008-05-04
I also need help with this!

---

### Post by drsox1899 on 2008-05-04
Hi to you all.

Try this easy HowTo. Works well.

[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+howto](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+howto)

Luck

PS Having a static IP address is not needed, but ensure that you tell the system that you don't.

See in the HowTo :

" .... -> wins support = yes

If your box doesn't have a static ip-address, or you cannot configure your router/server to provide you with a fixed dhcp-lease, change this configuration parameter to "no".

In this case you cannot use the benefits of WINS. .... "

---

### Post by GavinZac on 2008-05-04
from a terminal, run the command:

sudo nautilus

And then try to do what you were doing, inside the window that opens. You should have permission to do it then.

---

### Post by locky28 on 2008-05-04
I found I just needed to do a restart. Theres a bug listed in launchpad saying that it should tell you that you have to logout/restart before it will work.

---

