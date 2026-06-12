---
title: "Removing password promt for single application?"
date: 2012-01-25
forum: New to Ubuntu
---

### Post by hkarn on 2012-01-25
So I found a lot about removing the gksudo password prompt altogether but not how to do it for a single program.

I have an application that launches on start-up and need root privileges. So now every time I boot my laptop it is first the drive encryption password, then the Ubunutu account login and then the password again to give root privileges to the program. So yeah it gets annoying...

The program is openvpn tunnel from mullvad.net

It's launchfile is /usr/bin/mullvad and look like this:

#!/bin/sh

gksudo -k /usr/share/mullvad/mullvad.py

So is there something I can do to permanently remove the password challenge for this only but keep it for everything else?

---

### Post by Lars Noodén on 2012-01-25
> **hkarn said:**
> So is there something I can do to permanently remove the password challenge for this only but keep it for everything else?

Yes.  You can edit /etc/[sudoers](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sudoers.5.html)

```

%hkarn ALL=(ALL) NOPASSWD: /usr/share/mullvad/mullvad.py

```

If you do not want to allow parameters to be passed, then add empty quotes at the end.

```

%hkarn ALL=(ALL) NOPASSWD: /usr/share/mullvad/mullvad.py ""

```

[sudoers](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sudoers.5.html) can also handle regular expressions.

---

### Post by hkarn on 2012-01-25
I did that with and without "" and I don't get a password prompt anymore ... also the program won't start anymore ...

I remove the line again and it works fine. But with it mullvad only show up briefly in ps, it doesn't start the gui then shuts itself down again

---

