---
title: "How to uninstall packages? Remnants of uninstalled programs"
date: 2019-11-03
forum: New to Ubuntu
---

### Post by indognito on 2019-11-03
I have recently downloaded Ubuntu linux to learn. I uninstalled two programs. After uninstalling with purge I used the command "locate" to see if the packages were uninstalled properly.
It was able to find remnants of both programs.
After a lot of browsing I was able to do multiple things that seemed to erase the first one until I couldn't find any more traces. The second one still has remnants left.
What is happening here? Why is it so hard to completely uninstall packages?
The first was rocketchat and the second was sendmail.
Thanks

example
locate sendmail
/etc/fail2ban/action.d/sendmail-buffered.conf
/etc/fail2ban/action.d/sendmail-common.conf
/etc/fail2ban/action.d/sendmail-geoip-lines.conf
/etc/fail2ban/action.d/sendmail-whois-ipjailmatches.conf
/etc/fail2ban/action.d/sendmail-whois-ipmatches.conf
/etc/fail2ban/action.d/sendmail-whois-lines.conf
/etc/fail2ban/action.d/sendmail-whois-matches.conf
/etc/fail2ban/action.d/sendmail-whois.conf
/etc/fail2ban/action.d/sendmail.conf
/etc/fail2ban/filter.d/sendmail-auth.conf
/etc/fail2ban/filter.d/sendmail-reject.conf
/usr/lib/python3/dist-packages/fail2ban/tests/files/logs/sendmail-auth
/usr/lib/python3/dist-packages/fail2ban/tests/files/logs/sendmail-reject
/usr/share/perl5/Mail/Mailer/sendmail.pm
/usr/share/sosreport/sos/plugins/sendmail.py
/usr/share/sosreport/sos/plugins/__pycache__/sendmail.cpython-36.pyc

---

### Post by deadflowr on 2019-11-04
None are sendmail package related.

You have fail2ban, sosreport, and a common perl-based package installed.
Each has sendmail related configuration files,
but those files are not in anyway related to sendmail the package.

---

### Post by indognito on 2019-11-04
Thanks for your answer. 
Could you please explain a bit further?
Sendmail configuration packages...? Do you mean that when I installed fail2ban it contains config files for sendmail in the case I chose to install and use it alongside of fail2ban?

---

### Post by deadflowr on 2019-11-04
>  Do you mean that when I installed fail2ban it contains config files for sendmail in the case I chose to install and use it alongside of fail2ban?

Yes, more or less.
same for sosreport and same for that perl-based package: libmailtools-perl

---

### Post by Skaperen on 2019-11-04
the "[COLOR=#0000cd][FONT=courier new]**locate**[/FONT][/COLOR]" command tells you information it gets from a database that is usually updated daily.  it will show file names up to a day after they are gone.  do "[COLOR=#0000cd][FONT=courier new]**ls**[/FONT][/COLOR]" with the names you see to detect if they are actually there.

---

### Post by indognito on 2019-11-04
Thanks

---

