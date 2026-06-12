---
title: "Ubuntu Access files on a Windows DC"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by bprof on 2008-07-17
Hello,

I've been looking around for a way to allow Ubuntu (7.10 server) access Windows domain controller.

I found many guides on how to use Samba with work group, or make Samba a domain controller, but those don't help me do that.

Any help?

Thanks!

---

### Post by lazyart on 2008-07-17
I used sadms to join my ubuntu desktop to the domain.  Users are authenticated via AD and accessing shares is a piece of cake.

Don't know if you want to put a gui on your ubuntu server to go that route, but if you already have gone graphical, I'd suggest it.

---

### Post by bprof on 2008-07-17
Thanks for your input lazyart. GUI is not an option for me at this time.

---

### Post by bodhi.zazen on 2008-07-17
Then you need to edit the config file and add the windows domain

[https://wiki.ubuntu.com/ComprehensiveSambaGuide](https://wiki.ubuntu.com/ComprehensiveSambaGuide)

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

[http://www.onlamp.com/pub/a/onlamp/2008/04/01/step-by-step-using-samba-to-join-a-windows-domain.html](http://www.onlamp.com/pub/a/onlamp/2008/04/01/step-by-step-using-samba-to-join-a-windows-domain.html)

---

### Post by bprof on 2008-07-20
The links were very helpful thank you.

---

