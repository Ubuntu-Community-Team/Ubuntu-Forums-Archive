---
title: "How to verify ntpd runs as root or non-root?"
date: 2016-03-25
forum: New to Ubuntu
---

### Post by zephyr2 on 2016-03-25
TL;DR - Does 'ntpd' run as non-root by default in Ubuntu and, if so, how can I verify that?


I’m still new to Linux & computing in general but getting more comfortable with CLI all the time. I know I only understand very little about security, but the internet is a threatening place so i’m doing my best to learn and close unnecessary holes where I can. :)

I’ve been reading about security vulnerabilities that have cropped up in ntp over the last 24 months and wondered how severely these might potentially impact “regular” end-user, ntp clients. And apparently until 2005 or so ntp *was* [run as root in Debian]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=282941"), at least on ntp-server. 

Anyway, it’s not clear to me whether Ubuntu followed suit, since I see people asking about the security of 'ntpd' and getting answers suggesting [running it as non-root]("http://askubuntu.com/questions/635899/why-ntpd-needs-an-open-port/635968#635968") (implying that’s a non-standard thing to do?). 

I’d feel a lot better about the default ntp setup on my machine if I could verify it was running as non-root user and so was limited in the damage it could do. Can anyone kindly explain how I can do this verification?

Thanks!


Bonus question: checking Synaptic, I see I have 'ntpdate' on my laptop, as well. I'm sure I read somewhere that ntpdate is deprecated, though; I imagine this means it won't get support going forward / I'm better off removing it entirely from my system?

---

### Post by sandyd on 2016-03-25
> **zephyr2 said:**
> TL;DR - Does 'ntpd' run as non-root by default in Ubuntu and, if so, how can I verify that?


I&#8217;m still new to Linux & computing in general but getting more comfortable with CLI all the time. I know I only understand very little about security, but the internet is a threatening place so i&#8217;m doing my best to learn and close unnecessary holes where I can. :)

I&#8217;ve been reading about security vulnerabilities that have cropped up in ntp over the last 24 months and wondered how severely these might potentially impact &#8220;regular&#8221; end-user, ntp clients. And apparently until 2005 or so ntp *was* [run as root in Debian]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=282941"), at least on ntp-server. 

Anyway, it&#8217;s not clear to me whether Ubuntu followed suit, since I see people asking about the security of 'ntpd' and getting answers suggesting [running it as non-root]("http://askubuntu.com/questions/635899/why-ntpd-needs-an-open-port/635968#635968") (implying that&#8217;s a non-standard thing to do?). 

I&#8217;d feel a lot better about the default ntp setup on my machine if I could verify it was running as non-root user and so was limited in the damage it could do. Can anyone kindly explain how I can do this verification?

Thanks!


Bonus question: checking Synaptic, I see I have 'ntpdate' on my laptop, as well. I'm sure I read somewhere that ntpdate is deprecated, though; I imagine this means it won't get support going forward / I'm better off removing it entirely from my system?

By default, Ubuntu does not use ntpd (ntp package), and uses ntpdate. If ntpd is installed from the ntp package, it runs as the 'ntp' use, not root. From [https://launchpad.net/ubuntu/trusty/+package/ntpdate](https://launchpad.net/ubuntu/trusty/+package/ntpdate), it seems that the reason why ntpdate is used is due to the fact that the Ubuntu installation may not always have network access, so the use of ntpdate may be more accurate.

As to why ntpdate is no longer used, see [http://support.ntp.org/bin/view/Dev/DeprecatingNtpdate](http://support.ntp.org/bin/view/Dev/DeprecatingNtpdate) . That being said, ntpdate is part of the same source package as ntpd,

---

### Post by SeijiSensei on 2016-03-26
As sandyd says, ntpd runs as an unprivileged user, but it needs to be started as root.  Since Ubuntu is designed primarily for client workstations, it used ntpdate to contact one or more NTP servers, but doesn't include the ntpd server software by default.  

Programs like ntpd are started at boot time by the root user.  For better security, the initial root-owned process then changes its user and group IDs to that of the "ntp" user so if it were somehow compromised, the attacker could not get root privileges.  Some programs like the Apache web server keep a root-owned "stub" running after execution and spawn unprivileged listeners running as an ordinary user.  Attackers can only talk to the listeners and not the stub.

---

### Post by zephyr2 on 2016-04-01
Sorry this is so late--got tied up. I'll mark this as 'solved' since the question is moot and you've both explained why. 

Thank you both, sandyd and SeijiSensei, for making this clear! I do appreciate the straightforward responses. :-)

(ps - SeijiSensei: is "Mononoke" in your profile a ref. to Miyazaki's  *Princess Mononoke*?  Either way, it's making me want to see that film again. Cheers!)

---

### Post by SeijiSensei on 2016-04-01
That's my favorite of Miyazaki's works, but it really refers more to this: [http://www.crunchyroll.com/mononoke/](http://www.crunchyroll.com/mononoke/).

---

