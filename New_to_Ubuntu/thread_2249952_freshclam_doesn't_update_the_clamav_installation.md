---
title: "freshclam doesn't update the clamav installation?"
date: 2014-10-25
forum: New to Ubuntu
---

### Post by haplorrhine on 2014-10-25
Freshclam repeatedly says the ClamAV installation is outdated, but not main.cvd, bytecode.cvd, or daily.c[v,l]d.  So freshclam only updates the databases and not the installation?  Is updating the installation important?

sudo freshclam -v [verbose]

```

Current working dir is /var/lib/clamav
Max retries == 5
ClamAV update process started at Sat Oct 25 15:01:18 2014
Using IPv6 aware code
Querying current.cvd.clamav.net
TTL: 819
Software version from DNS: 0.98.4
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.98.1 Recommended version: 0.98.4
DON'T PANIC! Read http://www.clamav.net/support/faq
main.cvd version from DNS: 55
main.cvd is up to date (version: 55, sigs: 2424225, f-level: 60, builder: neo)
daily.cvd version from DNS: 19536
daily.cld is up to date (version: 19536, sigs: 1229828, f-level: 63, builder: neo)
bytecode.cvd version from DNS: 242
bytecode.cvd is up to date (version: 242, sigs: 46, f-level: 63, builder: dgoddard)

```

---

### Post by ajgreeny on 2014-10-25
The application version is much less important than the virus signatures so don't worry.

Do you really neeed a virus checker?  Normally for a simple desktop system which is not being used as a server, eg mail-server or web-server, a virus checker is superfluous.

See:-
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

I have not used any virus checkers since I stopped using windows in about 2006, and have never seen any virus/malware problems of any sort.

---

### Post by haplorrhine on 2014-10-25
Thanks ajgreeny.  I don't think I've ever discovered infected files, but it's not burdensome to do.

sudo clamscan -r /

Then I just do whatever while it scans the entire system.

---

