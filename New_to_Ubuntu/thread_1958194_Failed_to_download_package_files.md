---
title: "Failed to download package files"
date: 2012-04-13
forum: New to Ubuntu
---

### Post by DankVantam on 2012-04-13
I have had Ubuntu 11.10 installed for several months with no major issues.  I have had no problems updating or installing any files until this week.  This week, I was in a Microsoft class and was using the wireless connection there which showed up as unsecured but required a log on to a portal to enter a user name and password.  I have had no problems with VPN or Internet but I have not been able to update any files or install any applications since the class.  When I attempt to install anything via the Ubuntu Software Center, I get a generic error message 'Failed to download package files'.  Also, I last updated my system 3 days ago but when I go to update, it shows that I last updated 44 days ago.  After checking the forums, I saw that some people recommended running apt-get update.  When I do that, I get this error message:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/Release](http://security.ubuntu.com/ubuntu/dists/oneiric-security/Release)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release](http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.


At this point, I am not able to update or install anything.  Any ideas what I can do?

---

### Post by cortman on 2012-04-13
Hi,

You're on the right track with the apt-get update command. Please post the full output, wrapped in [CODE] tags- the tags are the hash mark (#) in the reply box editing toolbar.

---

### Post by oldos2er on 2012-04-13
[http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html)

---

### Post by DankVantam on 2012-04-14
> **oldos2er said:**
> [http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html)
Using method 1 as described in the link worked like a charm.

Thanks for your help.

---

### Post by oldos2er on 2012-04-14
You're welcome. Would you please mark the thread as 'Solved' under Thread Tools? Thanks.

---

### Post by mccartyj on 2012-04-18
Worked for me too! Thanks, Ann!

:guitar:

---

