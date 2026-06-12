---
title: "Unlock Keyring"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by Norfolk 'n' Good on 2008-07-26
Hi

Each time I log onto Ubuntu I get a message box...

```

Unlock Keyring

**Enter password for default keyring to unlock**

The application 'nm-applet (/usr/bin/nm-applet) wants access to the default keyring, but it is locked

```

(a) How do I stop this appearing every time?

(b) What is it and what is this business with keyrings?

Regards

---

### Post by Pro-reason on 2008-07-26
It's generally to do with [GPG]("http://en.wikipedia.org/wiki/GNU_Privacy_Guard").  Applications that use GPG include Thunderbird Enigmail, Seahorse, and KGPG.

I suspect that your desktop is set to "save session", and therefore some program that you had open is reopening.

---

