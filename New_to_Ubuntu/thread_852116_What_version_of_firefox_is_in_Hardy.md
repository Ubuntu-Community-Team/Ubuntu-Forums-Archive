---
title: "What version of firefox is in Hardy?"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by l951b951 on 2008-07-07
I just upgraded from Dapper to 8.04 using the update manager upgrade button.

I previously had used Ubuntuzilla to enable and use Firefox 2.  After the upgrade, I opened my firefox and everything seems the same including all my addons.  The Help->About lists my version as 2.0.0.13

Is that the correct version that comes with 8.04 or is this the Ubuntuzilla version?

---

### Post by hyper_ch on 2008-07-07
hardy uses FF 3 but you might need to replace it first because you still have FF 2 from dapper.

---

### Post by kansasnoob on 2008-07-07
I'd try just going to synaptic and searching for firefox. By default (look at my software sources screenshots below) I have the following packages ticked in synaptic:

firefox
firefox-3.0
firefox-3.0-gnome-support
firefox-gnome-support
ubufox

[ATTACH]76747[/ATTACH]

[ATTACH]76748[/ATTACH]

[ATTACH]76749[/ATTACH]

The reason I stress my "software sources" is that whatever version of FF3 I have is extremely stable!

---

### Post by Kevbert on 2008-07-07
If you open Firefox and select Help, About, it should tell you.

---

### Post by nanotube on 2008-07-07
> **l951b951 said:**
> I just upgraded from Dapper to 8.04 using the update manager upgrade button.

I previously had used Ubuntuzilla to enable and use Firefox 2.  After the upgrade, I opened my firefox and everything seems the same including all my addons.  The Help->About lists my version as 2.0.0.13

Is that the correct version that comes with 8.04 or is this the Ubuntuzilla version?

it's probably the ubuntuzilla version.
to make sure, see what /usr/bin/firefox points to:
```
ls -al /usr/bin/firefox
```

---

### Post by l951b951 on 2008-07-07
> @linuxbox:~$ ls -al /usr/bin/firefox
lrwxrwxrwx 1 root root 20 2007-08-19 11:03 /usr/bin/firefox -> /opt/firefox/firefox



I would imagine this is the Ubuntuzilla version.  How do I get rid of it and go with FF3?  I will try simply installing it using the package manager.

Edit: firefox 3 is installed, but all my firefox shortcuts point to the ubuntuzilla version.  How do I get rid of the ubuntuzilla version and make firefox 3 my browser.  When I am in terminal, and type "firefox", version 2.0.0.13 opens still.

---

### Post by nanotube on 2008-07-07
> **l951b951 said:**
> I would imagine this is the Ubuntuzilla version.  How do I get rid of it and go with FF3?  I will try simply installing it using the package manager.

Edit: firefox 3 is installed, but all my firefox shortcuts point to the ubuntuzilla version.  How do I get rid of the ubuntuzilla version and make firefox 3 my browser.  When I am in terminal, and type "firefox", version 2.0.0.13 opens still.

run:
```
ubuntuzilla.py -a remove -p firefox
```

that will set things back to "default".

---

### Post by l951b951 on 2008-07-07
That did it.  thank you.

---

### Post by nanotube on 2008-07-07
> **l951b951 said:**
> That did it.  thank you.

cool :) you're welcome :)

---

