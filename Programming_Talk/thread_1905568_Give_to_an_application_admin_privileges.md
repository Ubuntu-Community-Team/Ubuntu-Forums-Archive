---
title: "Give to an application admin privileges"
date: 2012-01-07
forum: Programming Talk
---

### Post by hakermania on 2012-01-07
Hello!

I know how to start an application with admin privileges, but I have an application which does specific tasks and none, except one, needs admin privileges.
I am not willing to start the application with administrator privileges because of this specific task and it came in mind what happens in the Ubuntu Software Center (USC):
When you click on install, then it prompts for password, and once you type it, the program gets (temporarily) admin privileges so as to install the selected software.
Can you en-light me on how this works so as to do the same or similar with my own app?
Thanks!

---

### Post by Lars Noodén on 2012-01-07
That would be [sudo](http://manpages.ubuntu.com/manpages/oneiric/en/man8/sudo.8.html) or a related program like [gksudo](http://manpages.ubuntu.com/manpages/oneiric/en/man1/gksudo.1.html)

---

### Post by hakermania on 2012-01-07
Lars, thanks for the help, but I don't think that these are the ones I need
(gksu  is  a  frontend  to  su  and gksudo is a frontend to sudo. **Their primary purpose is to run graphical commands that need root without the need to run an X terminal emulator and using su directly**.}

What I need is to give root permissions to an **already** running application, not to start an application with su privileges!

Thanks again.

---

### Post by sisco311 on 2012-01-07
USC uses polkit: [http://hal.freedesktop.org/docs/polkit/](http://hal.freedesktop.org/docs/polkit/)

If it's a CLI app, then you could make it setuid root: [http://en.wikipedia.org/wiki/Setuid](http://en.wikipedia.org/wiki/Setuid)

---

### Post by hakermania on 2012-01-07
Thanks a lot for any answers :)

---

