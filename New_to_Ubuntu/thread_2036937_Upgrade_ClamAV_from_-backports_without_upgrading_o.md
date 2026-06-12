---
title: "Upgrade ClamAV from -backports without upgrading other packages"
date: 2012-08-03
forum: New to Ubuntu
---

### Post by Nap_BlownApart on 2012-08-03
I want to setup CRON to automatically update ClamAV at regular intervals.  The problem I'm having is working out how to make *aptitude* or *apt-get* do it.
Since I'm using the -backports repositry, I don't want to upgrade all packages that are available, only ClamAV.

I'm using a script as follows:```
#!/bin/sh
aptitude -q update
aptitude -q safe-upgrade clamav clamav-daemon
```

I get an error saying safe-upgrade doesn't accept arguments.
Can anyone correct my script to make it work as I would like?

Cheers,
Nap

---

### Post by Paqman on 2012-08-03
You can just use "install", if there's a newer version available it'll upgrade it (since an install and an upgrade are essentially the same thing).

However, you can also just set your package manager to [automatically install all security updates]("https://help.ubuntu.com/community/AutomaticSecurityUpdates/").

---

### Post by Nap_BlownApart on 2012-08-03
paqman,  thnx.
  I've gone with the install method.  It was a bit simpler to understand.
  I also found a useful update/scan script at [http://code.google.com/p/clamav-cron/]("http://code.google.com/p/clamav-cron/") which sends an email report to nominated recipients.  A target folder can be specified for the scan.  But for ubuntu users, the /bin/mail at the end of the script needs to be changed to /usr/bin/mail.
I created two scripts out of this one; one for the update, one for the scan.  And I run them on different cycles.

Cheers,
Nap

---

