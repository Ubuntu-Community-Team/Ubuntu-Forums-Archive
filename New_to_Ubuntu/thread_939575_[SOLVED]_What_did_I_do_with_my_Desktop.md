---
title: "[SOLVED] What did I do with my Desktop?"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by Qrikko on 2008-10-06
Hi,

well, in short: my desktop stoped working.

in a bit more detail, nothing with the desktop interaction work (i.e. no menu on rightclick, no icons, no ALT-F1.. and so on)

I think I might have stoped something in session that could be the reason, and it work for other users, I created a dummy so it's not anything in the system.. I just did something clumsy I think..

what I suspect is either that it was something I took away from the session. But it could also be that I by mistake kind of moved the Desktop folder :$ I moved it on mistake and just moved it back. after it to be sure I did a:

```

sudo chmod 755 ./Desktop/
sudo chown user ./Desktop/

```

But well I just don't know what it is.. I guess if I don't find the answere here I maybe have to check the other user for Nautilus (guessing) related things in the session for the dummy and try to fix it that way.

Thanks

---

### Post by rybaxs on 2008-10-06
No message

---

### Post by terrorsathan on 2008-10-06
Hi,

maybe you killed nautilus. Hit ALT+F2, enter nautilus and hit Enter.
If that doesn't work I'm sure that you or some script changed something on the Nautilus configuration.
Try the following:
Hit ALT+F2, enter gconf-editor and hit Enter. In the editor which opens go to / > apps > nautilus > preferences and tick the property show_desktop.
Instead of doing that you could also enter the following in a terminal and hit enter:
```
gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop 1
```

After that, if the desktop still doesn't show up, try once again hitting ALT+F2, enter nautilus and hit Enter. This will restart nautilus, which includes the desktop manager.
I think this should work.

Regards,
terrorsathan

---

### Post by Qrikko on 2008-10-06
Thanks :)

I figured it out it was that I removed the start-up of nautilus from the default session. so if I run just "nautilus" from a terminal I get my desktop and functionality back.

So I added in the start-up of nautilus to my default session again. Thank you for the answers.

I thought that nautilus was running, because I could check through folders and stuff.. I guess that my terminology about nautilus was a bit misdirected :)

---

### Post by terrorsathan on 2008-10-06
No problem ;)

> **Qrikko said:**
> I guess that my terminology about nautilus was a bit misdirected :)

Well to be honest the whole nautilus thing is quite confusing :D

Regards,
terrorsathan

---

### Post by Qrikko on 2008-10-06
Haha, yes :P I didn't know that it integrate into the system a bit more.. I thought it was pretty much just a browser.. but I guess it is working a bit deeper :)

anyhow thanks again, was a very small problem, but sometimes it's just hard to know where to start :)

---

