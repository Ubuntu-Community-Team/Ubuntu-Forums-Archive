---
title: "how to block firefox bowser from launching"
date: 2009-02-13
forum: Philippine Team
---

### Post by Script Warlock on 2009-02-13
mga boss gusto ko sana e-block or lockdown lang ang firefox from launching sa net possible ba yun?..para sa server lang na ginamit ko sa shop at para naman CCL lang ang nakabukas..i tried to hide from the menu pero naopen pa rin thru terminal...any ideas?:confused:

---

### Post by Jucato on 2009-02-13
Not sure if this will actually work, but perhaps you can try removing the executable permission from the firefox binary.

Or better yet, use some form of ACL (Access Control List), like putting all those users under a group that cannot execute certain binaries.

Both ways are sort of hacky, the first one probably being the worse. There might be some "lockdown" or "kiosk" software that can be used with Ubuntu.

---

### Post by Script Warlock on 2009-02-13
merong r-kiosk pero hindi ang tamang solusyon ewan kung pwede ba to mablock ng firestarter or iptable pero naka ics ako ngayon bka apektado ang mga workstations tska di pa ako masyado kabisado sa mga iptables....kakatakot kulikutin...actually di naman kailangnan ang web browser sa server except lang kung ma-mount ko na zoneminder.

---

### Post by Script Warlock on 2009-02-15
oh, i got the workaround!....can we mark this thread solve...

ginawa ko lang sa option ng firefox sa banda advance>>network>>settings>>>  ginawa ko manual proxy tapos socks: _localhost_ tapos port is _9999_ tapos no proxy at _localhost 127.0.0.1_... the result is blank page ang makikita or error lahat url...then after everything download ko ang public fox tapos disable lahat options ng firefox tapos nilagyan ko ng impossibleng password(not even mitznik can crack the password)hehheeh...solve:KS

---

